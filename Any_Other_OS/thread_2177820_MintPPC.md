---
title: "MintPPC"
date: 2013-09-30
forum: Any Other OS
---

### Post by noah3 on 2013-09-30
Hello there,

First of all, I have a PowerPC Mac Pro G4.
Today I tried to install MintPPC on the computer mentioned above. This is how I did it:
1. Downloaded MintPPC 11 from the [mintppc.org]("http://ubuntuforums.org/mintppc.org") 
2. I burned the .iso file on a CD with the speed of 16x
3. I put the CD in the disk tray and tested if the PC would recognize it, it did.
4. I reboot my PC and hold down the 'C' key.
5. Nothing worked, even a brand new ATA HDD...
6. I tried booting into the Open Firmware mode with holding down the 'option' key, 'command' key, the 'O' key and the 'F' key. It had no problems
7. As there is a bug in the firmware here, I typed the following in: ```
boot hd;\install\yaboot
```
8. As I just pressed enter, there came a screen up that showed a big NO-NO sign (see picture).
9. And now I stranded here, asking for your help.

PICTURE:
[IMG]http://2.bp.blogspot.com/_BUfUZUCBj5Q/TILcqWGIvaI/AAAAAAAAA5k/gc4tt-3XH6A/s400/forbidden+sign.gif[/IMG]

Maybe you people can give me a better distro(?) or did I just do something completely wrong?


~noah

---

### Post by theDaveTheRave on 2013-09-30
Are you saying you can't boot into the normal system either?

I don't know much about power PCs, but I assume they have some sort of BIOS where you can modify the boot device order?

I appreciate that you burnt the CD at 16x but did you confirm that the ISO file had the correct MD5 sum ? if there was a download error you may find that you would be trying to run a bad ISO.

Once this is sorted you should be able to run the live CD, at the very least.

I'm sure there are others that have more experience with the power pc.

David

---

### Post by noah3 on 2013-10-01
> **theDaveTheRave said:**
> Are you saying you can't boot into the normal system either?
Well, I can boot the OS 10.4.x properly.


> I appreciate that you burnt the CD at 16x but did you confirm that the ISO file had the correct MD5 sum ? if there was a download error you may find that you would be trying to run a bad ISO.
I can confirm that the ISO file is correctly branded on it and that I can open it.


Sorry for the not so good explanation, it's not my greatest point, especially not in my native language ;)
Thanks anyways!

---

### Post by theDaveTheRave on 2013-10-03
> **noah3 said:**
> 
Sorry for the not so good explanation, it's not my greatest point, especially not in my native language ;)

No worries...

The first port of call is to boot from the live CD and see if you can find all the HDD on the system. I don't know how experienced you are with linux (and I don't know the PPC), but the disks should all appear in the file manager once you open it.

If you have mutliple partitions on your main disk, you should check them all.

Once you have confirmed that you can see them all (or not), you will want to compare the details with what you find if you boot directly into the system (ie no the live CD).

Post an update of what you find.

Also you may want to make use of gParted (the disk partitioner) that should be on the live CD, this will also show you all the disks and any sub partitions, and will tell you if you can 'see' the disk, but the partition is for some reason hidden. If you can take a screen shot of the output, also post output of
```

ls -lah /dev/disk/by-id

```

David

---

