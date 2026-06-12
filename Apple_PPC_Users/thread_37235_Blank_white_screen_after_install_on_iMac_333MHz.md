---
title: "Blank white screen after install on iMac 333MHz"
date: 2005-05-26
forum: Apple PPC Users
---

### Post by goran65 on 2005-05-26
Hi all!
I'm new to this forum and I would like if I was able to post success, but right now I have a problem. Recently acquired an old iMac G3 333MHz / 256Mb RAM / 6.4Gb HD / MacOS 9.2 installed. I didn't want to mess MacOS, took out HD and put empty one 8.4Gb in order to install Hoary. Don't need dual boot. Dloaded both live and install cds. Live cd works fine, I like ubuntu. 
Put in install cd, accepted defaults, installed base system, copied rest on HD and then after reboot just blank white screen. After some time mac folder with question mark in the centre. Guess that this means 'no bootable disk' or similar.
Went on this forums, found about 8G limit. Ok, try again. This time manually repartitioned disc:
32kb for some apple stuff (was like this after first try, didn't touch it)
~1M again apple stuff, bootstrap I guess (same as above)
2.3G for / (now it's under 8G limit, am I right?)
~6G for /home
rest ~350M swap (was like this)
Went thru installation again, install said that it will install yaboot, reboot ...
same as before - blank screen and ?folder? after some time/
Can anybody tell me what's going on? Why yaboot doesnt start or why it doesn't see installed linux?
I'll keep googling and trying and keep you informed, anyway, but does anybody have some ideas.

Cheers, Goran

---

### Post by Len on 2005-05-26
Yaboot doesn't work... why it really should on this machine.

It could be corrupt data in the PRAM or NVRAM on the Mac side. You can try holding "alt" when you power on your mac and see if you can choose the Linux (yaboot) partition as your startup disk. On this iMac this probably isn't implemented yet (have a rev C which doesn't do it, you have a rev D of the same line).

You could try booting manually (yes, it can be done although it is not in your manual) from your freshly installed system by holding Apple+Alt+p+r when you power your mac. You'll get a white screen where you can input commands directly to the OpenFirmware (BIOS).

Now to force the OpenFirmware to load Yaboot (and give error messages if it fails) type:
```
boot hd:1,\\yaboot
``` Where the '1' is your partition number and 'hd' is your main drive (the iMac only has one anyway). If it boots, congrats! 
If it gives the error "OF cannot open yaboot" you probably entered the wrong partition number.
Try to reinstall/configure yaboot when you're in Linux.
NOTE: I haven't used this method for over a year, so I don't know if the yaboot path is still the same!

You can reset the openfirmware. This will reset your date and time, resolution and some other settings (like boot disk), but will not harm your mac in any other way.
When at the scary white open firmware screen, type:
```
reset nvram
set defaults
reset all
```
Your mac should reboot and you should reinstall ubuntu to see if it works or, if you're more comfortable with linux, setup yaboot manually with help of the install or live CD without reinstalling.

If it still doesn't work this is probably a bug, but nothing you can't get around :).

Good luck!

---

### Post by goran65 on 2005-05-27
[COLOR=DarkGreen]On this iMac this probably isn't implemented yet (have a rev C which doesn't do it, you have a rev D of the same line)[/COLOR]
Yes, you are right
[COLOR=DarkGreen]... holding Apple+Alt+p+r when you power your mac. You'll get a white screen where you can input commands directly to the OpenFirmware (BIOS).[/COLOR]
Tried that. This resets PRAM (Parameter Ram, I suppose) and reboots computer.
Apple+Alt+o+f got me to the OpenFirmware (OF) screen. Tried what you said, with different partition numbers, no luck. Says something like "can't see device".
[Apple technote](http://developer.apple.com/technotes/tn/tn2001.html) have some commands for OF. Tried ```
printenv
```, boot-device has no value, in technote has ```
boot-device   hd:,\\:tbxi
```.
Hardware (hdd) should be ok, me think, because when I boot live cd, go to root terminal and type
```
mac-fdisk -l /dev/hda
```
I have
```

/dev/hda
        #                type name         length   base     ( size )  system
/dev/hda1 Apple_partition_map Apple            63 @ 1        ( 31.5k)  Partition map
/dev/hda2     Apple_bootstrap bootstrap      1954 @ 64       (977.0k)  NewWorld bootblock
/dev/hda3     Apple_UNIX-SRV2 system      4394532 @ 2018     (  2.1G)  Linux native
/dev/hda4     Apple_UNIX-SRV2 swap         749321 @ 15732487 (365.9M)  Linux swap
/dev/hda5     Apple_UNIX-SRV2 data       11335937 @ 4396550  (  5.4G)  Linux native

Block size=512     Number of blocks=16481808
DeviceType=0x5007  DeviceId=0x501f

```
Well, what confuses me is that linux (live cd) sees the disk and looks ok to me, but OF doesn't see it. I will try to put back old HD (with MacOS) to see what will happend.
Cheers, Goran

P.S. More useful links for people with similar problems. 
[http://developer.apple.com/technotes/tn/tn2001.html](http://developer.apple.com/technotes/tn/tn2001.html)
[http://www.debian.org/releases/potato/powerpc/ch-init-config.en.html](http://www.debian.org/releases/potato/powerpc/ch-init-config.en.html)
[http://www.debian.org/releases/potato/powerpc/ch-rescue-boot.en.html](http://www.debian.org/releases/potato/powerpc/ch-rescue-boot.en.html)
If somebody have some good ideas, please, let me know. I would really like to put ubuntu on this machine because live cd looks sooo wonderful  :grin:

---

### Post by Len on 2005-05-27
Whoops, sorry! apple+alt+O+F whas what I meant indeed.

boot hd:2,\\yaboot should work, that's your bootstrap partition. It is very strange it won't. You have the harddisk set to 'master' by the way? No idea if the iMac cares but who knows...

You could also try 'boot hd:2,\\:tbxi' . If that also doesn't wort Yaboot isn't even installed properly. You should try booting from a CD that has Yaboot and set it up manually (the LiveCD?). You can also boot from the installer CD and mount the 2nd partition (mount -t hfs /dev/hda2 /mnt/yaboot where /mnt/yaboot can be any existing folder on /). I remember it was  HFS standard. If it is HFS+ you should use mount -t hfsplus ... etc.

It is too long ago I worked with yaboot that way, I don't even know for sure if 1 MB is large enough for it (although it should be).

Good luck!

EDIT: A nice addition:
Typing
**dev / ls**
and
**devalias**
in the OF will list the available devices. It won't list partitions.

---

