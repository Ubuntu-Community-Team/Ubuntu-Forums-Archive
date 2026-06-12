---
title: "This Grub Thing!!!"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by lovloss on 2006-11-02
I like this "grub" thingy and all, but I am running Ubuntu off an external HD, and I feel like I have to rely on it just to boot up my computer. During bootup it will say I have a grub error unless the external's plugged in, which isn't good. It should just continue into windows.
 How can I make it so that if the external HD is not plugged in, my computer loads windows? I want grub to load up when it boots from the external drive (my BIOS is set to boot first from USB)

---

### Post by dillbertdabomb on 2006-11-02
that wasn't a good way to install...
the grub files are on your external...

---

### Post by dillbertdabomb on 2006-11-02
Yay! i rembered
get on windows, when it starts hit f8 until a screen with a menu apperars. then go to recovery console (it might be in select os or sometin like that...) than once you get in there you type in fixmbr or somtin like that hope it hepls

---

### Post by &#12465;&#12452;&#12488; on 2006-11-02
dillbertdabomb is right about being able to write a new Windows MBR by doing that, but why would it be erased from the internal drive if he only wrote GRUB to the external disk?

---

### Post by dillbertdabomb on 2006-11-02
becuase grub has some files on the mbr and the settings in /boot/grub

---

### Post by lovloss on 2006-11-02
Okay, so I need to fix the microsoft bootup... thats fine. I do need the windows cd for that right?

If I do this, and restore mbr, will it still start up grub if the external is connected, since that's its primary boot location? Itd be nice to have linux and the drive be modular from windows.

---

### Post by &#12465;&#12452;&#12488; on 2006-11-02
It'll probably work, yes.

Do as dillbert said, boot Windows while pressing F8 to get some options, then select the recovery console.

There, type **map** to list your hard drives. When you've found the one with Windows on it, type **fixmbr \Device\harddisk0** to write a new MBR.

---

### Post by gn2 on 2006-11-02
> **lovloss said:**
> Okay, so I need to fix the microsoft bootup... thats fine. I do need the windows cd for that right?

If I do this, and restore mbr, will it still start up grub if the external is connected, since that's its primary boot location? Itd be nice to have linux and the drive be modular from windows.

If you are seeing Grub at boot with the external drive disconnected, I would suggest it can only mean that Grub is nestling in your Windows MBR.

fixmbr can be run from a Windows boot floppy, or repaired using the Super Grub Disk.

Once you've done that, you'll need to re-install Grub to the external hard drive, preferably with the Windows drive disconnected.

---

### Post by lovloss on 2006-11-02
So if my internal has the mbr, and my external has the grub, then whichever one boots up first will run... right?

---

### Post by TheMono on 2006-11-02
Grub has two parts. The first part is on your MBR, as it is for almost everyone. All the first part does though is pass onto the second part, as the second part is too large to store in the MBR.

This is where you fall over, as the second part is installed on your external HDD.

Not sure how you can easily fix this, but that's the problem  - that grub is split.

---

### Post by TheMono on 2006-11-02
There is a way you could do it by having a seperate partition on your internal drive for Ubuntu's /boot folder.... But that could be complicated and I'm not sure it would work either.

---

### Post by lovloss on 2006-11-02
But if the whole of it was on the external, that might work

---

### Post by devilsadvocate1987 on 2006-11-02
fixin MBR using the windows cd is a bad idea. You wont be able to boot into ubuntu again. What you need to do is to setup grub completely on your internal. While doing that isnt really that big a deal  while installing, changing things now will be a little difficult. 

You will need a small ext2 or ext3 partition on your internal for the grub config files, preferably in the initial portion of the disk. You'll have to install grub on that partition and make the part of grub on th MBR point to the new grub on the internal.

There is also a grub for windows which you can look at. This might just be easier to do beacuse it wont need to do any partitioning

---

### Post by lovloss on 2006-11-02
Im so confused :( All I need is a plug-and-play linux external HD. when its out, windows. When its in, windows or linux. I dont know why this is so complicated... maybe I should just do that, get a windows grub. Or just put the grub on a cd.

---

### Post by lovloss on 2006-11-02
My bios order is CD, USB, C:/ by the way, so it'll see USB before the internal disk

---

### Post by gn2 on 2006-11-02
> **lovloss said:**
> My bios order is CD, USB, C:/ by the way, so it'll see USB before the internal disk

There is absolutely no requirement whatsoever for Grub to be on the Windows drive.

You just need Grub to boot Ubuntu. Install grub to the USB drive. Put USB before Internal hard drive in boot order, and Ubuntu will boot.
Unplug USB and Windows will boot.

Better yet install PCLinuxOS on the USB drive with the Windows drive physically disconnected. It has an automated installer for doing so. [http://www.pclinuxos.com/](http://www.pclinuxos.com/)

This may shed some light, although it's not specifically about USB hard drives: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by lovloss on 2006-11-02
thanks :D Now i think i can take care of this. Thank you so much. I know its a very specific problem, but I like the setup of having linux in a tiny portable device ^_^

---

### Post by &#12465;&#12452;&#12488; on 2006-11-05
Why couldn't you rather make the BIOS boot to the internal drive first, and then have a GRUB installation on that disk? Make it boot Windows by default, unless you select Ubuntu from the menu (which points to the external drive's Ubuntu partition). That'd be a lot easier, right?

---

### Post by mo79 on 2006-11-05
If you have a Boot Menu option (F12 on a Dell, for instance) when your computer starts up you could just select the relevent drive to boot from. Do indeed make sure that Windows MBR is restored first though.

---

### Post by gn2 on 2006-11-05
> **&#12465 said:**
> Why couldn't you rather make the BIOS boot to the internal drive first, and then have a GRUB installation on that disk? Make it boot Windows by default, unless you select Ubuntu from the menu (which points to the external drive's Ubuntu partition). That'd be a lot easier, right?

No, if it's at all possible to keep Grub off the Windows drive that's preferable for an inexperienced user.

In this case it's simply a matter of installing Grub on the USB drive, with The USB drive before the hard drive in the boot order.
That way, to boot Windows, just unplug the USB drive.

Grub on the Windows drive can be a major P.I.T.A. unless you know *exactly* how to fix it before (when) it goes wrong.
And it WILL go wrong..... It just takes time.

---

### Post by bulldog on 2006-11-05
> **gn2 said:**
> No, if it's at all possible to keep Grub off the Windows drive that's preferable for an inexperienced user.

In this case it's simply a matter of installing Grub on the USB drive, with The USB drive before the hard drive in the boot order.
That way, to boot Windows, just unplug the USB drive.

Grub on the Windows drive can be a major P.I.T.A. unless you know *exactly* how to fix it before (when) it goes wrong.
And it WILL go wrong..... It just takes time.

LOL,keep up the good work,mate,but don't overdo,GRUB on your MBR with windows and Ubuntu works fine,things go wrong when users are going to experiment with it,without noing what they're doing.

But indeed,you're right,if possible keep GRUB and windows bootloader on separate hard disk if you can.

---

### Post by gn2 on 2006-11-05
> **bulldog said:**
> things go wrong when users are going to experiment with it,without noing what they're doing.



That's certainly a major cause of problems:oops: , kernel upgrades and Grub updating itsself are others.....

---

