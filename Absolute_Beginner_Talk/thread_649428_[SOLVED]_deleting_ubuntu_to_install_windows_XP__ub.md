---
title: "[SOLVED] deleting ubuntu to install windows XP / ubuntu duel boot"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by mangurt on 2007-12-24
Greetings all,
I have a complete hard drive installed with ubuntu, and I now need to install windows XP on my system.  I'm kinda lost here because when I place my windows disk into the system, and try to install, windows state that there is no hard drive.
I've tried to delete and change over the partitions with the live cd, but I can not delete 2 paritions (I used gparted).
What I would like to do is duel boot my system (using windows for work), and ubuntu for everything else.
Any ideas?
Thanks!

---

### Post by adam.tropics on 2007-12-24
Windows doesn't see the filesystem. You need to make space for it and format it to something it can recognise from gparted, off a livecd. Also, I don't know about genuine windows disks, but i have found with manufacturer restore disks, they will only work (for me) if the empty partition is the first on the drive.

---

### Post by Moop on 2007-12-24
Using the live cd and gparted turn off swap and then you should be able to delete the swap partition and the extended partition. 

Create a windows partition the size you want and format it to ntfs. Now your XP cd should be able to see the hdd and install.

---

### Post by mangurt on 2007-12-24
Hmm...how do I turn off the swap parition?  I think I tried doing that, but it was locked (had a pad-lock symbol next to it).

---

### Post by zero-9376 on 2007-12-24
if the xp install cd is not even seeing a hard disk then partitions don't matter, are you using a sata hard disk, you may need to load drivers for your mainboard before when windows say Press F6 to load third party.... not sure exactly but you should see this step before it starts loading all the device drivers. you should hopefully be able to find what you need on the manufacturers website or cd that came with your motherboard

---

### Post by Moop on 2007-12-24
> **mangurt said:**
> Hmm...how do I turn off the swap parition?  I think I tried doing that, but it was locked (had a pad-lock symbol next to it).

I think the lock just means it's on. Highlight the partition and right click and there should be a option to turn it off. 

Zero-9376 is right. XP should see your hdd.

---

### Post by horry on 2007-12-24
> **mangurt said:**
> Greetings all,
I have a complete hard drive installed with ubuntu, and I now need to install windows XP on my system.  I'm kinda lost here because when I place my windows disk into the system, and try to install, windows state that there is no hard drive.
I've tried to delete and change over the partitions with the live cd, but I can not delete 2 paritions (I used gparted).
What I would like to do is duel boot my system (using windows for work), and ubuntu for everything else.
Any ideas?
Thanks!

first of all, merry X-mas. 
why did you can't delete some partitions, what's the error information?
i installed the dual systems serveral days ago. i boot from live cd, and then clicked 'install', when step to partition, i can delete any partition both linux partitions and windows partitions. you can give the error information, there maybe someone can help you.

---

### Post by zero-9376 on 2007-12-24
if mangurt  can clarify whether the xp installer actually sees the hard disk we can focus on addressing that issue, alternatively the xp cd should be capable of seeing the partitions, but they will be of unkown type. It is also able to delete any partition even if it cant recognise the filesystem on the partition.

---

### Post by CCNA_student on 2007-12-24
I would suggest that you completely erase your hard drive and install Windows XP first. Then install Ubuntu. You cannot not install Windows XP second as this erases the GRUB boot loader, so this is why I had to install Ubuntu second. I am sure it is possible to somehow to restore GRUB, but I do not know how. I hope that this helps you.

       Sin Cere,

       CCNA

---

### Post by adam.tropics on 2007-12-24
> **CCNA_student said:**
> I would suggest that you completely erase your hard drive and install Windows XP first. Then install Ubuntu. You cannot not install Windows XP second as this erases the GRUB boot loader, so this is why I had to install Ubuntu second. I am sure it is possible to somehow to restore GRUB, but I do not know how. I hope that this helps you.

       Sin Cere,

       CCNA

Pretty simple one that....[URL="http://ubuntuforums.org/showthread.php?t=224351"]details here.
[/URL]

---

### Post by meierfra on 2007-12-25
Please open a terminal (Applications->Accesories->Terminal) and post the output of

```
sudo fdisk -l
```

This will allow us to  give you more qualified advice.

---

### Post by mangurt on 2007-12-25
Sorry for the delay in getting back, but I had to play Santa last night...

Ok, here's what I got, I did the remove partition in live cd, and placed the windows xp disk into my system, got to the point where it said that I needed to push F6 to have xp see my hard drive, then I got to a page where is said toss in a floppy disk to install drivers.

The major problem is that when I try to install windows xp (god I hate windows, but I need to use a PKI card for reserves, and it only works in XP)

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xabacc689

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9587    77007546   83  Linux
/dev/sda2            9588        9964     3028252+   5  Extended
/dev/sda5            9588        9964     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    7  HPFS/NTF

That is the results of the sudo fdisk command...

this community is so incredible!!  Thank you all very much

Merry Christmas

---

### Post by bumanie on 2007-12-25
I am no expert on grub but will make the following comments.
1) Windows does need to be on the first partition of the master drive.
2) Windows does overwrite grub
3) As ubuntu should have had grub at (hd0,0), without a reinstall of ubuntu, following the windows install, (I think - wait for further confirmation form someone who understands grub better) you would probably have to edit the /boot/grub/menu.lst to direct grub to the new partition it will be on.
4) The link given does reinstall grub, but I think it is only valid if partitions are the same as before. That is if you reinstall windows to a partition windows was already on. In your case windows is not on the drive already, therefore that scenario dose not apply to you.
5) If you have a separate /root and /home partition, you should be able to save (on external media) or may be move your /home to a 'safe' area and just reinstall ubuntu to /root. If you have this setup, it should save a lot of headaches.
Hope this makes sense.
Remember I am not a grub expert, but believe what I have said is basically sound.

---

### Post by mangurt on 2007-12-25
Hmm...don't know if GRUB is the answer or not.

If I try to install windows with my external hard-drive attached, the installation process sees the external hard-drive, but if I have it unplugged, it does not.  I don't know if I want to mess around with installing windows on my external hard drive because I would have to put a partition on it, unless I do that with gparted, but I would hate to lose all my information on the external hard-drive.

I am trying to find the driver to put onto a floppy disk to I can load windows onto my sata hard drive, but wow, this is a pain with an older hard drive.

---

### Post by meierfra on 2007-12-25
> am trying to find the driver to put onto a floppy disk to I can load windows onto my sata hard drive, but wow, this is a pain with an older hard drive.

I won't be able to help you with this.
So I just assume that you  will find the drivers  somewhere.

All your other problems should be fairly easy to solve. But I need to know  which drive would you like to install  XP on? As far as I can see  you should be able to install XP on either drive. So you can make your  pick. (Personally I  would   XP on the internal drive. )

How large would you like the  XP partition to be?
Are you willing to resize the Ubuntu partition, to make room for the  XP.
What is on the external drive. Would you be willing to  shrink that partition to make room for XP?

Once you decide where you want to install XP, I can tell you how to do it. (except for the driver problem)

---

### Post by meierfra on 2007-12-25
> f I try to install windows with my external hard-drive attached, the installation process sees the external hard-drive, but if I have it unplugged, it does not..

Why do you want the installation process to see the external drive?

---

### Post by mangurt on 2007-12-25
> **meierfra said:**
> Why do you want the installation process to see the external drive?

I forgot to unmount my external hard drive when I was doing the installation process, that's why the external hard drive was noticed.  I have all of my movies, music, other stuff backed up on my external hard drive.  I have enough room to make a partition for XP, but I'd rather install it on my internal hard drive.

As for finding the drivers, I've been googling like a mad man, and went to the hard drive web site, but of course everything is a .exe file, and wine is having problems running it.

It might be easier just to make a partition on the external hard drive and go from there...

---

### Post by meierfra on 2007-12-25
> It might be easier just to make a partition on the external hard drive and go from there...

I'm trying to understand. Is your external drive IDE and you would not need the  drivers?

---

### Post by Moop on 2007-12-25
You won't find the driver from the hdd mfg, you would get it from your pc mfg or motherboard mfg. 

If you have that info it shouldn't be to hard to find a driver for your floppy.

(a driver to go on your floppy for the f6 option)

---

### Post by mangurt on 2007-12-25
Well, that might be the problem, I will turn this system off and take a look at my motherboard.  Hopefully I can find that information there.

---

### Post by meierfra on 2007-12-25
What are you planning to do with XP. For most things  you can  run XP  in a virtual environment. So you  would  not have to dual boot.

---

### Post by mangurt on 2007-12-25
Well, what I need to do in windows is run a PKI card reader to log onto secure websites for the military.  I tried running the PKI program through wine and that did not work.  That's pretty much all I need to do.

---

### Post by meierfra on 2007-12-25
> PKI card reader 

No ideas whether that works in a Virtual XP. But a little bit of googling might tell.

---

### Post by mangurt on 2007-12-25
Don't know about virtual XP.  The card reader reads information off of my military ID (digital security).  I was using my wife's PC but it died the other day....I guess I will check out virtual XP.  Ok, I did a quick look for virtual xp and I did not find anything....any links?

---

### Post by meierfra on 2007-12-25
[VMserver]("https://help.ubuntu.com/community/VMware/Server")
[VirtualBox]("https://help.ubuntu.com/community/VirtualBox")

This should get you started. Don't know much about it myself.

---

### Post by mangurt on 2007-12-25
Ok, trying to install VMserver and having a bear of a time doing it....I hope I can figure this out....

---

### Post by meierfra on 2007-12-25
Good luck. Never did it myself, so I won't be able to help you.

---

### Post by mangurt on 2007-12-25
Just an FYI, got virtualbox up and running, and it looks like I will have XP running through that.  God I hate to use windows at home, but if I can get my military work done on that, and run ubuntu for everything else, I will be very happy!!

---

### Post by mangurt on 2007-12-26
Well, it looks like I am back at square one.  I got XP up and running on via virtualbox, but XP did not see the USB items.  I looked around at virtual box to find an answer and the website stated that this was a known problem and they hope USB support would be developed at a future time.

Now I am back to scratching my head and trying to get XP to see my hard drive for the installation.  It would be really nice if I had my recovery disk, but that got lost a few years ago...

I went to the support website to try and find the drivers, but that really did nothing except give me a headache...

Any ideas?

Thanks again

---

### Post by meierfra on 2007-12-26
> but XP did not see the USB items 

Sorry for leading you down the wrong track.

> Any ideas?

Is it correct that you could install Windows to the external drive without the drivers (since the external drive is not a SATA)?

To install to the external drive, use gparted to resize  the existing partition. Windows can be only installed to the  first hard drive in the boot order in the bios, So you will have to change the boot order. There is some chance that  that is not good enough for windows and you will have to physical disconnect the internal drive.

P.S. I never have installed Windows to an external drive, so I have no idea what other complication you might run into.

---

### Post by mangurt on 2007-12-26
Well, I think I can install XP on my external hard drive.  Windows sees that hard drive if I leave it plugged in while doing the installation process.

I guess I will try and partition my external hard drive with gparted.  I looked at this before, and the partition was locked, so I will have to remember how I unlocked it....

Thanks for the help, hopefully this will work...

---

### Post by zero-9376 on 2007-12-27
this might help you with your usb problems in virtualbox [http://buranen.info/?p=187](http://buranen.info/?p=187)

were you able to locate drivers for your motherboard to allow windows to install to the sata disk?

---

### Post by mangurt on 2007-12-27
No, I never did find the drivers for my motherboard, which makes this even harder.

---

### Post by Moop on 2007-12-27
I think XP with SP2 will recognize your sata drive without a driver. You can download SP2 and integrate it into a new XP install cd. There are guides for doing that and it's not to hard. 

Or maybe you can borrow a newer XP cd that has SP2 integrated.

---

### Post by mangurt on 2007-12-27
> **Moop said:**
> I think XP with SP2 will recognize your sata drive without a driver. You can download SP2 and integrate it into a new XP install cd. There are guides for doing that and it's not to hard. 

Or maybe you can borrow a newer XP cd that has SP2 integrated.

Hmm, I never knew that.  I guess I will try doing that....wish me luck! :)

---

### Post by mangurt on 2007-12-28
Well, I got XP with SP2 downloaded and tried to that but it did not work either.  I am really at a loss with trying to get this up and running to the point that I am going to say screw it to XP (which I pretty much did anyway).  My wife has been wanting a computer, so I will probably get one up and running for her, and go from there.
Thanks for all the help.

---

### Post by mangurt on 2008-01-03
Problem solved.  Ended up resetting the bios on my motherboard.  As soon as I did this, the motherboard found my hard-drive.  I got XP loaded up on a 15 partition, and installed ubuntu on the rest of the partition.

Thanks for all the suggestions and helping me out.

---

