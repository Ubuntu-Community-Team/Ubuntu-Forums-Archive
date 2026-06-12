---
title: "Ready to install Ubuntu.. just want someone to doublecheck something."
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by arcooke on 2007-06-23
First off.. does /dev/sda _always_ = HD0 and /dev/sdb _always_ = HD1?  If that is the case, you probably don't need to read any further.  If not please keep reading.

I had a topic last night asking questions about my installation of Ubuntu7.04.  Someone was talking to me about grub and the mbr.  Now I think I know what to do but I want to make absolutely sure so I don't screw something up on my windows installation.

My setup:
- I'm installing ubu on an external USB hard drive (40GB).
- My primary OS is XP on an internal drive (500GB).

Last night, he told me to set my external hard drive to my first boot device to make it HD0 so the mbr would be written to the correct drive.  I did what he said, but it looks like nothing has changed.  The internal drive is still listed as /dev/sda, and the external as /dev/sdb. 

Please look at my attachments to see the settings I currently have.

I went further through the installation where it gave me the "Advanced" button allowing me to change where to put the boot loader.  As he said, by default it is set to (HD0).  Currently, my external drive is showing up as /dev/sdb, so does that mean I need to change HD0 to HD1?

I'm really nervous about continuing with this.  It's a lot more complicated than I had expected it to be.

Ideas?

Thanks

---

### Post by dstew on 2007-06-23
The question is, how do you want to boot your ubuntu installation? Do you want to have a choice at boot time between the external drive ubuntu and your XP? Or, do you want to try to select the boot drive from BIOS? If it is the latter, install grub to (hd1). If it is the former, you will have to create a at least a boot sector on your internal drive, in order to get a grub menu in case the external drive is not attached, so you can boot XP.

EDIT: /dev/hda is not always (hd0), nor is /dev/sdb always (hd1). The /dev's are device names used by Linux, and are given to the drives at boot time depending on the Linux software. The grub names (hd0) etc. are really BIOS enumerations that are borrowed by grub. Sometimes, the BIOS will enumerate disks differently than Linux, and so /dev/hda is not always (hd0). However, grub has a device.map file that can force a BIOS drive to be counted as a certain Linux drive.

---

### Post by Phixion on 2007-06-23
To ensure you don't write over your Windows drive/partition you can always unplug it during the Ubuntu install process.

Can you not "manually edit" the partitions to make sure you are installing it to the right disk/partition?

According to your screenie you are installing to a 40-50gb Samsung HDD, if that's your external then you should be fine :)

---

### Post by arcooke on 2007-06-23
> **dstew said:**
> The question is, how do you want to boot your ubuntu installation? Do you want to have a choice at boot time between the external drive ubuntu and your XP? Or, do you want to try to select the boot drive from BIOS? If it is the latter, install grub to (hd1). If it is the former, you will have to create a at least a boot sector on your internal drive, in order to get a grub menu in case the external drive is not attached, so you can boot XP.

Well, preferably, I would like to have a menu come up each time I boot asking me which OS I want to go into.  But like the guy said last night (and what I think you're saying here).. I want to make sure I'll still be able to boot into XP even if the external drive is disconnected/off.

If you can give me some details on how to accomplish this, that would be great. 

Thanks ;)

> **Phixion said:**
> To ensure you don't write over your Windows drive/partition you can always unplug it during the Ubuntu install process.

Can you not "manually edit" the partitions to make sure you are installing it to the right disk/partition?

According to your screenie you are installing to a 40-50gb Samsung HDD, if that's your external then you should be fine :)
Well, it's not so much that I'm worried about overwriting my windows drive, I'm already pretty sure I have that one selected correctly in the installer. I just want to make sure I get this boot loader put in the right place.  And yes, my external is the Samsung 40gb, which is where I want to install.

Thanks

---

### Post by Phixion on 2007-06-23
Then just install your bootloader (GRUB) to your primary HDD. It'll then bring up a menu when you start your PC asking you what OS you want to boot into.

---

### Post by arcooke on 2007-06-23
> **Phixion said:**
> Then just install your bootloader (GRUB) to your primary HDD. It'll then bring up a menu when you start your PC asking you what OS you want to boot into.

Ok, so then going back to my first question, is my primary HDD HD0 or HD1?  I set the boot order in the bios to boot my external before the internal.  The guy last night said that would probably force my external drive to become HD0.  In the installer, it is listing my external as /dev/sdb.. so does that automatically mean it is HD1 or is there no connection between those two things?  That's where I'm really confused.

---

### Post by Phixion on 2007-06-23
sda is your first HDD, sdb is your second, partitions are listed as sda1, sda2 etc etc.

It look's as if your internal is counted as your first HDD.

---

### Post by nutz on 2007-06-23
I run my Ubuntu from an external hard drive. Easiest way to install to a USB storage device is to disable all internal storage devices so the installer doesn't see them and include them in grub. If they get included in grub then your problems begin...

I made a post on this a while back. I will see if  I can find it...

---

### Post by nutz on 2007-06-23
Here you go; check my post half way down the screen...

[http://ubuntuforums.org/showthread.php?t=458003&highlight=install+external](http://ubuntuforums.org/showthread.php?t=458003&highlight=install+external)

---

### Post by arcooke on 2007-06-23
Thanks guys.  One last thing.  In my talk last night, the guy helping me (confused57) said this:

> your main concern is not to install grub to your internal hard drive's mbr, you wouldn't be able to boot your internal hard drive with the external drive disconnected.
That's why I'm stressing to set your external hard drive in bios to boot before your internal hard drive and just to be sure select "/dev/sdb"(or whatever you external hard drive is recognized as by the partitioner) as the location you want grub installed.

Many people make the mistake of installing to an external drive and don't realize that grub is installed to (hd0) by default...this would be the internal hard drive, if it is set to boot before the external hard drive.

So he's saying if I install grub to my internal drive, it would cause me not to be able to boot to my internal drive if the external drive is disconnected.  But you (Phixion) are saying I should do that if I want a boot menu. 

So I'm getting conflicting answers.. I just want to make absolutely certain that if my USB drive is turned off or disconnected, I will still be able to boot to my XP installation no matter what.

The thread is [HERE]("http://ubuntuforums.org/showthread.php?t=481921") if you want to see what was going on.



**@nutz**
I tried setting the boot order like that last night and it wouldn't let me. I had
1. External HDD
2. CD
3. Nothing

And when it tried to start up, it just said "NTLDR is issing - Ctrl-Alt-Del to reboot." because the external drive was not yet bootable.

---

### Post by nutz on 2007-06-23
> **arcooke said:**
> Thanks guys.  One last thing.  In my talk last night, the guy helping me (confused57) said this:



So he's saying if I install grub to my internal drive, it would cause me not to be able to boot to my internal drive if the external drive is disconnected.  But you (Phixion) are saying I should do that if I want a boot menu. 

So I'm getting conflicting answers.. I just want to make absolutely certain that if my USB drive is turned off or disconnected, I will still be able to boot to my XP installation no matter what.

The thread is [HERE]("http://ubuntuforums.org/showthread.php?t=481921") if you want to see what was going on.

That is right. If grub gets put on the internal disk and it has a reference to the external drive in it then it will freak out if ever that external drive is unavailable. However if Grub is on the external drive then no modifications need to be made to the internal drive. So you can save yourself the hassle and just disable the internal drive from your bios for the install then you don't have to worry about grub or anything else being put on it.

Just treat it like a regular install where the external drive is your only disk. If you disable all the others in the bios before launching the install it will not see them so this will be the case. Grub is happiest this way...

I will add to this that the installer gives you the option to place grub whereever you want it. But this does not solve all your problems because even if you select this option the installer can still see your internal hard drive and it will include it in the grub menu. You don't want that either just in case you have to use it on another machine. This will cause grub to freak out and the only computer it will work on will be the one it was originally installed on. Without manual editing of grub that is...

---

### Post by Phixion on 2007-06-23
Well, if you install GRUB to your external drive and it's turned off, how are you going to access Ubuntu or Windows?

The guy may be right about that, but as you said, you want to be able to access your OS's even when your external drive is turned off... you can't have it both ways :P

---

### Post by nutz on 2007-06-23
> **arcooke said:**
> Thanks guys.  One last thing.  In my talk last night, the guy helping me (confused57) said this:



So he's saying if I install grub to my internal drive, it would cause me not to be able to boot to my internal drive if the external drive is disconnected.  But you (Phixion) are saying I should do that if I want a boot menu. 

So I'm getting conflicting answers.. I just want to make absolutely certain that if my USB drive is turned off or disconnected, I will still be able to boot to my XP installation no matter what.

The thread is [HERE]("http://ubuntuforums.org/showthread.php?t=481921") if you want to see what was going on.



**@nutz**
I tried setting the boot order like that last night and it wouldn't let me. I had
1. External HDD
2. CD
3. Nothing

And when it tried to start up, it just said "NTLDR is issing - Ctrl-Alt-Del to reboot." because the external drive was not yet bootable.

If you do not see an option to boot to a USB hard drive then chances are your bios/chipset doesn't support it.

If your computer can boot to an external storage device then you will be able to select that option in your bios, if you can't then it doesn't.

---

### Post by nutz on 2007-06-23
> **Phixion said:**
> Well, if you install GRUB to your external drive and it's turned off, how are you going to access Ubuntu or Windows?

The guy may be right about that, but as you said, you want to be able to access your OS's even when your external drive is turned off... you can't have it both ways :P


Because when the external drive is disconnected it boots Windows. When you plug it in it boots Ubuntu.

No boot menu needed because no changes are made to the internal drive with this process.

---

### Post by ajgreeny on 2007-06-23
1  Disconnect internal windows drive.
2  Install Ubuntu on external drive, including grub there too.
3  Reconnect windows internal drive.
4  Reset bios to boot from the external drive first and internal drive second.  This means that if the external drive is connected it will boot and grub will start Ubuntu.  If it is disconnected the windows MBR will appear instead of grub and should boot windows.

I hope this all makes sense to you and good luck.

---

### Post by Kubunteando on 2007-06-23
I would follow Phixion suggestion and I would unplug the Internal HDD until Ubuntu is completely installed. Once you can boot Ubuntu normally,  you can plug the Internal HDD back.

The issue is that in Feisty it seems that grub installation tries to install itself in the MBR of the main HDD usually the internal one, but the grub menus will be installed in your Ubuntu installation what will be in the External HDD So if you disconnect it you will not be able to boot Windows.

It happened to me a couple of times, and I restored the MBR using the Windows XP Installation CD, I think the command is "fixmbr". 

That is the safest way.

---

### Post by nutz on 2007-06-23
> **ajgreeny said:**
> 1  Disconnect internal windows drive.
2  Install Ubuntu on external drive, including grub there too.
3  Reconnect windows internal drive.
4  Reset bios to boot from the external drive first and internal drive second.  This means that if the external drive is connected it will boot and grub will start Ubuntu.  If it is disconnected the windows MBR will appear instead of grub and should boot windows.

I hope this all makes sense to you and good luck.

+1, that is exactly what you are looking for. Just follow that guide and it will go smoothly provided your bios supports booting to external USB storage devices.

---

### Post by arcooke on 2007-06-23
nevermind.. I think I got everything figured out thanks to you guys.  And yes, my bios does support booting from USB

I'm going to give this a shot. I'll be back in a few (hopefully) :)

Thanks everyone!

-EDIT- 
I disabled the internal drive in the bios (turned auto-detect off and manually selected NONE), and ubuntu is still listing it in the installer, and it is still listing it as the first drive.  I guess I have to open up the computer and manually disconnect my hard drive.  What a pain.. grr.  Will be back.

---

### Post by arcooke on 2007-06-23
Everything seems to be working great.  Thanks again guys!

I'm now the proud owner of a shiny new copy of Ubuntu.  First time I've ever used Linux.

My only complaint so far is that Firefox seems a lot more sluggish than on Windows.  I suppose that could be because I'm using a MUCH slower hard drive.. I think the manual said it maxes out at 12Mbps transfer speed.  Heck, my internet connection is even faster than that at 15Mbps lol

---

### Post by nutz on 2007-06-23
Glad you got it working. It shouldn't be that much slower unless your drive is not USB2.0...

My Ubuntu installation runs better than the XP installation that is on the internal disk. But then again this laptop has a 4200rpm drive so their actual transfer rates and seek times are not that far off from each other. The main difference is in I/O's, the USB interface just can't handle as many at the same time compared to SATA. But their actual raw transfer rates are probably pretty close...

I think the reason yours is running so much slower is the amount of memory you have. If you are using a lot of swap memory on the external disk this would explain your slowdown. Having it use that swap memory puts a bigger I/O requirement on the drive then without thus more quickly depleting it's response time. With 2gb of memory I have never even seen it use the swap file which may explain why I don't see any slowdown or speed difference between the two...

I would sugest you get some more memory or you could pick up a cheap flash drive and use that for your swap partition to take that I/O load off the external drive.

---

### Post by CrispyFried on 2007-06-23
> **nutz said:**
> 
I think the reason yours is running so much slower is the amount of memory you have. If you are using a lot of swap memory on the external disk this would explain your slowdown. Having it use that swap memory puts a bigger I/O requirement on the drive then without thus more quickly depleting it's response time. With 2gb of memory I have never even seen it use the swap file which may explain why I don't see any slowdown or speed difference between the two...

I would sugest you get some more memory or you could pick up a cheap flash drive and use that for your swap partition to take that I/O load off the external drive.

I know this would complicate things (and after all its running ok now) but wouldnt making a swap partition on the internal drive speed things up? 

it wont effect windows as it will just ignore the swap partition but when ubuntu on the external drive is running the swapping to the internal drive would be much faster as well as reducing the i/o demand on the external drive

however adding ram would be the simplest thing and be of benefit to both windows and ubuntu, making both faster.

flash memory has limited read/write cycles so if you go that route think of it as a disposable drive and dont store anything important on it.

---

### Post by nutz on 2007-06-23
> **CrispyFried said:**
> I know this would complicate things (and after all its running ok now) but wouldnt making a swap partition on the internal drive speed things up? 

it wont effect windows as it will just ignore the swap partition but when ubuntu on the external drive is running the swapping to the internal drive would be much faster as well as reducing the i/o demand on the external drive

however adding ram would be the simplest thing and be of benefit to both windows and ubuntu, making both faster.

flash memory has limited read/write cycles so if you go that route think of it as a disposable drive and dont store anything important on it.

Your sugestion is a good one but the main goal here is to leave the internal disk untouched. Or at least that is what my goal was, I think his was too...

As far as the flash drive goes yes they do wear out but not for quite a while. I have one Ubuntu install on a USB flash drive that I use for fixing and troubleshooting stuff and it is still going strong after many months of constant use. Only time will tell just how long it will last and of course it depends on useage and quality of the flash memory itself.

---

