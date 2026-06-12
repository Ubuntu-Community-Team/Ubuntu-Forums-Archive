---
title: "cpanal / plesk"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by conntaxman on 2007-10-15
I installed ubantu lamp instead of the full ubantu. and I am wondering how to get it to show all the files ,like on the server that I am paying for now.
 Would i install ubantu lamp server and then install the PLESK cpanel? and then go from their, so that I could put all my files in the correct folders and give them the correct permissions.
I have  tried windows with apache and it did work somewhat.
  another thing, I thought that the Ubantu "desktop" was more then just firefox. or am I wrong on that.Firefox is good/is that the linux version.
tks
Johnny

---

### Post by jaygo on 2007-10-16
hey johnny
The LAMP server installs without a GUI. In other words, you're stuck with the command line. It sounds like you're new at the linux game, so I'd highly recommend you install a GUI on your LAMP server while you get used to everything. This will let you see the files, move the files, install software, etc. 

After logging into your LAMP, try using apt-get to install a GUI:
```
sudo apt-get update
```
```
sudo apt-get install ubuntu-desktop
```
```
startx
```
 ... this will make your computer run a bit like a standard ubuntu desktop PC. And it should get you started with linux. PLESK & cPanel are non-free software so you won't be able to use them on your LAMP without buying them, as far as I know.

Keep in mind, learning linux and how to manage a LAMP server is a lot at once.

As for ubuntu desktop, it's a full replacement for windows, and comes with a number of programs already installed, such as firefox and openoffice. These are all linux versions of the programs.

I'd highly recommend that you start reading through the [ubuntuguide.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") It covers beginning & advanced topics, so you'll get a lot out of it. Good luck.

---

