---
title: "Windows install missing..."
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Stone9 on 2008-02-19
Hi guys,

I had an existing install of Vista on my machine before I installed Ubuntu. After installing Ubuntu, my Vista install is missing. 

The drive is listed as SDA5, so when I insert a Vista option in the menu.lst with hd(0,4), it says it's missing.

When I use the Vista CD to do a recovery, it cannot find the Vista OS.

I've tried the bootrec, fixboot, fixmbr with no luck. I get errors that say the element cannot be found.

I've deleted my Ubuntu installation (very quick reinstall after I fix windows!)

Does anyone know what I can do to rescue my windows install?

Thanks,

Stone9

---

### Post by SunnyRabbiera on 2008-02-19
Err you might have really messed yourself up sorry to say.
There is a way to list windows in the boot menu list if you set a dual boot up, but if you used the re install disk you might have ruined your chances of using your current version of vista again.
Vista has a limited amount of how many times you can re install it, even more so then XP.

---

### Post by Yuki_Nagato on 2008-02-19
Was your version of Windows pre-installed from the distributer of the computer?  You might have chopped  up the Windows partition when installing Ubuntu.  If you used any(?) of the automatic partition setup options, and not the manual one, this might have happened.

---

### Post by SunnyRabbiera on 2008-02-19
Yeh and if that is the case you messed yourself up...
hopefully you have a option for recovery, if not you might be up the creek without the paddle.
But please do tell us what you did and perhaps we can help

---

### Post by jcitguy78 on 2008-02-19
Vista isn't very friendly and if your machine came already partitioned then you should have used GParted to redo the partitions. Sounds like you reformated the windows side.

---

### Post by Yuki_Nagato on 2008-02-19
Hopefully there is someone nearby who can feed you a decent boot CD of this three hundred dollar peice of eye candy software.  My feelings go to you otherwise.

---

### Post by Stone9 on 2008-02-19
It was a machine I built myself...

I think I may have muffed up the partitions :(

---

### Post by SunnyRabbiera on 2008-02-19
Yeh its a possibility, sorry.

---

### Post by Stone9 on 2008-02-19
I used the manual option in Ubuntu to create the ext3 and swap paritions. However, I didn't erase my Vista install, because it is still there. I can go into that partition in Ubuntu and see the files for the 64-bit Vista.

Does this mean there is stil a chance of a rescue?

---

### Post by teknosexual on 2008-02-19
> **Stone9 said:**
> I used the manual option in Ubuntu to create the ext3 and swap paritions. However, I didn't erase my Vista install, because it is still there. I can go into that partition in Ubuntu and see the files for the 64-bit Vista.

Does this mean there is stil a chance of a rescue?

Yes, that is good news. It is possible your boot sector got corrupted during partitioning (I just had this happen actually). 

You can download TestDisk:
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

It's a bootable ISO, so burn it, then reboot just like you would with a LiveCD.  You can skim through these pages to familiarize yourself with the program before using it if you want:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

We might need to do a few things here but let's start on this path:

- Select the hard drive where Vista is installed.
- Then next screen will be your partition table type: TestDisk automatically highlights the correct type (in most cases).
- Next, choose Analyse. 
- Once your partitions are listed, you'll want to make sure there is a * beside your Vista partition so that it is bootable. If your Vista partition is not listed there, then you'll need to do a Search for it.
- Then you'll need to Write the changes (if there were any).

Now let's look at your Boot sector:

- Back at the main screen, choose Advanced File System Utils and then NTFS: Boot and MFT Repair.
- The next screen (after choosing hard drive maybe?) should list two boot sectors, one of which is backup. Now, it may be the main boot sector is bad or the backup one, make sure you take notice which one. Of if they are both okay, exit out and see if you can boot Windows now.
- If one of the boot sectors is bad, we'll need to repair it. So if the main boot sector is bad, we'll overwrite it with the backup boot sector using the option: Backup BS. If the backup boot sector is bad, we'll need to choose the other option to overwrite the backup boot sector with the correct main boot sector: Orig. BS. Be careful here, and make sure you pick the right options!

If both boot sectors are bad, have a look at Rebuilding Boot Sector and Repairing MFT at the TestDisk FAQ:
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by jcitguy78 on 2008-02-19
do you get a gurb menu at boot up?

---

### Post by Stone9 on 2008-02-19
Thanks for the reply! However, I'm not sure I see the .ISO download. I see a few zip files. Do you know which one is the ISO?

---

### Post by Stone9 on 2008-02-19
Yes, I get the grub at startup, but no vista option. I edit the menu.lst, but it says it can't find the device.

---

### Post by teknosexual on 2008-02-19
> **Stone9 said:**
> Thanks for the reply! However, I'm not sure I see the .ISO download. I see a few zip files. Do you know which one is the ISO?

[http://www.cgsecurity.org/testdisk-6.9.linux26.tar.bz2](http://www.cgsecurity.org/testdisk-6.9.linux26.tar.bz2)

You'll need to extract it. The ISO is inside the archive.

---

