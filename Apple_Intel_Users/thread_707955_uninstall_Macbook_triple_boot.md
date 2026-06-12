---
title: "uninstall Macbook triple boot"
date: 2008-02-25
forum: Apple Intel Users
---

### Post by smocksturr on 2008-02-25
Okay, so, I have my drive set up like so:
1. Mac OSX
2. Ubuntu
3. Windows XP

I've enjoyed my little Linux trip for now and would like to regain my space on the Windows side of things.
Can I just remove the partition and resize the Windows one, or will Windows scream some weird error message at me because the boot order changed?

---

### Post by Sam Lars on 2008-02-25
Are you using the Linux Grub bootloader?  If you are, you'll have to reinstall whatever you were using before.

---

### Post by smocksturr on 2008-02-26
Nope, I'm using rEFIt to boot the OSes.  Grub purely boots Ubuntu.

---

### Post by cyberdork33 on 2008-02-26
There is no guarantee that everything will work afterwards. Most people that have done this only had dual-boot systems. I am sure that OS X will be OK, but Windows may be a problem.

---

### Post by smocksturr on 2008-02-26
So, this would be accurate then?

Me:  Half Life 2 EP2... 7 gigs. Hm...  A'ight, see ya later, Ubuntu.
Ubuntu: Try it, kid.  You take me down, I'm taking the whole system down.
Windows: Oh no! My boot.ini!
Mac: WTF, guys.  I'm sda1.


What exactly would you suggest, can I mess with boot.ini to set windows up as the second partition?

---

### Post by cyberdork33 on 2008-02-26
> **smocksturr said:**
> So, this would be accurate then?

Me:  Half Life 2 EP2... 7 gigs. Hm...  A'ight, see ya later, Ubuntu.
Ubuntu: Try it, kid.  You take me down, I'm taking the whole system down.
Windows: Oh no! My boot.ini!
Mac: WTF, guys.  I'm sda1.


What exactly would you suggest, can I mess with boot.ini to set windows up as the second partition?
Well, honestly, if you were just planning to "play" with Ubuntu, then i would never have partitioned and installed it in the first place. That is what VMs are for. (At least some other machine than your primary computer.)

I can't tell you want will happen because I have not tried to do what you are doing, but gathering from info that I have seen, Windows gets pretty upset when you change the partitioning scheme on the hard drive after it has been installed, so removing the Ubuntu partition(s) will likely give a similar problem (yes the hal.dll issue). Although the edit boot.ini solution should work, and has for some people, it hasn't for others, so you are still at risk.

If you have to remove Ubuntu, then do it, just make a backup of your game saves in Windows first because you might end up reinstalling.

Some edits to your scenario:
OS X doesn't have to be in sda1, you can put it wherever you want.
Ubuntu doesn't care if you remove it, Windows does (at least on a Mac it does). It does nothing malicious to your system to try to break windows.

---

### Post by smocksturr on 2008-02-26
I get ya, I was just doing so for the sake of giving computer operating systems personality.
Anyhow, yeah, to get the system to this point i had to reinstall windows about 7 times, so I figured I'd have to do it again.
I'll try what you said.
.

---

### Post by aletheianalex on 2008-02-26
OSX is easy... just clone the partition and then restore it later.  Windows is much harder.  What you need to do is use sysprep within XP to prepare the system for deployment on a new partition, then you can clone it and then restore it later.  Then wipe the drive and run the boot camp utility to set up the Mac/Win partitions and resotre your cloned systems.

Another option is just to boot from your OSX installer disk and wipe out the Ubuntu partition by formatting it as FAT32.  Then you can use it for storage for both OSX and XP since it will show up in both OS'es.   Windows should be fine with that... and if not, you can boot into a recovery console and fix the confused table.   That is the option  that I would take unless you are hell-bent on only having 2 partitions.

---

### Post by lex1 on 2008-02-26
I am not familar with sysprep?

"
"Another option is just to boot from your OSX installer disk and wipe out the Ubuntu partition by formatting it as FAT32"

other than windows, which other operating sysyems can run on FAT32?


lex1

---

### Post by aletheianalex on 2008-02-26
> **lex1 said:**
> I am not familar with sysprep?

"
"Another option is just to boot from your OSX installer disk and wipe out the Ubuntu partition by formatting it as FAT32"

other than windows, which other operating sysyems can run on FAT32?


lex1


Sysprep is a utility for mass deployment of a Win32 OS.  You can set it up to strip off all the HID/hardware/setup, etc, force PnP redetection so that you don't get craziness when you try to restore a clone (like the stupid HID not found or corrupt error) or move an XP install to a different drive.  If you just do a straight clone and then restoreit, you will PROBABLY not have a bootable system.  You can search on Windows boards and Microsoft knowledge base for details.  It is the recommended way of doing things if you have to move XP to another partition or a larger disk, etc.

My XP disk is OEM so it does not install sysprep  on my drive, so I have to boot from the XP CD and run the recovery console to expand the sysprep stuff from the .CAB file  to my install, and then boot into the install and run it from a command prompt.  I am sure there is an easier way to do it though.

As far as OS'es on FAT32... I am not sure.  I think OS/2 will run, a few *NIX, and later versions of DOS--I THINK 7.1, but I am not sure.  Most OS'es can read and write to it though, so I usually have a FAT32 partition around for swapping files between multi-booted OS-es.  There are a few versions of Slackware that ran on Fat32.  ReactOS will.

---

