---
date: 2024-06-10
authors:
  - Alexander @proofconstruction
  - Valentin Gagarin @fricklerhandwerk
  - Daniel Ramirez @wamirez
myst:
  html_meta:
    "keywords": "tutorial, django, python, requests, nix, nixpkgs"
---

(django-tutorial)=
# Setting up a Django project with Nix

Add brief introduction

## Overview
### What will you learn?
### What do you need?
### How long does it take?



## from bfca97bb3c3d7d88c748d0f7756d9f5f90629608

### Setting up pre-commit hooks in `default.nix`

Set up `npins`, `treefmt` and `nixfmt` in the `default.nix` file.

To ensure correctness and readibility in further commits, enable options such that those found on: [statix](https://search.nixos.org/packages?channel=24.05&show=statix) and [deadnix](https://search.nixos.org/packages?channel=24.05&show=deadnix).

```{code-block} nix
:caption: default.nix
{
  system ? builtins.currentSystem,
  sources ? import ./npins,
  pkgs ? import sources.nixpkgs {
    inherit system;
    config = { };
    overlays = [ ];
  },
}:
let
    programs.statix.enable = true;
    programs.deadnix.enable = true;
  };
in
{
  shell = pkgs.mkShell {
    packages = [
      pkgs.npins
    ];
  };
}
```

## from ef64b1bf15dce496de163fbc3cf177f82ac05bd1
### add .envrc and .gitignore
