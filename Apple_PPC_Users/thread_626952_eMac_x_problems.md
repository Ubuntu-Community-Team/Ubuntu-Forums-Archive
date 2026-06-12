---
title: "eMac x problems"
date: 2007-11-29
forum: Apple PPC Users
---

### Post by dcast on 2007-11-29
Hi, I just acquired an eMac and I want to run linux on it, Ubuntu preferably, but I am open to other distributions. I am having trouble with x on the live cd. The only one I have right now is 6.06 ppc, it boots fine with the loader, but x is disabled when gdm would start. It is a 1ghz G4, with a Radeon 9200 video card, according to what a reconfigure of x autodetects. What do I need to change to get it running? Thanks for all your help!

Dcast.

---

### Post by dcast on 2007-11-29
Update: I just tried 7.10, same problem. Hope someone can come up with a solution for this! Thanks, David Castle

---

### Post by frog_pilot on 2007-11-30
I dont know if this helps, but on 7.04 there was a problem with the adressing of the VRAM by the ati-driver. To fix this issue simply add the line```
Option "NoInt10" "yes"
```to the xorg.conf driver section. that it looks like this:
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon RV250 If [Radeon 9000 Pro]"
	Driver		"radeon"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"	"false"
	Option		"NoInt10"	"yes"
EndSection
```

---

### Post by Auria on 2007-11-30
on eMac you need to change some monitor settings. i don't remember them though, but with the search featrue (or with a knowledgeable person) it should be possible

---

### Post by oswaldkelso on 2007-12-01
> **Auria said:**
> on eMac you need to change some monitor settings. i don't remember them though, but with the search featrue (or with a knowledgeable person) it should be possible


Lots of ppc stuff here


[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

go to the X11 directory

CODE: cd /etc/X11

Backup your xorg.conf file

CODE: sudo cp  xorg.conf xorg.confbackup

edit the original file

CODE:sudo nano xorg.conf

If you have an emac change settings to 71-73 for vertical and 70-140 horizontal

control x to write to the file Y to save

restart (I cant remember the restart x command off the top of my head. anyone?)

CODE: sudo shutdown -r now

My debian how to if it all goes awol it also has lots of little ppc bits n bobs many will be relevant to ubuntu

[http://www.my2bits.org/?p=76](http://www.my2bits.org/?p=76)

---

### Post by dcast on 2007-12-01
Hey guys, thanks for all the suggestions, but I am going to have to hand this one to openSUSE 10.3, it worked almost flawlessly right off the bat (other than 3d support and sound). Thanks,

Dcast.

---

