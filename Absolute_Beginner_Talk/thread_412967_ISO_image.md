---
title: "ISO image"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by bluewagon on 2007-04-18
i burned the ISO to my dvdcd, but when i put it in the cd rom and restart nothing ever happens, am i suppose to do something to the ISO? because i dont recall ever doing anything besides just burning it

---

### Post by taurus on 2007-04-18
How did you burn it?  Did you burn it as an ISO image or as a data?  If you look at the content on the CD (from Windows), you should see a bunch of files and directories.  However, if you see only one large file that you downloaded, then you have burnt it wrong.

Also, make sure you go into the BIOS and move CD-ROM to the top of the list in the boot order.

---

### Post by JayTheHun on 2007-04-18
It could be a couple of things:  1)  did you actually "burn an ISO image" or just burn the .iso file onto a DVD/CD? and 2) your computer's BIOS setup might not be set to boot off of CD first.

---

### Post by bluewagon on 2007-04-18
just the ISO image is on the cd, none of the files or anything.. how do i burn it properly?

---

### Post by JayTheHun on 2007-04-18
> **bluewagon said:**
> just the ISO image is on the cd, none of the files or anything.. how do i burn it properly?

Check around the menus of your burning software.  Look for something like "Burn ISO image."

---

### Post by kpkeerthi on 2007-04-18
Right click on the iso file in nautilus and select burn.

This may help if you are using windows... [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by bluewagon on 2007-04-18
thank you for the help and the link :) nero wouldnt let me burn onto dvd

---

### Post by bluewagon on 2007-04-18
ok.. now ive run into another problem.. i burned on a new dvd, but when i put it in the dvd drive it says that it cannot read it because it is in a format not ocmpatible with windows?

---

### Post by wormser on 2007-04-18
> **bluewagon said:**
> ok.. now ive run into another problem.. i burned on a new dvd, but when i put it in the dvd drive it says that it cannot read it because it is in a format not ocmpatible with windows?

What is this ISO images of?  

If it is Ubuntu then it does not load in Windows.  You need to restart the computer and go into the BIOS.   Look for boot order and set cdrom to the first.  Then save and exit.  The computer will restart and load Ubuntu.

PS  to get into the BIOS you have to press a key during the boot up.  The key depends on what brand of computer.  Common ones are F2 and the Delete key.

---

### Post by bluewagon on 2007-04-18
but when i look into it in my cd drive, it will open up but it says its empty and nero pops asking for something to burn onto it

---

### Post by battleshipterry on 2007-04-18
Yea What is this ISO images of? this is a important question.

---

### Post by Fireblend on 2007-04-18
1. Burn ISO image into CD with Nero, etc etc. You should end up with a CD/DVD with a bunch of files and directories.

2. Put your CD inside the tray and restart the computer.

3. Either this worked or you have to set the boot order. If it didn't go to step 4.

4.Get into your computer's BIOS (when you turn your computer on you'll see instructions on how to do this) and navigate it until you set your computer to boot first from the CD drive your CD is in.

5. Now that the computer will give priority to the drive instead of the hard drive, it should work.

---

### Post by wormser on 2007-04-18
> **bluewagon said:**
> but when i look into it in my cd drive, it will open up but it says its empty and nero pops asking for something to burn onto it

You need to give us more details for us to help you.

What is the CD of?
Is Nero giving you an error when burning the ISO? - have you tried a different disk?

---

### Post by bluewagon on 2007-04-18
Ive tried two DVD-RW discs, i tried to use Nero first, i clicked the dvd tab and click an burn an image, but it kept telling me i needed a CD, so i used CDBurnerXP and burned the iso on it, after it was ocmpleted i tried opening it in my drive, only to have it say that it is completely empty(in my CD drive) or say it might be corrupted or in a wrong format(my DVD drive)

---

### Post by wormser on 2007-04-18
What is the ISO image of?

Try using a normal CDR or DVDR and not a RW.

[This guide shows you how to burn an ISO in Nero]("http://www.wizardskeep.org/mainhall/tutor/neroiso.html").

---

### Post by Ambimom on 2007-04-18
Did you try burning the image to a CD (not DVD)?

If you're using Nero, it sounds like Nero is expecting to burn the image to a CD. 

If I were you, I'd have Nero verify the burn, just to make sure.  Afterwards, load the CD, it should be readable and will load with a menu of software.

If you get that menu, then power down, switch the boot options to boot from CD, and reboot.

---

### Post by kittyhawk63 on 2007-04-26
.

---

### Post by Maxtine on 2007-04-26
Hi everyone. I’m new to Ubuntu but I think that this will help bluewagon. If you follow the directions at [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto).  Use Infra Recorder you do not need Nero to burn your CD and don’t forget to change your BIOS as JayTheHun stated.

---

