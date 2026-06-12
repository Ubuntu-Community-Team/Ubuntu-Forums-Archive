---
title: "how do you write a bash script ot run several commands"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2006-07-19
kind of like the old dos batch files? I seem to be able to do it as:
sudo sh filename

This works but i want to see whats happening in my terminal window.

Baasically how do you turn a basic text file into a script? Ideally id like to be able to run it by clicking on its icon.

---

### Post by Kurt` on 2006-07-19
If you start a file off with this line:

!#/bin/bash

Ubuntu will recognize it as a Bash script.

You will also need to set the file to be executable. Open its properties and check off the correct box (or open a terminal and type 'chmod +x filename').

Also, be careful with running scripts as the superuser (via sudo), make sure you know what you're doing, as you could seriously harm your system!

---

### Post by frodon on 2006-07-19
To make a bash script, just start your file by ***#!/bin/bash*** to tell that the following lines use the bash shell syntax.
Then just paste your command lines/script and make the file executable, once done just type the name of the script to launch it (you may need to type the full path of the script).
If you don't want to type the full path of the script put it in /usr/bin.

---

### Post by dgrafix on 2006-07-19
Thats the thing, i want to run it as user (theres no need to be root)


Thanks for the tip

---

