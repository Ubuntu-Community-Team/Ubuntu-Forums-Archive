---
title: "[PPC] How to make a Live CD a Live USB stick"
date: 2008-05-03
forum: Apple Hardware Users
---

### Post by Skeeve42 on 2008-05-03
Boot Ubuntu Live CD from a USB Stick

I needed 4 days, but the solutiion is quite simple...

Here are the instructions, step by step.

But before that let me tell you that I'm German and so my english might be not as good as it could be. I also will drop some hints for the German readers, mostly because of our different keyboard layout. This is a free translation of my german instructions posted on [apfeltalk.de](http://www.apfeltalk.de/forum/tut-ubuntu-live-t144587-p1387002.html#post1387002).

Information sources used
[LIST=1]
[*][Where to download Ubuntu for PowerPC and other frequently asked questions](http://ubuntuforums.org/showthread.php?t=427714)
[*][Instructions on help.ubuntu.com](https://help.ubuntu.com/6.10/ubuntu/installation-guid/powerpc/boot-usb-files.html)
[*][Wie man mit Yaboot auf PowerPC bootet](http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/index.de.shtml) (German)
[/LIST]

[SIZE="5"]Step 1: Get the data[/SIZE]

Fetch an ISO image for a Live CD [[1]]("http://ubuntuforums.org/showthread.php?t=427714"). Burn a CD(-RW) using the OS X Disk Utility.

You should format the USB Stick with a Name you can recognize.


[SIZE="5"]Step 2: Boote the Live CD[/SIZE]

UInsert the CD einlegen and reboot. At the Bootup sound press C to boot from CD.

A bit later the "boot: " Prompt will appear. I had to enter

[FONT="Fixedsys"]live video=ofonly[/FONT]

in ordre to boot. My advise is to use

[FONT="Fixedsys"]live-nosplash video=ofonly[/FONT]

**Hint:** The keyboard is set to US layout. German users will have to press the keys "liveßnosplash video´ofonlz".

[SIZE="5"]Step 3: Creating the bootstrap-partition[/SIZE]

Wenn Ubuntu is up, open the Terminal.

Now try to find the device name your USB stick currently has. So connect the USB stick now, if not already done.

[FONT="Fixedsys"]df[/FONT]
```

Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                   775652       268    775384   1% /lib/modules/2.6.24-16-powerpc/volatile
tmpfs                   775652       268    775384   1% /lib/modules/2.6.24-16-powerpc/volatile
varrun                  775652        96    775556   1% /var/run
varlock                 775652         0    775652   0% /var/lock
udev                    775652       120    775532   1% /dev
devshm                  775652        12    775640   1% /dev/shm
tmpfs                   775652        16    775636   1% /tmp
/dev/sdc1               990156        12    990144  72% /media/BOOTSTICK

```

Here the device name is /dev/sdc. **Note:** The device name can be different after each boot. /dev/sdc in this instruction is to be replaced with the devicee name of your stick.

Now we have to switch to superuser

[FONT="Fixedsys"]sudo -s
umount /dev/sdc1[/FONT]

Then we start partitioning using "mac-fdisk"

[FONT="Fixedsys"]mac-fdisk /dev/sdc[/FONT]
```

/dev/sdc
Command (? for help):

```
Enter "i" for initialising the partition map.

```

Command (? for help): i
size of 'device' is 1980416 blocks: 
new size of 'device' is 1980416 blocks

```

Review the map by entering "p"

```

Command (? for help): p
/dev/sdc
        #                  type name     length   base  ( size )  system
/dev/sdc1   Apple_partition_map Apple        63 @ 1     ( 31.5k)  Partition map
/dev/sdc2            Apple_Free Extra   1980352 @ 64    (967.0M)  Free space

Block size=512, Number of Blocks=1980416
DeviceType=0x0, DeviceId=0x0

```

Now we crate the bootstrap-partition. Newer versions of mac-fdisk know the command "b" for this. If you have an older one you need to enter "C xxxx 800k bootstrap Apple_Bootstrap". The xxxx is to be replaced with the number of the start block, which is 64 in the map shown above.

```

Command (? for help): b
First block: 64
Command (? for help): p
/dev/sdc
        #                 type name       length   base ( size )  system
/dev/sdc1  Apple_partition_map Apple          63 @ 1    ( 31.5k)  Partition map
/dev/sdc2      Apple_Bootstrap bootstrap    1600 @ 64   (800.0k)  NewWorld bootblock
/dev/sdc3           Apple_Free Extra     1978752 @ 1664 (966.2M)  Free space

Block size=512, Number of Blocks=1980416
DeviceType=0x0, DeviceId=0x0

```

This concludes the creation of the map and we have to write it to the stick.

```

Command (? for help): w
IMPORTANT: You are about to write a changed partition map to disk. 
For any partition you changed the start or size of, writing out 
the map causes all data on that partition to be LOST FOREVER. 
Make sure you have a backup of any data on such partitions you 
want to keep before answering 'yes' to the question below! 

Write partition map? [n/y]: y
The partition map has been saved successfully!

Syncing disks.

Partition map written to disk. If any partitions on this disk 
were still in use by the system (see messages above), you will need 
to reboot in order to utilize the new partition map.

```

You leave mac-fdisk with "q".


[SIZE="5"]Step 4: Filling the bootstrap-partition[/SIZE]

Now you format the bootstrap-partition with hfs

[FONT="Fixedsys"]hformat -l bootstrap /dev/sdc2[/FONT]
```

Volume name is "bootstrap"
Volume was created on Fri May  2 19:04:53 2008
Volume was last modified on Fri May  2 19:30:32 2008
Volume has 799744 bytes free

```

mount it

[FONT="Fixedsys"]hmount /dev/sdc2[/FONT]
```

Volume name is "bootstrap"
Volume was created on Fri May  2 19:04:53 2008
Volume was last modified on Fri May  2 19:30:32 2008
Volume has 799744 bytes free

```

and copy yaboot onto it and set some attributes
.
[FONT="Fixedsys"]hcopy -r /cdrom/install/yaboot :
hattrib -c UNIX -t tbxi :yaboot
hattrib -b :
humount[/FONT]

yaboot needs a configuration file. Fortunately we can use the one from the CD with just a small change

[FONT="Fixedsys"]mount /dev/sdc2 /mnt
cp /cdrom/install/yaboot /mnt[/FONT]

We saw in the partition map that there is a partition 3. We will copy the live CD onto that partition. We have to inform yaboot about the fact that the system resides on partition 3.

[FONT="Fixedsys"]vi /mnt/yaboot.conf[/FONT]

You will find information about yaboot.conf's structure on the internet. For now it's just important thatwe put the partition number near the top of the file. For example in the line directly after "timeout=300". For this, move the cursor into that line and press enter to activate the insert mode of vi. Then type

[FONT="Fixedsys"]partition=3[/FONT]

after that press the escape key to leave the insert mode.

**Note:** Here you can add severeal settings you like the system to always use. For example your locale or your keyboard layout. This example is for a German locale with german keyboard. Also added is the (mandatory?) video=ofonly:

Please type in vi:
```

:1,$ s/ --"/ locale=de_DE bootkbd=de console-setup\/layoutcode=de video=ofonly --"/

```

You might also want to cnhange the "default=live" to "default=live-nosplash".

When done, the changed file need to be saved:

[FONT="Fixedsys"]:wq![/FONT]

Now we can unmount the partition

[FONT="Fixedsys"]umount /dev/sdc2[/FONT]


[SIZE="5"]Step 5: Copy the CD[/SIZE]

First we need to format Partition 3:

[FONT="Fixedsys"]mkfs -t ext3 /dev/sdc3[/FONT]
```

mke2fs 1.40.8 (13-Mar-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
61952 inodes, 247344 blocks
12367 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=255852544
8 block groups
32768 blocks per group, 32768 fragments per group
7744 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376

Writing inode tables: 0/81/82/83/84/85/86/87/8done                            
Creating journal (4096 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 38 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

```

and mount it:

[FONT="Fixedsys"]mount /dev/sdc3 /mnt[/FONT]

To copy the files I usually use this command sequence I'm usin since the last millenium ;-)

[FONT="Fixedsys"](cd /cdrom ; tarcBpf -.) | (cd /mnt ; tar xvBpf -)[/FONT]
```

./
./README.diskdefines
./.disk/
./.disk/casper-uuid-powerpc
./.disk/casper-uuid-powerpc64-smp
./.disk/info
./.disk/release_notes_url
./casper/
./casper/filesystem.manifest
./casper/filesystem.manifest-desktop
[...]
./ppc/bootinfo.txt
./preseed/
./preseed/cli.seed
./preseed/ltsp.seed
./preseed/ubuntu.seed
./ubuntu

```

This will last some time, but when done, we can unmount the partition

[FONT="Fixedsys"]umount /dev/sdc3[/FONT]

and now we can boot from the stick!


[SIZE="5"]Step 6: Boot from the stick[/SIZE]

[FONT="Fixedsys"]reboot[/FONT]

Sooner or later the CD will be ejected. Press enter then. When you hear the boot sound press the 4 keys: alt-cmd-o-f. Soon after that, the Open Firmware prompt should appear.

First we try to find the bootstick:

[FONT="Fixedsys"]dev / ls[/FONT]

**Hint:** US keyboard! Germans pleas press "/" to get the "-".

You will see a longish hierachical list.

Somewhere in that list you will find a "/usb..." and somewhere below that a "/disk...". Maybe a "/hub..." is between that, should the stick be plugged into a usb hub.

It's important to write down that part.
```

  /usb@15,1
    :
    :
    /disk@1

```

With the command

[FONT="Fixedsys"]devalias[/FONT]

we look whether or not there is a "shortcut" for the /usb@15:

Here is what my system has:

```
usb1    /pci@f2000000/@15,1
```

To boot from the stick, I enter:

[FONT="Fixedsys"]boot usb1/disk@1:2,\\:tbxi[/FONT]

the :2 is the bootstrap-partition we created earlier.


That was it. After some time yaboot's "boot: " prompt should appear. Depending on the changes you made to yaboot.conf, you simply press enter or select the appropriate image to boot.

---

### Post by avtolle on 2008-05-03
Outstanding! Congratulations on making it work. 

Your English is much better than my Deutsch (took one semester while in college, or should I say it took me? :-( ), and I am able to follow your instructions quite well.

---

### Post by BeautyandSong on 2008-09-04
I'm trying this on my G4 PPC. It doesn't work after Step 4. This is the error I get when I try to "fill the bootstrap" partition. Any help, comments, appreciated.

> root@ubuntu:~# hformat -l bootstrap /dev/sdb12
hformat: /dev/sdb12: error opening medium (No such file or directory)
root@ubuntu:~# 

FYI: I followed the Instructions to T up until Step 3. Everything looked exactly the same.

**[COLOR="Red"]EDIT: Since this method is not working for me right now I'm trying to look for alternatives, but it's completely messed up my pen drive and it cannot be read anymore. I really need your help right now, or at least if you could tell me how to return my pen drive to normal (using OS X) so I can maybe try something else would be greatly appreciated.[/COLOR]**

---

### Post by cyberdork33 on 2008-09-04
> **BeautyandSong said:**
> I'm trying this on my G4 PPC. It doesn't work after Step 4. This is the error I get when I try to "fill the bootstrap" partition. Any help, comments, appreciated.



FYI: I followed the Instructions to T up until Step 3. Everything looked exactly the same.

**[COLOR=Red]EDIT: Since this method is not working for me right now I'm trying to look for alternatives, but it's completely messed up my pen drive and it cannot be read anymore. I really need your help right now, or at least if you could tell me how to return my pen drive to normal (using OS X) so I can maybe try something else would be greatly appreciated.[/COLOR]**you had a typo sdb12 instead of sdb2.

You pendrive should be fine, it just needs repartitioned / reformatted to be usable normally again.

---

### Post by BeautyandSong on 2008-09-05
> **cyberdork33 said:**
> you had a typo sdb12 instead of sdb2.

You pendrive should be fine, it just needs repartitioned / reformatted to be usable normally again.

Actually, the pen drive was located at /dev/sdb1, and the bootstrap partition was 2. Hence /sdb12. If I tried to run the hformat command using /dev/sdb1 as the destination, it gave a slightly different error, but I've closed all my windows now. I think it said it couldn't find the file/destination without the "error opening medium" line. 

I know the pendrive has to be reformatted, but how? Mac OS X won't read it, and I can't load it in Disk Utility... Thanks!

---

### Post by cyberdork33 on 2008-09-05
> **BeautyandSong said:**
> Actually, the pen drive was located at /dev/sdb1, and the bootstrap partition was 2. Hence /sdb12. If I tried to run the hformat command using /dev/sdb1 as the destination, it gave a slightly different error, but I've closed all my windows now. I think it said it couldn't find the file/destination without the "error opening medium" line. 

I know the pendrive has to be reformatted, but how? Mac OS X won't read it, and I can't load it in Disk Utility... Thanks!
Except that is the wrong terminology. sdb would be the device... sdb1 would be a partition. so if you were trying to access the second partition on the device, it would be sdb2. And just for completeness, additional devices would be sdc, sdd, etc.

I am not sure what the process you followed actually does to the drive, but you might try using gparted to view and partition the device. FAT32 partitions are the norm for these devices since it is most compatible with other filesystems.

---

### Post by rednose0607 on 2008-09-07
Hi!
I found the thread very interesting and I tried to go through all the steps. I have a PB 15" G4 with an external LACIE firewire disk. It is a "pen disk" i.e. it is powerd via the firewire cable, the disk has no power supply.

I dedicated the disk to ubuntu, then partition 2 is the boot partition 3 is the copy of livecd.

When I enter openfirmware I run a command like:

boot fw/node/sbp-2/disk@0:2, \\tbxi

I can hear the disk starting to spin a bit, e.g. the command address the disk. Then a receive a message:

sbp-2:Open -> login?
speed=ffffffff 2 2 MAC-PARTS - LOAD (non interposed) not supported load-size=0 adler32=1
LOAD_SIZE is to small

And obviously I can't boot :-)

Any useful hint/idea ? Any help is MUCH appreciated :-) Thanks a lot!

R.

---

### Post by pxwpxw on 2008-09-07
> **rednose0607 said:**
> Hi!

When I enter openfirmware I run a command like:

boot fw/node/sbp-2/disk@0:2, \\tbxi

I can hear the disk starting to spin a bit, e.g. the command address the disk. Then a receive a message:

R.

```

0> boot fw/node/sbp-2/disk@0:2, \\tbxi

that has a colon :  missing, and a bad space should be 

0> boot fw/node/sbp-2/disk@0:2,\\:tbxi

or you can just boot yaboot -

0> boot fw/node/sbp-2/disk:2,yaboot


```

also try these

```

to list the files -
0> dir fw/node/sbp-2/disk:,\
0> dir fw/node/sbp-2/disk:2,\

```

---

### Post by Alexstone on 2009-02-17
Ok fellas, i've followed this until i got to the bit that said "G4 laptop cannot boot from usb, only firewire."

Here's the challenge:

I understand the process up to booting from firewire. The internal optical drive in my G4 is now officially toast, so i'm keen to install Ubuntu ppc from firewire. I have an external box that i've temporarily attached a cd drive to. (It works, but it's not pretty. Pile of wires, live power at my fingertips, literally. You get my drift.)

So far, from either OF or simply yaboot second stage bootstrap, i can put in the following command, the firewire CDrom gets all energetic, and screams like a z-list pop singer, but then just cycles down to a low hum, and the screen message says:

Welcome to yaboot version 1.3.13
boot: fw/node/sbp-2/disk@0:2,\\:txbi
Please wait...Loading kernel


Doesn't work. I fell asleep on attempt 483, and it still said the same thing when i woke up 3 hours later.


So;
When i do a dir, and question this in OF, i get a whole string of block messages (write-block? 17, then write-block? 3, etc, with a few retrys exceeded thrown in as well.)

I've burned 4 discs on a borrowed win pc (they're cheap) to use, and all come up with the same message when i try to use dir in OF to find stuff on the disk.

What am i doing wrong here? md5 sums are ok, so that's alright.

What sort of command do i have to put in in either OF, or at boot prompt to fire up an install. (The OS on the HD is toast, so i need to reinstall fresh. Don't ask. User Error...)

I'm no Linux Gandalf, so simple instructions would be thrilling.

I don't get the sudden enthusiasm from the FW cdrom, as that tells me the laptop is locating and using the device ok. It works the same way every time.

But if i have yaboot 1.3.13 already in place, how can i tell the firewire cdrom to get on with it and start my fresh install?


Some will no doubt say the old G4 is a good candidate as a boat anchor, but i'll be honest here, i'm rather attached to the old bitch. She might be missing a cdrom drive, and spit the dummy at installing from usb, but she's been a fair way round the world with me, and i know just how she ticks, at least until now.

So what i am trying to do?

Install Ubuntu ppc from a firewire cdrom.

Alex.

---

### Post by truerobotech on 2009-03-29
I have assumed its a bad initial install so im working on the boot from usb process.

When i get to this point

(cd /cdrom ; tarcBpf -.) | (cd /mnt ; tar xvBpf -)

I get a mssg back 

bash: tarcBpf: command not found


When i space it differently I get

(cd /cdrom;tarcBpf-.)|(cd /mnt;tar xvBpf-)
tar: Old option `f' requires an argument.
Try `tar --help' or `tar --usage' for more information.
bash: tarcBpf-.: command not found


can someone point out another method or at what point im fat fingering the syntax. Thanks

OH sorry forgot to toss in a thanks credit to the author, for a translation andwith me a total noob its explained well

---

### Post by shawnhcorey on 2010-03-28
> **truerobotech said:**
> I have assumed its a bad initial install so im working on the boot from usb process.

When i get to this point

(cd /cdrom ; tarcBpf -.) | (cd /mnt ; tar xvBpf -)

I get a mssg back 

bash: tarcBpf: command not found


The command you want is:
```
(cd /cdrom ; tar cBpf - .) | (cd /mnt ; tar xvBpf -)
```
There are some spaces missing in the original.

I have create my own version of how to do this:  see attached.

---

### Post by linuxopjemac on 2010-03-28
I recently made a similar manual, to boot via USB to then install Debian or Ubuntu via the net:

[http://mac.linux.be/phpBB3/viewtopic.php?f=10&t=75](http://mac.linux.be/phpBB3/viewtopic.php?f=10&t=75)

Can I post your manual on my site too ? I will make a reference to here of course.

---

### Post by shawnhcorey on 2010-03-28
> **linuxopjemac said:**
> I recently made a similar manual, to boot via USB to then install Debian or Ubuntu via the net:

[http://mac.linux.be/phpBB3/viewtopic.php?f=10&t=75](http://mac.linux.be/phpBB3/viewtopic.php?f=10&t=75)

Can I post your manual on my site too ? I will make a reference to here of course.

Sure, attached is the original, written in Perl POD format.  It can be converted to others like LaTeX or HTML.

---

### Post by linuxopjemac on 2010-03-28
Great, I had a manual also here:
[http://mac.linux.be/content/booting-open-firmware#USB](http://mac.linux.be/content/booting-open-firmware#USB)

Yours seems a little more idiot proof ;)

---

### Post by Georges_Gaune on 2010-12-29
I'd like to install Ubuntu Desktop on my old PowerPC G5 PowerBook Titanium. The hard drive is dead and that is why I want to install Linux on a USB flash drive 4 gig. The procedure *Bootable_usb.txt* seems perfect, but only when the drive operates. How can we do without the disk. Can I use another USB key to the temporary folder *isofiles*. If yes, how is it done?

Thank you

Paul

---

### Post by shawnhcorey on 2010-12-29
AFAIK, the only way to boot from anything but the hard drive and CD drive is to go through Open Firmware.  If you haven't read them, these may help.

[LIST]
[*][HOWTO Create A Bootable USB Drive From An ISO Image For Apple PowerPCs In Linux]("http://sites.google.com/site/shawnhcorey/howto-create-a-bootable-usb-drive-from-an-iso-image-for-apple-powerpcs-in-linux")
[*][HOWTO Boot Apple PowerPCs From A USB Drive In Open Firmware]("http://sites.google.com/site/shawnhcorey/howto-boot-apple-powerpcs-from-a-usb-drive-in-open-firmware")
[/LIST]

You'll need [FONT="Courier New"]mac-fdisk[/FONT] to format the boot partition on the USB drive.

---

### Post by Georges_Gaune on 2010-12-29
Thank you for the links.

 But already, I find that I can not follow this method. In fact, I do not have enough RAM (768 meg) to download and extract the. iso file. I know, I tried this morning and after 200 or 300 meg, the Mac crashed. That's why I think I have to use two USB keys: one to extract the. iso and the second would be my bootable USB. But how, I do not know.

Regards,

Paul

---

### Post by shawnhcorey on 2010-12-29
This command:
```
mount -t iso9660 -o ro,loop=/dev/loop0 ./xubuntu-10.04-desktop-powerpc.iso ./iso

```
will mount an ISO file as a file system.  You need to change the file and mount directory names to match your system.

Then you can use cp to transfer the files.  Don't forget the hidden files and directories, the ones that start with a period.

---

### Post by Georges_Gaune on 2010-12-29
Hi !

Excuse me, I'm fairly new to Linux. I wrote the command line, but nothing happens visible. Is it supposed to do a RAM disk so that I can copy the image. iso (Ubuntu). How this command line in your part?

For your info, I checked, I have exactly 300.5 meg of ram available.

Thanks !

---

### Post by shawnhcorey on 2010-12-29
In that case, I think you should try booting from the network.  This requires a small ISO file.  But it's been a long time since I tried it, so maybe someone can give you more up to date info.

Have you tried the [forums at Linux on your Apple Mac]("http://mac.linux.be/phpBB3/index.php")?

---

### Post by commodore256 on 2010-12-30
Is there a way to make a live USB from Windows?

I have a AMD Card, so I don't wanna risk losing all my data just so I can install Linux on my old Mac.

Anyway, I tried unetbootin and I couldn't boot from USB. (optical drive is busted/removed/discarded)

Did I mess up unetbootin?

Anyway, what's the proper command when I hold Command+Option+O+F?

I typed in ***dev / ls*** and got this:

```
/usb@18
 /disk@1
```

and typed in ***devalias*** and got...
```
0usb                         /pci@f2000000/mac/@usb18
```

I'm sure that's the important data, but I don't know what to do with it.

---

### Post by shawnhcorey on 2010-12-30
> **commodore256 said:**
> Is there a way to make a live USB from Windows?

If you're running Windows, then it's not a PowerPC.

You need mac-fdisk, Apple's version of fdisk(8), to create a HFS+ bootable partition on the device.

> **commodore256 said:**
> Anyway, what's the proper command when I hold Command+Option+O+F?

I typed in ***dev / ls*** and got this:

```
/usb@18
 /disk@1
```

and typed in ***devalias*** and got...
```
0usb                         /pci@f2000000/mac/@usb18
```

I'm sure that's the important data, but I don't know what to do with it.

Read the link on how to boot from Open Firmware.

[LIST]
[*][HOWTO Create A Bootable USB Drive From An ISO Image For Apple PowerPCs In Linux]("http://sites.google.com/site/shawnhcorey/howto-create-a-bootable-usb-drive-from-an-iso-image-for-apple-powerpcs-in-linux")
[*][HOWTO Boot Apple PowerPCs From A USB Drive In Open Firmware]("http://sites.google.com/site/shawnhcorey/howto-boot-apple-powerpcs-from-a-usb-drive-in-open-firmware")
[/LIST]

---

### Post by perspectoff on 2010-12-30
Does the "Create a LiveUSB" utility in Ubuntu not work? Perhaps I am missing something?

---

### Post by shawnhcorey on 2010-12-30
> **perspectoff said:**
> Does the "Create a LiveUSB" utility in Ubuntu not work? Perhaps I am missing something?

Do you have a PowerPC?  I have not got it to work on a PowerPC, but you may have more luck.

---

### Post by commodore256 on 2010-12-31
> **shawnhcorey said:**
> If you're running Windows, then it's not a PowerPC.

You need mac-fdisk, Apple's version of fdisk(8), to create a HFS+ bootable partition on the device.



Read the link on how to boot from Open Firmware.

[LIST]
[*][HOWTO Create A Bootable USB Drive From An ISO Image For Apple PowerPCs In Linux]("http://sites.google.com/site/shawnhcorey/howto-create-a-bootable-usb-drive-from-an-iso-image-for-apple-powerpcs-in-linux")
[*][HOWTO Boot Apple PowerPCs From A USB Drive In Open Firmware]("http://sites.google.com/site/shawnhcorey/howto-boot-apple-powerpcs-from-a-usb-drive-in-open-firmware")
[/LIST]

I have more than one Computer. I was trying to make the live usb from windows so I can boot my imac G3 that has an OS9 Virus and no optical drive.

I'm in ubuntu 10.04 _x86_ right now and I'm still trying to get ubuntu server 10.04 _PPC_ (screw arch for now) to boot on my 450mhz imac G3.

I know the right command in the apple firmware, I just can't make a live USB.

Oh, and the "mac-fdisk" command doesn't exist and I found binary packages for PowerPC. That's good, but I'm on x86 trying to get a mac with a virus to boot. (Justin Long was lying about macs with viruses or at least with OS9)

---

### Post by commodore256 on 2010-12-31
Here's a better idea of What I tried to do all day yesterday...
[http://www.youtube.com/watch?v=EYyrkxKIEcc](http://www.youtube.com/watch?v=EYyrkxKIEcc)

The plan was to install a CLI distro and then install xorg/e17 on top of that.

So, my Idea is to now use x86 ubuntu to set up a ppc ubuntu server liveusb and then install e17.

It should work fine, it has 192MB of ram.

P.S. I threw away the other iMac with 32MB of RAM.

---

### Post by shawnhcorey on 2010-12-31
> **commodore256 said:**
> So, my Idea is to now use x86 ubuntu to set up a ppc ubuntu server liveusb and then install e17.

I don't think x86 Ubuntu comes with mac-fdisk.  Only the PPC has it.  Without it, you can't create a bootable partition on the drive.

I suggest you create the first two partions, the partition map and the bootable HFS+ one, using the PPC and then use your x86 to load the ISO files.

---

### Post by commodore256 on 2010-12-31
Which Utilities should I use? Regular fdisk? Gparted? and how would I use them so it would boot when I go into the open firmware and tell it ```
boot usb18/disk:1,\\:tbxi
```

I think that's the right command, but it just boots into OS9.

---

### Post by Georges_Gaune on 2011-01-09
I got to create a live USB to my Mac Powerbook G4 Titanium. I managed to counter the problem of my broken hard drive using the CD-ROM as a resource for Ubuntu and a second USB drive as temporary. The only problem I have is set, the file is "yaboot.conf. I can not understand what I need to edit this file. I know I must add this:

 root = / dev / ram
 score = 3
 message = / install / boot.msg

 But I do not know where.

 Can anyone help me?  Thank you !

---

### Post by Georges_Gaune on 2011-01-13
Well, I finally boot with a USB key that contains Ubuntu 10.10. I remember my hard drive died. I can easily boot the live CD, but with the USB I have a problem: Ubuntu starts, then the PC is looking for a CD and then it appears an error message Initramps in Busybox. Then he looks for a medium, as if he did not recognize the image of my USB key.

Someone had this problem with Initramps and Busybox?

---

### Post by Ivan_Avery_Frey on 2011-06-28
There were still two typos in the original message. When copying the yaboot.conf file from the live cdrom the .conf extension was left out.

Missing space in the first tar command: tar cBpf -

---

### Post by rsavage on 2011-06-29
There is a much easier way to create a live USB stick:
 
 
First, find out the device name of the USB device. Look in the disk utility program or something for this. Mine is /dev/sda
 
Then use the 'dd' command to copy the iso to disk. WARNING!! This will erase your USB stick so only do this if it hasn't got anything important on it! Also, double check you have the device name correct as you don't want to erase a hard drive or anything like that by mistake! The 'dd' command will do its thing even if you have the device mounted. The command you want will be something like this:
 
sudo dd if=~/Downloads/ubuntu.iso of=/dev/sda
 
where ~/Downloads/ubuntu.iso is the path of the iso file and /dev/sda is the USB device.
 
 
Restart the machine into openfirmware (hold down o and f and command and option while turning on). To boot the stick type 
 
boot usb0/disk@1:2,\\yaboot 
(or something similar like 'boot usb1/disk@1:2,\\yaboot')
 
The above is based on this thread [http://ubuntuforums.org/showthread.php?t=1602512](http://ubuntuforums.org/showthread.php?t=1602512) .
 
Btw, to return the USB stick to 'normal', you'll need to repartition and reformat it!
 
EDIT: I've given further info on using a usb in more messages below....
 
EDIT2: I've recently discovered Gentoo have a good guide to booting from usb here [http://en.gentoo-wiki.com/wiki/LiveUSB_on_PPC](http://en.gentoo-wiki.com/wiki/LiveUSB_on_PPC) . Some more random stuff is here [http://hints.macworld.com/article.php?story=20060301112336384](http://hints.macworld.com/article.php?story=20060301112336384) .

---

### Post by dodino on 2011-06-29
Anyone can tell me if exist a simple procedure (like this for PPC) to make an USB stick with an Ubuntu installation (or live) bootable on a macbook? I have tried many guides found in this forum but none of them has ever worked, the boot of the usb stick with ubuntu does not work for me on a macbook. Thanks in advance..

Edoardo

---

### Post by linuxopjemac on 2011-06-29
Some MacBooks don't have the right EFI firmware allowing to boot from USB. I own a MacBook 2,1 which is unable to boot from USB for example. Not all MacBooks are the same.

---

### Post by rsavage on 2011-06-29
Anybody got the PPC alternate CDs or minimal CDs to work with USB? The 10.04 alternate CD gets so far and then tells me it can't mount the cdrom. The minimal CD seems to just hang at some point (don't know if it is downloading or something? It doesn't say it is.)
 
The 10.04 live cd works perferctly. The debian mini works perferctly.
 
I do have an exceptionally dodgy USB stick so it might just be me.

---

### Post by rsavage on 2011-06-29
Just to expand on the above. I want to install a minimal ubuntu and build up. That is why I was interested in the minimal CD and alternate versions. 
 
SOLVED NOW!
 
If you get a problem with the alternate CD telling you it can't mount the CD then this is what to do....
 
Press Ctrl-Alt-F2 to take you to a Busybox terminal
 
Type 'umount /dev/sda' (or whatever your usb device is)
Then type 'mount /dev/sda1 /cdrom'
Then type 'exit' and swap back to the installation ctrl-alt-F1
 
You can continue installing now (not sure if I skipped the detect cd-rom bit - can't remember). Installation may then throw an error at the can't install base system bit "Failed to determine the codename for the release". Go to the installer menu and choose "load installer components from cd". Tick the bit for detecting and loading ISOs ("load-iso: blah blah blah...."). Installation then sprang into life for me. 
 
Hope this helps.

---

### Post by rsavage on 2011-06-30
Solved now. Have edited the above post with instructions.
 
New Update: A wierd thing has happenend in that I can't repeat exactly the steps I've described above. This time the Ctrl-Alt-F2 thing doesn't want to work so I've had to use the "execute shell" option from the menu. Also, the umount command doesn't want to work, but that now bizarely doesn't seem necessary this time. Anyway, hopefully you've all got enough info to get a working system.
 
Update 2: I've remembered what the difference was. One was using the 'cli' install and one the normal install. Strange how they behave differently.
 
Update 3: I can confirm the power pc minimal install cd for 10.10 works "out of the box". I don't think previously I had left it for long enough. This time when it appeared to be doing nothing I left it. When I looked back at the screen a couple of minutes later the installation was in full swing. I did choose the manual option for setting the mirror to check it was right (ports.ubuntu.com with directory /ubuntu-ports/), but don't think this made any difference. [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by rsavage on 2011-07-05
If you want to make the usb from Mac OS X then the instructions to do so are here [https://help.ubuntu.com/community/Installation/FromUSBStick#From Mac OSX](https://help.ubuntu.com/community/Installation/FromUSBStick#From Mac OSX) . You'll have to boot it through openfirmware like if you did it from linux (not holding down alt as it describes).
 
These comments [http://ubuntuforums.org/archive/index.php/t-1445659.html](http://ubuntuforums.org/archive/index.php/t-1445659.html) suggest it can be done.
 
Note, this method also wipes the data on your usb device so make sure it has nothing important on it!

---

