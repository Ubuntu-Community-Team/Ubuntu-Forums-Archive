---
title: "The meaning of life game"
date: 2011-02-24
forum: Cafe Games
---

### Post by jazzerit on 2011-02-24
HEAR YE! HEAR YE!

I have invented a way to find out... THE MEANING OF LIFE!

Here's how it works.
1. We start to write a bash script.

2. the next person writes the next line, or adds another word.

3.if anybody posts exit, killall $0, or similar, it automatically counts as while [ -z "$var" ]; do echo "hello world"; var=var; done


You can use any program that comes as default on ubuntu, kubuntu, or xubuntu. That includes calling python or dash, etc. Here goes: (#!/bin/bash is obvious

**if [ "$(whoami)" != god ]; then echo "so, you want to know the meaning of life, huh?"; read answer; else echo "erm... you don't need this."; fi**

GO!

---

### Post by tame_lx_tech on 2011-02-25
cowsay `fortune`

---

### Post by jazzerit on 2011-02-28
We need more! The universe craves more!

So I shall add another.
comm="!!"; if [ "$comm" != "cowsay" ]; then echo "The universe seems broken."; exit 1; else; echo "the universe is working well so far..."; fi

---

