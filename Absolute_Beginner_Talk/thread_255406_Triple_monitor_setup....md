---
title: "Triple monitor setup..."
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by Fevvahz on 2006-09-11
Guys,

I'm new to Linux, but Ubuntu has convinced me to give it a go.  I have a triple monitor setup on my XP install using UltraMon.  Now, Linux being Linux, I know I've got to work for my triple monitor goodness.  Now I know that triple monitor is in itself a pretty advanced topic *but* I've done some reasearch, and I know what I need to do, but being new to Linux I dont know how to do it, hence the post in 'Beginners'.

There are another of questions I havem but I'll begin at what I presume will be the beggining, and ask them as each one is resovled in turn if you dont mind? I'm running an Asus Pundit SFF machine which has a Radeon 9100 IGP, and I have a Radeon 9200 PCI card with 2 x outputs which I'm using as well.

Now, firstly, I understand that I need to change the configuration of xorg, specificly xorg.conf.  Now I know where this is, in the \etc\ directory, and I know I need to edit this file.

Ubuntu recognises all of the devices in Device Manager, and I need to add two more entries for the other ATI card like the one below:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9100 A5 (R200 IGP)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection
```

...but, in device manager, the above card isnt listed as its described there, even though its the same card!  Also - I cant find any properties field for any of the devices which lists the BusID.  

Where am I supposed to find this information?

---

### Post by bodhi.zazen on 2006-09-11
LOL :lol:

You will need to write xorg.conf yourself.

Start with dual monitors and then add a third.

You will need a lot of google.

Start here:
[How to Xinerama](https://help.ubuntu.com/community/XineramaHowTo)

Then look here:
[How to Dual Monitor](http://ubuntuforums.org/showthread.php?t=240150)

Then google a little and post specific questions here.

---

### Post by Fevvahz on 2006-09-11
> **bodhi.zazen said:**
> LOL :lol:

You will need to write xorg.conf yourself.

Start with dual monitors and then add a third.

You will need a lot of google.

Start here:
[How to Xinerama](https://help.ubuntu.com/community/XineramaHowTo)

Then look here:
[How to Dual Monitor](http://ubuntuforums.org/showthread.php?t=240150)

Then google a little and post specific questions here.

All the guides I've read, and the two you've posted work on editing the xorg.conf file from the one that Ubuntu generates based on your hardware - sounds like a logical step to me, modifying a known working file!

Well, my first speficic question, as I asked above - how do you know what Bus ID has been assigned to a piece of hardware? I cant find them in Device Manager.

---

### Post by BeeRockxs on 2006-09-11
> **Fevvahz said:**
> 
Well, my first speficic question, as I asked above - how do you know what Bus ID has been assigned to a piece of hardware? I cant find them in Device Manager.

Open a Terminal, and run "lspci".

---

