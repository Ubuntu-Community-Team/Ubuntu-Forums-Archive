---
title: "Ruh Oh... few questions. :O Dual Booting trouble."
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by virtuexru on 2006-06-26
OK, so I have a dual boot system setup with Win 2000 and Unbuntu and GRUB. Problem now..

I loaded into UNBUNTU, downloaded all updates and restarted. Now there is a new version of UNBUNTU in GRUB Boot Loader. I load into that one. Tinkered around some more, restarted.

Now the graphics are messed up to the point where I can't use it. Everything is decolorized and off to the right of the screen.

So I restart and load into the older version and everything works fine. What should I do now? How do I get rid of the new version?

Also, quick question. How do you uninstall Linux? If you format the EXT32 Partition will GRUB be deleted too? Will windows boot normally if you do this?

---

### Post by jcjones on 2006-06-26
Well, newbie helping a newbie here. :)

I don't know exactly how you'd go about fixing your X problem, but I'd suggest taking a look at the /etc/X11/Xorg.conf (I think) and see if your video settings are what you'd normally use.

To answer your second question, it's very simple to "uninstall" Linux. Simply delete the ext3 partitions, boot into MS-DOS with a boot disk of any sort (I believe Win2k/WinXP's disk can be booted for a recovery console as well) and use this command:

```
fdisk /mbr
``` 
That should format the Master Boot Record, giving Windows control of boot procedures again.

Don't give up just yet on Linux! Use VMWare to load Windows if you must!

Jared

---

### Post by mscman on 2006-06-26
For your messed up graphics (an X server problem it sounds like), when you get fully loaded into Ubuntu, assuming you are seeing a desktop, hit Ctrl+Alt+F1 to get to a virtual console.  Login using your username and pass.  Then run the command:
```
sudo dpkg-reconfigure xserver-xorg
```
and follow the on-screen dialogue until it returns you to the black and white prompt.  Then press Ctrl+Alt+F7 to return to your normal desktop.  You'll still see the messed up graphics, because Xserver is still running from boot.  To restart the Xserver, press Ctrl+Alt+Backspace.  That should *hopefully* fix your graphics problem.

As for uninstalling Linux, yes, you can reformat the partition.  Once you do that, you'll need to use a Windows install CD and boot into recovery mode (press 'R' when prompted.) Then you can run the command
```
fixmbr
``` to restore your Master Boot Record.  You could try the fdisk /mbr as instructed above, but I've never used that method.

Hope this helps!  Have fun with Ubuntu :-D

---

### Post by loserboy on 2006-06-26
yea i had a prob with my mbr with xp and i had to do it the way mscman said

---

### Post by missmoondog on 2006-07-22
you can simply remove whichever linux-image from within synaptic. just search for it just like i typed it. with the - in the middle. 

whenever you update the linux kernel you have to also reconfigure your xserver. simply copy your old config file over is easiest.

---

