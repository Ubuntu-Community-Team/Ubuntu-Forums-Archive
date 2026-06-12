---
title: "Don't get the Ubuntu option at startup"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by GreatHype on 2008-01-02
I've recently installed Ubuntu and I guess everything has gone ok, the file ubuntu.bin showed up in my fat32 partition like the howto said it would.  I copied it to my C:\ drive and typed the ubuntu thing in the boot text file, but I'm not getting an option to boot Ubuntu when I start my computer.  Windows just automatically starts.  Any help would be greatly appreciated.

---

### Post by PeterJS on 2008-01-02
That's not the standard install procedure, do you have a link to the guide you're using?

---

### Post by GreatHype on 2008-01-03
I kind of feel like an idiot because I just read that it says "installing on a toshiba laptop" at the top.  Here it is.
[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

...and if you didn't get it, I don't have a toshiba laptop.

---

### Post by PPAAUULL on 2008-01-03
I don't think that is how install should go first of all and second if you are going to have windows and Ubuntu you need to install GRUB to so you can switch between the two.

---

### Post by ~LoKe on 2008-01-03
Yeah...you'll want to boot up the LiveCD or alternate install CD...heh.

---

### Post by GreatHype on 2008-01-03
I did install GRUB, I used the alternate CD and followed all the steps and then installed GRUB into the Linux partition.

---

### Post by twin_57103 on 2008-01-03
You should be able to run the Live CD and install from there - this will install everything you need to dual-boot.  The installation is in wizard format and straightforward.  Boot from the Ubuntu Live CD and it will do the dirty work for you.

---

### Post by ~LoKe on 2008-01-03
> **GreatHype said:**
> I did install GRUB, I used the alternate CD and followed all the steps and then installed GRUB into the Linux partition.

When your computer is starting up...does it say something like....
"Grub loading boot stages..."
Then count down from 3 to 1?

---

### Post by PPAAUULL on 2008-01-03
Well grub has to go to MBR and if you are new I would just use the livcd and follow the instructions or follow a howto on the Ubuntu Wiki the one you gave is very.... well interesting.

---

### Post by PeterJS on 2008-01-03
Yeah I wouldn't trust that guide. Any guide that recommends not installing grub is not quite right. These days installing ubuntu amounts to opening the installer from the liveCD and following the instructions on screen.

---

### Post by GreatHype on 2008-01-03
No, like I said I don't get any option for a dual boot it just goes straight to windows, and I tried to use the live CD first to see what it was like, but I wouldn't get a display when I clicked install so I was told to use the alternate CD.

Edit - It says to install GRUB just to install it into the Linux Partition, if the Live CD doesn't work I'll go back and install it into the MBR.

---

### Post by GuitarRocker2562 on 2008-01-03
did you try wubi?

---

### Post by GreatHype on 2008-01-03
Not quite sure what that is.

---

### Post by GreatHype on 2008-01-03
Well anyway, I installed into MBR and now I get the option to boot into Ubuntu, but when I do I my monitor goes into power save mode which is what it did when I tried to use the live CD.  What do I do now?

---

### Post by ~LoKe on 2008-01-03
> **GreatHype said:**
> Not quite sure what that is.

You can find wubi and information about it [here](https://wiki.ubuntu.com/install.exe/Prototype).  It allows you to install Ubuntu within Windows.

---

### Post by GreatHype on 2008-01-03
Well I already did install Ubuntu and its working now I just don't get any display.

---

