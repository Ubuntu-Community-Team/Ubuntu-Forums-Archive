---
title: "copy installation from one system to another?"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by eilu on 2006-12-14
I *might* be getting a laptop for the holidays (go me! :D) so I want to know: is there a way I can "copy" my current Ubuntu installation from my PC to the laptop? I'm thinking of the kernell updates, the drivers, applets, etc. that I have installed on this one that I won't have on the new system... and all the hours it'll take me to download everything going since I'm on dial-up.

So far, I have: 
[LIST]
[*]the "automatically turn on numlock" thingy... forgot what it's called
[*]GNOME PPP
[*]kernell update(s)
[*]Wine
[*]HPLIP 1.6.10; Gutenprint
[*]Gaim beta
[*]Flash plugin 9 d78
[*]Gwget
[*]Automatix- plus its configurations for playing MP3's and aother sound files
[*]Some games- not essential but very nice.
[*] M$ core fonts
[*]and every dependency these files have.
[/LIST]

Does Synaptic store the debs soemwhere before it installs them? Wouldn't mind manually installing everything, it's the download times I loathe. Or will it be better if I grab a new liveCD of dapper/edgy (semi-related question: which of these two to pick?)? Will a new liveCD have the new kernels in it? it's the biggest single file there; I can probably summon the patience to download the rest.

---

### Post by xyz on 2006-12-14
> **eilu said:**
> I *might* be getting a laptop for the holidays (go me! :D) so I want to know: is there a way I can "copy" my current Ubuntu installation from my PC to the laptop? I'm thinking of the kernell updates, the drivers, applets, etc. that I have installed on this one that I won't have on the new system... and all the hours it'll take me to download everything going since I'm on dial-up.

So far, I have: 
[LIST]
[*]the "automatically turn on numlock" thingy... forgot what it's called
[*]GNOME PPP
[*]kernell update(s)
[*]Wine
[*]HPLIP 1.6.10; Gutenprint
[*]Gaim beta
[*]Flash plugin 9 d78
[*]Gwget
[*]Automatix- plus its configurations for playing MP3's and aother sound files
[*]Some games- not essential but very nice.
[*] M$ core fonts
[*]and every dependency these files have.
[/LIST]

Does Synaptic store the debs soemwhere before it installs them? Wouldn't mind manually installing everything, it's the download times I loathe. Or will it be better if I grab a new liveCD of dapper/edgy (semi-related question: which of these two to pick?)? Will a new liveCD have the new kernels in it? it's the biggest single file there; I can probably summon the patience to download the rest.
Would this help:
[http://ubuntuforums.org/archive/index.php/t-33530.html](http://ubuntuforums.org/archive/index.php/t-33530.html)

---

### Post by pg99 on 2006-12-14
you would also have to make sure you copy the sources.lst file from your current installation if you have modified it

---

### Post by wolf202 on 2006-12-14
this might help

[http://www.wikitut.org/index.php?title=How_to_Clone_a_Ubuntu_Installation](http://www.wikitut.org/index.php?title=How_to_Clone_a_Ubuntu_Installation)

gives you a list of all installed packages and a easy way to que up all the downloads and installs at once.

-wolf

---

### Post by macogw on 2006-12-14
If the target hard drive is the same size or bigger, you can boot from a live cd and use dd to copy the old hard drive (attach it with an external enclosure, but don't mount it) to the new one.  Just open a terminal and type:
dd if=/dev/sda (or whatever the external is called) of=/dev/hda (or whatever the internal is called)

---

### Post by _duncan_ on 2006-12-15
eilu,

All the update packages are stored in '/var/cache/apt/archives' of your current installation. Last time I checked, the files take up about 200-300 MB.

It's just a matter of porting these packages to your new install (to exactly the same folder) by whatever means is convenient to you: burning it to CD, flash drive, etc.

After that, when you update the new installation, synaptic will recognize the existence of these packages and will not download them anymore but instead use it to update the new system.

P.S. It's nice to meet a fellow pinoy here! Mabuhay!

---

### Post by Kazna on 2006-12-15
What if OP just used something like [XXClone](http://www.xxclone.com/) or similar utilities on UBCD?

---

### Post by eilu on 2006-12-16
I think I'll try _duncan_'s method, it sounds exactly like what I want to do. Thanks everyone. I hope Santa briongs me a laptop! :p 

@_duncan_: right back at you :)

---

