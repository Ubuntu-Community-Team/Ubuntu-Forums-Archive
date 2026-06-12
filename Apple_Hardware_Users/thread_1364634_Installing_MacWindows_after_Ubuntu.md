---
title: "Installing Mac/Windows after Ubuntu"
date: 2009-12-26
forum: Apple Hardware Users
---

### Post by gdavge2003 on 2009-12-26
Here's my situation: my Macbook Pro 2.1's Mac OS X completely died (kernel panic). A friend told me about Ubuntu a few days ago, and I installed Karmic on a cleanly reformatted HDD on my MBP. It works great and after some tweaking, I'm absolutely sure I got everything up and running, with the exception of the iSight webcam.

I will be reinstalling a Mac OS (Snow Leopard) once my ordered installation disks arrive, and afterward, I'll be using Bootcamp to install a copy of Windows 7.

My worry: how's the partitioning going to work? I only know some of the basics in partitioning (came from googling and reading about all the options Ubuntu offered for partition during my installation of it). Currently, I have 3 partitions:
- /dev/sda1 Unknown (977 kb)
- /dev/sda2 ext4 (143.33 gb)
- /dev/sda3 linux-swap (5.72 gb)

I'm not sure if they're primary or logical partitions, but I do know that all 3 are needed for Ubuntu to run. I read somewhere that a single HDD can only have 4 primary partitions. Also, Windows must be installed on a primary partition for it to work.

I don't want to reinstall Ubuntu again, as I did a lot of configurations/tweaks on it. So I'm wondering, is it possible to do the following?
- Resize partition of sda2 ext4 to allocate space for Mac/Windows (using gParted)
- Convert partitions to logical partitions (how would I do this?)
- Create a hfs+ partition and install Mac OS X 10.6 (using Mac installation disk)
- Create a ntsf partition using remaining disk space (using Bootcamp)

Would these steps work? Is there some flaw in them? Would I lose any data by resizing my Ubuntu partition? Any help is greatly appreciated!

---

### Post by phillw on 2009-12-26
Hi, I'm not upto speed with Macs, but on your partitioning issue.
Yes, you can only have 4 primary partitions.

If you're after running Win, Ubuntu & Mac, then I'd be hedging my bets to make one of your primary partitions into an extended partition.

How and where / what Mac requires I don't know.

I'm guessing (and it is a best guess, on what Mac's use) that /dev/sda1 is the Mac boot sector 

For the ubuntu area, it is easy.

Make one of your primary partitions into an extended partition.

For example, /dev/sda3 - That'd leave sda1 & sda2 free for mac and win to fight over ;-)

You can then put ubuntu onto that extended area either as
/dev/sda5 = /swap
/dev/sda6 = /

Or,

/dev/sda5 = /swap
/dev/sda6 = /
/dev/sda7 = /home

Having a seperate /home is advantageous if you plan on doing upgrades from 9.10 -> 10.04 etc...

The others on here will be able to tell you if you should use Grub2 as your boot-loader or a different boot-loader.

Regards,

Phill.

---

