---
title: "Hoary to Breezy and cant logged in"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by webbie180 on 2005-10-08
First time trying to upgrade.  Upon rebooting, saw GNOME display manager and deferred execution scheduler showing failed next to them.  No graphical log-in screen shown.  Is there anyway to rectify this?  At a loss now and have to use another comp to post this.

---

### Post by webbie180 on 2005-10-08
Dying here, pse help.

---

### Post by Jussi Kukkonen on 2005-10-08
Well, in case the install was interrupted for some reason, you could try 
```
sudo dpkg --configure -a
```
to configure everything not yet configured.

If that doesn't work: There have been some serious xorg changes between Hoary and Breezy... Try starting X from command line
```
startx
```
If there are problems you should try reconfiguring the x server
```
sudo dpkg-reconfigure xserver-xorg
```
and maybe your display drivers (if you have something special).

If the problem wasn't X, maybe there is something wrong with gdm. Then you could try 
```
sudo dpkg-reconfigure gdm
```
to force re-configuration.

---

### Post by ubuntu_demon on 2005-10-08
also make sure you don't miss any important packages by (without the $'s) :

$ sudo apt-get update
$ sudo apt-get install ubuntu-base ubuntu-desktop
$ sudo apt-get dist-upgrade

by the way to reinstall a specific package that gives troubles :
$ sudo apt-get install packagename --reinstall

---

### Post by webbie180 on 2005-10-08
I get errors while trying out all the solutions, is there any way to reverse back to Hoary?

---

### Post by ubuntu_demon on 2005-10-08
[QUOTE=webbie180]I get errors while trying out all the solutions, is there any way to reverse back to Hoary?[/QUOTE]
If you can't get it working and do not wish to spend more time on this problem reinstalling is the best solution.

It is not yet recommended to run breezy unless you know what you are doing and you have another OS to work on if necessary (for example dual boot).

But if you want we'll help you get that graphical login screen ==>  First post these errors you tell us about.

---

### Post by Jussi Kukkonen on 2005-10-08
[QUOTE=webbie180]I get errors while trying out all the solutions, is there any way to reverse back to Hoary?[/QUOTE]

Post the error messages webbie, it's probably something that can be fixed...

---

### Post by webbie180 on 2005-10-08
How do I post the error message because I'm using Windows to post this?

---

### Post by Jussi Kukkonen on 2005-10-09
[QUOTE=webbie180]How do I post the error message because I'm using Windows to post this?[/QUOTE]

Well, paper and pen is lo-tech, but works really well to a certain 
point ;) If the messages really are too long to write by hand, 
you'll first need to redirect them to a file and then get them out 
of your ubuntu machine.

**1. Saving standard output and standard error to a file** 
(replace* command* with the whatever you want to run. 
*cmd.log* is the resulting file): 
```
command >cmd.log 2>&1
```

[B]2. Getting the file out of the machine:
[/B]If you dual-boot and if you can write to a fat partition from 
Ubuntu, and read it from windows, then you can just save the log 
files to the fat partition.

If you have a network connection you could 
a) use *w3m* (or another text mode browser) and post the 
messages here
b) mail the messages to yourself (you'll need a text-mode mail 
agent naturally).

[EDIT: I originally posted this message from w3m, so it's possible. w3m is a little different though -- ask if you have problems]

---

