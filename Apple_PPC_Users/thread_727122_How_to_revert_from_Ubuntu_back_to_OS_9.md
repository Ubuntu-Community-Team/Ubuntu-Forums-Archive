---
title: "How to revert from Ubuntu back to OS 9 ?"
date: 2008-03-17
forum: Apple PPC Users
---

### Post by spystyle on 2008-03-17
Hello from Maine,

I received a couple free Imac G3 slot loaders, I am new to Mac and Linux, I tried Ubuntu then later *acquired* OS 9 disks (on CD-R).

When trying to boot I hold C, then power on, all the while holding C with the OS 9 CD in the drive, I get to Ubuntu's boot loader and it will not boot the CD.

So I deduce that either the Ubuntu boot loader does not like the OS 9 disk *or* the OS 9 disk is not burned correctly.

When I boot into Ubuntu desktop and then insert the OS 9 disk it says "unable to mount"

Any advice? I would like to try OS 9 on this old G3.

Thank you,
Craig

---

### Post by Fire_Chief on 2008-03-17
Sounds like the CD is a bad burn. To be sure, you could try booting with the CMD(apple)-Option-SHIFT-DEL key combo. It will attempt to boot from any/all other sources before the hard drive. If it can find a recognizable boot file then it will attempt to boot from it. If no other bootable media/devices are found, it will default to the hard drive.

---

### Post by spystyle on 2008-03-18
> **Fire_Chief said:**
> Sounds like the CD is a bad burn. To be sure, you could try booting with the CMD(apple)-Option-SHIFT-DEL key combo. It will attempt to boot from any/all other sources before the hard drive. If it can find a recognizable boot file then it will attempt to boot from it. If no other bootable media/devices are found, it will default to the hard drive.

I think you're right, I held command + option + delete + shift while resetting via the reset button and I got an icon with a question mark, as if the computer was telling me it could not read the disk.

So, I have an OS 9 "ISO" and I have tried burning it with Nero and IMGburn, on two different burners, and I have no luck. How am I supposed to burn a mac compatible disk on a PC ?

Thanks,
Craig

---

### Post by Fire_Chief on 2008-03-18
Is it an actual .ISO file or is it a .dmg or .img file? I've used TransMac (windows app) to successfully burn .img files before when Nero and all others failed me. I'm not sure of a linux app that handles .img files properly. :(

Also, when you get the ? icon on the startup, let go of the keys and it will start searching for the bootable/readable media. I don't think it starts looking until you let go of the keys.

---

### Post by spystyle on 2008-03-18
I am running Windows 2000, I will try to find and use TransMac, thank you :)

---

### Post by spystyle on 2008-03-18
Bummer, not even TransMac will burn the two ISO's I acquired...

I think it may be a Windows 2000 issue.

Would anyone send me an OS 9 copy for some bux ? PM me :)

Thanks,
Craig

---

### Post by MONODA on 2008-03-18
> When trying to boot I hold C, then power on, all the while holding C with the OS 9 CD in the drive, I get to Ubuntu's boot loader and it will not boot the CD.
i dont think that you should hold down the C key but rather repeatidly press it. try that

---

### Post by spystyle on 2008-03-18
That too does not work. Maybe I should install XP via virtual machine and try to burn it on that? The ISO's came from p1r@tebay and there were no comments about them not working, and it's safe to assume all of those guys were running XP, so it may be a 2K issue...

---

### Post by ristosu on 2008-03-18
Mac OS CD's use the same file system as Mac OS HD's: HFS or HFS+. I don't think they need any special treatment to become bootable, like ISO's do.

---

### Post by gregj777 on 2008-03-18
I'm having the same problem. HELP!!  I have a clamshell G3 ibook SE with CD/DVD ROM.

When I load ANY cd/dvd (I tried a movie too) it will not mount the disc. I want to reinstall OS9 or OSX and remove Xubuntu  completely. 

I have tried holding the C, all the command+shift stuff, and it won't boot from the install dvd's. I have confirmed it is a dvd drive.

The weird thing is that I get the question mark screen you mentioned when I try to boot from OS9. From OSX Tiger I get the Apple logo and then the system crashes and says the driver wasn't loaded, and ends with "we're hangin here". BUT when I put in my LEOPARD dvd it recognizes it and the pinwheel actually comes up and spins... but continues to spin and never stopped. I let it spin for about 30 minutes just to see if it was loading, but nothing happened.

I thought about buying an old Panther cd from eBay but surely there's a way to fix this. I also did the nram and reset-all thing and that didn't work either.

---

### Post by ristosu on 2008-03-19
There is always the possibility that the drive has gone bad. Mac install disks should be readable in Open Firmware (Cmd-Opt-O-F after chime):

```
dir cd:,\
```

If that doesn't work (show a file listing), then it's probably time to replace the CD unit. Note however that Open Firmware cannot interperet the directory on all types of disks, but at least HFS should work on NewWorld machines. This seems to depend on Open Firmware version, too (>=3 on NewWorld).

---

### Post by gregj777 on 2008-03-19
I don't know what HFS is, or where to go to to enter dir cd:,\.

---

### Post by ristosu on 2008-03-19
HFS stands for Hierarchical File System, it is invented by Apple and used in their OS's to keep track of file locations on disk.

Open Firmware prompt can be entered right after the computer is booted, press and hold Cmd-Opt-O-F, all 4 at the same time, after the chime sound has ended. Cmd = Apple logo, Opt = alt.

---

### Post by gregj777 on 2008-03-19
ah ok.. I'll try that this evening when I get home. But I wouldn't think it's the drive because it does recognize the drive titles (the name of the disc or movie) and it did start reading the Leopard dvd. I didn't expect Leopard to load on the machine but it's odd out of all the discs it would read that one.

Thanks for your help!

---

### Post by oswaldkelso on 2008-03-19
if Zapping the pram has no effect I would try removing the battery first. This has fixed things for me when stuck in a loop on my g4. Also many pc and mac burning apps wont let you burn as a pure  9660 iso but burn platform specific  iso's.


I had a lot of bad burns in osx. So this is what I do now it works for me so I've never changed.

download the disc image.
open disc utility.
drag the disc image into the left hand pane on disc utility.
select the image in the pane.
then select burn.

you must not open the disk image with the finder it can mess it up!!

 use burnfreex [http://www.macupdate.com/info.php/id/13824](http://www.macupdate.com/info.php/id/13824)

If you use toast in os 9,burn using the straight iso 9660 not pc, mac, etc

---

### Post by gregj777 on 2008-03-19
> **ristosu said:**
> HFS stands for Hierarchical File System, it is invented by Apple and used in their OS's to keep track of file locations on disk.

Open Firmware prompt can be entered right after the computer is booted, press and hold Cmd-Opt-O-F, all 4 at the same time, after the chime sound has ended. Cmd = Apple logo, Opt = alt.

I tried this, and it did show me a directory of the contents of the Apple install dvd that was in the drive. But then I went to boot it from the dvd and same thing, "we're hanging here" at the end. 

i bought an external dvd drive and tried to use it but I have no idea how to make Xubuntu recognize it and it didn't automatically do so. I'll have to take it back tomorrow. 

I'm presently downloading Mandriva, to see if it may contain some drivers or something that this install of Xubuntu presently has omitted or something, but I don't know if I'll know how to install it when it finishes downloading or not.

---

