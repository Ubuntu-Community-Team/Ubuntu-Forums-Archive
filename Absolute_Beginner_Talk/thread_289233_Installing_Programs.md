---
title: "Installing Programs"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Nut on 2006-10-30
hi.
okay, here's the story. i'm trying to connect to the internet via usb network adapter (linksys). i can't install wlassistant or ndiswrapper or any of that without internet, so i downloaded them and put them on a thumb drive and put them on my desktop. so, yeah. i'm a noob. but i know some commands and stuff.

so, i need wlassistant (i think) to help me connect. so how do i install? i mean, it's just a little package box thing with a bunch of files in it. no setup or anything (dur, linux).

what do i need to install to connect to the internet? how do i install it?

note: i can't install from add/remove apps without the internet... so it's no use to me.

---

### Post by Hmarroqu on 2006-10-30
i would say going to device manager to make sure ur adapter is requeknized ( totaly dont know how to spell )then as for the installation of ur program, im mad noob at this as well but shit works wen u just drag and drop in the terminal, i think u use the sudo command first, but im nooobish to so hopefully a leet ubuntu user will help u out more

---

### Post by Nut on 2006-10-30
thanks i'll try it. yes it's recognized.

---

### Post by tronica on 2006-10-30
did you download a .deb, if not that your easiest way to get this installed.

[http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fw%2Fwlassistant%2Fwlassistant_0.5.5-1_i386.deb&md5sum=6d7f2accb86bb10d990f442567557ef5&arch=i386&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fw%2Fwlassistant%2Fwlassistant_0.5.5-1_i386.deb&md5sum=6d7f2accb86bb10d990f442567557ef5&arch=i386&type=main)

put that on you ubuntu machine, just double click it to install it.

---

### Post by aysiu on 2006-10-30
There's something *ndiswrapper*-related on the installation CD: ```
sudo apt-cdrom add
sudo aptitude update
aptitude search ndiswr
```

---

### Post by Nut on 2006-10-30
didn't work... just brought up it's adress or whatever. like home/connor/blah blah blah/.

i tried:
sudo install (adress)
sudo (adress)

does it need to be extracted? i've been doing it while extracted... i'll try with it not.

---

### Post by Nut on 2006-10-30
what's a .deb? and uhhhhh... i tried installing without the program a long time ago... sudo aptitude ndiswrapper etc.. didn't work.

---

### Post by aysiu on 2006-10-30
> **Nut said:**
> what's a .deb? and uhhhhh... i tried installing without the program a long time ago... sudo aptitude ndiswrapper etc.. didn't work.
You have to add your CD-ROM as a source first (since you have no internet).

That's that first command I gave you.

---

