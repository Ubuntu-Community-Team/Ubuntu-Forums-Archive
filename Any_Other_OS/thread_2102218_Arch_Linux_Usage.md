---
title: "Arch Linux Usage"
date: 2013-01-06
forum: Any Other OS
---

### Post by ProxyCyber on 2013-01-06
I just installed the "text-based" operating system. Arch Linux. When it starts up, a terminal-like things pops up, well... because that's your computer. My question is, what is the CODE to install a browser (doesn't matter which... just need a code.) Also, what is the code to access "My Files" or "My computer."?   Thanks a lot!

---

### Post by Björn on 2013-01-06
Hi, if you want a normal browser you will have to install a graphical interface and window manager etc. (xorg and gnome for example). You can also use text based browsers for example links or lynx. The command for installing that would be something like: ```
pacman -S links 
``` you might need to run it as root (type su and enter the root password). 

To go to different directories in any linux shell you type cd _name of directory_ or just cd for your home directory. 

For a better answer i suggest you ask in an arch linux forum, however you might want to ask yourself why you want to have a purely text based OS.

Björn

---

### Post by kevinmchapman on 2013-01-06
No offence, but clearly Arch is not for you. Some basic command line skill and a desire to find things out for yourself are necessary to use Arch. You may be able to get away without the former, but not the latter.

---

### Post by screaminj3sus on 2013-01-06
You should really take a look at the arch wiki, especially the beginner's guide: [https://wiki.archlinux.org/index.php/Beginner%27s_Guide](https://wiki.archlinux.org/index.php/Beginner%27s_Guide)

---

### Post by fantab on 2013-01-06
> **ProxyCyber said:**
> I just installed the "text-based" operating system. Arch Linux. When it starts up, a terminal-like things pops up, well... because that's your computer. My question is, what is the CODE to install a browser (doesn't matter which... just need a code.) Also, what is the code to access "My Files" or "My computer."?   Thanks a lot!

First of all, Arch is not exactly a "text-based". Its installation 'core' is MINIMAL. You won't get any GUI unless "YOU want it". 

Unless there is some special need ARCH is NOT recommended  without Intermediate level know how of Linux command line and Linux itself. Read [**THE ARCH WAY**]("https://wiki.archlinux.org/index.php/The_Arch_Way").

AFAIK, [**LINKS**]("http://en.wikipedia.org/wiki/Links_%28web_browser%29") browser is present in the CORE** Arch install.**  For more [**READ HERE**]("https://wiki.archlinux.org/index.php/Beginners%27_Guide") and get yourself on the [**ARCH FORUM**]("https://bbs.archlinux.org/").

Good Luck...

---

### Post by mips on 2013-01-07
My suggestion is to go read the wiki, especially the beginners guide or move to another distro.

---

### Post by kazuya on 2013-01-09
It is also not a bad idea to start with Manjaro linux which is based on arch linux, but comes with a graphical package manager, but also gives you the option to use the commandline to install and do stuff.
 
to install a browser or something in arch install.
 
pacman -Syu
pacman - S firefox
pacman -S midori
 
Arch install does not even have X or a graphical desktop installed by default
pacman -S xfce4 lxde 
 
Have to add gdm or ldm or kdm. - refer to Archlinux Beginner Guide.
 
With Manjaro, you can learn these at your pace without having to go through these tedious steps. Doing these tedious steps help you master and learn your system better on the long run.

---

### Post by viperdvman on 2013-01-10
I went with straight Arch Linux as my first venture into the Arch community. I didn't play with Cinnarch nor Manjaro first *(Chakra doesn't count since it's forked from Arch)*. Following the begginers wiki, installation wiki, and advice from a friend in a Nintendo-themed IRC chat who's also an Arch user, helped me to get Arch running.

It's always best to get the core system running first as the wikis point out. Once you have a working Arch install that boots into command line every time, then you can install the desktop environment of your choice (GNOME, KDE, Xfce, LXDE, openbox, E17, whichever). 

Do read the Arch Wiki and search the desktop environment of your choice. After you finish everything in the begginers wiki, installation wiki, or both... then read through the article on your desktop environment of choice before installing it. The Arch Wiki is very informative, and helps people new to Arch with getting a working system.

Good luck with Arch, and don't let anyone try to turn you away from it 'cause you're a noob when it comes to Arch. These forums have a number of Arch users who are hardcore into Arch who'd be glad to help you :)

---

### Post by mamamia88 on 2013-01-10
Well arch doesn't seem for you but you managed to get it installed so i'll try and help.  pacman -S links or elinks for text browser.  you might want to install a gui though.  for browsing files just cd /directory which stands for change directory and then ls -a for listing all files.

---

