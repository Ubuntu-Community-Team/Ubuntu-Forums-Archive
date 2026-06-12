---
title: "Linux on External Hard Drive"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by freebieking on 2007-12-13
Not sure where this goes plus this is actually 3 questions:

1)
I installed Ubuntu on an external hard drive for backup purposes and also to learn how to use it.  When I disconnected the external hard drive Grub wouldn't load into windows as usual.  It said, "Error 21" and stopped.  The only problem I see is if my external hard drive dies (since it is an older one) .  So how do I boot into windows if my external drive dies? I don't want to depend on an external hard drive to boot up my machine.  

2) 
I tried to backup another hard drive in windows but windows will not assign the hard drive a letter.  It does recognize the drive but I can't access it.  Any ideas?

3)
If I ever want to uninstall or remove Ubuntu, how would I go about doing so?  This doesn't seem to be as easy as a windows. 

Thanks,
freebieking

---

### Post by Dr Small on 2007-12-13
It sounds like GRUB installed on the internal hard drive, instead of the external one.

---

### Post by logos34 on 2007-12-13
> **Dr Small said:**
> It sounds like GRUB installed on the internal hard drive, instead of the external one.

Ditto.

1) Reinstall windows bootloader.  Use XP install cd, go into recovery console and run command **fixmbr**.

This means you will have to change the bios boot order when you want to boot ubuntu on the usb.  Either that or use [Wingrub]("http://users.bigpond.net.au/hermanzone/p9.html").

Boot from ubuntu live cd and[ restore grub to the usb drive mbr]("http://ubuntuforums.org/showthread.php?t=224351"). Except you want 'setup (hd[COLOR="Red"]1[/COLOR])'--assuming the external usb is the only other hard disk. 

You'll also need to edit /boot/grub/menu.lst, because the minute you change the boot order in the bios, the drive designation changes to '(hd0)'. See post #502 in[ this thread.]("http://ubuntuforums.org/showthread.php?t=80811")


2) not sure

3) use gparted on the live cd to remove ubuntu.  Since grub will be on the external drive it won't cause any problems with windows

---

### Post by aonegodman on 2007-12-14
> **freebieking said:**
> Not sure where this goes plus this is actually 3 questions:

1)
I installed Ubuntu on an external hard drive for backup purposes and also to learn how to use it.  When I disconnected the external hard drive Grub wouldn't load into windows as usual.  It said, "Error 21" and stopped.  The only problem I see is if my external hard drive dies (since it is an older one) .  So how do I boot into windows if my external drive dies? I don't want to depend on an external hard drive to boot up my machine.  

2) 
I tried to backup another hard drive in windows but windows will not assign the hard drive a letter.  It does recognize the drive but I can't access it.  Any ideas?

3)
If I ever want to uninstall or remove Ubuntu, how would I go about doing so?  This doesn't seem to be as easy as a windows. 

Thanks,
freebieking

You installed Ubuntu on a Ext HD that you obtained for backing up your Windows stuff on originally, as I ubderstand it.  

What you are also saying is, if I understand you, that if your internal HD crashes you no longer have a backup to restore and boot Windows back up. Is that right?

If so then start as suggested above by using your Windows System Disk and restoring you MBR first.

Next make an Emergency System Floppy Disk(if you have floppy) for Windows and write protect it.

Next, get a copy of Hiren's Boot CD and burn it to CD, must have utility for all kinds of disk related problems.

Next, run Ubuntu off of the LiveCD until you decide if you like it and really want to install it.

Then I suggest running them as two seperate systems on your computer like I did and forget about intergration. I had the same type of problem trying to install on my USB External HD.

One reason Windows may no longer see your Ext HD is due to type of file system you may have formatted it with, i.e. Ext3.

GRUB boot loader could have corrupted.

Not sure how to uninstall Ubuntu off of shared system setup, I'm sure there is a thread on the forum for that - just run a search. But in my case all I have to do is reformat my Ext HD - GONE!

My BIOS is set up to Boot in this order:  1) CDROM  2) Floppy  3) USB Ext HD  4) Int hd0  5) Others

Not all BIOS can boot to USB devices I understand, mine can.

Since I find NO reason to work in both Windows and Linux at the same time, I simply decide which I want to start up - by making CDROM first I can install a system CD for repairs or upgrades.

I use a floppy to boot into my Windows XP and thereby protect my Boot from virus or other malware since it is on a write protected disk. So when I'm ready to work in Windows I stick the floppy in and it boot directly to Windows on hd0.

Going to Ubuntu, which I am doing more and more now \\:D/  I don't put anything in the CDROM or Floppy and my computer boots directly to my USB Ext drive.

To me this is the safest and most practical way to set up my computer. No worries, no conflicts. :)

I installed Ubuntu on my USB Ext drive by opening my computer and unlugging my internal hard drives off the HD Controller bus( after shut down, ground self to box, unlug).

If your box has the slide off side better still, just leave it off until your done.

Next, place the LiveCD in the 1st Boot seek CDROM and power up!

Once Ubuntu desktop is loaded you will see only one device on your desktop - the Ext HD and the Install to HD icon.

DClick on the Install. Follow the prompts. Your Ext HD will be reformatted and loaded with Ubuntu.

Shut down your LiveCD Session and Computer. Cautiously(grounding yourself to box) replug

the HD Controller cable inside your computer. Close up. Reboot.

Go into BIOS menu and configure your boot sequence to suit your machine and preferences, save it.

This is one way only. There are others on the Forum that explain it better than I have perhaps and they were a great help to me. I find the search function works great to get you the answers you need quickly. Just got to dig a little.

---

