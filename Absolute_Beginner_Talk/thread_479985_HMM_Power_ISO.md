---
title: "HMM Power ISO"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Ssj3_man on 2007-06-20
How to I run this program to get it to process my .daa file? I get to run input the file, hit open and then it disappears, like when I minimize a window. Do I have to fetch it from somewhere? :(

---

### Post by wormser on 2007-06-20
I think this [link]("http://www.cyberciti.biz/faq/how-do-i-open-daa-direct-access-archive-files-under-linux-or-unix-oses/") will help you.

---

### Post by Ssj3_man on 2007-06-20
I'm still confused, I don't like Linux to much typing and they mix in the GUI I don't know what they want when I go to execute a simple command.

Open .daa file - Linux only program

Download poweriso here. Or use wget program:
$ wget [http://poweriso.com/poweriso.tar.gz](http://poweriso.com/poweriso.tar.gz)
$ tar -zxvf poweriso.tar.gz
Output:
poweriso

Would some one please type up the code for me to feed into the terminal.

My file is    XPVOL_EN.daa

Maybe I need this 
Extract files/directories from image file

Extract all files and directories in root direcory of /mnt/iso/obsd39/cd39.iso to /tmp recursively:
$ ./poweriso extract /mnt/iso/obsd39/cd39.iso / -od /tmp :(

---

### Post by wormser on 2007-06-20
Try [this]("http://www.cyberciti.biz/tips/extract-convert-mount-iso-bin-daa-nrg.html") gui program.  There are command line directions on how to set up.  Go to Applications> Accessories> Terminal to enter the commands.

---

### Post by shirilover on 2007-06-20
I would try this
```

poweriso convert XPVOL_EN.daa -o XPVOL_EN.iso -ot iso

```
Also, I would copy poweriso to /usr/local/bin

---

### Post by Ssj3_man on 2007-06-21
[QUOTE=
Also, I would copy poweriso to /usr/local/bin[/QUOTE]
 what is this I don't dare navigate pace the desktop I'm afraid I'll give my self a major migraine.

dah I'm a lost cause just help me so I can run my cracked version of windows XP.

ben@one:~$ sudo apt-get install kommander p7zip
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
ben@one:~$ # apt-get install AcetoneISO-6.7.deb
ben@one:~$  apt-get install AcetoneISO-6.7.deb
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ben@one:~$ # rpm -ivh AcetoneISO-6.7.noarch.rpm
ben@one:~$  acetoneiso &
[1] 30118
ben@one:~$ bash: acetoneiso: command not found

Cant wait till i get to the acetoneiso GUI I sort of comprehend it just by looking at it. 
I'm still :( get me out of hear! Please

---

### Post by silverglade00 on 2007-06-21
So let me get this straight... you're upset because you can't understand the instructions that you need to run an illegal copy of a different operating system than the one this forum supports? That's like getting mad at Ford for not explaining the wiring in the steering column of a train you are trying to steal in a manner that you can understand. Maybe you need to find a different hobby. I'm just sayin....

---

### Post by Ssj3_man on 2007-06-21
put a side the fact that what i want is a no no

its just that this OS complicates a rather simple command to other wise execute in windows XP.

---

### Post by Ssj3_man on 2007-06-21
If i can get this _copy poweriso to /usr/local/bin_ I think I'll be set

So whats terminal code for that ?

Or whats the Linux based equivalent of windows explorer so I can find that place and insert a copy? :confused:

---

