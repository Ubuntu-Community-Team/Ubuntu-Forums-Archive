---
title: "Totally Lost at Where To Begin...."
date: 2005-08-23
forum: Absolute Beginner Talk
---

### Post by Slayer213 on 2005-08-23
I downloaded and burned the X86 iso of Ubuntu, no problems there.

Shut down Windows XP Pro, and the CD booted when I started the PC again.

I let it go through all the options, network etc but I got stuck with the Partition part. I have a 6.6gb hidden partition, which is in use, and I have another 6gb partition which is visible as another drive in Windows and is NTFS. 

But when I was in the Ubuntu setup, it didn't detect the partition I made.

How do I make a new partition from the HD that Windows is on inside the Ubuntu setup?? ](*,)

---

### Post by Knome_fan on 2005-08-23
If I understand you correctly, your problem is that your windows partitions don't show up in Ubuntu.

Unfortunately, there isn't a graphical tool right now in ubuntu, though there will be in the next version. However, do not despair, but take a look at the ubuntuguide:
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

Also take a look at the wiki:
[https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windows%29](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windows%29)


Hope this helps!  :grin:

---

### Post by Lord Illidan on 2005-08-23
It also depends on the size of your HDD? If it is too small, I recommend against partitioning, and towards putting a new hard drive..

---

### Post by Slayer213 on 2005-08-23
[QUOTE=Lord Illidan]It also depends on the size of your HDD? If it is too small, I recommend against partitioning, and towards putting a new hard drive..[/QUOTE]
 i got 80gb hdd.

What Partition types are valid for installing Ubuntu on?

Also, how do I make it so that I can choose which OS i want to start with (Dual Boot)

For the links Knome_fan posted, where do I enter all that stuff, I havent even got Ubuntu installed yet :(

---

### Post by Stormy Eyes on 2005-08-23
[QUOTE=Slayer213]What Partition types are valid for installing Ubuntu on?[/quote]

ext3, reiserfs, xfs -- none of these are Windows-compatible filesystems, and you can't install on FAT32 or NTFS.

[QUOTE=Slayer213]For the links Knome_fan posted, where do I enter all that stuff, I havent even got Ubuntu installed yet :([/QUOTE]

Have you considered using a LiveCD first? If you configure your PC's BIOS to boot from the CD-ROM before booting from the hard drive, you can use a LiveCD to try out Linux and get used to it before altering your Windows setup.

---

### Post by Slayer213 on 2005-08-23
[QUOTE=Stormy Eyes]ext3, reiserfs, xfs -- none of these are Windows-compatible filesystems, and you can't install on FAT32 or NTFS.



Have you considered using a LiveCD first? If you configure your PC's BIOS to boot from the CD-ROM before booting from the hard drive, you can use a LiveCD to try out Linux and get used to it before altering your Windows setup.[/QUOTE]
 its just that..... downloading 600-700mb isnt fun with 256k internet......

ill try it though

---

### Post by Stormy Eyes on 2005-08-23
[QUOTE=Slayer213]its just that..... downloading 600-700mb isnt fun with 256k internet......[/QUOTE]

Try installing [Gentoo Linux](http://www.gentoo.org) with 56K dialup. You can probably download the ISO for the LiveCD overnight.

---

### Post by Slayer213 on 2005-08-23
[QUOTE=Stormy Eyes]Try installing [Gentoo Linux](http://www.gentoo.org) with 56K dialup. You can probably download the ISO for the LiveCD overnight.[/QUOTE]
 no need for this thread. Ubuntu installed im posting from it now :)

---

### Post by Stormy Eyes on 2005-08-23
[QUOTE=Slayer213]no need for this thread. Ubuntu installed im posting from it now :)[/QUOTE]

Welcome to Ubuntu, then.

---

