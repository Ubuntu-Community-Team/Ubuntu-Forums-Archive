---
title: "Running Perl scripts (specifically DVDRip)"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by CafeHarrar on 2007-02-26
I'm feeling a little dumb right now...  I am trying to back up a dvd and have installed DVDRip from Synaptic, as recommended at help.ubuntu.com  (I can't seem to get acidrip working properly)  Anyways, I have it and all the dependencies, but I can't figure out how to run it!  I tried alt-f2, entering dvdrip like it says, I have tried adding it to the applications menu with Alacarte, but I can't figure out which file to use as command, including just typing the package name.  This is probably really simple and I'm just having a brain dead day, but thanks for your help!

---

### Post by netkid91 on 2007-02-26
You'll want to use the name of the script file, but make sure to give it execution permission "chmod +x [filename]" or it won't run.

---

### Post by tronica on 2007-02-26
i just installed it with apt-get, and then ran it from the terminal with

> dvdrip

worked fine, try that and see if it outputs any error in the terminal.

---

