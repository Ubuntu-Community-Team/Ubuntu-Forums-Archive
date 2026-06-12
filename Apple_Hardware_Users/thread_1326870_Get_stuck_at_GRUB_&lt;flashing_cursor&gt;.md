---
title: "Get stuck at GRUB &lt;flashing cursor&gt;"
date: 2009-11-14
forum: Apple Hardware Users
---

### Post by colinhh on 2009-11-14
Hi,

I'm trying to get Ubuntu 9.10 running on my MacBook Pro (hardware 5.1).

It did actually boot from the hard disk once, but then I started downloading some packages, and since then the boot procedure doesn't get further than displaying GRUB and a flashing cursor.


Not sure where even to look for the problem. I thought I'd followed the instructions on the wiki (except that I *did* create a swap partition).

I had (and still have, I assume) Windows XP Professional installed previously (using Bootcamp).

My disk partitions look a little odd now:

sda1: the efi thingy
sda2: Mac OS X on HFS+
sda3: Linux on ext4
sda5: swap
sda4: Windows XP


Reinstalling Ubuntu doesn't help, neither did the *sync*.efi (forgotten the exact name now) command in the rEFIt shell.


I've been away from Linux for several years now - and am a bit Mac damaged. You know: double-click on a *.dmg click, click &#8212; it works. And while I have scrambled around under desks, with a torch, trying to read the exact number on various ethernet and graphics chips, that's a while back now. I'm not used to it any more.

What this means is, I don't feel like deciphering someone's shell scripts and looking at the rEFIt and/or GRUB source code in order to get Linux to boot. I know &#8212; I sound lazy and ungrateful. Sorry, frustration does that to me.

---

### Post by 311005901 on 2009-11-14
I've got the same problem. My partition table is almost exactly the same as yours, the only difference is I have Vista.

I think the problem has to do be something with the location of GRUB. Do you know where you installed it?

---

### Post by colinhh on 2009-11-14
Hmmm,

first time round I didn't change anything in "Advanced", so it might have tried the MBR (assuming there is one). Next time around I think I followed the Installing on an intel Mac wiki a bit better and put it in /dev/sda3. I think it worked a bit after that. Then I started reading some GRUB documentation and saw that it had (hd0) as default. So I changed that to (hd0,2).

In principle, I'm pretty sure it's supposed to be /dev/hda3 (ie. the partition where Linux is).

BTW, wonderful idea inventing a new ambiguous meaning for "device". But then the Ubuntu installer doesn't seem to mind one way or the other :-)

I suppose it's important for a boot loader to have support for skins, but I have to admit I miss lilo's single config file and confirmation of what it's done.

I thought there might be some problem with screen modes, because during boot from the CD the Ubuntu icon appears centred on (at a guess) 400,300 then there's some ugly screen mode experimentation and eventually it jumps to the correct 720,450.


The thing is, I don't really want to **learn** GRUB. I want to download some files to an ext3 partition on a flash drive, so that I can carry on with my actual project. Unfortunately the ext3 for OS X software doesn't compile under OS X 10.6.2 (thank you Apple, now I can work with all those 4+ Gbyte files I have).


Nice that Mac OS X still boots though.

---

### Post by tom4everitt on 2009-11-15
From my experience, two things are required for linux to boot on a mac:

1. partion tables in sync (easily fixed with refit partitioner).

2. grub correctly setup. This should be the case after a fresh install. Generally I think grub installed to (hd0) works better than grub installed to (hd0,2) (both places simultaneously will work fine too). 

It is quite easy to install grub again from a live cd (without reinstalling the entire system). All you have to do is to boot from a live-cd and follow this guide:
[http://www.supergrubdisk.org/wiki/Howto_Fix_Grub#GRUB_solution_.28Linux_shell.29](http://www.supergrubdisk.org/wiki/Howto_Fix_Grub#GRUB_solution_.28Linux_shell.29)

---

### Post by colinhh on 2009-11-18
> This should be the case after a fresh install.

Thanks, it should be, yes. :)


I actually tried installing elilo (using apt-get install) yesterday. A penguin icon appeared in rEFIt. Clicking on it resulted in an elilo screen and error along the lines of "operation not supported". The docs suggested running elilo.efi directly to get better error messages. I managed that (eventually - EFI seems to have a bit of a DOS mentality) and got an error along the lines of "32 bit efi command not supported on 64 bit EFI system".

Aha!

I downloaded the latest elilo from sourceforge.

I thought of doing a compile but apt-get didn't find gnu-efi, so I just tried the supplied x86-64 version of elilo.efi.

That worked! - except that it hung after (or during?) the loading of the initrd.

*sigh*

Anyway, that got me wondering whether there's some 32/64 bit problem going on?

---

