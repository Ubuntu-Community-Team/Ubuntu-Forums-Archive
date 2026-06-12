---
title: "Root File System Not Defined"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by amneziac on 2007-08-02
I am trying to dual boot Windows and Ubuntu but when I get to the partition page it says that no root file system is defined.

/dev/hda1       ntfs          /media/hda1/    100027 MB     43500 MB
/dev/hda5       swap                                 100002 MB       3300 MB

The first partition is where Windows is installed and I set it as the root
The second is where I want Ubuntu installed and I made a swap but I'm still getting an error about the root file system not defined

---

### Post by undertakingyou on 2007-08-02
Do you have a swap partition?  You really should.  Nothing bigger than 2 GBs.

There should be something that you can click on to "edit" the partition, and there you can change the mount point from "swap" to "/".  After that say ok and then you should have it defined.

---

### Post by amneziac on 2007-08-02
/dev/hda5 swap 100002 MB 3300 MB <isnt that the swap partition?

---

### Post by amneziac on 2007-08-02
actually no its too big for it to be lol
how do i create a separate swap partition?

---

### Post by bodhi.zazen on 2007-08-02
You need a third partition for Ubuntu, the root or / partition, not just a swap partition.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by milosz.galazka on 2007-08-02
Hello,

I don't know if ntfs filesystem can be used on root partition. I thought that it can't. As bodhi.zazen said you need another partition for your root.

---

### Post by amneziac on 2007-08-02
ok so now I have 4 partitions
2 of them are ntfs
1 is swap
1 is root

now I want to make sure that I don't erase Windows XP
it asks me if I want to import the accounts documents and settings from Windows, so should i do so in order to keep both OS's?
Migration Assistant: Windows XP

so please just tell me if ive done the right thing in order to keep Windows XP on and if I should import the accounts on Windows in order to prevent Windows from being erased
Thanks

---

### Post by Raineer on 2007-08-02
As long as you didn't "delete" any of the NTFS partitions during all this your data should be fine.  You do *not* need to import them to keep them safe, this will just boot ubuntu with the pretty XP wallpaper (or whatever you had) and transfers over some other selections.

The main problem you had is you just misunderstood what is meant by "root", which is totally understandable.  Linux likes multiple partitions to run most effeciently and Windows doesn't (though I love a seperate swap partition for XP as well), the "root" you are asked to create is the Linux root.

Your "default" operating system when booting is set elsewhere, and that's maybe what you meant by root.

---

### Post by amneziac on 2007-08-02
Thanks a lot everyone, I'm gonan install Ubuntu now and hope it all goes well

Wish Me Luck!

---

### Post by amneziac on 2007-08-02
crap, when I was installing the OS, when it was almost finished it said Cannot Install GRUB (hda0), This is a fatal error.

:(:(:(:(:(:(:(:(

---

### Post by milosz.galazka on 2007-08-02
You can use ubuntu live cd to install grub on /dev/hda0 or on linux root partition but then remember that it must be active (cfdisk /dev/sd0 -> flags set to boot).

But I think that somebody will tell easier solution :)

---

### Post by bodhi.zazen on 2007-08-02
Just install grub to hda (not hda0) ...

We can walk you through manually grub installation if you need ...

---

### Post by groundhog on 2007-08-03
I have a couple questions:

(1) How big (or small) should the root file system partition be?  A post above said 'nothing larger than 2 Gb.'  But is there a lower limit to the size?  I have a partition that is 107 Mb, is that sufficient space?
-- Oops, that was swap space the post above referred to, not root system space. --

(2) Does ubuntu need swap space?  I also have a 1.1 Gb partition designated as swap, left over from the Red Hat installation.

Thanks in advance.  How did we ever get by before forums...?  :rolleyes:

- djb

---

### Post by milosz.galazka on 2007-08-04
> **groundhog said:**
> 

(1) How big (or small) should the root file system partition be?  A post above said 'nothing larger than 2 Gb.'  But is there a lower limit to the size?  I have a partition that is 107 Mb, is that sufficient space?
-- Oops, that was swap space the post above referred to, not root system space. --



1. It depends on your needs and goals. 107Mb can be sufficient if you assign other partitions to /home, /usr, /var. 

If you want to use that system at home then create bigger root partition and after some time you will know what are your needs.  

Using one big root partition is easier to start with it but it will be good to use separate partition for /home so you could preserve user directories if you reinstall os.

2Gb limit apply only to older computers where root partition can be bigger but kernel needs to be in the first 2Gb of hard drive or it will not boot.

> **groundhog said:**
> I have a couple questions:

(2) Does ubuntu need swap space?  I also have a 1.1 Gb partition designated as swap, left over from the Red Hat installation.



2. Swap partition suggested size is 2 x installed memory but it depends on applications you use and size of memory you installed. My home computer has 1 Gb RAM and swap partition is just 256 Mb (~40 Mb used). I can go without it and nothing wrong will happen but I use this computer mainly for browsing.

---

### Post by groundhog on 2007-08-05
OK, I was a bit confused about the root partition, it's the amount of disk space allocated for the entire Linux installation.  I was thinking it was just for the boot files. Once I got that squared away I was ready to install ubuntu.  But I could not get ubuntu version 7.0.4 to install.  I burned two CDs from two different ISOs.  I kept getting the apparently well known debootstrap error.  
[ [http://ubuntuforums.org/archive/index.php/t-76316.html](http://ubuntuforums.org/archive/index.php/t-76316.html) ]
So I downloaded the earlier version 6.06.1 ISO, and it installed without incident. I think the 7.0.4 version of the ubuntu install has issues.  

So now I have ubuntu loaded and working great, but the grub boot loader is still not working properly.  It's the exact same issue I had with RedHat:  grub cannot boot the Windows OS located on the secondary disk (i.e., a disk other than the one grub is installed on.)
[RedHat bug report: [https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=115980](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=115980)  ] 
The problem is apparently a deficiency in the way Windows boots, but I'm starting to believe this is also a SATA issue.

In the GNU grub online manual, in the DOS/Windows section of installation notes, it talks about mapping the drives to trick Windows into thinking it is on the primary drive when it really isn't.  After that discussion, there is this note of caution:
"This is effective only if DOS (or Windows) uses BIOS to access the swapped disks. If that OS uses a special driver for the disks, this probably won't work."
[grub manual: [http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows](http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows) ]

It is, in fact, the case that the bios on my mobo does not recognize SATA drives, and there is a "special driver" (Silicon Image SI3112) for both SATA drives on my PC.  So it looks like I may have to resort to switching the cables on my SATA drives in order to boot the new Windoze OS... :cry:

- djb

system:
AMD Athlon XP Barton 2800+
Asus A7N8X-E Deluxe mobo
1 Gb Kingston dual channel DDR RAM
80 Gb Seagate ST380013 SATA hard drive
   (primary disk with ubuntu and WinXP SP1)
400 Gb Western Digital WD4000AAKS SATA hard drive
   (secondary disk with WinXP SP2)

---

### Post by puner on 2007-12-19
Sorry to dig an old thread, but i rather do this than make a new thead.

Im having the exact same problem. I have three partitions made on windows. 1) xp 2) vista 3) ubuntu.

The only OS installed on my system is xp right now.

When I go into the LiveCD and choose to manually install ubuntu I choose the ext3 partition made for ubuntu on windows.

But I get:

```

No root file system is defined

```

Screenshot: [http://imagenerd.com/show.php?_img=screenshotpJ1M.png](http://imagenerd.com/show.php?_img=screenshotpJ1M.png)

Im sure that i have not made that "swap" partition. 

Where do I make it and how big does it have to be?

---

### Post by bodhi.zazen on 2007-12-19
Swap = RAM x2, max 1 Gb

Or if you have a laptop and want to suspend / sleep swap = ram

There is a bug in the installer, this may help :

[http://ubuntuforums.org/showpost.php?p=1700787&postcount=29](http://ubuntuforums.org/showpost.php?p=1700787&postcount=29)

---

### Post by puner on 2007-12-19
Alright so I made a 512 mb swap partition and the rest on " / " and installed ubuntu fine.

When I boot it goes into WinXp right away because that partition is my primary and the rest are logical.

Do I need to edit the settings in bios to boot ubuntu first over WinXp?

---

### Post by bodhi.zazen on 2007-12-19
No, you have to install grub :

Line this ; (don't let the title fool you)

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

### Post by psusi on 2007-12-19
> **puner said:**
> Sorry to dig an old thread, but i rather do this than make a new thead.

Im having the exact same problem. I have three partitions made on windows. 1) xp 2) vista 3) ubuntu.

The only OS installed on my system is xp right now.

When I go into the LiveCD and choose to manually install ubuntu I choose the ext3 partition made for ubuntu on windows.

But I get:

```

No root file system is defined

```

Screenshot: [http://imagenerd.com/show.php?_img=screenshotpJ1M.png](http://imagenerd.com/show.php?_img=screenshotpJ1M.png)

Im sure that i have not made that "swap" partition. 

Where do I make it and how big does it have to be?


That's because you have not defined a root ( / ) partition.  Your ext3 partition is set to be mounted as /media/sdb5, not /.

---

### Post by puner on 2007-12-19
Alright sweet Ubuntu installed. But GRUB did not, so right now it just boots WinXp. My boot partition is hd1,5.

Using the "Quick Start" option found here;

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I cannot figure if for me it should be:

grub> setup (hd**1**) #Hit <Enter> key
or
grub> setup (hd**a**) #Hit <Enter> key

Also, what does the number sign mean at the end of the code line, do I need to put that in?

---

### Post by bodhi.zazen on 2007-12-19
# = comments

setup (hd0)

---

### Post by puner on 2007-12-24
Ok it worked, it installed. But when I choose to run ubuntu  from the boot menu, all I see is a blank screen  forever. I see the option to run Windows Xp on boot menu too and it runs fine.

---

### Post by puner on 2007-12-25
Okay I finally installed it, but Im getting "error 21" on booting GRUB

---

### Post by bodhi.zazen on 2007-12-26
Sounds like grub is mis configured. Hard to know exactly.

Here is some information about an error 21 :

[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

You can try Supergrub or post the contents of /boot/grub/menu.lst


[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

