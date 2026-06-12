---
title: "Problem booting Grub Error 22"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by LethalLavaLand on 2008-03-31
Hi. I had a dual boot Vista/Ubuntu but decided to remove Ubuntu because I wanted to switch to 100% Vista and then a Virtual PC with Ubuntu.

So I went into diskmanagement and removed the partitions containing Ubuntu and allocated the free space to my other partitions.

Everything seemed ok. However, when I restarded the computer I get the error mentioned in the title.

I would be forever grateful if someone could take their time and help me with this. I know it's my fault for being stupid but please help.

I thought of 2 solutions. Possibly installing Ubuntu again. Or getting a Vista DVD and booting from that and choosing "repair". Would this work? Is there some easier way?

---

### Post by luceerose on 2008-03-31
I have never used Vista, but I understand that Vista's install disc can repair an mbr.

---

### Post by bumanie on 2008-03-31
The best way would be to repair vista's mbr with an installation disk, You could however try super grub disc (get the live cd version) from here [http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)
It can repair windows mbr, at least it does xp, not 100% sure with vista.
Another way would be to download test disc and if ubuntu and vista are the only two OSes that have been on your computer, test disc could retrieve the vista partition at the stage it was prior to you installing ubuntu. Get test disk here (live cd again)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
Vista installation disc is really the easiset option if you have one.

---

### Post by LethalLavaLand on 2008-03-31
I have a Vista installation disc now. And I have booted my comp with it. But when I select "repair this PC" it doesn't detect an operating system. Am I screwed?

It says that if one doesn't see one's operating system listed then one should "load drivers" but I'm unsure what to search for...

Edit: Nevermind searching for anything, I can't access my files anyways =o...

---

### Post by LethalLavaLand on 2008-03-31
Ok. I am currently just re-installing Linux. It seems to be able to find my hard drives and everything just fine.

I chose "guided - resize partition and use free space". But when I come to the window just before installation it says that it will format "partition#2" and "partition #5".

By this I hope it doesn't refer to my two partitions that I have? I don't want to lose my files on them...

Does the counting start at #0 ? That is, is it possible that my old partitions are partition #0 and partition #1 and will not be touched?

Edit: it seems that from ubuntu live cd I have complete access to my old partitions. Surely there must be someway I can fix this now?

---

### Post by bumanie on 2008-03-31
Before you go any further, you should get a gparted live cd and provide screenshots of how the drive/s are set up. Also read this 
Quoted from the GNU/GRUB manual

    22 : No such partition
        This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 

For example there might be a mistake in the menu.lst file in the partition number, if there is no such partition as specified in the 'root (hdx,y)' line.
example,
title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
Look at your partitions with your partitioning software or run 'sudo fdisk -lu' in a terminal and make sure you have the partition number correct here in your menu.lst boot entry.

This is also the error that people often see after they delete their Linux partition but they still have that partition's GRUB's stage1 written in the MBR.

They can easily cure that by overwritting the existing GRUB IPL code with code for another bootloader in another operating system.
In other words either re-install GRUB or re-install Windows bootloader or some other bootloader or boot manager. In Super GRUB Disk, go 'English Super Grub Disk'-->'Windows'-->'Fix Boot of Windows', or see my 'Un-install Page'.
Don't bother doing anything if a new (Linux) operating system will soon be installed, the new operating system will install a new bootloader and cure this error automatically.

If there is another operating installed in the computer, re-writing the bootloader'e MBR code for that operating system's bootloader and overwriting the now useless GRUB code will cure the problem. This can be easily done with Super GRUB Disk.
1) Re-install a GRUB to MBR from another Linux
2) Re-install a Windows Bootloader to MBR.
     (These two above items are both options in Super Grub Disk that can be selected and SGD will do it for you).

I got GRUB error 22 myself one time after doing quite a lot of work to the partitions in my wife's computer. I tried to fix the boot of grub with an older version of Super Grub Disk, not realizing her partition numbers had been unexpectedly changed somehow by disk partitioning software.
I installed grub from the wrong partition by accident.
Later I found out the real cause of all the trouble was a dirty DVD/CD-ROM drive that caused read problems from my partitioning CD.

 Anyway I got  Grub Loading Stage1.5
       Grub Loading Stage1.5
       Grub Loading Stage1.5
       Grub Loading Stage1.5...and so on, scrolling endlessly down the monitor.

I couldn't even boot with Super Grub Disk's 'English Menu'-->'Gnu-Linux'-->Boot Gnu/Linux Directly'.
After much mumbling and head scratching and trying various ideas I decided to run a file system check with my GParted -- LiveCD. When that was done I clicked on the triangular buttons for a report and found that GParted LiveCD had repaired quite a few problems in that filesystem.

So tried again, this time from the Super Grub Disk menu I pressed 'c' for a Super Grub Command Line Interface, and booted manually using a direct kernel style boot
The operating system booted and I was able to re-install Grub to MBR, and configure menu.lst with new partition numbers.

GParted LiveCD saved the day for me. I didn't have to sleep in the doghouse after all! :)
The lessons here are,
1. keep my CD-ROM drives clean, and
2. to try a filesystem check if I am having unusual troubles booting.

It's easy to run a file system check on any file system with a GParted -- LiveCD, just boot with the CD and click on the filesystem (partition) to be checked and click 'check'.
Click 'Apply' (on the toolbar), and then 'Apply' again (in the confirmation box).
Then wait a few minutes.
When it's finished it's a good idea to click on the arrow shaped 'Details' button in GParted to expand the output box. Make sure you click on all the subsequent arrow buttons too, so you will expand it all fully so you can read the report and see what was done to fix your file system.
See my File Systems and Mounting Page for more about file system checking in Ubuntu.

That is from this site that has heaps on grub
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by LethalLavaLand on 2008-03-31
"This is also the error that people often see after they delete their Linux partition but they still have that partition's GRUB's stage1 written in the MBR."

That sounds exactly like my problem.

Thank you for that post. I will try Super Grub and see what happens.

---

### Post by LethalLavaLand on 2008-03-31
Super Grub worked out great! Thank you so much!!! This topic may be closed.

---

