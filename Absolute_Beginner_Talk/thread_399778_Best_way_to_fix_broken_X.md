---
title: "Best way to fix broken X"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by doctor bangali on 2007-04-02
Hi,
A couple of times I my X configuration files have mysteriously broken and I get to see an ugly screen informing me about the error upon rebooting.

I searched and found dpkg-reconfigure

So, is 
>sudo dpkg-reconfigure xserver-xorg 

the best way to fix a broken X, or are there better ways.

---

### Post by wpshooter on 2007-04-02
I think that depends on what the problem might be.

As far as the dpkg-reconfigure xserver-xorg command is concerned, I don't know who came up with that idea, but as far as I am concerned it is NOT a good one.  When I have attempted to run this command, it starts displaying a bunch of prompts and asking questions that, IMO, the average user is not going to know how to answer, at least I don't on most of them.  They really need to come up with GUIs to handle the editing of these files with help screens with definitions of the terms in these configuration files and perhaps even suggested answers based on your setup.

Now that I have vented back to your problem.   What brand/model of video card do you have ?

---

### Post by Sammi on 2007-04-02
The xorg.conf file is going to be completely abolished in about a half to one years time when xorg 7.3 is released. Xorg 7.1 is in Edgy, Xorg 7.2 is in Feisty and if we're lucky Xorg.conf will be gone by Feisty +1 when v. 7.3 probably lands.

---

### Post by zorkerz on 2007-04-02
Interesting any idea what will replace xorg?
The best is to have a backup of xorg.conf i would say.

 "dpkg-reconfigure xserver-xorg" does ask alot of questions but if you leave them all at default unless you know not too i find it normally works out well. 

There should be a way to go through the installation setup of xorg again because that only asks about language and somehow automatically fills out the rest of the info.

Does anyone know how xorg is generated on install and if there is a way to do this without installing?

---

### Post by bodhi.zazen on 2007-04-02
Easiest ways to fix X :

[list=number][*]Restore from backup. You did backup a working copy of xorg.conf before you modified it did you not ? If not, open a terminal and type "I will back up system config files before I edit (modify) them" 100 times. Actually if you used gedit (or nano -B) you may have a backup in /etc/X11/xorg.conf~


[*]If not, ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
The -phigh flag selects defaults for everything except resolution and may be easier if you are unfamiliar with all the options available ...[/list]

HTH

---

### Post by zorkerz on 2007-04-02
-phig very handy to know

---

### Post by rafaelpriego on 2007-04-03
> **bodhi.zazen said:**
> 
Restore from backup.
HTH

Quick and stupid question: Once I've broken xorg.conf and when I DO have a backup, how do I fall back to that backup from the terminal? Thanks :)

---

### Post by kinson on 2007-04-03
@rafaelpriego:

```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

Assuming that "xorg.conf_backup" is what you named your backup file. :)

Cheers, hope it helped.
Kinson.

---

### Post by zorkerz on 2007-04-03
if its named otherwise
```
ls /etc/X11/
``` to list all files in the directory. Then replace xorg.conf_backup with the appropriate name.
ls /etc/X11/
Unless you put the backup in some other directory.

---

