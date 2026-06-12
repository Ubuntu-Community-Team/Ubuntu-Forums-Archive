---
title: "[SOLVED] yaboot.conf oops"
date: 2008-06-06
forum: Apple Hardware Users
---

### Post by blampars on 2008-06-06
running an ibook g3 500mhz 192ram

i was editing my yaboot.conf so i could try to get my brightness keys working..

now i'm getting
```
/pci@f4000000/ata-6@d/disk@0:3, \\hda3: unable to open file, invalid device
``` when i rebooted

this wasnt the original entry in my yaboot.conf, but I cant remember what the original is and I don't have a bootable cd. i do have a backup of yaboot called yaboot.conf.bak but i dont know how i can access it. i'm stuck at the 2nd stage boot menu.

help please :)
-b

---

### Post by stream303 on 2008-06-06
At the second-stage of the yaboot boot: prompt, hit -tab- to stop the countdown.

Now you can go into single-user mode, ala

```
Linux single
```

at the 2nd-stage yaboot boot: prompt.

You'll have to choose which partition to drop into a shell from, typically /dev/hda3 if you let guided partitioning use the whole disk when you installed it.  Just try them all until you get into a shell if you can't remember.

If you made the yaboot.conf.bak file in the same directory of /etc, you could then issue

```
ybin -v -C /etc/yaboot.conf.bak
```

THIS is one of the major reasons I like to use the long version of ybin, btw, so you can do a ybin on any filename in any path you choose to get your yaboot working again.

You may have to find your yaboot.conf.bak file if it isn't save to /etc, so perhaps run

```
locate yaboot.conf.bak
```
or
```
find / -name yaboot.conf.bak
```

to find out where you hid it. :)

---

### Post by blampars on 2008-06-06
not working.. anything I type I get errors..

```
Welcome to yaboot version 1.3.13
Enter "help" to get some basic usage information
boot: Linux single
Please wait, loading kernel...
/pci@f4000000/ata-6@d/disk@0:3, /boot/vmlinux: Unable to open file, Invalid device
```

:confused:

[EDIT] ok i found my ubuntu server 8.04 disk (now that i'm at home). booting from that into the shell it says my hard disk will be mounted at "/target" though i'm not seeing it..

we can either start now from this, or we can continue on without using the cd. whichever is best

thanks,
-b

---

### Post by stream303 on 2008-06-07
Ah, what it is asking for is what partition to drop your shell into, a root partition.  Highlight or type in what you know to be the root partition, and if you don't know, start with /dev/hda3 and work your way up if you can't get a shell.

Which model do you have?
[http://www.everymac.com/systems/apple/ibook/index-ibook.html](http://www.everymac.com/systems/apple/ibook/index-ibook.html)

What may be an issue is that with only 192mb of ram, you may be facing a lot of disk thrashing to swap with a full Ubuntu install when all is said and done.  Even Xubuntu could be too slow for your tastes - hard to tell since everyone has their own level of patience. :)

Do you have an existing OS on the drive, and are you interested in keeping it?  If not, the easiest route may be to just start over, and allow guided partitioning to "use the whole disk" - although that means you lose everything previously installed.

I also think you are on the right track with the server install - and from there you can layer on a lightweight X and use more efficient lightweight apps.

If you want to go this route, I'd recommend taking a look at this excellent guide, even though the very beginning describes use with x86:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Everyone has their favorite window manager, but for my money at this stage, I'd recommend the XFCE4 window manager.

Something to think about anyway - do you want to fix your yaboot, start over and use the whole disk, or perhaps start over with a minimal server install, and layer your own stuff on top?  Either way is ok as long as it doesn't get you too frustrated. :)

---

### Post by blampars on 2008-06-07
here's the model i have.. [http://www.everymac.com/systems/apple/ibook/stats/ibook_500.html](http://www.everymac.com/systems/apple/ibook/stats/ibook_500.html)

I'm not using a full ubuntu install.  I started out this little ibook project of mine from a server install.  I installed xfce but found that it only ran slightly better than os x 10.3 panther that was on it when I got the ibook.

I've since installed fluxbox and have been using it as my window manager which has been a huge increase in functionality over xfce.

I do not have another OS on the drive, this is a dedicated linux install.

I'd really like to just fix my yaboot.conf.  I've put alot of work into getting this little ibook up and running just the way I want it and I'm not going to let something as stupid as 1 line in my yaboot.conf make me reformat and start over.

I've now got the ubuntu server 8.04 cd i used to install on the ibook in the first place.  I can boot to the busybox shell from the main menu in the cd.  I've tried mounting the drive/partitions but can't seem to get going in that regard. it's just always unable to mount..

here's what i've figured out but havnt made any progress..
list-devices disk
and it tells me the drive is on /dev/hda
i do list-devices partition
and it tells me
/dev/hda1
/dev/hda2
/dev/hda3
/dev/hda4
though i didnt make 4 seperate partitions i should just have the one main partition for the drive as thats how i set it up.

so i try mount /dev/hda /mnt
and get unable to mount /dev/hda is not a directory or something like that

just get me rollin here and i'll be good to go i think.

thanks,
-b

---

### Post by hpp3 on 2008-06-08
Don't mount directly to /mnt... it's just not a good idea.
make a directory to mount stuff to, like so:
```

mkdir /mnt/disk

```
and you didn't make 4 partitions, your install did.
Partition 1 is the partition table, and partition 2 is the Apple_bootstrap partition that needs to be there to keep the firmware from ignoring your drive.
All the goodies are on partition 3, and your swap space is partition 4.
So...
Mount partition 3 on your new mount point:
```

mount /dev/hda3 /mnt/disk

```
Now do a 'ls /mnt/disk' and see what shows up...

---

### Post by Scientia on 2008-06-08
Wonder if you could ctrl-alt-f1? That took me to CLI when i had this same problem.. Then you could use ybin -v -C /etc/yaboot.conf.bak from there.. 
I'm just another noob using an iBook G3 too.

---

### Post by blampars on 2008-06-08
ok, tried the:
```
mkdir /mnt/drive
mount /dev/hda3 /mnt/drive
```

but i get:
```
Mounting /dev/hda3 on /mnt/drive failed: Invalid Arguement
```

suggestions anyone? ;)

I also tried the ctrl alt f1 combo but that didn't do anything :/

thanks people,
-b

---

### Post by blampars on 2008-06-09
anyone have any other suggestions for me before i decide to reformat/reinstall my system?

i'm at the end of the line as far as patients and i've used every bit of my 2 months of linux experience to get my system back up and running with no luck.

i'm quite baffled that i cant access my drive through either the server cd i have or the xubuntu live cd i made last night. :confused:

---

### Post by hpp3 on 2008-06-10
Wow, that's stumped me...
I can't imagine what you could have done that makes your drive inaccessible like that, especially if you can see everything from the shell...

Sorry, I'm not much help at this point. Hopefully you didn't have anything important saved on that drive.
:(

---

### Post by blampars on 2008-06-10
i fixed my computer this morning! :)

when i had edited my yaboot.conf i had made a .bak copy but i also just commented out my original file and put new stuff in on top.

i have no idea why, but booting from the ubuntu server cd and using rescue option, then entering the busybox shell it would not let me mount my partitions.
what i ended up doing was just pressing enter and going into the normal installation mode. hitting escape to take me to the main installation menu and then detecting/mounting my cdrom from the options in the menu.
i then selected execute a shell from the main menu when that was finished. note that i couldnt get access to my partitions without first using the detect cdrom option first..

from this shell i was able to mount my root partition on /dev/hda3
i edited my yaboot.conf to its original form
chrooted in but couldnt run the ybin -v -C /etc/yaboot.conf because my boot partition (hda2) and proc file system were not mounted.

i wasnt sure how to mount those so that the ybin command could do its thing, so instead i exited chroot back to the busybox shell and mounted hda2

from there i edited the yaboot.conf in that partition back to its original form and saved. exited the shell and selected abort installation. the computer reboots, loads x and here i am on my newly fixed laptop writing this message.

i'm so happy that i didnt have to do a reinstall!
hope this may help anyone who accidentally screws up their yaboot.conf and needs to get things back running again. it only took me 4 days to figure out. :lolflag:

---

### Post by stream303 on 2008-06-10
Congratulations!

I know that jaw-dropping feeling - one of two things happen: I either stand up like a rocket, or push the chair back when my mind is blown. :)

The best part is you have the confidence to optimize the system and restore it if things go wrong.

---

