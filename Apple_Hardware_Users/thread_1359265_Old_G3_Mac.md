---
title: "Old G3 Mac"
date: 2009-12-19
forum: Apple Hardware Users
---

### Post by phillw on 2009-12-19
No sniggering ;-)

I've tracked down 9.04 Xubuntu for PPC. It's going to have a 'play' on an old G3 with 512Mb RAM. In theory, it should be okay - Does anyone know of any 'horrors' that I should be aware of - Or a different version of Xubuntu that I should be using for a low RAM'd G3 PPC ?

Regards,

Phill.

---

### Post by rjcalifornia on 2009-12-20
well, the ram you have is more than enough to run xubuntu, so you wont face major problems

---

### Post by phillw on 2009-12-20
Thanks for the reply,

First snag (I can boot off the cd).

I need to keep os9 (Mac OSX partition is expendable & is where I was aiming to put Xubuntu)

From my reading, it seems that xubuntu can't recognise Mac partitions & will take out both OS9 (a BIG no-no) and OSX (Yes please).

I've been reading through the archives & this is the nearest I can find -->  [http://ubuntuforums.org/showthread.php?t=327236](http://ubuntuforums.org/showthread.php?t=327236)

BootX has been replaced with yaboot. So, I'm a bit lost as to how to proceed. 

I have an external FireWire Drive that is formatted in HFS+ and also a 9.2 CDrom - So I could backup data & re-install.

I'd be grateful for any pointers,

Phill.

---

### Post by tiresia on 2009-12-21
Do you have the beige G3 or the blue and white one?

---

### Post by phillw on 2009-12-21
> **tiresia said:**
> Do you have the beige G3 or the blue and white one?

Blue & white.

I've done some digging thru' the archives - but still unsure about how to 'nuke' the OSX partition and keep the 9.x partition.
They're both seen as seperate entities on the mac, so it knows the difference - It's just that it seems any install script cannot decide the difference. I really need a 'dummys guide' to this one.

Phill.

---

### Post by tiresia on 2009-12-22
Your g3 belongs to the so called NewWorld, therefore you don't need BootX to boot the Linux Kernel.
[COLOR="Red"]**MAKE A BACKUP OF ALL YOUR DATA!!!**[/COLOR]

Before doing anything:
[COLOR="Red"]If you want to keep MacOS9 - do you still have a MacOS9 Installer?
[/COLOR]
Download the PPC Desktop Installer (LiveCD) and burn it in MacOSX with the Apple Drive Utility at LOW SPEED.
Boot the burned CD pressing C at bootup. At the first (yaboot) prompt, press TAB. There you will see different options. Choose (writing) linux-nosplash-powerpc, if you have video problems, reboot adding at that line video=ofonly

Be patient, it can take a while. Start the Partition Editor (gparted, you find it in System>Administration) and delete everything is not your MACOS9. If you need help, post here your partition map, BEFORE deleting anthing. You will get free space where you can install Ubuntu.

Start the Ubuntu Installation, choosing to install Ubuntu on the Free Space. After rebooting, Yaboot should give the option to boot in MacOS9 pressing the m-key. If you don't get this option, don't worry, we can edit the yaboot configuration file (/etc/yaboot.conf) so that you will be able to boot in MacOS9.

[COLOR="Red"]**BACKUP YOUR DATA!!!**[/COLOR] Have I said it? :-)

---

### Post by phillw on 2009-12-25
> **tiresia said:**
> Your g3 belongs to the so called NewWorld, therefore you don't need BootX to boot the Linux Kernel.
[COLOR=Red]**MAKE A BACKUP OF ALL YOUR DATA!!!**[/COLOR]

Before doing anything:
[COLOR=Red]If you want to keep MacOS9 - do you still have a MacOS9 Installer?
[/COLOR]
Download the PPC Desktop Installer (LiveCD) and burn it in MacOSX with the Apple Drive Utility at LOW SPEED.
Boot the burned CD pressing C at bootup. At the first (yaboot) prompt, press TAB. There you will see different options. Choose (writing) linux-nosplash-powerpc, if you have video problems, reboot adding at that line video=ofonly

Be patient, it can take a while. Start the Partition Editor (gparted, you find it in System>Administration) and delete everything is not your MACOS9. If you need help, post here your partition map, BEFORE deleting anthing. You will get free space where you can install Ubuntu.

Start the Ubuntu Installation, choosing to install Ubuntu on the Free Space. After rebooting, Yaboot should give the option to boot in MacOS9 pressing the m-key. If you don't get this option, don't worry, we can edit the yaboot configuration file (/etc/yaboot.conf) so that you will be able to boot in MacOS9.

[COLOR=Red]**BACKUP YOUR DATA!!!**[/COLOR] Have I said it? :-)
Thanks very much for the reply, and I apologise for my tardy response. (My sister chose Christmas Eve to get married !!!)

Said Aged Mac does not have a cd-R drive. I have a firewire DVD-CD/RW drive that it can write to, but not sure about writing an iso image (.dmg thinggies :-) ) - would that be okay ? At present I'm using my Ubuntu installation on piglet (my intel based laptop) to burn ppc images to disk - Said Mac does boot off them okay.
I do back the Mac up to a firewire Hard-drive and do have the Mac OS9 install CD - It is in the pack with the OSX re-install along with 4 CDs of software re-install, Apple Hardware Test one and Applications one. (The full set that was shipped with said Mac).

I have the xUbuntu-9.04-alternate-powerpc-iso  Image - Is this the one I should be using, or do I need a different one ?

Once i know which LiveCD to use - I can assure you that I will post what it finds here, before I proceed :-)

Once again, thanks for your help on this one.
/edit -- P.S. would xubuntu have usb2 drivers with it, or would I still be on USB1 - It's no big deal, as I use firewire devices on it, but USB2 would be nice ;-)

Phill.

---

### Post by tiresia on 2009-12-26
(x)Ubuntu 9.04 is fine. If you want, you can try also the latest Karmic, but it has a sort of bug, i.e. the iso image is a bit bigger than 700MB. Either you burn it to a DVD or you try other tricks. For the moment, I would suggest not to make the thing more complicate than it is.

Of course, burn the iso image as 'image' - I mean do not mount it and do not copy just data

You should be able to boot from your fw-cdrom (actually, you should be also able to boot from your fw-HD...). Insert the installer and boot pressing the opt-key. Open Firmware will show you a cd image with a pinguin if it is able to read and boot. Choose it using the mouse.

About USB: no problem with USB 2 - as long as it is an USB 2...

---

### Post by phillw on 2009-12-26
Hueston, we have a problem ....

> Boot the burned CD pressing C at bootup. At the first (yaboot) prompt, press TAB. There you will see different options. Choose (writing) linux-nosplash-powerpc, if you have video problems, reboot adding at that line video=ofonlyI have ....```

install
expert-powerpc
oem
cli
cli-expert-powerpc
ltsp-server
check
rescue
install-powerpc
install-powerpc64
oem-powerpc
cli-powerpc
cli-powerpc64
ltsp-server-powerpc
check-powerpc
rescue-powerpc
expert
expert-powerpc64
oem-powerpc64
cli-expert
cli-expert-powerpc64
ltsp-server-powerpc64
check-powerpc64
rescue-powerpc64
```(They're in 3 banks)

So, I have 
```
boot:
```Which one do I choose, or have I got the wrong disk ?

Thanks,

Phill.

---

### Post by avtolle on 2009-12-26
You have the correct disk. At boot: you could just hit <Return>, which will select the default (install). Good luck.

EDIT: Just wanted to add that the line after boot: should,  imo, read "install video=ofonly" (without the quote marks, of course).HTH.

---

### Post by phillw on 2009-12-26
> **tiresia said:**
> 
Be patient, it can take a while. Start the Partition Editor (gparted, you find it in System>Administration) and delete everything is not your MACOS9. If you need help, post here your partition map, BEFORE deleting anthing. You will get free space where you can install Ubuntu.

 
Posting :)
```

IDE1 master (hda) - 20.5GB MAXTOR 4K020H1
#1  32.3 kB        Apple
#2  28.7 kB        Macintosh
#3  28.7 kB        Macintosh
#4  28.7 kB        Macintosh
#5  28.7 kB        Macintosh
#6 262.1 kB        Macintosh
#7 262.1 kB        Macintosh
#8 262.1 kB        Patch Partit
     134.2 MB FREE SPACE
#10  9.4 GB  hfs+   Apple_HFS_Un
     134.2MB  FREE SPACE
#12  9.4 GB  hfs+   Apple_HFS_Un
     1.4 GB   FREE SPACE

```

What can I say ??? ---  YIKES!!! seems a good one !!

I hope that makes sense to you good people, Heck, it's gr8 being a n00b again ;-)

Phill.

---

### Post by tiresia on 2009-12-26
As I said you can delete everything is not MacOS9 - since you told that you want to keep only MacOS9. But reading the Partition Map you posted, I can only say that MacOS9 is either on #10 or #12. You should check it booting in MacOSX and having a look starting the Apple Disk Utility.

But I see there something that I would try to avoid. Of course your HD was partitioned with the Apple Disk Utility, and it is quite usual that it leave some free, unused space between partitions (none knows why). But on your hd, there is also more than 1GB free space at the end - which is quite a lot considering that your HD has only 20GB.

Therefore I would consider to erase the HD, and to install again MacOS9 after making two partitions with the Apple Utility. Install MacOS9 on the second partition. I don't know, what you want to do in MacOS9, but it could be enough just 1-2GB (the system needs less than 500MB). 

Before doing anything BACKUP EVERYTHING, and maybe let us know what you want to do with MacOS9. If you want to exchange files between the two OS's could be also a good idea to make a sharing partition (linux can read HFS+ and can also write *not* journaled HFS+ but MacOS is not able to read/write ext2/ext...)

---

### Post by phillw on 2009-12-26
> **tiresia said:**
> As I said you can delete everything is not MacOS9 - since you told that you want to keep only MacOS9. But reading the Partition Map you posted, I can only say that MacOS9 is either on #10 or #12. You should check it booting in MacOSX and having a look starting the Apple Disk Utility.

But I see there something that I would try to avoid. Of course your HD was partitioned with the Apple Disk Utility, and it is quite usual that it leave some free, unused space between partitions (none knows why). But on your hd, there is also more than 1GB free space at the end - which is quite a lot considering that your HD has only 20GB.

Therefore I would consider to erase the HD, and to install again MacOS9 after making two partitions with the Apple Utility. Install MacOS9 on the second partition. I don't know, what you want to do in MacOS9, but it could be enough just 1-2GB (the system needs less than 500MB). 

Before doing anything BACKUP EVERYTHING, and maybe let us know what you want to do with MacOS9. If you want to exchange files between the two OS's could be also a good idea to make a sharing partition (linux can read HFS+ and can also write *not* journaled HFS+ but MacOS is not able to read/write ext2/ext...)


I booted into OSX and just copied and pasted the 9.2 partition onto the external drive --- yeah, so it's a sloppy way to a backup - lol

There is nothing in OSX that I need.

The accounts system is only carbon, so it's 9.2 or nothing. I can certainly do a complete wipe of the machine - It's had them in the past.

9.2 would want about 5GB for the dbase, but as the xubuntu area is only for web-browsing, SAFELY with https stuff I'm pretty easy on a 50:50 split, as it allows me to use 1/2 the disk to backup the other 1/2 & still retain the external hard-drive along with USB memory-stick backups of the accounts stuff. (Okay - so I like backups... When it is dealing with folding money & what companies owe & your Mum is a book-keeper, you get used to this sort of thing !!)

So, if I get this right,
 I need to boot with the OSX-asennus disk, 
wipe the system completely, 
make a 5GB mac partition, leaving the rest of it unallocated, 
put OS9 onto the partition
Boot & see that OS9 is alive
boot to xubuntu CD & put it on the remainder.
Boot and see if i get a choice of both systems ?


Again, thanks,
Phill.

---

### Post by tiresia on 2009-12-27
> **phillw said:**
> 
9.2 would want about 5GB for the dbase, but as the xubuntu area is only for web-browsing

Please, note that on ppc there is no Adobe Flash plugin, and the open source substitutes do not always work... You can still watch YouTube with other tools

>   
So, if I get this right,
 I need to boot with the OSX-asennus disk, 
wipe the system completely, 
make a 5GB mac partition, leaving the rest of it unallocated, 
put OS9 onto the partition
Boot & see that OS9 is alive
boot to xubuntu CD & put it on the remainder.
Boot and see if i get a choice of both systems ?

Yes, but before installing Xubuntu, please post your partition map here. Because you need to make a manual partition, otherwise you will end up with two partitions for the Partition Map.
Are you using the Desktop CD or the alternate-CD?

---

### Post by phillw on 2009-12-28
> linux can read HFS+ and can also write *not* journaled HFS+As said Mac doesn't do too much work - what is the performance hit by turning journalling off ? I believe (and correct me if I'm wrong) that linux can then read & write to a HFS+ area with journalling turned off
I think I'll do my usual cowards way & make a FAT32 area, though ;-)

Also, is that correct - for me to put OS9 on the last partition ? Or, if I am making a FAT32 parition, would I make it like this ?

#1 - Free (For xubuntu)
#2 - Mac os9
#3 - FAT 32


Where #1 is the lowest number the system gives me :-)

>  Are you using the Desktop CD or the alternate-CD?I have the xUbuntu-9.04-alternate-powerpc-iso  Image - Is this the one I should be using, or do I need a different one ?

Thanks,

Phill.
P.S. As i'll be on 'hold' once I've don'e the initial partitioning & posting here, with the Mac unusable - Would you let me know when you're likely to be on-line, thanks !!

---

### Post by phillw on 2009-12-29
Well, in the absence of any further advice on re-posting my altered partition table ....

1) Back up os9 & macosx

2) Boot with os9 cd -- Disk utilities - divide into 3 partitions @ 6.8GB each told it 1 hfs - install os9, 2 unused.
3) Boot with xubuntu cd - manually allocate 1 partition to fat32 - to mount as /dos
4) set other partition to free space (delete)
5) Auto install xubuntu on largest available free space.

I still have the multitude little partitions, but have 3 main partitions, each 6.8GB in size (My maths = 20.4 GB - which is pretty darn kewl & using that 1.4GB bit that was unused previously)
the ubuntu 6.8GB gave 1GB to boot, about 5.4GB to xubuntu and about 400MB to swap - Heck, that's how it wanted to slice it up, who am I to argue ?  

Phill.

---

### Post by phillw on 2009-12-29
:cry:

Put xubuntu on. It told me it was ejecting the CD then re-booting.

When it did i get a choice of l - linux or c -cdrom -- I chose **l** as the cdrom has been ejected (seemed like a decent choice).

lt blinks, then has a look round and returns me to the **boot:** prompt.
typing help, gives some info about where things are & that <tab> wil give me a list of boot areas

<tab>'ing from there i have **old** or **Linux** Niether work, the computer just shuts down.

I don't get any option to boot into 9.2, which was working fine before the installation ....

So, ... in one word ....

HELP !!  :confused:

Phill.

---

### Post by tiresia on 2009-12-29
> **phillw said:**
> Well, in the absence of any further advice on re-posting my altered partition table ....

Sorry, I was not at home these days and I had no internet connection...
What do you get, if you press the Opt-Key at boot up?

---

### Post by phillw on 2009-12-29
Alt key gives me macos9, or the penguin.

selecting macos9 then pressing ==> gives the disk with the flashing question mark in it (not good)

selecting the penguin, then ==> 
gives the message i reported above, if no input it shuts down - if i select l then i get the boot: message.

Firewire drive, that used to be able to boot is no longer seen as an option, even when i press the 'circly' refresh button.

So... Helps, hints, tips etc.... please... begs..... don't want to give up now :-(

Regards,

Phill.

---

### Post by tiresia on 2009-12-29
After you installed MacOS9 could you boot it?

---

### Post by phillw on 2009-12-29
> **tiresia said:**
> After you installed MacOS9 could you boot it?

yup - it was fine.

Made sure of that before i touched the two unallocated areas -- i did it like i posted above.

-- bit stuck, don't know where i went wrong :-(

Phill.

---

### Post by tiresia on 2009-12-29
We can easily fix the Xubuntu partitions (it looks like Xubuntu cannot find the root partition). But it is strange that you cannot boot in MacOS9 after pressing the Opt-Key. Did you erase any of those small partitions you mentioned (they hold drivers for MacOS9)?
And another question before getting to bed (here in Berlin is 3:30): you wrote that after the guided partitioning you have 1 GB boot??? It is right? Because it is not correct

---

### Post by phillw on 2009-12-29
There is no data on the mac at present, so if you can think of a different way to do the install from a mac os9 disk, I'm all ears - like i said - i got back all the unallocated area, but kept those daft little partitions at the start. I'm not sure if I need instructions as to how to get rid of them, but i still start at about #9, or #10 with os9, then fat32 as /dos., then xubuntu made /boot, xubuntu area and swap.

But, i let it install into 'free disk space' i dunno if that was right. I did try making swap manually and then an ext3 area - but it said i hadn't made a boot area - which is what has probably knocked out the os9 boot thinggie.

Mebbie i should put xubuntu on 1st, then add fat32 & macos9 - i simply don't know.

Phill.

---

### Post by tiresia on 2009-12-29
If you want an easy solution:
1. Make three partitions with the Apple Disk Utility
[INDENT]#1 Free
#2 HFS+
#3 HFS+[/INDENT]
2. Install MacOS9 on the third
3. Check that MacOS9 is bootable
4. Start from the Xubuntu Installer and choose the guided partitioning (it will create four partitions: one for the Apple Partition Map, one for the Bootloader, one for Xubuntu and one as swap area)


Don't worry if after that you can't boot from the yaboot prompt in MacOS9 - we'll fix it later. But you must be able to boot MacOS9 pressing the Opt-Key at boot up.

If you want FAT32 on the Second Partition, you can format it later.

---

### Post by phillw on 2009-12-29
> **tiresia said:**
> If you want an easy solution:
1. Make three partitions with the Apple Disk Utility[INDENT]#1 Free
#2 HFS+
#3 HFS+[/INDENT]2. Install MacOS9 on the third
3. Check that MacOS9 is bootable
4. Start from the Xubuntu Installer and choose the guided partitioning (it will create four partitions: one for the Apple Partition Map, one for the Bootloader, one for Xubuntu and one as swap area)


Don't worry if after that you can't boot from the yaboot prompt in MacOS9 - we'll fix it later. But you must be able to boot MacOS9 pressing the Opt-Key at boot up.

If you want FAT32 on the Second Partition, you can format it later.


okies - does it matter that I'll still have #1 ~ #9 with those silly little areas like before ?

Or should i try using the osx assensus disk for it ?

Phill.

---

### Post by tiresia on 2009-12-30
> **phillw said:**
> okies - does it matter that I'll still have #1 ~ #9 with those silly little areas like before ?

Or should i try using the osx assensus disk for it ?

You NEED those small partitions! So, please, do not delete them. I wrote just #1 Free... because in the Apple Disk Utility those small partitions are hidden.

---

### Post by phillw on 2009-12-30
Hi - I have the choice of **Mac OS Standard** or **Mac OS Extended** - which do I use ?

There are other choices, if you want the full list .

Thanks,

Phill.

---

### Post by oswaldkelso on 2009-12-30
Standard if it's hfs so you can read and write form the GNU/Linux side.  (non journalled) This is faster so good for a low end machine 

If you don't need that you can use the extended hfsplus or hfs+ (journalled) This is safer but slower. I can't remember for sure if it's called  hfsplus or hfs+. I think it's the former.

I would google a bit as I've not run either OS9 or OSX for a while.

edit. This is for creating your OS9 partition

---

### Post by phillw on 2009-12-30
Thanks, I do recall reading about ubuntu being able to read & write if journalling was turned off - And did ask what the performance hit would be to have it turned off. Looks like it may be a boost :-)

#1 Unallocated (7.5 GB)
#2 Mac Standard (HFS) - Empty (5 GB)
#3 Mac Standard (HFS) - Mac OS9 (6.5 GB)

Just putting OS9 onto #3 .. Then check it boots - then to pop xubuntu onto #1
I've given #1 an extra GB, as it uses 1GB for / and about 500 MB for swap.

Regards,

Phill.

---

### Post by oswaldkelso on 2009-12-30
It's normal to put mac OS on the first partition (OSX) anyway. From memory if it's not there it may not boot!

---

### Post by phillw on 2009-12-30
He he - Tried that last night !! - It failed.

So, I'm doing as I'm told this time :)

:lolflag:  (**Before** someone says "That'll be a first"

Phill

---

### Post by tiresia on 2009-12-30
> **oswaldkelso said:**
> It's normal to put mac OS on the first partition (OSX) anyway. From memory if it's not there it may not boot!
Hey Oswald, that's not thrue!!!
And Linux can read and write HFS/HFS+ [i.e. HFS/HFS extended]
Linux can't write on HFS+ Journaled
For MacOS9 is advisable to use HFS+ [i.e. HFS extended]

[Btw, I like your blog :)]

---

### Post by phillw on 2009-12-30
Grrrrr.... I've now got OS9 booting happily on the 3rd partition - but as HFS (Or whatever MAC Standard is) - Do I need to re-do it to Mac Extended ?

I'd rather do it now, [b]before[/] I try putting xubuntu onto the 1st partition.

Whichever way, Do I tell it use Unallocated space and "get on with it" ?

:confused:

Phill.

---

### Post by tiresia on 2009-12-30
Well, it should not take so much time, to reinstall MacOS9 (I guess not more than 20min). HFS (Standard) was the old Apple File System, and was replaced by HFS+ (also called HFS Extended or HFS Plus), if I remember well with the MacOS8 (but here doesn't matter) MacOSX requires HFS+ Journaled

For Xubuntu, yes, after installing MacOS9 and checking it, install Xubuntu just following the guided partition. Before formatting and installing, the Installer will ask you to confirm if you want to proceed. I'm online for the next two/three hours, you can contact us again, if you like

---

### Post by phillw on 2009-12-30
> **tiresia said:**
> Well, it should not take so much time, to reinstall MacOS9 (I guess not more than 20min). HFS (Standard) was the old Apple File System, and was replaced by HFS+ (also called HFS Extended or HFS Plus), if I remember well with the MacOS8 (but here doesn't matter) MacOSX requires HFS+ Journaled

For Xubuntu, yes, after installing MacOS9 and checking it, install Xubuntu just following the guided partition. Before formatting and installing, the Installer will ask you to confirm if you want to proceed. I'm online for the next two/three hours, you can contact us again, if you like


Okies - I'll go reformat #2 & #3 as Mac Extended & pop MacOS9 back on. I won't be using MacOSX on this rig.

Phill.

---

### Post by phillw on 2009-12-30
:cry:

Same as last night.

MacOS9 was booting happilly

Put in the xubuntu CD & booted.

In partitioning, i had to delete that 1st partition, and then used guided partitioning to install into largest unused area - all seemed fine.

#9  1MB  B       k  Boot
#12 8GB          f   ext3  /
#13 412.8MB     f    swap   swap
#10 5.2GB       hfs+  untitled2   (To Be DOS)
#11 6.8GB       hfs+  untitled3   (MacOS9)

Holding down the opt key - shows me Mac & penguin

Selecting Mac - gives diskette with **?** in it
Selecting Penguin - starts to boot okay, choose l for Linux - goes to boot: for a couple of seconds, tries to boot, then turns off.

I'm probably missing something really simple here, just not used to how it boots with xubuntu on it.

Phill.

---

### Post by tiresia on 2009-12-30
It would be useful to know what you see *before* you delete anything when you install Xubuntu. You say> In partitioning, i had to delete that 1st partition do you remember the number 'the Linux way' of the partition you deleted. Was it /dev/hda9? Do you have any small free space?

---

### Post by phillw on 2009-12-30
The partition was there - but, despite my saying 'unallocated' (or whatever the bottom option was in disk-tools) it was not 'free-space'.
There was & is a little partition left over after #14 of a few kB

It was #9. That is why, me figures, that it goes 
#9 Boot
Then back to..
#10 - hfs+
#12 - hfs+
with 
#13 and #14 being tagged on at the end. They were not there before I used guided partitioning after deleteing #9 to free-space & then using the "Use largest available Free Space" option of the install.

#9 *had* about 9.5GB size.

Hope that helps.

/edit > And another question before getting to bed (here in Berlin is 3:30): you wrote that after the guided partitioning you have 1 GB boot??? It is right? Because it is not correct   No,it should have read 1MB

Phill.

---

### Post by tiresia on 2009-12-30
Ok, it looks like you have```

/dev/hda9 unallocated space
/dev/hda10 Apple_HFS untitled
/dev/hda11 FreeSpace (very small)
/dev/hda12 Apple_HFS untitled 2
```
The Installer, after you delete /dev/hda9, creates```

/dev/hda9 Apple_Bootstrap bootstrap (800.0k) [where yaboot is located]
/dev/hda13  Apple_UNIX_SVR2 / [the Linux partition]
/dev/hda14 swap [swap area]
```

Actually it looks ok. But you should take care that /dev/hda1 is correctly detected as Apple_Partition_Map **It looks like that the Installer makes problems with the Partition Map**. Otherwise I can't explain why also MacOS9 is unbootable. It would be also interesting to see the whole list (you should have also /dev/hda2 Apple_Driver43 Macintosh, /dev/hda3 Apple_Driver43 Macintosh, /dev/hdb4 Apple_Driver_IOKit Macintosh&#8230;)

I would suggest therefore to try with another Installer (Debian Lenny or Xubuntu 8.10), or to follow again together the installation with Xubuntu 9.04, or to partition manual 

Before trying anything, could you please tell me what happens if you reset PRAM and NVRAM (restart the computer and press and hold the Command-Option-P-R keys). Can you now boot MacOS9 after pressing the Opt-Key?

---

### Post by oswaldkelso on 2009-12-30
> **tiresia said:**
> Hey Oswald, that's not thrue!!!
And Linux can read and write HFS/HFS+ [i.e. HFS/HFS extended]
Linux can't write on HFS+ Journaled
For MacOS9 is advisable to use HFS+ [i.e. HFS extended]

[Btw, I like your blog :)]


Thank you for correcting me. (and everyone else :D )
Glad you liked my blog. Though to be honest I just use it as an odds an sods on line store. 

I'm afraid the freedom and stability of Debian has won me over :P Still, I pop in here every now and then to dig through the archives. (hint for PPC newbies) Just to refresh my memory, even though I've not really needed to run slave-ware (OSX) for over a year now. 

Back on topic. I'll watch the thread and sober up before my next post. :D

---

### Post by phillw on 2010-01-04
Hi, as promised (belatedly)

No, resetting the PRAM had no effect :-(

Partition table after xubuntu was installed :

#1   32.3 k                                    Apple
#2   27.6 k                                    Macintosh
#3   37.9 k                                         " 
#4   27.6 k                                         "
#5   37.9 k                                         "
#6  102.4 k                                         "
#7  262.1 k                                        "
#8  262.1 k                                   Patch Parfit
#9     1.0 M     B   k    boot              untitled
#12    8.0 G               ext3                  "             
#13 412.8 M               swap             swap        swap
#10    5.2 G               hfs+             untitled 2
#11    6.8 G               hfs+             untitled 3
         11.3 kB            FREE SPACE

Where Mac OS9 was installed on untitled 3
and #9  was about 8.5 Gb. I used the xubuntu to 'delete' #9 and make it 'free space' then told it to use largest free space. Hence #12 & #13 not running in order !!

I've had to re-format back to three partitions - all hfs+  to put Mac 9.2 back on as it is needed for work.

When it's sorta figured out - I'd be delighted to have another go !!

:popcorn:

Thanks everyone !!

Phill.

---

### Post by idratheruseamac on 2010-02-20
I've read and followed all of this thread, and reached exactly the same point. It doesn't work.  It seems abundantly clear that the bundled partition editor 'gparted' destroys the MacOS 9 partition table, making it impossible to retain any working MacOS 9 systems if you use it.   Apart from that, there are a few fundamentals that are critical: The MacOS 9 disc driver patches must be retained. These are those small partitions at the start of the disc. There are four or more depending on which version of MacOS was used to initialize the disc, and whether it has been udgraded by successive intallations. The MacOS 9 boot partition must be retained {I think this contains the boot loader called by Open Firmware to load the bootfile specified in boot-device} The bootable MacOS 9 system partition must begin before the 8 gigabyte boundary on the disc. The bootable partition for the linux installation must also begin before the 8 gigabyte boundary.  I'm now reading up on mac-fdisk to try and build a disc ready to receive the MacOS 9 system into pre-configured partitions.  Then I've got to work out how to install ubuntu without using the installer.

---

### Post by phillw on 2010-02-20
> **idratheruseamac said:**
> I've read and followed all of this thread, and reached exactly the same point. It doesn't work.

Hi, and welcome to the forums - I'd have loved to have gotten a resolution on this one, but time was against me. I'm sure it **can** be done, just with it being a time window of Christmas & New Year before I had to put said Mac back into service, I ran out of time.

As you can tell, I do keep a notification on this thread hoping for a solution. The contributers who were helping me are pretty 'clued up' on xubuntu & Macs - If you do have the time scale - please liase with them & get a working solution.

Regards,

Phill.

---

### Post by tiresia on 2010-02-21
> **idratheruseamac said:**
> It seems abundantly clear that the bundled partition editor 'gparted' destroys the MacOS 9 partition table, making it impossible to retain any working MacOS 9 systems if you use it.

Well the partition editor in the (Debian) is 'partman' - anyway I think you are right, but I can't check it right now. The last time I installed Linux together with MacOS9 was on a PowerMac G4 and I didn't have any problems. I installed Xubuntu 9.04 or 8.10, I'm sure anymore. Therefore in the last post I suggested to use another Installer, it can be that the last version is buggy from this point of view
My impression is that the Installer (partman) overwrites the Apple_Partition_Map.
> I'm now reading up on mac-fdisk to try and build a disc ready to receive the MacOS 9 system into pre-configured partitions.  Then I've got to work out how to install ubuntu without using the installer.
I'm not sure that I understand what you want to do. But you don't need mac-fdisk to prepare an installation of MacOS9.
I would say you have three possible solutions 
1. Installing another (older) version (Ubuntu or Debian) after MacOS9
2. Making a manual partitioning and formatting (mac-fdisk and mkfs)
3. Installing MacOS9 after Linux - you need to reconfigure and to reinstall yaboot, but it is quite simple.

---

### Post by idratheruseamac on 2010-02-23
Installing MacOS9 after Linux is not that simple. Firstly, the Mac won't recognise the disc unless it has the intact driver and patch partitions, and these are not intact after using the installer. I've just tried doing it the Apple way, (i.e. let the Mac do it for you) by electing to partition the disc using Disc Setup according to a pre-defined Linux-PPC arrangement:  /dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map /dev/hda2        Apple_Driver_ATA Macintosh                 54 @ 64        ( 27.0k)  Unknown /dev/hda3        Apple_Driver_ATA Macintosh                 74 @ 118       ( 37.0k)  Unknown /dev/hda4      Apple_Driver_IOKit Macintosh                512 @ 192       (256.0k)  Unknown /dev/hda5           Apple_Patches Patch Partition          512 @ 704       (256.0k)  Unknown /dev/hda6               Apple_HFS MacOS/Preferred LinuxPPC  15558347 @ 1216      (  7.4G)  HFS /dev/hda7         Apple_UNIX_SVR2 A/UX Root           23337520 @ 15559563  ( 11.1G)  Linux native /dev/hda8         Apple_UNIX_SVR2 Swap                  102400 @ 38897083  ( 50.0M)  Linux swap /dev/hda9         Apple_UNIX_SVR2 Usr file system     23337520 @ 38999483  ( 11.1G)  Linux native /dev/hda10        Apple_UNIX_SVR2 Opt file system       614400 @ 62337003  (300.0M)  Linux native /dev/hda11        Apple_UNIX_SVR2 Home file system    93350083 @ 62951403  ( 44.5G)  Linux native /dev/hda12             Apple_Free Extra                      2 @ 156301486 (  1.0k)  Free space  This arrangement allows you to install MacOS9 in the shared partition in /dev/hda6  I now need to work out how to install Ubuntu on to this disc without knackering the OS9 system. If I put the linux loader in the shared partition, and set another environment variable in Open Firmware to load it by typing boot linux at the OF prompt, that should involve minimum disruption. A more capable person might be able to reprogram OF to accept the 'l' key as a shortcut while starting. But how can I get the installation into place without using the installer or the partition editor.?

---

### Post by linuxopjemac on 2010-02-23
you also need a bootloader partition. To my opinion it should be in the beginning right after the Apple drivers section, see my scheme (I don't have OS) though):

[http://ubuntuforums.org/showthread.php?t=1389625&page=2](http://ubuntuforums.org/showthread.php?t=1389625&page=2) (post #13)

---

### Post by sword_king on 2010-02-23
Funny how y'all are having problems with your partitions. That is one issue that has never come up before for me, and I've done quite a few installations of Ubuntu, Xubuntu, Kubuntu, Mandriva and YDL, the latest being Xubuntu 9.10 on a iMac g3 600.  I usually use a Mac boot CD to partition the disk (total loss) but this time (and the reason I found this thread) I used the partition editor during installation to shrink a Mac partition towards the end to install Linux towards the start of the drive. The automatic partitioner should have made a 1mb boot partition first (after all the driver, etc. partitions), followed by the root partition, the swap partition, and finally the HFS+ partition. Theoretically, if I zap the PRAM, yaboot should become the bootloader, no matter what I've been doing with the start-up control panel or preferences, but it's not working the way I want or expected and I can't choose which MacOS to boot.

So it's back to the old way for me.  Backup documents, boot with OS9 CD, create 3 partitions of the sizes I want (20G for Linux, 18 for OSX, & 2G for OS9 for the apps that don't work under Classic), install OS9, check that it boots properly and make sure the time and date are correct, install Xubuntu telling the partitioner to use the first partition, which it'll separate similar to what I described above, then install OSX, and last of all, boot into Xubuntu and fix yaboot.conf and run ybin.

That way I can boot to OS9 when I want, and still use it as Classic in OSX if need be, and if somehow someone changes the Start-Up Preferences, I can still get it back. I'll be doing that today, with the 'new' partitioner included with Xubuntu, and let y'all know how it works out.

SK

---

### Post by sword_king on 2010-02-25
I had some troubles backing up files to a USB hard disk, but otherwise the re-partitioning and re-installations went as planned.  I had to restart the installation of Xubuntu after changing the partitions, because the installer refused to continue.  That was the only issue I haven't had in the past.  It didn't mess with the Apple, Macintosh, or patch partitions.

Unlike previous versions, Xubuntu 9.10 actually starts up in 800x600x256 colors, which is usable but slow and cumbersome, and it takes some fiddling with xorg.conf to get it to millions (24 bit). I'm still not satisfied I have it right, but it's working snappily at 1024x768xmillions.

Yaboot didn't recognize OS9.  That was the first time I've had that happen, but it's no biggie, because I had to go in and edit yaboot.conf for OSX anyway.

So far, so good.

---

### Post by phillw on 2010-02-25
That is well good news :p

I've currently got the mac set up with 3 partitons - all done by the Mac.

One has 9.2, one has OSX 10.1.5 and one is empty.

Obviously all the 'mac' bits are there. If you could write up how you got it all running I'd be mightily obliged.

Regards,

Phill.

---

### Post by sword_king on 2010-02-28
Feb. 28, 2010

I've been experimenting and messed Xubuntu up so bad it wouldn't get past the login screen, so I'm composing this on another 'puter while just now re-installing on this iMac g3 600 (YMMV on anything else).

Using Karmic Xubuntu 9.10 Alternate CD:

<tab> at very first prompt brings up various alternatives.  I used:

install-powerpc video=aty128fb:vmode:17 [from YDL instructions -- 'video=ofonly' didn't cut it on this particular machine].

From there, it's pretty much self-explanatory. I chose a macintosh keyboard, cuz that's what I'm using (can be changed at GDM login screen if it doesn't work right), & I'm hardwired to my router, so the installer picks that up.  Remember, last week, using my OS9 install CD, I had already made 3 partitions: I left the first large partition blank (unformatted) for Linux, then a large HFS+ partition for OSX, and a smaller partition (2G) for OS9. I installed OS9, then Xubuntu, then OSX, and then fixed yaboot.conf to show OS9.  This time I already had OS9 and OSX in other partitions, so it takes just a little finagling with yaboot.conf to get them both to show up in the bootloader after Xubuntu is installed.  This time I just chose to use the previous Linux partition for / and everything worked out. The swap and boot partitions were still there and recognized. (Now off to work on a woodstove....)

Upon reboot, it comes to a 256 color login screen, so I logged in, opened Synaptic and set its preferences and repositories the way I like.  While it updated Quick Search, I pressed <alt>F2, typed:

gksudo mousepad /etc/X11/xorg.conf

in the dialog box, which opens a blank xorg.conf.  I started Firefox, found the xorg.conf text I want from the forums (see mine below), copy and paste, edited as wanted, saved and checked back w/ Synaptic, which was ready.  I typed "ati" into the Quick Search box and chose to install xserver-xorg-video-ati-dbg based on the advice here <http://ubuntuforums.org/showthread.php?t=1215154> & logged out. [I don't know if this is actually necessary.]

That brought me to a terminal (tty1) where I logged in, then updated (sudo aptitude update, etc., or use apt-get, if you prefer).  (I'd rather that all happens in the background while I'm fiddling with X and yaboot.conf, than to wait for X to start and do it from there and have to wait even longer til it finishes before restarting X (if I need to), but it can all be done from Synaptic or Update Manager if you want. I'd rather use the multi-tasking capabilities of Linux -- learned from CalderaLinux, BTW)  <alt>F2 starts a new terminal, where I typed "startx" and get back to a GUI login screen and X. My xorg.conf (the one that is working right now with 1024x768 resolution w/ 24 bit color) looks like this:

Section "Device"
     Identifier     "Configured Video Device"
     Option     "CCEusecTimeout"     "100000"
EndSection

Section "Monitor"
     Identifier     "Configured Monitor"
     HorizSync     58-62
     VertRefresh     75-117
EndSection

Section "Screen"
     Identifier     "Default Screen"
     Monitor     "Configured Monitor"
     Device     "Configured Video Device"
     DefaultDepth     24
     SubSection     "Display"
          Depth     24
          Modes     "1024x768"
     EndSubSection
EndSection

I used <tab> on the actual file, but the Forum doesn't show it, so it won't copy-and-paste quite right.  I'm not a great typist or proof-reader, so there may be typos, etc. (even tho' I went over it 3 times), but you can figure that out and I can edit this post if you tell me, so others who google it will maybe get it right the first time. :)

Then I had to reboot with my OS9 CD, choose Utilities/Drive Setup, click <not mounted>, choose Update Driver from the Functions menu and, when it completes, reboot to Linux.  Once back in X, start a terminal (Menu/Accessories/Terminal) and type:

'gksudo mousepad /etc/yaboot.conf' 

in the dialog box.  Edit it as posted a thousand time here in the forums to get the OS9 boot option to show up, then type 'sudo ybin -v' in the terminal, and watch as your boot partition gets blessed with 'Holy Penguin Pee'. :)

This has literally taken HOURS to install, type, format and correct.  I hope it works for you. I'm going to go have a cocktail.

SK

ps the cool thing is I just picked up a carbon copy of this machine at a thrift store yesterday, and I'm planning on doing the same to it, so I'll give myself a critical review... It may take a few days, cuz life gets in the way.

"Take my advice, don't listen to me..." -- Neil Young, "Hippie Dream"

pps. I edited this from within the installation I just wrote about, using Opera Browser.  Internet obviously working.  Sleep doesn't work, I had to reboot after letting this sleep while using the other computer to finish this post, and sound isn't working yet either.

---

### Post by Airamith on 2011-03-16
I know this this is going to make me look stupid, but I have to ask. I've never touched a mac before, never even wanted one. But I rented a storage shed and when I opened it there were 8 iMac G3's in it, all working with OS9 on them. I'm not interested in an apple OS, I just want to totally get rid of it and install xubuntu. Am I understanding it right when I come to the conclusion that what I want isn't possible? Do I HAVE to go through all the crud that you guys are going through in order to make this work? If so, can I just put a small hdd for windows in it and be done? Also, should I be making my own thread for these questions. They're completely related to this subject.

---

### Post by snafu006 on 2011-03-16
> **Airamith said:**
> I know this this is going to make me look stupid, but I have to ask. I've never touched a mac before, never even wanted one. But I rented a storage shed and when I opened it there were 8 iMac G3's in it, all working with OS9 on them. I'm not interested in an apple OS, I just want to totally get rid of it and install xubuntu. Am I understanding it right when I come to the conclusion that what I want isn't possible? Do I HAVE to go through all the crud that you guys are going through in order to make this work? If so, can I just put a small hdd for windows in it and be done? Also, should I be making my own thread for these questions. They're completely related to this subject.


No imac G3 are really ez to get ubuntu xubuntu running on them start a new post and we or i will help you

---

### Post by sword_king on 2011-05-08
Ha! you resurrected an old thread!

This thread is more about how to get OS9, OSX, and *ubuntu working together, than just installing *ubuntu on an imac. I related how I was able to get Xubuntu working on a g3 600mhz imac and probably gave more info than needed, but the xorg.conf file is the smallest I've seen, so if you have to type one in nano, it might be the one to try.

I came back here today to recover my xorg.conf, cuz I was in the process of updating to Lucid on one imac and installing Xubuntu Natty on another, and somehow I got messed up. I read your other thread, too, and the only thing I can say is, you will be better off having a small OS9 installation just to work out video issues, cuz these CRT imacs are just plain weird, and need the mac OS (geometry in the monitor control panel) to take advantage of all the screen real estate. I should probably post that in your other thread, too.

Natty works OK, but reaction time is as bad as OSX Panther. I'll switch over to Debian, or MintPPC if it bothers me too much.

---

