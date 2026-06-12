---
title: "Damn Small Linux"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by OlyPerson on 2007-12-21
Hi.  I want to put DSL on my old computer running Windows 98.  I put the CD for it in and it shows the option to boot from CD or do something else that confused me.  So I clicked boot from CD and all I get is a blank screen.
I looked at [this]("http://damnsmalllinux.org/dsl-hd-install.html") site and it says that I need to make a space for it on my hard drive by partitioning it.
I want to destry 98, so how can I wipe it completly and just use DSL?  How do I go about doing this in Windows 98?  Or do I even need to?

---

### Post by Duck2006 on 2007-12-21
DSL should load in to RAM from there you can partition the hard drive to what you want, if that will not do it for you use gpartde live cd to do it.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by OlyPerson on 2007-12-21
It can load onto my RAM even if I only have 31MB of it?

---

### Post by Duck2006 on 2007-12-21
Not sure how much ram DSL needs to run, but i think 31Mb is to small for it, you will have to go to there web site and look it up there.

---

### Post by OlyPerson on 2007-12-21
> Boot from a business card CD as a live linux distribution (LiveCD)
Boot from a USB pen drive
Boot from within a host operating system (that's right, it can run *inside* Windows)
Run very nicely from an IDE Compact Flash drive via a method we call "frugal install"
Transform into a Debian OS with a traditional hard drive install
Run light enough to power a 486DX with 16MB of Ram
Run fully in RAM with as little as 128MB (you will be amazed at how fast your computer can be!)
Modularly grow -- DSL is highly extendable without the need to customize

That's what it says on it's website.  So I'm assuming it can work on there.

Also, I have 128MB SDRAM PC133, but that computer uses PC100.  I have tried putting the 128 stick in there too, and it wasn't recognized in 98, is that just a Win98 thing or is it not compatable?

---

### Post by Duck2006 on 2007-12-21
> **OlyPerson said:**
> That's what it says on it's website.  So I'm assuming it can work on there.

Also, I have 128MB SDRAM PC133, but that computer uses PC100.  I have tried putting the 128 stick in there too, and it wasn't recognized in 98, is that just a Win98 thing or is it not compatable?

If it's PC100, you can't use PC133 but if it was PC133 you could use PC100.

---

### Post by OlyPerson on 2007-12-21
Dang, that stinks...
So how do I use the gparted disk to make a new partition?  It gives me a bunch of options like ```
GParted- live CD 0.3.4- 10 beta (auto configuraiton)
```
along with a bunch of other things.  What should I select?

---

### Post by CCNA_student on 2007-12-21
Use the configuration that says x86. That was what worked for me. I think that was the second option. I hope that this helps.

   Sin Cere,

   CCNA

---

### Post by CREEPING DEATH on 2007-12-21
PC133 will work just fine in a PC100 machine, I've run a 256MB PC133 in a machine that came with a single 32MB PC66.
You might have to go into the BIOS and enable it though...

CD

---

### Post by OlyPerson on 2007-12-21
How do I enable it in the BIOS?  I have a general idea but I don't want to mess something up.

And when I select the x86 option which is second, it gets caught up on a step that says
 ```
Freeing unused kernal memory: 304k freed
```
What's up with that?  Do I just wait a long time?

---

### Post by OlyPerson on 2007-12-22
Ok, so I can't seem to get GParted to work for me.  What can I do to wipe the hard drive in order to make room for DSL?

---

### Post by Shazaam on 2007-12-22
OlyPerson....
I run damnsmalllinux on an old Compaq LTE5000 with only 16mb of ram so it should run fine on your pc. The only problem you will have is with Firefox as it's memory heavy. Use dillo instead. As to the gparted livecd, when it boots to the options screen choose "Force Vesa" and it will boot. Slow, but it will run.

---

### Post by OlyPerson on 2007-12-22
> **Shazaam said:**
> OlyPerson....
I run damnsmalllinux on an old Compaq LTE5000 with only 16mb of ram so it should run fine on your pc. The only problem you will have is with Firefox as it's memory heavy. Use dillo instead. As to the gparted livecd, when it boots to the options screen choose "Force Vesa" and it will boot. Slow, but it will run.

Ok, I tried that but it still gets hung up on the "Freeing unused kernel memory: 384k freed" step. After that, nothing.

---

