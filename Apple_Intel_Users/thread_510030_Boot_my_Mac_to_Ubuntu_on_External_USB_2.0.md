---
title: "Boot my Mac to Ubuntu on External USB 2.0"
date: 2007-07-26
forum: Apple Intel Users
---

### Post by tigerplug on 2007-07-26
I have searched the forums here but nothing that I have found seems to cover this in just the way that I need.

I have an iMac Core 2 Due and an External 40GB USB 2.0 Drive.
I want to boot my Mac to Ubuntu - (Having Ubuntu installed on the USB Drive)

How can I go about this?
Is it just an option in the Ubuntu setup?

I have heard people talking about setting up the "Swap" - I'm going to assume that this means allocation of virtual memory. Is this correct?

Also my hard drive is formatted as HFS+ , I don't mind formatting it again but, I would like to know if Ubuntu will support HFS+


Any advice is appreciated.

Thanks

---

### Post by tigerplug on 2007-07-26
Any help on this one guys?

---

### Post by redfox on 2007-07-26
I'm also interested in this question now that I have a Firewire external drive.  What is the process for getting an install set up?

---

### Post by cyberdork33 on 2007-07-26
From what I have seen in other threads, people are unable to get that kind of setup working correctly. unsure why.

and yes Ubuntu can mount HFS+

---

### Post by tigerplug on 2007-07-27
> **cyberdork33 said:**
> From what I have seen in other threads, people are unable to get that kind of setup working correctly. unsure why.

and yes Ubuntu can mount HFS+

Thanks for the reply. :)


When you say that Ubuntu can "mount" HFS+ do you also mean that Ubuntu can be installed on HFS+ partitions?

---

### Post by cyberdork33 on 2007-07-27
> **tigerplug said:**
> Thanks for the reply. :)


When you say that Ubuntu can "mount" HFS+ do you also mean that Ubuntu can be installed on HFS+ partitions?

Well, I would assume that could be done, but I would definitely **not **recommend it. Grub (and other bootloaders) probably can not read HFS+, so you would have to have a separate /boot partition with a different filesystem, and furthermore, you would probably need a kernel with hfs+ support compiled in, and install hfsplus filesystem tools. So, yes, you **might** be able to get that working, but it would take **extra work**, and would be more appropriate to try with something like gentoo, so don't do it unless you just want to experiment, and expect to reinstall differently the next day.

---

### Post by tigerplug on 2007-07-27
> **cyberdork33 said:**
> Well, I would assume that could be done, but I would definitely **not **recommend it. Grub (and other bootloaders) probably can not read HFS+, so you would have to have a separate /boot partition with a different filesystem, and furthermore, you would probably need a kernel with hfs+ support compiled in, and install hfsplus filesystem tools. So, yes, you **might** be able to get that working, but it would take **extra work**, and would be more appropriate to try with something like gentoo, so don't do it unless you just want to experiment, and expect to reinstall differently the next day.

Sounds good to me!

I don't mind experimenting with it at all, Im here to learn.

;)

---

### Post by cyberdork33 on 2007-07-27
> **tigerplug said:**
> Sounds good to me!

I don't mind experimenting with it at all, Im here to learn.

;)

well here would be my suggestion... Make a /boot partition that is ext2/3, and make your / parition hfs+. You will have to deal with any errors along the way as they occur. I have no idea if ubuntu will stop you from installing onto hfs+ or not, and even if it does install, I seriously doubt that it will boot after it finishes. LiveCD's and chroot will be your friend.

---

### Post by ripdog on 2007-08-03
I tried that, with a USB external drive, in an ext3 partition. Trying to boot just gave a nice, welcoming black screen, not even a error message. Oh well.

---

### Post by kson on 2007-08-03
I just got it to work on my Macbook C2Duo 2.0!

Nothing worked until I used a 100mb big partition on my main harddrive as /boot and installed grub on that instead of any MBR. Now Refit shows Mac, Win and Linux on the main drive. Then grub is responsible for loading ubuntu from the external drive.

Now I got MacOSX, Windows XP and /boot on the internal 80gb drive and Ubuntu on an external 300gb drive.

Happy Days! Ubuntu works great on a Macbook! Even my bluetooth mouse!

---

### Post by cyberdork33 on 2007-08-03
> **kson said:**
> I just got it to work on my Macbook C2Duo 2.0!

Nothing worked until I used a 100mb big partition on my main harddrive as /boot and installed grub on that instead of any MBR. Now Refit shows Mac, Win and Linux on the main drive. Then grub is responsible for loading ubuntu from the external drive.

Now I got MacOSX, Windows XP and /boot on the internal 80gb drive and Ubuntu on an external 300gb drive.

Happy Days! Ubuntu works great on a Macbook! Even my bluetooth mouse!

well you are really loading up linux, and it is reading the external drive. as long as the bootable partition is on the main drive I think you are good.

---

### Post by pxwpxw on 2007-08-04
> **kson said:**
> I just got it to work on my Macbook C2Duo 2.0!

Nothing worked until I used a 100mb big partition on my main harddrive as /boot and installed grub on that instead of any MBR. Now Refit shows Mac, Win and Linux on the main drive. Then grub is responsible for loading ubuntu from the external drive.

Now I got MacOSX, Windows XP and /boot on the internal 80gb drive and Ubuntu on an external 300gb drive.

Happy Days! Ubuntu works great on a Macbook! Even my bluetooth mouse!

Good one.
Trying it here on my C2D with a USB flash stick.

---

### Post by kson on 2007-08-04
> **cyberdork33 said:**
> well you are really loading up linux, and it is reading the external drive. as long as the bootable partition is on the main drive I think you are good.

Exactly.

I think you have to partition with gma (or whatever they call their efi partitiontable) if you want to boot from the external drive directly

---

### Post by cyberdork33 on 2007-08-05
> **kson said:**
> Exactly.

I think you have to partition with gma (or whatever they call their efi partitiontable) if you want to boot from the external drive directly

Well that is not true entirely, because you can reformat the entire drive as a legacy MBR-only table, and it will still boot. Maybe for externals? BTW, it is GPT (GUID Partition Table).

---

### Post by kson on 2007-08-07
> **cyberdork33 said:**
> Well that is not true entirely, because you can reformat the entire drive as a legacy MBR-only table, and it will still boot. Maybe for externals? BTW, it is GPT (GUID Partition Table).

GPT it is! :popcorn: I hate those three letter names...

---

### Post by garethrv on 2007-09-18
I know I am VERY late.

But I am far from a hard core linux user and I was able to get 7.04 running (as it is right now) from my 40gig 2.5inch external.

All I did was run the live (64 bit) cd, then install to the external which I had formatted to MS Dos (I am pretty sure you cannot run from HFS) and then when that was done and my MBC2D would not recognise the drive at boot, I rebooted in the live 7.04 CD (OSX would not recognise the exteral drive either anymore) and then through terminal I just had to flag the external as bootable and now when I boot and hold option, I get to choose from my internal drive and "Windows" (Which is actually my external ubuntu install)

1 issue, I tried plugging the drive into my brothers MBP which has XP installed through bootcamp. It did not see my drive, only windooze and OSX.

Hope my belated response serves someone.

I will go and try an hunt down the commands I used to flag the drive, They were pretty simple.

If anyone knows them, please share. I know it brought up a list of things and I selected to flag the external to boot.

I love linux. As much as I love OSX also, i think just the vibe of using an opensource operating system makes it special! ha ha.

---

### Post by pxwpxw on 2007-09-19
> **garethrv said:**
> I know I am VERY late.

But I am far from a hard core linux user and I was able to get 7.04 running (as it is right now) from my 40gig 2.5inch external.

All I did was run the live (64 bit) cd, then install to the external which I had formatted to MS Dos (I am pretty sure you cannot run from HFS) and then when that was done and my MBC2D would not recognise the drive at boot, I rebooted in the live 7.04 CD (OSX would not recognise the exteral drive either anymore) and then through terminal I just had to flag the external as bootable and now when I boot and hold option, I get to choose from my internal drive and "Windows" (Which is actually my external ubuntu install)

1 issue, I tried plugging the drive into my brothers MBP which has XP installed through bootcamp. It did not see my drive, only windooze and OSX.

Hope my belated response serves someone.

I will go and try an hunt down the commands I used to flag the drive, They were pretty simple.

If anyone knows them, please share. I know it brought up a list of things and I selected to flag the external to boot.

I love linux. As much as I love OSX also, i think just the vibe of using an opensource operating system makes it special! ha ha.

**That is very interesting**.

I have a MacBook C2d here with ubuntu installed on an external WDC MyBook 300Gb, Msdos paritioning system. 
 I can only boot that external system ubuntu by using a boot partition with kernel and initrd on the internal drive. 
 I have Macox with refit, ubuntu, and Windows XP all on the internal drive, I think that may be the issue. Tried both firewire and usb, also setting the boot flag with fdisk, and setup grub stage1 on the external MBR and on the ubuntu root partition. Firewire external is seen by both Apple and Refit boot menus, usb only by refit - but neither will boot directly.


I would like to know:
Do you have only Macosx on the internal drive, or what.
Does your external system boot for both firewire and usb.
Any other comments.

---

### Post by cyberdork33 on 2007-09-19
> **pxwpxw said:**
> **...** also setting the boot flag with fdisk, ...

Note that fdisk WILL NOT update GPT, you need something like parted / gparted. You said the disk is a normal MBR so it may not matter, but the Mac may not recognize it as bootable still. Just some extra info.

---

### Post by pxwpxw on 2007-09-20
> **cyberdork33 said:**
> Note that fdisk WILL NOT update GPT, you need something like parted / gparted. You said the disk is a normal MBR so it may not matter, but the Mac may not recognize it as bootable still. Just some extra info.

Yes, thanks, understood, but I was checking out the situation for a MBR only external drive, no GPT to sync.

Might try GPT on the external later, or some sort of HFS boot partition.

But I think the limitation is probably in the Apple firmware dealing with the external device at startup.

Reverse engineering is fun.

---

### Post by entangled on 2007-09-20
I haven't done much testing on this but I have got consistent install and boot from external USB drive for MacOSX + Ubuntu + Sidux.

My main decision was to ensure that the external drive is MBR layout (not GPT - use OSX Disk Utility to set it). I think the Mac can detect either and start boot but the grub loader will fail on a GPT drive. 
It would be nice if grub could deal with GPT - it allows many partitions (but I suppose MBR does too, with the extended partition).

---

### Post by cyberdork33 on 2007-09-20
Grub 2.0 should have support for GPT. Maybe creating the MBR with Disk Utility is the key here. It should know how to set everything up to get a bootable volume.

---

### Post by garethrv on 2007-09-23
Hey,

My internal drive only has OSX installed. As I think I mentioned in my other post, when I plug the drive into my brothers MBPro which has windows and osx on the internal, I dont get an option to boot my drive.

Also, I got a bit fed up with the 64bit issues and downloaded 7.04 i386 live CD and formatted the external and reinstalled the new system. This time when I held down option the first time I booted with the fresh install it gave me the option to boot from the drive. No flagging required. Was quite happy as I was not able to find the command I used the first time anyway.

As I mentioned, I am new to this, so you may have to ask me specifics to get the info you need. I am more than happy to answer whatever you throw at me.

Just checked disk image, my internal is definitely just the one partition, which is home to OSX.

I just selected the usb drive when it asked me to install on the live cd (After I formatted it to MS Dos in OSX Disk Util) and selected to use the whole drive (Format it and start from scratch)

Its working great. (Apart from the wifi, which madwifi fixed on my 64bit install but now wont do so on my new install.... im lost)

Hope this helps.

---

### Post by garethrv on 2007-09-23
Oh, also, the usb drive I am using (40Gb 2.5 inch bus powered drive) is only usb 2.0 so I cant comment on the firewire.

Sorry.

---

### Post by pxwpxw on 2007-09-24
> **entangled said:**
> I haven't done much testing on this but I have got consistent install and boot from external USB drive for MacOSX + Ubuntu + Sidux.

My main decision was to ensure that the external drive is MBR layout (not GPT - use OSX Disk Utility to set it). I think the Mac can detect either and start boot but the grub loader will fail on a GPT drive. 
It would be nice if grub could deal with GPT - it allows many partitions (but I suppose MBR does too, with the extended partition).

Could you say where everything was with respect to internal and external drive? 
I see that the sidux manual has a usb stick install option.

---

### Post by pxwpxw on 2007-09-24
> **garethrv said:**
> Hey,

My internal drive only has OSX installed. As I think I mentioned in my other post, when I plug the drive into my brothers MBPro which has windows and osx on the internal, I dont get an option to boot my drive.

Also, I got a bit fed up with the 64bit issues and downloaded 7.04 i386 live CD and formatted the external and reinstalled the new system. This time when I held down option the first time I booted with the fresh install it gave me the option to boot from the drive. No flagging required. Was quite happy as I was not able to find the command I used the first time anyway.

As I mentioned, I am new to this, so you may have to ask me specifics to get the info you need. I am more than happy to answer whatever you throw at me.

Just checked disk image, my internal is definitely just the one partition, which is home to OSX.

I just selected the usb drive when it asked me to install on the live cd (After I formatted it to MS Dos in OSX Disk Util) and selected to use the whole drive (Format it and start from scratch)

Its working great. (Apart from the wifi, which madwifi fixed on my 64bit install but now wont do so on my new install.... im lost)

Hope this helps.

Thanks, that covers it for me for now, shows usb external boot works and possibly helped by having only Macosx on the internal (i.e. no competing legacy MBR loader).

Madwifi should work, try a separate post on that, or a search should uncover some howto and threads

---

### Post by entangled on 2007-09-24
For pxwpxw.
Just in case it helps -
The internal drive is MBR. Part 1 is OSX, Part 2 is linux swap, Part 3 is ubuntu7.04
The external USB drive is MBR. Part 1 is OSX (a clone from internal Part 1), Part 2 is linux swap, Part 3 is Sidux Gaia.
All OS boot, chosen from rEFIt.

If I remember correctly, I got OSX onto the internal drive by installing to original GPT drive, cloning it to external MBR drive (using CCCloner), converting internal drive to MBR, then cloning it back. Linux installs and boots on either drive.

---

### Post by pxwpxw on 2007-09-24
**entangled**

Thanks, gets even more interesting.

---

### Post by cyberdork33 on 2007-09-24
> **pxwpxw said:**
> Thanks, gets even more interesting.
Indeed

---

### Post by entangled on 2007-09-24
I've just had a chance to check what I said about the drives. 
I misled you about the internal drive. It is GPT. The external drive is MBR.
I was right about where the OS are installed.
So it seems I did install ubuntu on GPT and grub does boot OK off my internal GPT drive.
I know I have cloned MacOSX but probably not back to the internal drive as I claimed.
Next time I'll check first!

---

### Post by pxwpxw on 2007-09-26
> **entangled said:**
> I've just had a chance to check what I said about the drives. 
I misled you about the internal drive. It is GPT. The external drive is MBR.
I was right about where the OS are installed.
So it seems I did install ubuntu on GPT and grub does boot OK off my internal GPT drive.
I know I have cloned MacOSX but probably not back to the internal drive as I claimed.
Next time I'll check first!

Two more questions for you - is a grub (stage1) installed to both drives, and is it on the drive MBR or the linux partition boot sectors? ( I wondered if you might be booting the external drive using a grub menu on the internal).

---

### Post by entangled on 2007-09-26
I'll try to answer but I don't know how to find out where stage 1 is installed.
My ubuntu is on internal drive part 3 and that is where ubuntu grub root is set.
My Sidux is on external drive part 3 and that is where sidux grub root is set. The sidux menu.lst also has an entry for booting the ubuntu kernel on part 3 of the internal disk.
I don't think either grub is in the MBR but how would I tell?

---

### Post by pxwpxw on 2007-09-27
> **entangled said:**
> I'll try to answer but I don't know how to find out where stage 1 is installed.
My ubuntu is on internal drive part 3 and that is where ubuntu grub root is set.
My Sidux is on external drive part 3 and that is where sidux grub root is set. The sidux menu.lst also has an entry for booting the ubuntu kernel on part 3 of the internal disk.
I don't think either grub is in the MBR but how would I tell?

Thanks, thats helpful.

hexdump will show you what is on the mbr or the partition sector (512 bytes),

assuming your internal drive is /dev/sda

My internal disk MBR: (no grub stage1)
```

$ sudo hexdump -C -n512 /dev/sda
00000000  33 c0 8e d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |3.....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 07 8b  |...It.8,t.......|
00000040  f0 ac 3c 00 74 fc bb 07  00 b4 0e cd 10 eb f2 88  |..<.t...........|
00000050  4e 10 e8 46 00 73 2a fe  46 10 80 7e 04 0b 74 0b  |N..F.s*.F..~..t.|
....edited.....
00000160  65 6d 00 4d 69 73 73 69  6e 67 20 6f 70 65 72 61  |em.Missing opera|
00000170  74 69 6e 67 20 73 79 73  74 65 6d 00 00 00 00 00  |ting system.....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 2c 44 63  19 7a 19 7a 00 00 00 fe  |.....,Dc.z.z....|
000001c0  ff ff ee fe ff ff 01 00  00 00 27 40 06 00 00 fe  |..........'@....|
000001d0  ff ff af fe ff ff 28 40  06 00 30 3e 50 02 80 fe  |......(@..0>P...|
000001e0  ff ff 83 fe ff ff 58 7e  5a 02 08 04 00 01 00 fe  |......X~Z.......|
000001f0  ff ff 0b fe ff ff 60 82  5e 03 60 8a 7d 01 55 aa  |......`.^.`.}.U.|

```

My ubuntu partition sector - grub stage1 - has  some grub text
```

$ sudo hexdump -C -n512 /dev/sda3
00000000  eb 48 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |.H..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 03 02  |................|
00000040  ff 00 00 80 58 be a8 02  00 08 fa 90 90 f6 c2 80  |....X...........|
00000050  75 02 b2 80 ea 59 7c 00  00 31 c0 8e d8 8e d0 bc  |u....Y|..1......|
....edited....
00000170  06 be 94 7d e8 30 00 be  99 7d e8 2a 00 eb fe 47  |...}.0...}.*...G|
00000180  52 55 42 20 00 47 65 6f  6d 00 48 61 72 64 20 44  |RUB .Geom.Hard D|
00000190  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |isk.Read. Error.|
000001a0  bb 01 00 b4 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |........<.u.....|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|

```

My Macosx partition (all 0)
```

$ sudo hexdump -C -n512 /dev/sda2
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200

```

---

### Post by entangled on 2007-09-29
Thanks for the help.
I have Grub everywhere!
Its on internal MBR and internal part 3 (ubuntu) -- despite this having a GPT disklabel
Its also on external MBR and external part 3 (sidux).
I notice that gparted reports sda1 as fat32 and bootable.
gparted also reports my sdb1 as HFS+ but MacOSX boots from external too.

---

### Post by pxwpxw on 2007-09-30
> **entangled said:**
> Thanks for the help.
I have Grub everywhere!
Its on internal MBR and internal part 3 (ubuntu) -- despite this having a GPT disklabel
Its also on external MBR and external part 3 (sidux).
I notice that gparted reports sda1 as fat32 and bootable.
gparted also reports my sdb1 as HFS+ but MacOSX boots from external too.

Thanks, good stuff, amazing. Even booting a cloned copy of  macosx from the external MBR drive,  the HFS+ at sdb1.

I would think your internal drive will probably have GPT/MBR compatible partitioning.

From posts so far in this thread perhaps we can say -

1. People booting from external USB HDD have:

 - MSDOS  MBR partioning scheme on the external
 - Can have GPT/MBR compatible on the internal
 - Do not have windows XP on the internal. 

2. People not booting:
 -Have windows on the internal HDD.:(

Which leads me to think about removing XP to see what happens.

---

### Post by enilk on 2007-10-11
I got this working .. I had a hard time before but yeah  nuke windows partion off my internal hd ande only used usb on my firewire/usb enclosure and rEFIt as bootloader works great via firewire has an error msg saying apple has poor support for that kind booting or something to that gist. 

SOOOO
Use USB ONLY HD  install rEFIt burn livedvd(cd)  install livedvd restart boot from refit select Linux icon i was unable to get it working via the gui i decided to do a text interface and simply typed in install and bam it went alot faster than the gui based one. smooth sailing partioner app came saw all my hardrives just fine and best part i cud repair my aborted isntallations before somehow  sweet! am posting this using ubuntu for 1st time ever made a thread abt triple booting with 3 hard drives if u could help me out with my bluetooth problems?

---

### Post by pxwpxw on 2007-10-11
**enilk**

Thanks for the info, but IDK about bluetooth, just run a bluetooth post, should get answers.

---

### Post by lckennedy on 2007-10-19
I am 100% new to Ubuntu linux...and I want to be able to run it on my firewire drive.  I am having a hard time making this happen.  I noticed that a few of you in this thread have been able to, and I feel like you guys are making it out to be a simple process, of basically installing to the external hard drive, and if you don't have windows installed with bootcamp you should be ok.  That is what I have gotten out of this thread.  But when I try to boot from the external drive, I get an error saying it can't find the boot disk.  Any help would be much appreciated. my IM is in my profile, so you you can IM me if you feel like it...

---

### Post by pxwpxw on 2007-10-19
> **lckennedy said:**
> I am 100% new to Ubuntu linux...and I want to be able to run it on my firewire drive.  I am having a hard time making this happen.  I noticed that a few of you in this thread have been able to, and I feel like you guys are making it out to be a simple process, of basically installing to the external hard drive, and if you don't have windows installed with bootcamp you should be ok.  That is what I have gotten out of this thread.  But when I try to boot from the external drive, I get an error saying it can't find the boot disk.  Any help would be much appreciated. my IM is in my profile, so you you can IM me if you feel like it...

It seems to have been simple for those people who got it to work, ( booting linux installed  on the external drive ).

But it is not so simple to pin down all the conditions for it to work, the Windows factor is not certain, and there is more to it, I tried removing XP, and still unable to get it to work so far, it in my case.

However, one sure way to run an external linux system is, when installing and partitioning, to make a separate /boot partition on the internal drive (enough space for kernel files - about 50 MB should suffice). Then the full linux root system is on the external, just the small boot partition on the internal, which loads its local kernel.
That depends on some free space being available on the internal HDD.

---

### Post by garethrv on 2007-10-19
Hey everyone,

I have an interesting situation.

As you know I was booting ubuntu from a 2.5" USB 2.0 drive. Well I ended up formatting the drive and using it for storage until I get around to downloading 7.10.

In doing all of that, I was of the belief that I was not touching any of the internal workings of my mac, just the external drive.

However now, with nothing plugged into the laptop, when I hold down option at boot, I get presented with a windows option which when selected reports "GRUB Drive error" or something very similar, cannot remember the exact phrasing but can check if it helps.

So it looks like I have unknowingly written something to my mac. My question is, how can I clear it. I have read alot about windows PC's using fdisk to clear the MBR. But after much googling cannot find anything to help my mac.

It isn't a huge issue I guess, but I would very much like to at least understand what is going on.

Thank you for your help,

Gareth.

---

### Post by pxwpxw on 2007-10-19
> **garethrv said:**
> Hey everyone,

I have an interesting situation.

As you know I was booting ubuntu from a 2.5" USB 2.0 drive. Well I ended up formatting the drive and using it for storage until I get around to downloading 7.10.

In doing all of that, I was of the belief that I was not touching any of the internal workings of my mac, just the external drive.

However now, with nothing plugged into the laptop, when I hold down option at boot, I get presented with a windows option which when selected reports "GRUB Drive error" or something very similar, cannot remember the exact phrasing but can check if it helps.

So it looks like I have unknowingly written something to my mac. My question is, how can I clear it. I have read alot about windows PC's using fdisk to clear the MBR. But after much googling cannot find anything to help my mac.

It isn't a huge issue I guess, but I would very much like to at least understand what is going on.

Thank you for your help,

Gareth.

That seems  that grub stage1 for the external linux, was installed to an internal partition, which is again interesting. You can find out where it is using "hexdump" from macosx terminal or a ubuntu live cd. See my post 32  above. If everything else is working well enough, you could just leave it. How you would remove it depends on where it is.

---

### Post by garethrv on 2007-10-19
Hey,

If you could give me a little more help with getting a hexdump report I would really appreciate it.

I tried following your post (#32) and got no result.

I simply entered hexdump, which sent me into a hexdump process where whatever I enter, randomly it returns a single string every few entries.

Thanks for your help. As I mentioned, it doesnt seem to be having any adverse effects on the system, but an understanding would really help it sop nagging in the back of my mind.

The error when I select the windows option at boot is "Grub hard drive error"

Thanks,

Gareth.

---

### Post by jaybone on 2007-10-19
This is a sort of "I've done it as well, but I have questions too" post.

I have got Ubuntu 7.10 booting off a USB hard drive.

I installed 7.10 from the live CD using an MBR formatted volume, and it was booting happily using rEFIt. Then my internal (GPT/MBR hybrid) with Mac OS X crashed, and I replaced it.  

Ubuntu wouldn't boot from the external drive anymore, so I googled around and fixed grub, and now Ubuntu seems to boot happily without needing anything from the internal hard disk.

Now for my question, I have had only two entries in the rEFIt menu for a while, but now I have an extra entry in the rEFIt menu, and I was wondering how to get rid of it.  It's called "Boot Legacy OS".  I didn't have it before, but it just appeared one day and having an extra entry that does nothing for me is annoying.

Reading the previous posts, "hexdump" and how to use it might be the answer to my question as well, so I'm looking forward to hearing the answer too.

---

### Post by cyberdork33 on 2007-10-19
> **jaybone said:**
> This is a sort of "I've done it as well, but I have questions too" post.

I have got Ubuntu 7.10 booting off a USB hard drive.

I installed 7.10 from the live CD using an MBR formatted volume, and it was booting happily using rEFIt. Then my internal (GPT/MBR hybrid) with Mac OS X crashed, and I replaced it.  

Ubuntu wouldn't boot from the external drive anymore, so I googled around and fixed grub, and now Ubuntu seems to boot happily without needing anything from the internal hard disk.

Now for my question, I have had only two entries in the rEFIt menu for a while, but now I have an extra entry in the rEFIt menu, and I was wondering how to get rid of it.  It's called "Boot Legacy OS".  I didn't have it before, but it just appeared one day and having an extra entry that does nothing for me is annoying.

Reading the previous posts, "hexdump" and how to use it might be the answer to my question as well, so I'm looking forward to hearing the answer too.
you likely have boot code in your MBR and the Ubuntu Partition.

---

### Post by lckennedy on 2007-10-19
Im curious as to which versions of Tiger you guys are running...I have a feeling that the ones that are making it work might be using a different version than those of us that can't get Ubuntu to boot from an external...


I am running 10.4.9, and it won't work.  I have never isntalled bootcamp, therefore I have never installed windows, I have no idea how to find out about the MBR, or GPT thing, and I barely even know what that means.  I'm kinda new to all of this stuff.  So laymens terms would be awesome...

---

### Post by cyberdork33 on 2007-10-19
> **lckennedy said:**
> Im curious as to which versions of Tiger you guys are running...I have a feeling that the ones that are making it work might be using a different version than those of us that can't get Ubuntu to boot from an external...


I am running 10.4.9, and it won't work.  I have never isntalled bootcamp, therefore I have never installed windows, I have no idea how to find out about the MBR, or GPT thing, and I barely even know what that means.  I'm kinda new to all of this stuff.  So laymens terms would be awesome...I think they already eliminated all those factors.

---

### Post by 2cute4u on 2007-10-19
Before reading this thread, installed Gutsy on an external USB drive from the live DVD.  I told it to use the whole drive which was previously formatted as an  bootable disk OS X disk.  (I dont know what GPT and MBR are but from what i read i think that it's GPT).   everything look ed like it worked ok for the install, but when i rebooted,  The system didn't give me the option of booting from  the USB drive (holding doen the optoin key).  

I really don't want to mess around with the partition table on my internal HD at all, so I was wondering if there was a way to use a cd as a bootloader.  If so where would I get such a cd or what would be directions for creating it.  (I'm not much of a techie, so it would hae to be spelled out  the step by step in plain english) or if someone has a better solution please tell me, Up till now ive always run ubuntu in a virtual macihine. the reason i want to be ablt to boot from the usb is so that i can use accelorated graphics in compiz. So any solution would have to be able to load the ATI drivers.

---

### Post by garethrv on 2007-10-19
Hey,

Yeah I am running 10.4.10 so I doubt any deciding difference there.

Also I have never installed bootcamp. Remember I had to flag the drive as active through the live cd before it made itself known as an available boot option.

---

### Post by garethrv on 2007-10-19
Hey,

This exactly where I was after a fresh install. You just need to flag it as bootable. I wish I had written down how I did this as I found it after googling around for ages. If anyone knows can they help please!

You dont need to touch the internal.

Hmmm, just had a quick look and it seems you can flag a partition through ubuntus utilities some how. This would be helpful.

Other than that, the way I did it through terminal involved finding the place to flag in the format hd1,2 or whatever it was, and then setting the flag.

---

### Post by 2cute4u on 2007-10-19
> **garethrv said:**
> Hey,

This exactly where I was after a fresh install. You just need to flag it as bootable. I wish I had written down how I did this as I found it after googling around for ages. If anyone knows can they help please!

You dont need to touch the internal.

Hmmm, just had a quick look and it seems you can flag a partition through ubuntus utilities some how. This would be helpful.

Other than that, the way I did it through terminal involved finding the place to flag in the format hd1,2 or whatever it was, and then setting the flag.


Can you tell me exactly how to do this?  I'm not sure what ubuntu utility you mean.  Also did you use ext3?  From your post I thought you used an msdos partition.

---

### Post by garethrv on 2007-10-19
HEY! GOOD NEWS!

Alright, here is what I think will help you get into ubuntu.

By the way, yes I did have the drive formatted as msdos becasue this was the only way I could sucessfully install.

Alright, first of all, go here

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

This is the download for the Gparted live cd which I just used sucessfully on a macbook.

After initially selecting auto config and then your keyboard and language, you get into a really simple partition manager which showed me much more than disk utility in osx.

If you find your linux install partition (NOT THE SWAP) and flag it (right click, really easy) as boot

Looking forward to hearing your success.

Of course after that, reboot, hold option, and select windows. (I know, stupid... but its your new linux install)

---

### Post by 2cute4u on 2007-10-19
> **garethrv said:**
> HEY! GOOD NEWS!

Alright, here is what I think will help you get into ubuntu.

By the way, yes I did have the drive formatted as msdos becasue this was the only way I could sucessfully install.

Alright, first of all, go here

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

This is the download for the Gparted live cd which I just used sucessfully on a macbook.

After initially selecting auto config and then your keyboard and language, you get into a really simple partition manager which showed me much more than disk utility in osx.

If you find your linux install partition (NOT THE SWAP) and flag it (right click, really easy) as boot

Looking forward to hearing your success.

Of course after that, reboot, hold option, and select windows. (I know, stupid... but its your new linux install)
I downloaded and burned the liveCD , but when I booted it, it said "no devices detected"

---

### Post by pxwpxw on 2007-10-20
> **garethrv said:**
> Hey,

If you could give me a little more help with getting a hexdump report I would really appreciate it.

I tried following your post (#32) and got no result.

I simply entered hexdump, which sent me into a hexdump process where whatever I enter, randomly it returns a single string every few entries.

Thanks for your help. As I mentioned, it doesnt seem to be having any adverse effects on the system, but an understanding would really help it sop nagging in the back of my mind.

The error when I select the windows option at boot is "Grub hard drive error"

Thanks,

Gareth.

See the actual commands in my post, you have to run as sudo, and give the options and device. Essential to use -n512 or you might get a 300GigaByte dump.

```

 sudo hexdump -C -n512 /dev/yourdevice(partition)

```
No manual in Macosx, but there is one in ubuntu.

---

### Post by pxwpxw on 2007-10-20
> **2cute4u said:**
> I downloaded and burned the liveCD , but when I booted it, it said "no devices detected"

If you were getting only this, before any sign of grub:
> 
No bootable device - insert boot disk and press key.

In short you may need to turn the EFI partition boot flag back on, and after using gparted, run gptsync to update the MBR partition table (which is used for booting legacy/grub).

That error appeared here for the internal disk after using gparted, including a change to the internal boot flags.

In the process, the small 200MB EFI partiton#1  boot-flag got turned off, and the MBR version of the GPT/MBR tables was unusable (showed one EFI parition using whole disk).

After running gptsync - the rEFIt [Partitioning Tool], the MBR was partialy restored but still incorrect for the EFI partition, and declared untouchable by rEFIt (although that boot error message was eliminated). 

Then after using gparted (manage flags) to set the boot flag back to on for the EFI partition, and re-running gptsync, the MBR table was corrected, no data was lost.

However, changing the boot flag settings did not get me any where with external booting so far, but thats just for my system.

And also, the only way I can boot from the gparted CD is to use the Option key, (not the C key), and Apple Icons, and I then choose the MacBook option for a Fluxbox desktop, including gparted, alternatively drop to a grub command line using the c key at the opening menu .

---

### Post by pxwpxw on 2007-10-20
Thinking this may be hardware dependent on the external drive, for the record my drive and mac system specs attached.

External Drive,
 Western Digital MyBook 300GB, usb and firewire.(2006).
 MBR partitioning system.
MacBook C2D EFI firmware update 1.1

---

### Post by 2cute4u on 2007-10-20
> **pxwpxw said:**
> If you were getting only this, before any sign of grub:

In short you may need to turn the EFI partition boot flag back on, and after using gparted, run gptsync to update the MBR partition table (which is used for booting legacy/grub).

That error appeared here for the internal disk after using gparted, including a change to the internal boot flags.

In the process, the small 200MB EFI partiton#1  boot-flag got turned off, and the MBR version of the GPT/MBR tables was unusable (showed one EFI parition using whole disk).

After running gptsync - the rEFIt [Partitioning Tool], the MBR was partialy restored but still incorrect for the EFI partition, and declared untouchable by rEFIt (although that boot error message was eliminated). 

Then after using gparted (manage flags) to set the boot flag back to on for the EFI partition, and re-running gptsync, the MBR table was corrected, no data was lost.

However, changing the boot flag settings did not get me any where with external booting so far, but thats just for my system.

And also, the only way I can boot from the gparted CD is to use the Option key, (not the C key), and Apple Icons, and I then choose the MacBook option for a Fluxbox desktop, including gparted, alternatively drop to a grub command line using the c key at the opening menu .

I think you are answering a case different from what I have.

My case was that I got grub and gparted.  I was in gparted and gparted in the device list said no devices detected.  and refreshing the device list didnt bring up anythig either. 

Since my last post  I trieded agian usig the macbook option from the grub menu (even though i have an iMac) and in gparted i got the following partiotins
/dev/sdb1      ext3 
/dev/sdb2      extended    
/dev/sdb5      swap

I set the boot flag on /dev/sdb1, but when I but when i rebooted holding the option key, my internal hard disk was still the only disk that showed up.

---

### Post by pxwpxw on 2007-10-20
> **2cute4u said:**
> I think you are answering a case different from what I have.

My case was that I got grub and gparted.  I was in gparted and gparted in the device list said no devices detected.  and refreshing the device list didnt bring up anythig either. 

Since my last post  I trieded agian usig the macbook option from the grub menu (even though i have an iMac) and in gparted i got the following partiotins
/dev/sdb1      ext3 
/dev/sdb2      extended    
/dev/sdb5      swap

I set the boot flag on /dev/sdb1, but when I but when i rebooted holding the option key, my internal hard disk was still the only disk that showed up.

Yes I got it wrong. I found the easy way is to install to the external drive but in the install partitioning, make a partition on the internal drive about 100MB,  use as ext3, mount as /boot. Then the default install for grub goes to the MBR on the internal drive, and other OS are recognised in the defaults grub menu.lst, the external drive is booted by the kernel on the internal /boot partition. All gets done by the installer. Just did it with ubuntu 704 and upgraded to 710, I am posting from the external now. It works for both firewire and usb connecton to the WD MyBook external

If you can have the small boot partition on the internal, it does the job, easy to do..
(doesn't  solve the extenal bootloader question though)

---

### Post by 2cute4u on 2007-10-20
> **pxwpxw said:**
> Yes I got it wrong. I found the easy way is to install to the external drive but in the install partitioning, make a partition on the internal drive about 100MB,  use as ext3, mount as /boot. Then the default install for grub goes to the MBR on the internal drive, and other OS are recognised in the defaults grub menu.lst, the external drive is booted by the kernel on the internal /boot partition. All gets done by the installer. Just did it with ubuntu 704 and upgraded to 710, I am posting from the external now. It works for both firewire and usb connecton to the WD MyBook external

If you can have the small boot partition on the internal, it does the job, easy to do..
(doesn't  solve the extenal bootloader question though)

OK now you are going over my head techniocally.  I don't know how to do what you are saying, can you give me a step by step instruction?  Also I don't want to do anytihng that could mess up my internal HD because I currently don't have a back up drive (I used my backup drive to create for the ubuntu install)

---

### Post by pxwpxw on 2007-10-21
> **2cute4u said:**
> OK now you are going over my head techniocally.  I don't know how to do what you are saying, can you give me a step by step instruction?  Also I don't want to do anytihng that could mess up my internal HD because I currently don't have a back up drive (I used my backup drive to create for the ubuntu install)

Well, its not difficult, but you do need to use a partition on the internal drive as the /boot partition for your external system. 
 I cant give you any more detailed instructions, just the outline I have given. 

I was able to do what was needed using the Desktop install CD, but I have done it before.
You do need to be able to use the manual partitioning option in the installer, best to have done it before, or look for detailed howtos.

So if you are not happy with that or don't understand the idea, its is not for you..

You should be able to see any free space on the internal drive using gparted, but you should not  make any changes to partitions at this stage.  You need to note where the free space is located, apple likes to have 128MB spaces between some partitions, I used one of those. The partition selection is done during the installation (manual partitioning).

---

### Post by i_ll_be on 2007-10-25
Hi pxwpxw,

I have been reading this post very carefully because I am currently trying to get Ubuntu 7.10 running from my USB drive on my MBPro.

I have tried many things without changing anything on the internal HD but nothing was successful.

So yesterday I tried your solution of creating the /boot on the internal during the ubuntu install.

I specified my partitions as below (my USB drive uses GPT) :

/boot - 100 Mo on sda3 (internal)
/ - 10 Go on sdb2 (external)
swap - 1 Go on sdb4 (external)

I specified to install grub on /dev/sda3 at the last step of the installer.

After reboot I get to see the /boot partition when I press the option key (which is a victory after 1 week of efforts :) )

But when I hit enter, I get a sreen full of grubs, very strange !!!

My screen looks like that :

GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB _

1 GRUB will appear every 0.5 sec and it never stops.

I did not use the rEFIt partitioning tool to resync my partition tables. Would this help ???

Thanks for your tips.

---

### Post by garethrv on 2007-10-26
I got this also at one point of trying. I cant remember how I fixed it, although I think I had to reinstall grub from the live CD.

There are many "how to install grub from the live CD" how to's around, this might help.

Cheers,

Gareth.

---

### Post by i_ll_be on 2007-10-26
Thanks I will try this tonight.

If I am right I need to :

- boot the liveCD

- launch the following commands :

sudo grub
find /boot/grub/stage1
root (sd0,4)
setup (sd0,4)
quit

Will that do the job ?

I have an other questions about the rEFIt partitioning tool (gptsync) : is there any risk of damaging the OSX install by launching it ?

Thanks.:)

---

### Post by garethrv on 2007-10-26
Hey,

That sounds perfect.

Sorry I cant help out with the other question, im just a beginner too.

Cheers,

Gareth,

---

### Post by cyberdork33 on 2007-10-26
> **i_ll_be said:**
> Thanks I will try this tonight.

If I am right I need to :

- boot the liveCD

- launch the following commands :

sudo grub
find /boot/grub/stage1
root (sd0,4)
setup (sd0,4)
quit

Will that do the job ?

I have an other questions about the rEFIt partitioning tool (gptsync) : is there any risk of damaging the OSX install by launching it ?

Thanks.:)
I think your numbers are a bit off. (you also don't need the  'find /boot/grub/stage1' if you know where you want to install.)

If your boot partition is sda3, and you want to install to that same partition, then the correct grub terminology is (hd0,2).

There is no sd in grub, and grub starts counting from 0, so that sda = (hd0), sda1 = (hd0,0), sda2 = (hd0,1), etc

So
```
sudo grub
root (hd0,2)
setup (hd0,2)
quit
```gptsync will not do anything to your OSX install, in fact, it is quite likely it will do nothing. It will ask you for confirmation before it makes any changes anyway.

---

### Post by i_ll_be on 2007-10-26
I am posting from Ubuntu... running on my external HD !

Thanks to you all for your help.

I would advise all the intel mac users who want to use ubuntu from external HD to use this method of the boot partition on the internal (since the universal solution to boot from external is not available yet).

Actually to summarize the process which is very simple :

- boot liveCD
- launch install
- in the partitioning tool, create :
     - 1 partition ext3 of 100Mo mounted as /boot on the internal (normally after OSX install 134 Mo remain free, which cqn be used)
     - 1 partition ext3 mounted as / in the external
     - 1 swap partition on the external

After that finish the installation process normally (keep GRUB install on hd0,0).

Reboot holding the option key, and it is ok.

Simple, after 1 week of hard time searching on that every evening !!!

---

### Post by cyberdork33 on 2007-10-26
> **i_ll_be said:**
> After that finish the installation process normally (keep GRUB install on hd0,0).

This is probably OK in your situation, but if you were triple booting with windows, you would want grub on the boot partition and not the MBR so that you can keep the windows bootloader in tact, and not have to use grub to boot windows.

---

### Post by lckennedy on 2007-10-27
ok...so I gave up for a week, and now I am attempting to install Ubuntu again on my external...I gave up not putting a boot partition on my internal...But I'm not sure how to do this...

This is what I am about to do...

Just like it was said above...I selected the partitions manually.  I put boot directory on the 134mb of free space on my internal.  And then I partitioned my external, One partition for my swap, and then the other for root...is that all I need to do?  I just did all of this from the manual option in the partitioner.  I dont know any other way to do this since im totally new to all of this...I would love some help...


When i get to the last window before the install, this is what I have...
 SCSI5 (0,0,0) (sdb) <<thats my external

The following partitions are going to be formatted:
 partition #3 of SCSI3 (0,1,0) (sda) as ext3 <thats my boot
 partition #1 of SCSI5 (0,0,0) (sdb) as ext3 <thats my root
 partition #2 of SCSI5 (0,0,0) (sdb) as swap<thats the swap...

The last few times ive gotten an error when I was trying to install grub...I tried to install it manually with the instructions above, but I cant get it to mount the boot disc...

---

### Post by lckennedy on 2007-10-27
So It worked...I just thought I would post my solution...

There was 134 mb of free space left on my internal hard drive from the instalation of OSX.  I used this as my '/boot'.

Then I made a swap 500mb swap partition.  And a 5gb Fat32 partition to store files on to exchange between Ubuntu and OSX...

Then I just put root on my last partition, hit install, and it just worked.

Heres the thing, When I boot, the linux partition on my INTERNAL shows up to boot off of, and ofcourse, it thinks its windows.  But it all works fine!

---

### Post by cyberdork33 on 2007-10-27
> **lckennedy said:**
> So It worked...I just thought I would post my solution...

There was 134 mb of free space left on my internal hard drive from the instalation of OSX.  I used this as my '/boot'.

Then I made a swap 500mb swap partition.  And a 5gb Fat32 partition to store files on to exchange between Ubuntu and OSX...

Then I just put root on my last partition, hit install, and it just worked.

Heres the thing, When I boot, the linux partition on my INTERNAL shows up to boot off of, and ofcourse, it thinks its windows.  But it all works fine!
With a small boot partition like that you might want to edit /boot/grub/menu.lst to only keep 2 or 3 kernels, as after getting a few updates you might run out of space. This happened to me recently on another machine I use.

---

### Post by pxwpxw on 2007-10-28
It is also a handy idea to put a network instal/rescue kernel on /boot, self supporting.

I am currently running gutsy ubuntu-gnome and xubuntu in two separate root partitionns on the external WD Mybook (MBR), using the one /boot partition in the standard Apple 128MB spacer partition at sda2 as /boot.  Need to remove obsolete kernels.

---

### Post by 2cute4u on 2007-10-28
**This post could be related to an Ubuntu bug filed at**: on the internal Drive then reinstalled Ubuntu on my external drive, with grub on the external drive.  [br].[/br] ---------------------------- [br].[/br] [br].[/br]                 > **i_ll_be said:**
> Thanks I will try this tonight.

If I am right I need to :

- boot the liveCD

- launch the following commands :

sudo grub
find /boot/grub/stage1
root (sd0,4)
setup (sd0,4)
quit

Will that do the job ?

I have an other questions about the rEFIt partitioning tool (gptsync) : is there any risk of damaging the OSX install by launching it ?

Thanks.:)


When I installed grub on my internal drive, it made it impossible to install Leopard, and I had to backup the internal drive to my USB drive (which meant loosing my Linux install), then reformat and restore the internal drive.  :sad:


What I did, that finally worked, was install [rEFIt ]("http://refit.sourceforge.net/")on the internal Drive then reinstalled Ubuntu on my external drive, with grub on the external drive.

Now when I boot my machine,  I get an apple and a penguin on my screen, that I can choose from, to boot the OS of my choice :KS

---

### Post by WorldCitizeN on 2007-11-10
2 Weeks ago I installed Ubuntu 7.10 on an external USB 2.0, with " /boot " being on the internal disk and it all worked just fine. Today I installed WinXP on the internal erasing the /boot partition and Windows worked just fine (Ubuntu didn't work at all naturally). Now, I want to restore the Linux Installation, but I do not have a /boot point. I do not want to install rEFIt, my thought is to select boot from two icons on BootCamp, OSX or Windows, and then if Windows are selected, a GRUB menu to select between Windows and Ubuntu.
Your help would save me from a lot of trouble.

My Specs are: iMac Core2Duo (white), 2GB Ram etc.

---

### Post by ppcaric on 2007-11-21
Hi.
I've read this entire, interesting thread, but I still can't find a final answer to the following question:
can I install ubuntu 7.10 on an external firewire drive and boot from it WITHOUT changing anything on the internal drive of my MacBook Pro?

I see many problems solved here (modifying the internal drive) are concerned with using USB drives or wanting GRUB or rEFIt to do the boot choice.

I'd like to let the EFI choose the boot partition on the external drive, exactly as it happens if I install another MacOS X on the external drive (it only works for FW drives). In this case, at boot time, if I keep pressed the option key, two icons appear: one for the "internal" MacOS and another for the external one.

Ain't it possible to do the same for Ubuntu? (I'm not interested in native Windows, so BootCamp shouldn't be needed).
As far as I've understood till now, it should be sufficient to have the external drive using GPT, but I'm not sure what it means... :(
I have no problem formatting/partitioning the external drive as needed.

Can somebody help me?

Thanks

---

### Post by cyberdork33 on 2007-11-21
> **ppcaric said:**
> Ain't it possible to do the same for Ubuntu? (I'm not interested in native Windows, so BootCamp shouldn't be needed).

many people think you have to use bootcamp to get that OS selector screen on startup.
> As far as I've understood till now, it should be sufficient to have the external drive using GPT, but I'm not sure what it means... :(
I have no problem formatting/partitioning the external drive as needed.The issue is that OSX boots DIRECTLY from the EFI... so it can be anywhere you want to put it without an issue.

Windows / Ubuntu boot using the 'emulated' BIOS for legacy operating systems to boot. For some reason, it has a very hard time booting from an external hard drive (the usb vs firewire thing should make no difference).

You sound just about as confused as everyone else on booting from an external drive (including myself). As you can see in the thread, some people seem to have everything working completely on the external drive, others cannot get it working at all. We do know that creating a /boot partition on the internal drive DOES work, but theoretically, this should not be required, there is just not specific enough information yet on how to accomplish this correctly. Feel free to experiment and post your findings. Ubuntu will install just fine to the external drive, it just won't boot after that for some reason...

PS, if you would like to multi-boot, you may want to checkout rEFIt. This is just a nice boot menu that comes up at power on and allows selection between the bootable systems. It uses the Mac's bootloader, but just gives it a better interface and is easily removable if you do not like it. (It also allows you to make the legacy OS the default boot option over OSX if you want that).

So, to specifically answer your question, technically, 'YES', but in practice, that often changes to 'no'.

---

### Post by bananacrumpcake on 2007-11-25
I'm also trying to triple-boot on a C2D Macbook. I have OS X and XP on the internal drive via Bootcamp, and I want to install Ubuntu on a partition on my external USB drive.

I have the partitions made, booted up from the Live CD, selected partitions and a swap partition, made it to the installer, and then - it hangs on 15%, says something along the lines of "Detecting System Resources" or something like that.

Does anyone happen to know what this issue is? I'm new to Linux and want to try and break the ice with Ubuntu on the external.

I'm not really interested in installing rEFIt, the default bootloader works great for me (as I also have a bootable backup of my OS X partition on the external, I already have three options at boot - OS X, Windows, or the OS X backup, + the Live CD when it's in).
Since this is my first real venture into any distro, I don't really understand all the Gutsy and grub references (the reason why I chose Ubuntu and not a more tech-savvy distro), and I'd like if there's a solution to this that doesn't involve a lot of command-prompt work.

Anyway, if anyone knows or can help me out, I'd really appreciate it. It seems like such a tease to make it all the way to the installer just to watch it hang on 15%.

Edit: Running Ubuntu right now, off the Live CD. The exact words it says are "Installing system - 15%. Detecting file systems..." Yesterday I left it for about two hours and it didn't get past that.

---

### Post by zaqarov on 2007-12-08
I've read this topic entirely, but I'm confused about 2 things: 

1. Is it possible to have Mac OSX (Leopard) and Windows (Vista 32-bit) on the internal drive, and bootable Ubuntu (Gutsy) on an external USB2 drive? Please give me instructions/links on how to accomplish this. 

2. Is it possible without modifying the internal drive's partitions?

I am on a MacBook Pro (Santa Rosa 2,4GHz)


thanks
zaqarov

---

### Post by 2cute4u on 2007-12-08
> **zaqarov said:**
> I've read this topic entirely, but I'm confused about 2 things: 

1. Is it possible to have Mac OSX (Leopard) and Windows (Vista 32-bit) on the internal drive, and bootable Ubuntu (Gutsy) on an external USB2 drive? Please give me instructions/links on how to accomplish this. 

2. Is it possible without modifying the internal drive's partitions?

I am on a MacBook Pro (Santa Rosa 2,4GHz)


thanks
zaqarov


Yes, all you need is [rEFIt]("http://refit.sourceforge.net/").  You just install it using OS X, then at boot time (don't hold down any key) it will give you the option of booting from  any internal or external OS X, Linux, or Windows partition.

---

### Post by zaqarov on 2007-12-08
Hm I've tried that before, but i get all kinds of weird errors from rEFIt about legacy os boot and USB support on Apple hardware. 

zaqarov

---

### Post by cyberdork33 on 2007-12-09
There is a thread posted in the faq...

It is not as simple as you would expect.
[http://ubuntuforums.org/showthread.php?t=510030](http://ubuntuforums.org/showthread.php?t=510030)

---

### Post by Vekter on 2007-12-10
I bought a new hd for my C2D Macbook and an external USB/FW cabinet for the old one. I left the old hd's OS X partition untouched and it shows up in bootcamp at boot. And it _is_ bootable.
Perhaps someone finds this useful.  

Screen at boot:
[[IMG]http://img504.imageshack.us/img504/8858/img3637xx1.th.jpg[/IMG]](http://img504.imageshack.us/my.php?image=img3637xx1.jpg)

---

### Post by cyberdork33 on 2007-12-11
> **Vekter said:**
> I bought a new hd for my C2D Macbook and an external USB/FW cabinet for the old one. I left the old hd's OS X partition untouched and it shows up in bootcamp at boot. And it _is_ bootable.
Perhaps someone finds this useful.
Booting OSX of external drives has been done for a long time... It is booting Ubuntu off the external drive that is difficult.

---

### Post by lotus49 on 2008-01-03
Despite extensive research, I have not been able to find anyone who claims to have been able to boot Ubuntu (or XP for that matter) from an external USB drive on a MBP C2D with the latest firmware.

I think we all believe that this should be possible but so far I don't think anyone has managed it.

I had thought it was the latest firmware that caused the problem but I am beginning to think that this just doesn't work on the MBP C2D.

I am really keen to get this to work (really for XP not Ubuntu as I have a separate laptop with Ubuntu on it) so I am not giving up yet.

---

### Post by cyberdork33 on 2008-01-03
> **lotus49 said:**
> Despite extensive research, I have not been able to find anyone who claims to have been able to boot Ubuntu (or XP for that matter) from an external USB drive on a MBP C2D with the latest firmware.
There are a few in this thread. Here is one:
[http://ubuntuforums.org/showpost.php?p=3388223&postcount=16](http://ubuntuforums.org/showpost.php?p=3388223&postcount=16)

> **lotus49 said:**
> I had thought it was the latest firmware that caused the problem but I am beginning to think that this just doesn't work on the MBP C2D. It is actually all Intel Macs so far.

> **lotus49 said:**
>  I am really keen to get this to work (really for XP not Ubuntu as I have a separate laptop with Ubuntu on it) so I am not giving up yet.Any new information you can contribute would be great.

---

### Post by lotus49 on 2008-01-03
> **cyberdork33 said:**
> There are a few in this thread. Here is one:
[http://ubuntuforums.org/showpost.php?p=3388223&postcount=16](http://ubuntuforums.org/showpost.php?p=3388223&postcount=16)

 It is actually all Intel Macs so far.

Any new information you can contribute would be great.

That post actually refers to a "MBC2D" which I took to be a MacBook rather than MacBook Pro.  I have seen other posts on the net in which people have detailed getting this to work on a MacBook but not a MacBook Pro.

I am currently doing some experiments with different partition tables but I have to say that I am not optimistic.  I have had two USB HDDs with XP and Ubuntu that booted fine from other machines but rEFIt couldn't boot them.  The author of rEFIt (who almost certainly knows a lot more about this than I do) said that rEFIt's failure to boot was due to a firmware limitation 

I'll report back later.

---

### Post by cyberdork33 on 2008-01-03
> **lotus49 said:**
> That post actually refers to a "MBC2D" which I took to be a MacBook rather than MacBook Pro.  I have seen other posts on the net in which people have detailed getting this to work on a MacBook but not a MacBook Pro.

I am currently doing some experiments with different partition tables but I have to say that I am not optimistic.  I have had two USB HDDs with XP and Ubuntu that booted fine from other machines but rEFIt couldn't boot them.  The author of rEFIt (who almost certainly knows a lot more about this than I do) said that rEFIt's failure to boot was due to a firmware limitation 

I'll report back later.
There should be no difference between the Macbook's ability and the Macbook Pro's ability to boot from an external device... (or an iMac for that matter). I am sure it has something to do with Apple's implementation of EFI, and nothing to do with rEFIt. There are many combos of variables that could be tried, and I think that is part of the issue.

[LIST]
[*]GPT vs MBR partitioning
[*]partition boot flags
[*]4 partition limit of the Macs emulated BIOS
[*]Though not normally an issue on Macbooks and iMacs, some of the Mac Pro users have problems when trying to install when there are multiple hard drives... This problem could be related.[/LIST]I don't think this is a USB vs Firewire issue as there are those that have already tried either, but I guess it is a variable to consider.

Getting the combo of option you attempt, along with any error messages when attempting to boot (if you even can try to) would be helpful. My external hard drive controller is dead, so I can't really help anymore.

---

### Post by lotus49 on 2008-01-09
OK I shall try to summarise the various failed attempts I have made to get this working.

My objective (despite the fact that I am posting in an Ubuntu forum) is to get XP running from an external USB HDD on my MacBook Pro Core 2 Duo.  Due to the amount of time I have spent trying to achieve this and reading and posting on various forums I am beginning to think that, with my setup at least, this is currently not possible but I am writing this in the hope that someone will say "of course it is" and will tell me what I have been doing wrong.

Because there is a lot of this and I may not have time to document this now, I shall make a separate post for each method I attempted.

**Attempt #1**

My first attempt was to install XP on a USB HDD using my Compaq nc4200 laptop (which is running Ubuntu 7.10).  The installation went smoothly and XP booted and ran fine.

This disk was partitioned by Windows and has a MBR and standard partition table.

I tried to boot this disk on my MBP using rEFIt.  I tried rEFIt on the MBP HDD, on a USB flash drive and on a CD with identical results.  rEFIt saw the XP installation and recognised it as such, but when I selected it to boot I got the following error messages:

 rEFIt - Booting Legacy OS


Starting legacy loader
Using load option 'USB'
Error: Not Found returned from legacy loader
Error: Not Found returned from LocateDevicePath
Error: Not Found returned from LocateDevicePath
Error: Not Found returned from LocateDevicePath
Error: Not Found returned from LocateDevicePath
Error: Not Found returned from LocateDevicePath
Error: Not Found returned from LocateDevicePath
Error: Not Found returned from LocateDevicePath
Error: Not Found returned from LocateDevicePath
Error: Not Found returned from LocateDevicePath
Error: Not Found returned from LocateDevicePath
Error: Not Found returned from LocateDevicePath
Error: Not Found returned from LocateDevicePath
Error: Load Error while (re)opening our installation volume

The firmware refused to boot from the selected volume. Note that external
hard drives are not well-supported by Apple's firmware for legacy OS booting.

* Hit any key to continue * 

I also tried booting another external USB disk which had a working installation of Ubuntu 7.10 on it with identical results.

---

### Post by lotus49 on 2008-01-09
Curiously the installation of XP on the USB disk referred to in my previous post would not boot on another laptop which is very similar, a Compaq nc6220.  However the installation of XP on a USB HDD using this machine did work but only if the CD was in an external USB CD drive.

**Attempt #2**

I then tried to install XP directly on the MBP.  This worked up to the point where I was able to select the installation target.  I selected the USB HDD but on the next screen got the following error message:

[FONT="Courier New"]Your computer's startup program cannot gain access to the disk
containing the partition or free space you chose. Setup cannot
install Windows XP on this hard disk.

This lack of access does not necessarily indicate an error condition.
For example, disks attached to a SCSI controller that wasn't installed
by your computer manufacturer or to a secondary hard disk controller,
are typically not visible to the startup program unless special
software is used. Contact your computer or hard disk controller
manufacturer for more information.

On x86-based computer, this message may indicate a problem with the
CMOS drive type settings. See your disk controller documentation
for more information.

Press ENTER to continue.[/FONT]

Trying to boot the installation CD from an external USB CD drive did not help in this case.

So far so bad.

---

### Post by lotus49 on 2008-01-09
**Attempt #3**

I started to wonder if this was a Windows problem or a MBP problem so I decided to try the same thing with Ubuntu on the same disk that I had used previously with a MBR and standard partition table.

I tried booting into Ubuntu on a USB HDD and got the same rEFIt error message so my next step was an install from the MBP.

The installation proceeded all the way through (it may be worth pointing out that I have installed Ubuntu on USB HDDs lots of times and although I have encountered minor problems with the default content of menu.lst I have always been able to fix them) but when it came to booting I got the following error:

GRUB Hard disk error

**Attempt #4**

This time I partitioned the disk on my MBP only I selected GPT rather than MBR and created the appropriate partitions that I knew the Ubuntu installer would require.

This had precisely the same result as the previous attempt.

All in all this has taken a lot of my time and has been a dismal failure.  I have come to the conclusion that this is simply not possible, but that the problem lies not with Ubuntu or XP but with the MBP's firmware.  I would love to be proved wrong but I do not believe that the current firmware on MBPs is capable of booting XP or Ubuntu on an external USB drive.

It's not often that I give up on something, but unless someone can tell me that they have done this successfully on a MBP with up to date EFI firmware, I am going to have to throw in the towel - what a pain in the bum.

:(

---

### Post by cyberdork33 on 2008-01-10
I would point out that Windows is notorious for giving problems on external hard drives anyway. Usually, it is very dependent on the specific machine (as you have seen).

Also, if you are still willing to try some stuff, installing Ubuntu on the external drive seems to work, but grub has an issue booting from there for some reason. The Mac Pro (not Macbook Pro) users seem to have the same type of problem if they install Ubuntu to a non-primary disk (i.e. a second internal hard drive). I would have to search the forums for more specific info, but they normally have to change the grub config file to boot as if the install was actually on the primary hard drive... It is like the Mac always makes the booted drive, the primary one. So you might make various attempts at editing the menu.lst file to point to locations rather than the expected...

---

### Post by lotus49 on 2008-01-10
> **cyberdork33 said:**
> I would have to search the forums for more specific info, but they normally have to change the grub config file to boot as if the install was actually on the primary hard drive... It is like the Mac always makes the booted drive, the primary one. So you might make various attempts at editing the menu.lst file to point to locations rather than the expected...

I am actually quite familiar with error to which you refer as I've had it every time I have installed Ubuntu on an external drive.  The problem is usually that menu.lst points to the second HDD because that is what the HDD is when it is plugged into a machine which  already has an internal HDD.  However, when a machines boots first from the external HDD it regards this as the first HDD.

The solution is just to change all the references in menu.lst so it usually ends up looking exactly the same as the menu.lst file on the internal HDD.

The error I had is related to the boot sector rather than the config file as grub never runs properly (if it did you would get the option to use the grub command line) so I would be surprised if changing the menu.lst had any effect on my error.  I shall look into it further though.

---

### Post by cyberdork33 on 2008-01-10
> **lotus49 said:**
> I am actually quite familiar with error to which you refer as I've had it every time I have installed Ubuntu on an external drive.  The problem is usually that menu.lst points to the second HDD because that is what the HDD is when it is plugged into a machine which  already has an internal HDD.  However, when a machines boots first from the external HDD it regards this as the first HDD.

The solution is just to change all the references in menu.lst so it usually ends up looking exactly the same as the menu.lst file on the internal HDD.

The error I had is related to the boot sector rather than the config file as grub never runs properly (if it did you would get the option to use the grub command line) so I would be surprised if changing the menu.lst had any effect on my error.  I shall look into it further though.
well that is interesting. have you tring installing the grub stage 1 to a different place? a partition rather than the MBR? maybe even to a partition on the primary hard drive? (I wouldn't do it to your OSX partition though.)

---

### Post by lotus49 on 2008-01-12
I fixed the "GRUB Hard Disk Error" problem by booting into the Ubuntu live CD and reinstalling grub.  I also fixed the menu.lst file.  BTW I said in an earlier post that the menu.lst files on the internal and external disk should be the same.  This should have said "almost the same" as the GUIDs will be different.

I tried to boot into the Ubuntu installation on the USB HDD with the predictable result that rEFIt threw the same error message that I mentioned above.

I have come to the conclusion that this is simply not possible.  I keep saying this (here and in other forums) in the vain hope that someone will tell me I'm wrong, but I have finally decided to give up.  I am convinced now that until Apple releases some new and better firmware, this is not going to work no matter what I do.

XP and Linux will run well on a MBP, but neither will boot from a USB HDD.  There are ways around this such as booting from the internal HDD and mounting / from the external drive, but as I have said, I don't want to change anything on my internal HDD so I am out of luck.

---

### Post by lotus49 on 2008-01-13
Out of curiosity (and sheer bloody-mindedness - I was determined to get this to work somehow) I decided to try to use a boot CD.

A pure grub boot CD didn't work - grub couldn't see the USB HDD which is somewhat unsurprising considering the dismal failure of all my previous attempts.

However, a kernel boot CD did work (ie boots the kernel from the CD but mounts / from the USB HDD).  This is not elegant, partly due to needing a separate CD but mainly because the boot CD needs to be recreated each time the kernel is updated.

So, if you really must run Ubuntu (or any other Linux) without touching your MBP's internal disk, this is a workable, if inelegant approach.

However, in my case my real objective was to get XP working so I could run Windows-only games and since XP is a steaming heap of crap, this sort of approach is unlikely to work due to the inflexibility of the XP boot process.

At least no-one can say I didn't try...

---

### Post by lotus49 on 2008-01-15
**Postscript**

I happened across another site where someone claimed to have got Debian booting off a USB HDD fairly easily (see [http://ghaint.no-ip.org/~k2/debian/mbp-usb.html](http://ghaint.no-ip.org/~k2/debian/mbp-usb.html)) and I had never tried installing rEFIt onto a partition on the target USB HDD.

It is worth pointing out that the author of this page has a MBP CD not C2D.  I have also seen on this site [http://tubeshards.wordpress.com/2006/12/05/install-windows-to-a-macintosh-usb-drive/](http://tubeshards.wordpress.com/2006/12/05/install-windows-to-a-macintosh-usb-drive/) that someone got XP booting from a USB HDD on a MacBook.

Totally unsurprisingly, the install went well, I had to reinstall grub manually and ...

it didn't work.  I got the same rEFIt error as before.

I am mystified how my MBP can pick up the USB HDD, boot rEFIt from it and then fail to recognise the USB HDD, but there it is.

I am going to email the rEFIt authors and see if they can shed any light on this, but it still looks like I am completely out of luck.

---

### Post by cyberdork33 on 2008-01-15
> **lotus49 said:**
> **Postscript**

I happened across another site where someone claimed to have got Debian booting off a USB HDD fairly easily (see [http://ghaint.no-ip.org/~k2/debian/mbp-usb.html]("http://ghaint.no-ip.org/%7Ek2/debian/mbp-usb.html")) and I had never tried installing rEFIt onto a partition on the target USB HDD.

It is worth pointing out that the author of this page has a MBP CD not C2D.  I have also seen on this site [http://tubeshards.wordpress.com/2006/12/05/install-windows-to-a-macintosh-usb-drive/](http://tubeshards.wordpress.com/2006/12/05/install-windows-to-a-macintosh-usb-drive/) that someone got XP booting from a USB HDD on a MacBook.

Totally unsurprisingly, the install went well, I had to reinstall grub manually and ...

it didn't work.  I got the same rEFIt error as before.

I am mystified how my MBP can pick up the USB HDD, boot rEFIt from it and then fail to recognise the USB HDD, but there it is.

I am going to email the rEFIt authors and see if they can shed any light on this, but it still looks like I am completely out of luck.i don't think it is rEFIt's fault, or Ubuntu... I think it has to do with the BIOS emulation and the partitioning issues that go along with that that is the problem.

---

### Post by cyberdork33 on 2008-01-16
Well, this was in the mactel-linux-users mailing list today:
> 
Last weekend I installed Ubuntu 7.10 on an external harddrive attached
to my MacBookPro via USB.

- First installed rEFIt.
- Then installed Ubuntu to the external drive WITHOUT installing grub.
- Note the device name, /dev/sdb in may case.
- Then installed grub manually, using the device name from above.

After that the Ubuntu installation shows up as a boot option in rEFIt.

Hope this helps,
Zoltan

---

### Post by lotus49 on 2008-01-17
That is interesting, but is essentially what I did.  Neither of the times I tried to install Ubuntu did the grub installation succeed so I had to do it manually.  I also got this far, that is Ubuntu did show up as a boot option - the only problem was that it didn't actually boot.  Zoltan doesn't say it worked, but I presume it must have done or it was a rather silly thing to post.

I shall sign up for the mailing list and see if I can establish what sort of a MBP it was.  As I mentioned in an earlier post in this thread, I have seen someone else say that they had been successful but they had a Core Duo MBP rather than a C2D like mine.

If this turns anything up I shall report back.  Thanks for the pointer BTW.

---

### Post by cyberdork33 on 2008-01-17
> **lotus49 said:**
> That is interesting, but is essentially what I did.  Neither of the times I tried to install Ubuntu did the grub installation succeed so I had to do it manually.  I also got this far, that is Ubuntu did show up as a boot option - the only problem was that it didn't actually boot.  Zoltan doesn't say it worked, but I presume it must have done or it was a rather silly thing to post.

I shall sign up for the mailing list and see if I can establish what sort of a MBP it was.  As I mentioned in an earlier post in this thread, I have seen someone else say that they had been successful but they had a Core Duo MBP rather than a C2D like mine.

If this turns anything up I shall report back.  Thanks for the pointer BTW.He was responding to someone asking about how to go about it, so I would assume he had it working. It should be in the archives in nothing else.

---

### Post by lotus49 on 2008-01-21
Disappointingly, but unsurprisingly, Zoltan's machine is a Core Duo rather than a Core 2 Duo like mine.

All I can do now is sit it out and hope Apple issues some firmware for the Core 2 Duo that will boot "legacy" OSs from a USB drive.  I don't think I shall hold my breath while I wait though.

---

### Post by Rusty Spoork on 2008-01-22
Hey all,

I'm new to the forum and to Ubuntu.  I've never used Linux before and I am not very terminal or tech savvy, I'm a GUI person. 

So, I was trying to install Ubuntu on an external (actually internal 2.5" laptop HDD in a USB enclosure)  55.6 (60) Gb HDD which I formatted on a PC using NTFS as I had trouble in the beginning getting the Live CD to boot, it just sat there after it said "Loading the *something* scripts" after "Checking Battery Status". I did this in order to use WINE to use SolidWorks.  I checked SolidWorks-WINE compatibility there, since I didn't want to install windows and I'll do anything not to. 

-I burned a 7.10 Ubuntu Image, 64-bit, onto a CD-R and popped it into the computer.  I have a 15" MBP 2.2 GHz C2D w/ 2Gb RAM.  
-After Ubuntu booted, I ran the installer, chose my language options, and created three partitions on the external HDD, a 5Gb "/" ext3 partition, a 500Mb swap partition, and the rest of the space as a third ext3 partition all on the /dev/sdb.  I don't remember the SCSI* name.
-I ran the installer.  It finished successfully on the first try.  
-I selected eject the Live CD, and it did.
-Then, as I had found before, it just sat there running with a black screen, so I held down the power button for 10 sec, which I hate doing to my mac. 
-I turned it on, holding down the OPTION key and all I found was "Macintosh HD". So I booted that.
-After Leopard had loaded, but before the Gmail Notifier, bluetooth, Airport, volume, and battery (in the top right corner) had even loaded, I got this popup, which I get every time I plug the external HDD in now (before and after boot),
 [IMG]http://homepage.mac.com/bob2durr/UbuntuExternalHDDMountErrorAfterSuccessfulInstall.png[/IMG] .

I thought I would present this popup as my minuscule addition of information to the thread, since no one seemed to have mentioned it before.

I'm looking forward to any help you guys can offer.

Techies like you will save the world one day.

Thanks,

Rusty

---

### Post by cyberdork33 on 2008-01-22
> **Rusty Spoork said:**
> Hey all,

I'm new to the forum and to Ubuntu.  I've never used Linux before and I am not very terminal or tech savvy, I'm a GUI person. 

So, I was trying to install Ubuntu on an external (actually internal 2.5" laptop HDD in a USB enclosure)  55.6 (60) Gb HDD which I formatted on a PC using NTFS as I had trouble in the beginning getting the Live CD to boot, it just sat there after it said "Loading the *something* scripts" after "Checking Battery Status". I did this in order to use WINE to use SolidWorks.  I checked SolidWorks-WINE compatibility there, since I didn't want to install windows and I'll do anything not to. 

-I burned a 7.10 Ubuntu Image, 64-bit, onto a CD-R and popped it into the computer.  I have a 15" MBP 2.2 GHz C2D w/ 2Gb RAM.  
-After Ubuntu booted, I ran the installer, chose my language options, and created three partitions on the external HDD, a 5Gb "/" ext3 partition, a 500Mb swap partition, and the rest of the space as a third ext3 partition all on the /dev/sdb.  I don't remember the SCSI* name.
-I ran the installer.  It finished successfully on the first try.  
-I selected eject the Live CD, and it did.
-Then, as I had found before, it just sat there running with a black screen, so I held down the power button for 10 sec, which I hate doing to my mac. 
-I turned it on, holding down the OPTION key and all I found was "Macintosh HD". So I booted that.
-After Leopard had loaded, but before the Gmail Notifier, bluetooth, Airport, volume, and battery (in the top right corner) had even loaded, I got this popup, which I get every time I plug the external HDD in now (before and after boot),
 [IMG]http://homepage.mac.com/bob2durr/UbuntuExternalHDDMountErrorAfterSuccessfulInstall.png[/IMG] .

I thought I would present this popup as my minuscule addition of information to the thread, since no one seemed to have mentioned it before.

I'm looking forward to any help you guys can offer.

Techies like you will save the world one day.

Thanks,

Rusty
I would guess that it is saying that only because it is not formatted in an OSX filesystem. If you install ext2fs driver, then you should be able to mount the partitions in OSX. [http://sourceforge.net/project/showfiles.php?group_id=64713&package_id=101149&release_id=468470](http://sourceforge.net/project/showfiles.php?group_id=64713&package_id=101149&release_id=468470)

It is odd that it does not show up when holding the Option key. Can you try installing rEFIt? [http://refit.sourceforge.net/](http://refit.sourceforge.net/) It maybe able to recognize it better.

---

### Post by lotus49 on 2008-01-22
I am sorry to have to tell you Rusty, but I don't believe you will be able to get this to work, or at least not until Apple releases new EFI firmware.

If you read through the thread you will see that I have tried almost everything to get this to work and I am very familiar with Macs and Ubuntu - nothing worked.  I don't believe that anyone has ever managed to boot Linux or XP from an external USB disk on a MacBook Pro Core 2 Duo although people have managed it on a MacBook and a MacBook Pro Core Duo.

The problem is that firmware in the MacBook Pro Core 2 Duo will not boot what Apple terms a "legacy" operating system (ie Linux or Windows) if it is installed on an external USB disk.

Despite this you could install Ubuntu on the internal disk - that works fine but if you make a mistake you may trash your Mac OS X installation.

However, it is possible to create a boot CD that loads the Linux kernel and then runs from the USB disk.  Ubuntu runs fine from a USB HDD, it just won't boot.  I have actually created one of these recently and if you are new to Ubuntu and Linux you might find it a bit challenging so I could upload the image to rapidshare or mediafire if that would be helpful.

The error message you get is because by default Ubuntu uses the ext3 filesystem which Mac OS X doesn't recognise.  You would get a similar error if you plugged the disk into a Windows machine.

BTW you don't need to worry about having to power off by holding down the power button if you booted from a LiveCD, it won't do any damage to the filesystems or the machine.

---

### Post by Rusty Spoork on 2008-01-22
> I would guess that it is saying that only because it is not formatted in an OSX filesystem. If you install ext2fs driver, then you should be able to mount the partitions in OSX. [http://sourceforge.net/project/showf...ease_id=468470](http://sourceforge.net/project/showf...ease_id=468470)

It is odd that it does not show up when holding the Option key. Can you try installing rEFIt? [http://refit.sourceforge.net/](http://refit.sourceforge.net/) It maybe able to recognize it better.

Thank you.  I was doing the external install in order to keep my internal disk happy and safe.  I'll try rEFIt but I don't really want to do anything other than app installs to my internal HDD.


> However, it is possible to create a boot CD that loads the Linux kernel and then runs from the USB disk. Ubuntu runs fine from a USB it just won't boot. I have actually created one of these recently and if you are new to Ubuntu and Linux you might find it a bit challenging so I could upload the image to rapidshare or mediafire if that would be helpful.

That boot disk, does it need to be in the entire time I'm running Ubuntu?  If not, I would be very grateful, because I will be installing SolidWorks from a DVD to WINE, since DarWINE is based on Windows 2000 (too old), which is why I wanted Ubuntu, that and because I wanted to try Linux.  Also, I don't want to forgetfully eject my operating system.

Will the ext3 file system be usable with this boot CD?

I'm sorry if I presented too much information in my last post.  I had read the entire thread and I was more just presenting another case to use to find which variables were present for a  failed attempt.  

Thanks for your help,

Rusty

---

### Post by cyberdork33 on 2008-01-22
He is really just suggesting a method of booting the external drive via a loader on the cd. You would not need the cd once you have booted into the Ubuntu system.

---

### Post by Rusty Spoork on 2008-01-22
Oh, ok.  Thank you.  I'll let you guys know if I have any success with those attempts.

---

### Post by lotus49 on 2008-01-23
Cyberdork33 is quite right, the CD is only to boot.  Once Ubuntu has booted the CD is not used and you can remove it.

I have uploaded a boot CD image to [http://www.mediafire.com/?diid1acmdd2](http://www.mediafire.com/?diid1acmdd2)

This expects the root ext3 filesystem to be on /dev/sdb1.  If your root partition is somewhere else this CD won't work but I think you said this is where it is.  This is for the current latest kernel.

The key drawback to this approach is that the CD will need to be recreated when the kernel is upgraded (it will still boot the old kernel though).

Try it and if it works I'll help you with recreating the disk so you know how to do it.

If you haven't materially changed your USB Ubuntu installation you may find it will boot from the CD as it is.

---

### Post by Rusty Spoork on 2008-01-23
Thank you very much.  That information is correct as far as I can remember.  
I'd be happy to learn how to make these boot CDs.  Thank you for your help.

[EDIT]: Ok, so I tried the image, I burned it to a CD-R and it showed up as "Windows" on boot+OPTION.  When I clicked on it it loaded Ubuntu, but first it flashed something which I thought said PCI support failed or something, it was really quick. Then it loaded the Ubuntu Loading bar, and got about 1/20 of the way and flashed black.  It only displayed the blinking underline cursor in the top right corner for a bit then printed out "[ 197,492000] usb 2-4: can't set up config #1 error -71".  
In short, it still didn't work.  Oh well.  I'll just wait for new firmware.  Thanks for your help, though.  I thought about it and I don't want to get rEFIt because I don't think I'll need it.  I can wait for a firmware update instead.

---

### Post by lotus49 on 2008-01-25
> **Rusty Spoork said:**
> Ok, so I tried the image, I burned it to a CD-R and it showed up as "Windows" on boot+OPTION.  When I clicked on it it loaded Ubuntu, but first it flashed something which I thought said PCI support failed or something, it was really quick. Then it loaded the Ubuntu Loading bar, and got about 1/20 of the way and flashed black.  It only displayed the blinking underline cursor in the top right corner for a bit then printed out "[ 197,492000] usb 2-4: can't set up config #1 error -71".  
In short, it still didn't work.  Oh well.  I'll just wait for new firmware.  Thanks for your help, though.  I thought about it and I don't want to get rEFIt because I don't think I'll need it.  I can wait for a firmware update instead.

The first message is nothing to worry about, my laptops all come up with that message and everything works.  It is also the case that any boot disk with an MBR shows up as Windows even if it is actually Linux.

What appears to be happening is that the kernel is loading but it isn't finding the root partition.  This does definitely work and it should not be hardware dependent by which I mean you should be able to get this to work on almost any hardware built in the last 10 years.  I suggest you have a look on the net for instructions how to make a boot disk and try creating your own.

Do you have another machine you could boot the USB installation from?  If so then you should test it on that and if that doesn't boot you know there is a problem with the installation.  If that works, then something I configured in the boot CD doesn't match your configuration.

I wouldn't hold your breath waiting for a firmware update, I am not optimistic that I will see this fixed before I upgrade my MBP.  Installing rEFIt will not work at all with your setup so you can discount that option anyway.

---

### Post by Rusty Spoork on 2008-01-27
Alright.  I'll try to find some good hardware to test it on and if it doesn't work, I can go and find some instructions on that interweb-thing to make a boot CD.  As it stands, the windows POS that I have crashes whenever you plug a USB cable in, so I will need to find another computer.  I think its a short but I could care less.  

Thanks for your help,

Rusty

---

### Post by Rusty Spoork on 2008-01-28
Lotus, do you know of any good instructions for making these boot CDs?  I'm going to reinstall and write down everything but i'd like to be able to make these CDs.  Also, when you made that image was for the 64-bit version or does that even matter?

Thanks,

Rusty

---

### Post by cyberdork33 on 2008-01-28
> **Rusty Spoork said:**
> Lotus, do you know of any good instructions for making these boot CDs?  I'm going to reinstall and write down everything but i'd like to be able to make these CDs.  Also, when you made that image was for the 64-bit version or does that even matter?
You need to use the 64 bit kernel so, yes it matters.

Here is the official how to from grub... I don't know if this is exactly what he was using:
[http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html](http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html)

---

### Post by PaulFXH on 2008-01-29
@lotus49

I don't have any answers or suggestions for you but I'm also interested in getting WinXP to boot to my MacBook (C2D, 2.16 GHz) from a usb HDD.
I already have Fedora 8 and SabayonLinux 3.4f on the external drive which boot fine to the Mac.
Problem is I can't get WinXP to even INSTALL on the bloody usb drive, let alone boot from it.
You say in post #85 of this thread
> My first attempt was to install XP on a USB HDD using my Compaq nc4200 laptop (which is running Ubuntu 7.10). The installation went smoothly and XP booted and ran fine.
How did you do this? On the two computers where I have tried this, the Windows Setup complains that installing to the external drive is just not possible.
In googling around, there indeed does not seem to be any ready fix to this although [this]("http://www.ngine.de/index.jsp?pageid=4176") seems to be the most promising.
I might give this a shot but I'd be interested to know how you got over this barrier first.
Thanks
Paul

---

### Post by Dark Dragon of Fire on 2008-02-05
Hello everybody,

I may have found a solution to this problem. I tried to install xubuntu on a 8 GB pendrive, with the same result as reported by other users - EFI fails to boot. Now here is a thought that I came up with: 
I accidentally installed GRUB on my hard drive during a xubuntu install from the LiveCD. It did not bother me since GRUB resides in the MBR which is unimportant to OS X, but together with it, a Linux symbol appeared in rEFIt. When I clicked on it, (probably) GRUB told me something like "No bootable drive found. Insert a bootable media and hit any key to continue.". Later, I messed up the MBR of my harddrive in order to get rid of the Linux icon, but it did not work.
Now that I read through this thread, my idea is as follows: Wouldn't it be possible to install GRUB or LILO on the internal harddrives MBR and modify it in a way that it offers an option to boot from an external drive? That would spare out the need for a CD.

The only disadvantage would be that the resulting MBR is a bit fragile, as it could be treated as error by some disk repair tools under OS X.

Sorry for any wrong grammar or spellings.

---

### Post by cyberdork33 on 2008-02-05
> **Dark Dragon of Fire said:**
> Now that I read through this thread, my idea is as follows: Wouldn't it be possible to install GRUB or LILO on the internal harddrives MBR and modify it in a way that it offers an option to boot from an external drive? That would spare out the need for a CD.

The only disadvantage would be that the resulting MBR is a bit fragile, as it could be treated as error by some disk repair tools under OS X.
This is essentially what you are doing by placing /boot on the internal drive. You need to have the grub configuration on the internal drive as well, although I don't know if it has been tried to have the kernel on the external, with grub on the internal... Mac Pro users tend to have issues booting from a second internal drive even because the Mac changes how secondary drives are seen by the system... the second disk becomes sda instead of sdb as one would expect, but only if you boot from that drive..., but I found a workaround that is similar to what you are stating, so it might be worth a try on an external drive: [http://wiki.debian.org/DebianOnIntelMacPro#line-188](http://wiki.debian.org/DebianOnIntelMacPro#line-188)

---

### Post by Dark Dragon of Fire on 2008-02-06
Just tried to create another partition on my hard drive using gparted: It failed, corrupting the sector tables (thats what I got a rescue disk for). So basically, I have the problem of now knowing how to add a partition to my HD without reformatting it. Any ideas? 

Btw: Has anyone written an email to Apple yet?

---

### Post by lomlate on 2008-02-10
I just read this entire thread, I found it all very interesting and am hoping to hell someone with technical knowledge has filed off an e-mail to apple about this. It's interesting to see that a year has passed without a solution on this issue!

I'm trying to install using whole disk encryption, which would pretty much make the whole boot partition on the 100meg of free mac space not workable, yes? Or if not, how would you go about ensuring everything is encrypted? 

Secondly, if you did it using a bootcd, for someone who has never used such a CD, how long do you think it would add to the boot time? If it would only add 30seconds to a minute I think that would be an acceptable solution for me, which bootcd would you recomend that doesn't load all of the other uneeded things but just goes straight into helping you boot onto the external?

Lastly what about a network boot? I have no idea how this works but if you set up a NAS as appose to a USB hard drive could you get it working like that? That would be an interesting way to do it if anybody knows how...

---

### Post by lotus49 on 2008-02-11
> **cyberdork33 said:**
> You need to use the 64 bit kernel so, yes it matters.

Here is the official how to from grub... I don't know if this is exactly what he was using:
[http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html](http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html)

That is what I was using and the CD image I sent you was a 32 bit image.  The boot CD worked for me but wasn't really much use as I was just experimenting with Ubuntu to attempt to to diagnose the problem I had with XP (I much prefer Ubuntu to XP and I run it on several machines, but the games I wanted XP for don't run on Ubuntu).

---

### Post by lotus49 on 2008-02-11
> **PaulFXH said:**
> @lotus49

I don't have any answers or suggestions for you but I'm also interested in getting WinXP to boot to my MacBook (C2D, 2.16 GHz) from a usb HDD.
I already have Fedora 8 and SabayonLinux 3.4f on the external drive which boot fine to the Mac.
Problem is I can't get WinXP to even INSTALL on the bloody usb drive, let alone boot from it.
You say in post #85 of this thread

How did you do this? On the two computers where I have tried this, the Windows Setup complains that installing to the external drive is just not possible.
In googling around, there indeed does not seem to be any ready fix to this although [this]("http://www.ngine.de/index.jsp?pageid=4176") seems to be the most promising.
I might give this a shot but I'd be interested to know how you got over this barrier first.
Thanks
Paul

You cannot do this with a standard XP install CD.  If you follow the instructions here [http://www.ngine.de/index.jsp?pageid=4176](http://www.ngine.de/index.jsp?pageid=4176) VERY carefully you can edit the CD so it will install on a USB drive.

It is a bit of a faff, but as long as you are meticulous, it works well (but not on a MacBook Pro unfortunately).

---

### Post by jhinz03 on 2008-02-12
> **lotus49 said:**
> I fixed the "GRUB Hard Disk Error" problem by booting into the Ubuntu live CD and reinstalling grub.  I also fixed the menu.lst file.  BTW I said in an earlier post that the menu.lst files on the internal and external disk should be the same.  This should have said "almost the same" as the GUIDs will be different.

I tried to boot into the Ubuntu installation on the USB HDD with the predictable result that rEFIt threw the same error message that I mentioned above.

I have come to the conclusion that this is simply not possible.  I keep saying this (here and in other forums) in the vain hope that someone will tell me I'm wrong, but I have finally decided to give up.  I am convinced now that until Apple releases some new and better firmware, this is not going to work no matter what I do.

XP and Linux will run well on a MBP, but neither will boot from a USB HDD.  There are ways around this such as booting from the internal HDD and mounting / from the external drive, but as I have said, I don't want to change anything on my internal HDD so I am out of luck.

I am currently having the same issues and it doesnt appear anyone has gotten this working yet but havent seen an update to this issue in a long while.  Was wondering if anyone has gotten this working yet and how.  Im on a C2D Santa Rosa MBP.  Ive already had issues booting the liveCD but finally got it working in Safe Graphics Mode.  Install went great but just cant boot.

---

### Post by cyberdork33 on 2008-02-12
> **jhinz03 said:**
> I am currently having the same issues and it doesnt appear anyone has gotten this working yet but havent seen an update to this issue in a long while.  Was wondering if anyone has gotten this working yet and how.  Im on a C2D Santa Rosa MBP.  Ive already had issues booting the liveCD but finally got it working in Safe Graphics Mode.  Install went great but just cant boot.It is not working off an external drive yet.

---

### Post by PaulFXH on 2008-02-13
> **lotus49 said:**
> You cannot do this with a standard XP install CD.  If you follow the instructions here [http://www.ngine.de/index.jsp?pageid=4176](http://www.ngine.de/index.jsp?pageid=4176) VERY carefully you can edit the CD so it will install on a USB drive.

It is a bit of a faff, but as long as you are meticulous, it works well (but not on a MacBook Pro unfortunately).

Thanks for the reply.

First, I should say that I realize that this is a side-issue to the main one being discussed here and has little or nothing to do with Ubuntu. I apologize for that and hope people can bear with me.

lotus49:
Indeed, I did modify my install CD as you describe (the link in my post is exactly the same as yours).
However, I still couldn't get Windows XP to want to install on a usb HDD and I tried it on 4 different computers including a MacBook.
My attempts either ended with the exact same complaint from the Windows Setup that it can't install on a usb drive or I got the infamous BSoD.
Perhaps, I didn't modify the install CD as carefully and meticulously as you advise:(
I also note that the ngine guide (from the link) stresses that this will only work if the computer actually supports booting from a USB drive in the first place (even though my interest is solely in installing to the external drive and not booting to it in the normal way).
Now, this rules out the MacBook.
The other three computers I used were all Dell Desktops (4550, E520 and 9200). All of these CAN boot to a usb drive but not in the conventional way in that the usb drive doesn't show up in the BIOS boot sequence. Instead, pressing F12 during the boot allows you to choose from a number of alternative booting options which include whatever usb devices you have connected.
I'm not sure if this is sufficiently close to the stipulation the ngine makes about the computer supporting usb booting.
Comments welcome.

---

### Post by lomlate on 2008-02-13
I installed ubuntu using the alternate install cd and lvm encryption, with the thumbdrive mounted as sdb1. I then tried to use the boot cd mentioned earlier in this thread (I don't know how to make my own and suspect it's beyond my technical abilities). When it boots up it shows an "ubuntu" screen. If the drive is not plugged in it freezes at that screen. If the drive is plugged in it then goes to a command prompt "initramfs" with a few built in commands.

Does anyone know what's going on here?

---

### Post by PaulFXH on 2008-02-14
I've had this problem a few times.
I have a 250GB usb drive hooked up to my MacBook (C2D) where I can boot to a number of Linux OSes although I actually have Gutsy on the Mac internal drive.
The problem usually, if not always, ocurrs after an update that changes /etc/fstab and/or /boot/grub/menu.lst
In my case, the problem invariably is due to an unrecognized UUID in the kernel line of menu.lst which means the real root is unreachable after loading the kernel which means you can't go any further and you're stuck with initramfs.
What I do (and as I know very little about your situation so YMMV) is:

Load up the Gutsy install CD
Reboot to the CD (hard reboot needed here, I'm afraid)
Open up a terminal when the LiveCD environment opens
Check in /dev to see what your flash drive is called (maybe sdb1 or sdc1 and don't rule out sda1) -- must have it plugged in here.
Whatever it's called, put  relevant entry in /etc/fstab such as
```
/dev/sdb1  /media/sdb1  defaults   0 0
```
Save the /etc/fstab
Then in a terminal go to /media and sudo mkdir sdb1 (or whatever you want)
Then mount /media/sdb1 with
```
sudo mount /media/sdb1
```
Now, your unbootable system is accessible.
Next look in the flash drive /boot/grub/menu.lst with
```
cd /media/sdb1/boot/grub
sudo gedit menu.lst
```
If your situation is the same as mine, the menu entry where you are trying to boot your flash drive will contain in the kernel line something like
```
root=UUIDXXXXXXXXXXXXXXXXXXXXXX
```
Substitute this with root=/dev/sdb1 (or whatever your flash drive device is called)
Save the file and reboot.
This works for me. but as I said, YMMV
Good luck

---

### Post by lotus49 on 2008-02-14
> **PaulFXH said:**
> Thanks for the reply.

First, I should say that I realize that this is a side-issue to the main one being discussed here and has little or nothing to do with Ubuntu. I apologize for that and hope people can bear with me.

lotus49:
Indeed, I did modify my install CD as you describe (the link in my post is exactly the same as yours).
However, I still couldn't get Windows XP to want to install on a usb HDD and I tried it on 4 different computers including a MacBook.
My attempts either ended with the exact same complaint from the Windows Setup that it can't install on a usb drive or I got the infamous BSoD.
Perhaps, I didn't modify the install CD as carefully and meticulously as you advise:(


It did take me a couple of goes to get this to work, but I did in the end.

It has just occurred to me that there was one weird problem I had.  The first machine I tried it on had an external DVD drive and I did have a problem with the second machine when I tried booting from the internal CD drive but it worked perfectly with an external CD drive - do you have one to try it with?

---

### Post by lotus49 on 2008-02-14
> **PaulFXH said:**
> I've had this problem a few times.
I have a 250GB usb drive hooked up to my MacBook (C2D) where I can boot to a number of Linux OSes although I actually have Gutsy on the Mac internal drive.
The problem usually, if not always, ocurrs after an update that changes /etc/fstab and/or /boot/grub/menu.lst
In my case, the problem invariably is due to an unrecognized UUID in the kernel line of menu.lst which means the real root is unreachable after loading the kernel which means you can't go any further and you're stuck with initramfs.

There are other reports of this working on MacBooks but not MacBook Pros - you are in luck.

I am a big fan of running alternative OSs on USB disks and I am familiar with the problems with menu.lst configuration and in this case that is definitely not the problem unfortunately.

---

### Post by PaulFXH on 2008-02-14
> **lotus49 said:**
> It did take me a couple of goes to get this to work, but I did in the end.

It has just occurred to me that there was one weird problem I had.  The first machine I tried it on had an external DVD drive and I did have a problem with the second machine when I tried booting from the internal CD drive but it worked perfectly with an external CD drive - do you have one to try it with?

Thanks for this advice.
The fact that you had problems too encourages me to try a few more times.
But that thing with the external CD drive is weird. I'll keep that in mnd if all else fails.

---

### Post by lomlate on 2008-02-17
Sorry for everyone's time but I would really love some help with this one.

I used the 100meg partition to install ubuntu, with a flash drive. I used the 10.5 alt install cd and made /boot the 100meg partition, with root being the partition i made on the flash drive. 

It installed perfectly, but now when i try and boot the ubuntu loading bar never gets past one loader thing. 

People have said in this thread about "menu.list" configuration? Is that related to what I'm experiencing and if so, how do I edit it. What's going wrong here? I figure that the boot partition is having trouble finding the flash drive. how do I encourage it?

the flash drive is using LVM encrypted partitions, which could comlicate things immensely.

---

### Post by cyberdork33 on 2008-02-17
> **lomlate said:**
> I used the 100meg partition to install ubuntu, with a flash drive. I used the 10.5 alt install cd and made /boot the 100meg partition, with root being the partition i made on the flash drive. just for clarification, did you mean 7.10?

> **lomlate said:**
> It installed perfectly, but now when i try and boot the ubuntu loading bar never gets past one loader thing.boot without the quiet and silent options on the kernel in grub, this will allow you to see where the boot is stalling.

> **lomlate said:**
> People have said in this thread about "menu.list" configuration? Is that related to what I'm experiencing and if so, how do I edit it. What's going wrong here? I figure that the boot partition is having trouble finding the flash drive. how do I encourage it?Possibly, I would check the system messages first as described above. basically, the mac sets the boot device as sda instead of how it normally works in a pc where the primary internal drive is always sda no matter what. you will have to try different things to find what your root device is actually referred to as.

> **lomlate said:**
> the flash drive is using LVM encrypted partitions, which could comlicate things immensely.yea you might want to cut that out of hte equation temporarily to get it working inthe first place before adding encryption (though LVM shouldn't really make a difference).

---

### Post by PaulFXH on 2008-02-17
@lomlate
Why don't you post your /boot/grub/menu.lst here so others might have a better chance of helping you.
To do this, boot to the Live CD and mount your "unbootable" flash drive system (as I described in my earlier post).
Then, if your flash drive system is mounted as "/media/sdb1", open up the menu.lst file in a text editor (I'm assuming Gedit) with
```
sudo gedit /media/sdb1/boot/grub/menu.lst
```
Now the text editor (this is just like Notepad if you're a Windows user) will open and display what's inside the menu.lst file.
Copy and paste this into a post here on the forum.
If you think you see what's wrong in the menu.lst file and want to make a change, MAKE SURE you back it up first with something like
```
sudo cp /media/sdb1/boot/grub/menu.lst /media/sdb1/boot/grub/menu.lst.old
```
So if you mess up, you can always get back to where you were.
I agree with cyberdork33 that you should take out the lvm thing until you get your system straightened out
Good luck

---

### Post by lomlate on 2008-02-18
> **PaulFXH said:**
> @lomlate
Why don't you post your /boot/grub/menu.lst here so others might have a better chance of helping you.
To do this, boot to the Live CD and mount your "unbootable" flash drive system (as I described in my earlier post).
Then, if your flash drive system is mounted as "/media/sdb1", open up the menu.lst file in a text editor (I'm assuming Gedit) with
```
sudo gedit /media/sdb1/boot/grub/menu.lst
```
Now the text editor (this is just like Notepad if you're a Windows user) will open and display what's inside the menu.lst file.
Copy and paste this into a post here on the forum.
If you think you see what's wrong in the menu.lst file and want to make a change, MAKE SURE you back it up first with something like
```
sudo cp /media/sdb1/boot/grub/menu.lst /media/sdb1/boot/grub/menu.lst.old
```
So if you mess up, you can always get back to where you were.
I agree with cyberdork33 that you should take out the lvm thing until you get your system straightened out
Good luck

Firstly I want to just say: wow. All of you guys are incredibly kind and it's very exciting to know that I'm slowly learning things about mount points and partitions as I go through this.

Attached is my menu.lst file, and i was thinking of editing the "sdb1" until I found something that worked, I'll update with a copy+paste of where it goes wrong in recovery/text mode.

in code is an approximation of the last page of the boot in recovery mode before it stops working. the 4106MB is the flash srive. i've dried booting to sdb1 with the same problem. 

scsi 4:0:0:0 Direct-Access    USBDISK RUNDISK    1.00 PQ : 0 ANSI: 2
sd 4:0:0:0: [sdb] 8020000 512 hardware sectors (4106 MB)
sd 4:0:0:0: [sdb] Write protection is off
sd 4:0:0:0: [sdb] Assuming drive cache: write through
sd 4:0:0:0: [sdb] 8020000 512 hardware sectors (4106 MB)
sd 4:0:0:0: [sdb] Write protection is off
sd 4:0:0:0: [sdb] Assuming drive cache: write through
sdb : sdb1
sd 4:0:0:0: [sdb] Attached SCSI removable disk
sd 4:0:0:0: [sdb] Attached scsi generic sg2 type 0
done.

Check root=bootarg cat /proc/cmdline
or missing modules, devices cat /proc modules ls /dev
ALERT! /dev/mapper/sda1_crypt does not exist. Dropping to a shell!

---

### Post by PaulFXH on 2008-02-18
@lomlate
OK, it seems your problem is definitely that the boot process cannot find your real root which is where your Ubuntu is installed (yr flash drive).
Your /boot/grub/menu.lst has this kernel line
```
kernel		/vmlinuz-2.6.22-14-generic root=/dev/mapper/sda1_crypt ro quiet splash
```
and the boot output shows:
```
ALERT! /dev/mapper/sda1_crypt does not exist
```
I have no experience using LVM so can't comment on this but do you really need it at this early stage.
I would suggest
1. Take out that lvm thing
2. Then use your LiveCD to get back to your unbootable system and check out what usb stuff  are included in /dev in your system (i.e. /media/sdb1/dev when entered from the LiveCD environment)
The stuff you're looking for will start with "sd" like sda1 or sdb2 or sdc3 or whatever.
One of these will be the drive you need in kernel line in your /boot/grub/menu.lst.
I really don't know what that "mapper" directory is in the /dev folder unless it's got something to do with LVM. But then this should go when you take out LVM.
When you're looking at /media/sdb1/dev in the LiveCD environment, you might want to check if there really is a "mapper" folder in there too.
Another thing you should do is to take out "quiet" in the kernel line which will give you the same "verbose" output during boot that you get when you use the recovery mode boot (notice there's no "quiet" in the recovery mode kernel line)
You can do this by changing
```
kernel		/vmlinuz-2.6.22-14-generic root=/dev/mapper/sda1_crypt ro quiet splash
``` 
to
```
kernel		/vmlinuz-2.6.22-14-generic root=/dev/mapper/sda1_crypt ro #quiet splash
```
The "#" means it'll be ignored but you can get it back easy when everything is straightened out by just removing the #.
Remember to back up your file before you make changes.
BTW, are you actually using a MacBook? If so, what type?
On my MacBook (C2D, 2.16 GHz), I cannot get my usb flash drive to show up in /dev so that's why I'm a bit surprised that it seems to be working for you.
Good luck

---

### Post by lomlate on 2008-02-18
Yeah I'm using a 2.0ghz macbook listed as MacBook3,1. it's the newest revision. I'll print that stuff out and give it a go, thanks.

---

### Post by lomlate on 2008-02-18
It worked like a charm without the LVM. the flash drive is /dev/sdb1 and the boot partition is /dev/sda3. I'm not quite sure how to figure out if this is a problem with the LVM itself and how I installed it, a problem the LVM has with being on a flash drive or a problem the boot loader has with the LVM. It's a tricky one.

For people reading this thread. To get this going i booted into the install cd, i created an ext3 partition in the 100meg space at teh end of the hardrive, set it to bootable and then mounted it to /boot. I then set / to the thumbdrive.

the new menu.lst reads:


title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=1...removedbylomlate...a ro quiet splash
initrd		/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=1...removedbylomlate...a ro single
initrd		/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin
quiet

---

### Post by shampshi on 2008-02-27
So here's what I was wondering:  Is anyone trying to do the external drive boot thing with an iMac?  It seems that most people who said what kind of hardware they were running were using MBs or MBPs.  I just got a 20" iMac C2D, running Leopard of course, and would like to not mess with my internal.  (I'm just recovering from what almost became a complete data loss from my G5 iMac.)  I'm new to Linux and am learning it partially to help out my man because he's learning Ubuntu for his job.  Do this same issues apply?  Should I just try it and see what happens?  If there's trouble, I'll be sure to post.  Thanks in advance everyone.

---

### Post by cyberdork33 on 2008-02-27
> **shampshi said:**
> So here's what I was wondering:  Is anyone trying to do the external drive boot thing with an iMac?  It seems that most people who said what kind of hardware they were running were using MBs or MBPs.  I just got a 20" iMac C2D, running Leopard of course, and would like to not mess with my internal.  (I'm just recovering from what almost became a complete data loss from my G5 iMac.)  I'm new to Linux and am learning it partially to help out my man because he's learning Ubuntu for his job.  Do this same issues apply?  Should I just try it and see what happens?  If there's trouble, I'll be sure to post.  Thanks in advance everyone.I have a 20" iMac (pre aluminum) It doesn't work for me. It has been a long time since I actually tried it though. I would go ahead and try it won't hurt.

---

### Post by metalelf0 on 2008-03-14
> **lotus49 said:**
> 
The key drawback to this approach is that the CD will need to be recreated when the kernel is upgraded (it will still boot the old kernel though).

Try it and if it works I'll help you with recreating the disk so you know how to do it.


Why do you say this? Do you refer to the vmlinuz link still pointing to the all kernel? Or does the stage2-eltorito file change from kernel to kernel, making the cd unable to boot a new kernel revision?

Thank you very much for making this file, I'm gonna try it soon!

AS

---

### Post by cyberdork33 on 2008-03-14
> **metalelf0 said:**
> Why do you say this? Do you refer to the vmlinuz link still pointing to the all kernel? Or does the stage2-eltorito file change from kernel to kernel, making the cd unable to boot a new kernel revision?

Thank you very much for making this file, I'm gonna try it soon!

AS
Well, if the kernel is on the cd, then you cannot update it without creating a new disk...

---

### Post by metalelf0 on 2008-03-14
> **cyberdork33 said:**
> Well, if the kernel is on the cd, then you cannot update it without creating a new disk...

I didn't get this, I thought the cd could boot the kernel directly from the external disk. I've seen this only when I burnt the cd... no problem anyway, I'll use a rewritable disc for this. Thanks!

---

### Post by sludgeball on 2008-03-26
Can someone please post detailed instructions on how to make a grub cd to boot ubuntu from the external? (im a newbie at linux)

and  how should i change the grub "menu.lst" config?

i changed the install of ubuntu so grub is installed onto my external as well, so are the settings correct?

---

### Post by billbear on 2008-04-02
Is it possible to use yaboot instead of grub on intel Macs?
If it's possible, i think booting an intel Mac to ubuntu from an external disk will be easy.
Just a thought

---

### Post by cyberdork33 on 2008-04-02
> **billbear said:**
> Is it possible to use yaboot instead of grub on intel Macs?
If it's possible, i think booting an intel Mac to ubuntu from an external disk will be easy.
Just a thought
I don't think so. yaboot was just for PPC macs running open firmware. Weren't you the guy that had like 5 OSs booting on one Mac? How did you get Linux root partitions beyond #4 to boot?

---

### Post by billbear on 2008-04-03
> **cyberdork33 said:**
> I don't think so. yaboot was just for PPC macs running open firmware. Weren't you the guy that had like 5 OSs booting on one Mac? How did you get Linux root partitions beyond #4 to boot?

i think linux understands GPT, so installing to a GPT disk and creating partitions beyond #4 is ok.
But it seems grub can only be installed on an MBR disk, since apple maintains a mixture of GPT/MBR, this is not a problem, just install grub to the MBR or among the first 4 partitions then it boots.
GRUB seems not to be completely unaware of GPT, once GRUB is loaded, it finds the root partition or /boot partition beyond #4 and reads menu.lst there to continue booting. 

i have not found a way to boot ubuntu from an external disk. i think those who claim they have done this may have installed grub to the internal.  i believe apple's firmware just cannot boot legacy OSes on external disks, that's why i think about using yaboot. Or maybe someone could develop a bootloader similar to PPC yaboot for intel Macs. i don't know much about yaboot, it seems to use an HFS partition to boot linux, cheating Mac to think it's booting MacOS, am i wrong?

---

### Post by entangled on 2008-04-03
Sorry if this point has already been discussed but we know that Ubuntu live CDs boot OK (using the Alt key to show bootable devices) so it *is* presumably possible to boot off drives other than the internal and without any grub-like entries on the main disk.

---

### Post by cyberdork33 on 2008-04-03
> **billbear said:**
> i think linux understands GPT, so installing to a GPT disk and creating partitions beyond #4 is ok.
But it seems grub can only be installed on an MBR disk, since apple maintains a mixture of GPT/MBR, this is not a problem, just install grub to the MBR or among the first 4 partitions then it boots.
GRUB seems not to be completely unaware of GPT, once GRUB is loaded, it finds the root partition or /boot partition beyond #4 and reads menu.lst there to continue booting. I understood that you could use partitions beyond #4, but I though that the "bootable" partition (i.e. /boot or / ) had to be one of the first four also. I guess it is just Grub.

> **billbear said:**
> i have not found a way to boot ubuntu from an external disk. i think those who claim they have done this may have installed grub to the internal.  i believe apple's firmware just cannot boot legacy OSes on external disks, that's why i think about using yaboot. Or maybe someone could develop a bootloader similar to PPC yaboot for intel Macs. i don't know much about yaboot, it seems to use an HFS partition to boot linux, cheating Mac to think it's booting MacOS, am i wrong?yea but I think that is because it emulates a Apple Partition Format I believe, which may still be no good on an Intel Mac.

Those that do get it working tend to have used a standard MBR format. and marked the boot partition with a boot flag. It also seems that most use Diskutility to create the MBR disk.

> **entangled said:**
> Sorry if this point has already been discussed but we know that Ubuntu live CDs boot OK (using the Alt key to show bootable devices) so it *is* presumably possible to boot off drives other than the internal and without any grub-like entries on the main disk.Yes, but I think the key is that it is a block device on a usb/firewire port. Has anyone tried booting a cd from a USB Optical Drive? If that is possible, then basically installing Ubuntu to a hard drive that looks like a cdrom device should work.

---

### Post by metalelf0 on 2008-04-03
> **cyberdork33 said:**
> Has anyone tried booting a cd from a USB Optical Drive? If that is possible, then basically installing Ubuntu to a hard drive that looks like a cdrom device should work.

I had tried, without success. The problem is how the firmware handles the USB bus: booting linux systems from usb keys is also impossible.

---

### Post by billbear on 2008-04-03
> **cyberdork33 said:**
> I understood that you could use partitions beyond #4, but I though that the "bootable" partition (i.e. /boot or / ) had to be one of the first four also. I guess it is just Grub.


It's not a must for /boot or / to be one of the first four. The quad boot method i posted on forum.onmac.net just works.

---

### Post by billbear on 2008-04-03
> **cyberdork33 said:**
> 

yea but I think that is because it emulates a Apple Partition Format I believe, which may still be no good on an Intel Mac.

Those that do get it working tend to have used a standard MBR format. and marked the boot partition with a boot flag. It also seems that most use Diskutility to create the MBR disk.



Can those who claimed that they had got ubuntu boot from external HD post a detailed repeatable process? Remove your internal HD, if you can still boot ubuntu then you can say you boot it solely from external. And this external should be able to boot every PC. ( If it can only boot one machine i don't see a reason to install it on a removable disk. My ubuntu@removable can boot every PC that supports booting from external, so i really really like to be able to boot my mac too)

---

### Post by billbear on 2008-04-03
> **cyberdork33 said:**
> 
Has anyone tried booting a cd from a USB Optical Drive? If that is possible, then basically installing Ubuntu to a hard drive that looks like a cdrom device should work.

Yes, booting from external optical drive is possible, Mac/XP/Vista/Ubuntu install disks can all boot. Holding alt upon boot cannot give you a chance to boot them, but with rEFIt, power on my macbook, when the rEFIt menu comes out, select reboot, Macbook reboots while external cd still rotating, when the rEFIt menu comes out again the external cd icon will appear. If not, reboot again. It seems the external cd must be recognized in a given time or it will not appear as a choice but if it's in the internal optical device no matter how long it takes macbook just waits.

But external HD is really something else. How can one make it "looks like" a cdrom?

---

### Post by cyberdork33 on 2008-04-03
> **billbear said:**
> Can those who claimed that they had got ubuntu boot from external HD post a detailed repeatable process? Remove your internal HD, if you can still boot ubuntu then you can say you boot it solely from external. And this external should be able to boot every PC. ( If it can only boot one machine i don't see a reason to install it on a removable disk. My ubuntu@removable can boot every PC that supports booting from external, so i really really like to be able to boot my mac too)As I said, it seems to only work with certain Macs for some reason. Some have suggested it is a firmware change. There are those on the Mactel mailing list that claim to have it work as well. 

People want to install to an external because they do not want to partition their internal disk and I don't really blame them... It was a mess to fix that partitioning if you only have Tiger available without losing data. Transportability is definitely a plus though, I am not saying that shouldn't be a goal.

> **billbear said:**
> Yes, booting from external optical drive is possible, Mac/XP/Vista/Ubuntu install disks can all boot. Holding alt upon boot cannot give you a chance to boot them, but with rEFIt, power on my macbook, when the rEFIt menu comes out, select reboot, Macbook reboots while external cd still rotating, when the rEFIt menu comes out again the external cd icon will appear. If not, reboot again. It seems the external cd must be recognized in a given time or it will not appear as a choice but if it's in the internal optical device no matter how long it takes macbook just waits.

But external HD is really something else. How can one make it "looks like" a cdrom?I don't know. It was just an idea to throw out there. How does the layout of a bootable cd rom differ from a hard drive? I mean a cd does not have a MBR...

---

### Post by billbear on 2008-04-05
ok i understand i cannot use yaboot.
what about grub 2 ? Has anyone tried? GRUB 2 FAQ says:

2. What is the status of GRUB 2?
It is usable, but we are still making incompatible changes from time to time. Stabilizing the features is planned in November, 2008. It is working on PC, OpenFirmware-based PowerPC machines (PowerMac and Pegasos) and EFI-based PC (IntelMac), and being ported to RiscOS/ARM, UltraSparc, and coreboot (formerly, LinuxBIOS).

---

### Post by cyberdork33 on 2008-04-05
grub2 is a full EFI bootloader (as is elilo). Unfortunately, booting from EFI (on a mac) is not working well at all yet. I think the mac mini is the only machine that can work very well at all (3d acceleration included).

[http://grub.enbug.org/TestingOnEFI](http://grub.enbug.org/TestingOnEFI)

---

### Post by billbear on 2008-04-06
> **cyberdork33 said:**
> grub2 is a full EFI bootloader (as is elilo). Unfortunately, booting from EFI (on a mac) is not working well at all yet. I think the mac mini is the only machine that can work very well at all (3d acceleration included).

[http://grub.enbug.org/TestingOnEFI](http://grub.enbug.org/TestingOnEFI)

Thank you. I did not hear about elilo. I'm doing some research into it and i believe this will be the solution.

---

### Post by billbear on 2008-04-06
After "blessing", i am able to boot into both elilo and grub2 from my external HD.
But i don't know how to configure them to boot the linux kernel. 
The documents on them are rare and unclear.
Can anyone help?
Maybe i have to wait for the final grub2 release...

---

### Post by czechmate on 2008-04-09
I am very close to getting this working, but have not quite managed just yet.

The key is that there is a hidden FAT32 partition as part of the GPT/EFI setup on the MBP.
My plan is to install grub stage1 in the MBR, and stage2 in the FAT32 partition.
The problem has been that grub can not see the external disk, presumably because the BIOS emulation does not provide the drive id. This led to me also putting the kernel and initrd on the hidden FAT32 partition too.

This is very similar approach to using the boot CD, but instead the boot files will be on the hidden (and mostly unused) FAT32 partition.

I had to modify grub to recognise the EFI partition with ID EE as real FAT32. 

So far I have installed GRUB ok, and booted a kernel and initrd. As a test I've used the kernel and initrd from a Fedora install DVD, and that recognises the external disk. That means I know it is possible to do what I want. However, I've not yet managed to get a kernel and initrd of my own to boot.

---

### Post by czechmate on 2008-04-09
Note that this method does not require rEFIt (although works with it). It is also booting in bios emulation mode, so the graphics et al should work ok. I believe elilo and grub2 will actually be proper EFI loaders, and without bios emulation there will be other non-trivial issues to overcome (see the rEFIt page for a discussion of this).

---

### Post by billbear on 2008-04-09
> **czechmate said:**
> I am very close to getting this working, but have not quite managed just yet.

The key is that there is a hidden FAT32 partition as part of the GPT/EFI setup on the MBP.
My plan is to install grub stage1 in the MBR, and stage2 in the FAT32 partition.
The problem has been that grub can not see the external disk, presumably because the BIOS emulation does not provide the drive id. This led to me also putting the kernel and initrd on the hidden FAT32 partition too.

This is very similar approach to using the boot CD, but instead the boot files will be on the hidden (and mostly unused) FAT32 partition.

I had to modify grub to recognise the EFI partition with ID EE as real FAT32. 

So far I have installed GRUB ok, and booted a kernel and initrd. As a test I've used the kernel and initrd from a Fedora install DVD, and that recognises the external disk. That means I know it is possible to do what I want. However, I've not yet managed to get a kernel and initrd of my own to boot.

How did you write to the hidden FAT32 partition? Is it safe to write to that partition? What is the use of that partition? I read somewhere it's for apple firmware update.

Seems you have installed grub to the internal, this is not what i want. I want ubuntu to boot solely from the external, without changing anything on the internal. I plan to use hybrid GPT/MBR partition table on my external HD, install grub on its MBR and grub2 on a partition (hidden FAT32 partition of the external should be ok) so it will be able to boot every PC/Mac.

---

### Post by dazzur on 2008-04-10
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

---

### Post by billbear on 2008-04-10
> **dazzur said:**
> [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

This link may work for a PC. Unfortunately Macs are very different.

---

