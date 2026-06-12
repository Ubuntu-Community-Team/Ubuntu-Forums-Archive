---
title: "[SOLVED] Can't mount or view SD minidisc. Worked once."
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by zvilikestv on 2008-03-16
I bought an SD microdisc and MobileMate SD+ Memory Card reader to use with my cellphone. The first time I plugged it into my computer running Gutsy, it worked just fine. I unmounted it properly, stuck it back in my cellphone, and fiddled with it in there a bit.

Then, when I tried to reinsert in my computer, the computer didn't appear to recognize that a drive had been inserted, and I couldn't find an icon or a folder to mount that seemed appropriate. Please tell me what I need to do.

---

### Post by Slipmyknot101 on 2008-03-16
Hi.
Try popping the SD microdisc back into your computer, and open a terminal session and type: > sudo mount -l and post those results.

If you are familiar and/or not afraid of command prompts, take a look at this information and see if you can pick anything useful out of it (btw, this is the same output for you if you opened a terminal session and typed: > mount --help but for reference purposes, I have posted it anyways. See below:
> mount --help
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .Glad to help,
Trevor

---

### Post by niteshifter on 2008-03-16
Hi,

I'm going to assume a couple of things here: That the card functioned correctly in the phone and the external card reader connects via USB (it's a SanDisk MobileMate SD+, correct?)

Before we tear off on troubleshooting mounts, let's see if the card reader works:
Without the card reader connected run this command in a terminal window:
```
lsusb
```
Then connect the card reader (without a card in it) and give the command again.

For reference purposes this is what happens on my system:
> dlk@dlk-lt-1420:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
dlk@dlk-lt-1420:~$ lsusb
Bus 007 Device 002: ID 0781:b4b5 SanDisk Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
dlk@dlk-lt-1420:~$ 

What we're looking for is a difference, like the text on the lines above that begin with "Bus 007 ...". 

No change? It's probably a bad connection with the USB cable (I have a SanDisk ImageMate card reader, standard USB cables won't work without modifying them - the connector on the SanDisk is recessed to deep. SanDisk seems to be fond of proprietary connectors. Works great with the SanDisk supplied cable.)

Next up on the list of probables is it's a dead reader, can you try it with a different computer?

Another possibility - rare, but it does happen - is the computer's internal USB hub has shut that port or shut itself down. Test for this by shutting down Ubuntu (to power off), Start back up and try the reader again.

Let us know what happens.

---

### Post by zvilikestv on 2008-03-16
```
/dev/sda1 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
```

These were the results of running mount -l, whether or not the card was in or out.

```
Bus 002 Device 005: ID 0781:b2b5 SanDisk Corp.
```

This line was added to the output when I ran lsusb with the card reader in, as opposed to when it was not in.

What should I do next?

---

### Post by niteshifter on 2008-03-16
Hello again,

Ok, the cconnection to the reader is intact. Now on to mount issues....

Let's see if automount has become disabled. I'm assuming Ubuntu / Gutsy which normally means the GNOME desktop:

Click on System, then Preferences, then Removable Drive and Media.
These boxes should be checked:

Mount removable drives when hot-plugged.
Mount removable media when inserted.
Browse removable media when inserted.

Check those boxes if they are not - especially the first two.

Did that help?

---

### Post by zvilikestv on 2008-05-12
Oh, in the end, it turned out to be a hardware problem. The cardreader isn't registering the minisdisc slot. I put the minisdisc in the sdisc adapter and it works fine. Weird.

---

