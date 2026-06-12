---
title: "Compiling (Myth and others)"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by ryth on 2007-11-24
Hi folks, 

While not an **absolute** beginner per se, I certainly am when it comes to compiling a program that I'd like to install on Ubuntu.

I'm currently running:

7.10 Gutsy AMD-64
ATI X1950
Gnome
Compiz (via XGL)

Essentially I am running into the ATI/MythTV blue-face problem [documented here]("http://www.mythtv.org/wiki/index.php/AtiProprietaryDriver#Wrong_colors").

Now according to that wiki i need to uncommented the mentioned section and then *recompile* myth.

Here are the questions:[b]

1.  By recompiling, do I need to uninstall and re-install the program?
2.  Is there an easy guide/How-To about compiling programs for Ubuntu, or even better one specifically for compiling Myth on Gutsy-64?[/b] (preferrably something step by step)

Thanks for your patience.

r.

---

### Post by Paul820 on 2007-11-24
If you installed the program without making the changes mentioned, and the changes require you to do something to the source code, then yes you will have to remove the program, make the changes and recompile it. It does say comment out a line of code in a cpp file so a recompile is required.

Most of the programs you compile have a file called README or INSTALL in the folder, they are the best instructions about compiling that particular program you are going to get as those were written by the author of that program.

Any other program that don't require specific instructions only need
> ./configure
make
sudo make install

---

