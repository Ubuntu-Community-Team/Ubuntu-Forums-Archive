---
title: "iPod doesn't display tunes"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by Aholiab on 2007-12-28
I've managed to transfer files to my iPod nano (3rd gen.). At least, that's what Rhythmbox says, and Banshee and gtkpod all agree.

However, when I browse the iPod, nothing is there. I know, this isn't quite an Ubuntu question.

Are these tunes really on my iPod? Why can't I see them?

---

### Post by buckykat on 2007-12-28
my friend has this same problem. apparently, the new database for the nano 3rd gen is way different form the old one and hasn't yet been reverse-engineered to work with non-itunes programs.

---

### Post by metalpancake on 2007-12-28
is it possible to put videos on a video ipod using rythmbox?

---

### Post by glok_twen on 2007-12-29
i am having the same problem. very frustrating. i assume this means we need to use itunes for now until some updates to gtkpod/amarok etc? anyone know whether these changes are being pursued?

---

### Post by glok_twen on 2007-12-30
in case anyone is still looking here are the answers:

[http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)
[http://ubuntuforums.org/showthread.php?p=4027223](http://ubuntuforums.org/showthread.php?p=4027223)
[http://ubuntuforums.org/showthread.php?t=650094](http://ubuntuforums.org/showthread.php?t=650094)

---

### Post by Aholiab on 2007-12-30
Concerning the notes at [http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)

I installed the following two packages, but in the reverse order:

libgpod-dev_0.5.3+actually0.6.0-0.1_i386.deb
libgpod2_0.5.3+actually0.6.0-0.1_i386.deb

Then I tried to execute the following as described for my context:

/usr/bin/ipod-read-sysinfo-extended [/dev/xxxx] /media/IPOD

But here I’m getting this error:

Couldn’t write SysInfoExtended to /media/PL_iPod

Can anyone help?

---

### Post by glok_twen on 2008-01-01
have you tried preceding the command with sudo?

---

### Post by Aholiab on 2008-01-01
Yes. Note that I entitled my iPod "Phil’s iPod" in iTunes (my daughter's Mac), but apparently it's mounted at /media/disk. So here's what I got:

phil@Phil-VAIO:~$ sudo "/usr/bin/ipod-read-sysinfo-extended /dev/sdb2 /media/Phil’s iPod"
[sudo] password for phil:
sudo: /usr/bin/ipod-read-sysinfo-extended /dev/sdb2 /media/Phil’s iPod: command not found
phil@Phil-VAIO:~$ /usr/bin/ipod-read-sysinfo-extended /dev/sdb2 /media/disk
Couldn't write SysInfoExtended to /media/disk
phil@Phil-VAIO:~$ sudo /usr/bin/ipod-read-sysinfo-extended /dev/sdb2 /media/disk
Couldn't write SysInfoExtended to /media/disk

---

### Post by ryanVickers on 2008-01-01
> **buckykat said:**
> my friend has this same problem. apparently, the new database for the nano 3rd gen is way different form the old one and hasn't yet been reverse-engineered to work with non-itunes programs.

It's not that they haven;'t tried, it's quite the opposite actually... As far as I know, they have tried very hard to make an iPod only work with iTunes, and iTunes only detect iPods... :p

Apple locks you into the proprietary thing almost as much as micro$oft, but at least your locked into good products ;)

---

### Post by glok_twen on 2008-01-01
aholiab - do you use kde? the one thing i'd try next is to open a knoqueror window and navigate upward until you see a device icon for your mounted ipod. if you right click on it and look at the various tabs (i think the 3rd one over), you can see for certain which /dev it is, and also which mount point eg /media...

nautilus very likely has a similar feature but i haven't checked it.

---

### Post by Aholiab on 2008-01-01
I'm using Gnome. The developer of Floola tells me that at least one of my problems is that my iPod is formatted on a Macintosh. I can read files, but I cannot write to the iPod. So I'm going to reformat it in Windows ASAP.

---

