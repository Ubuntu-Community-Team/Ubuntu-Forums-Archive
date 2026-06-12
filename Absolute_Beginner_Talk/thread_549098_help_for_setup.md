---
title: "help for setup"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by leras on 2007-09-12
iam trying to install ubuntu in my laptop i choose the first choice in the install cd and when is loading sudenly is giving me this 
busybox v1.1.3 (debian 1:1.1.3-3ubuntu3)built -in shell (ash)
enter 'help'for list of built in commands
/bin/sh: can't access tty; job control turned off
(initramfs)_

any help what to do the lapto is an hp pavilion 6543ev

---

### Post by Jimmyfj on 2007-09-12
First you can try to start the live cd in safe graphics mode. If this does not help then you might wanna try the alternate install cd.

---

### Post by leras on 2007-09-12
i have try that iam now downloading again ubuntu to burn it again but i think this is not the problem

---

### Post by Sef on 2007-09-12
Read [this post]("http://www.linuxquestions.org/questions/showthread.php?t=474493&page=2") in Linux Questions.

---

### Post by leras on 2007-09-12
ok i follow theese steps


Hi!

I was trying to install kubuntu on my dell laptop but I got the following error message:

BusyBox V1.1.3 (Debian 1:1.1.3 - 3Ubuntu2) built-in shell (ash)
Enter 'help' for a list of built-in commands
/bin/sh: can't access tty; job control turned off
(initramfs)

I used the solution found on [https://bugs.launchpad.net/ubuntu/+bug/99757](https://bugs.launchpad.net/ubuntu/+bug/99757)


The solution was using the F6 boot option and adding the string break=top
It looked than like:
.........quiet splash break=top
After you hit than the enter key the error message appears immediatel.
Type than
modprobe piix
exit

The LiveCD starts now. But It won´t start the graphical interface because the nvidia driver are not yet on the system.
You have to change now the driver to the vesa driver by changing the /etc/X11/xorg.conf with sudo vi /etc/X11/xorg.conf
You will find there the driver "nv" or "nvidia" change they to vesa.
After saving the file start the kde with startx

Greetings
Max

i instaled ubuntu and now
when iboot from my hard drive i have the same error and i do again the same thinks 
(modprobe piix
exit) and ubuntu boots up
so how  can i fix the error

---

