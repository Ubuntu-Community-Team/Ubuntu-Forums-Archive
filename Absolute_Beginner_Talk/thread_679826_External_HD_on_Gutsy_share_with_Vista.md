---
title: "External HD on Gutsy share with Vista"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by daytimer045 on 2008-01-27
Okay, got SAMBA working after hitting myself over the head with it for a week.  I can now successfully access the external HD plugged into the Gutsy box from my Vista machine

..but only after ....

I have logged into GNOME from the Ubuntu box

Otherwise, Vista won't let me in giving me Error code: 0x80070035 The network path was not found.  Interestingly the share name does appear in Vista as "EXHD1" but gives this error after accessing it.

I thought it might be permissions, so I:
sudo chmod -R 777 /media/EXHD1 (my external HD)

This didn't help.

It seems that the GNOME desktop does something to the permissions or the sharing that let's Vista in.  I really don't want to use my Gutsy box directly at all.  (Want to use it as a file and print server)  So logging in after restart is not ideal.

Could it be Ubuntu permissions, Vista permissions, my smb.conf file...or what?

Thanks a lot for assistance.  Without this the Ubuntu adventure will have been a loss!

Attached is my smb.conf file if it provides any insight:

[global]
        workgroup = MSHOME
        netbios name = birch
        security = SHARE
        auth methods = guest
        domain master = No
        wins support = no

[PG]
        comment = My Home
        path = /home/pg
        read only = No
        guest ok = Yes

available = no
browsable = no
public = no
writable = no

[EXHD1]
        comment = External HD
        path = /media/EXHD1
        read only = No
        guest ok = Yes

available = yes
browsable = yes
public = yes
writable = no

---

### Post by blueridgedog on 2008-01-27
Your /etc/fstab is mounting this as /media/EXHD1, which is a user mount (note the "media" location).  As such, it is not mounted until you log in (therefore you have the ability to mount it and unmount it).

If you want to resolve the problem, you can edit /etc/fstab to automount the volume.  If you post your /etc/fstab, I can make a suggestion for an edit.

---

### Post by daytimer045 on 2008-01-27
Thanks!  This is an angle I had never thought of.  Additional help would be greatly appreciated.

The external HD is a Western Digital 250GB USB drive




# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=7ea4bad8-47a3-45bf-8c5c-ff1dfadd6806 /               ext3    defaults,erro$
# /dev/sda5
UUID=52760ada-5d0a-4b56-905c-7793ab5ae425 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by blueridgedog on 2008-01-27
I don't see it in your fstab (I assume what you posted was the complete file).

Can you post:
```

sudo fdisk -lu

mount
```

---

### Post by daytimer045 on 2008-01-27
Here are the requested outputs.  I don't see my USB HD in here either!  I guess it is only being mounted when I login....?


Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       80325    38957624    19438650    7  HPFS/NTFS
/dev/sda3        38957625    57673349     9357862+  83  Linux
/dev/sda4        57673350    58605119      465885    5  Extended
/dev/sda5        57673413    58605119      465853+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001    7  HPFS/NTFS


mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/EXHD1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

---

### Post by blueridgedog on 2008-01-27
> **daytimer045 said:**
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001    7  HPFS/NTFS


/dev/sdb1 on /media/EXHD1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

So, /dev/sdb is the external drive and sdb1 is the partition that you want mounted when you boot.

First, make a backup of your fstab file:

```
sudo cp /etc/fstab /etc/fstab20080127
```

Then edit your fstab file (note, you can screw things up here, so be mindful of what you are editing and don't touch any existing lines):

```
gksudo gedit /etc/fstab
```

And add a line:

```
/dev/sdb1 /media/EXHD1 fuseblk defaults 0 0
```

However, I would use ntfs-3g rather than fuseblk, but your system is currently using fuseblk, so I included it above.

When you restart, it should be mounted and shared w/o you logging in.

---

### Post by daytimer045 on 2008-01-27
Thanks for that.
 Did as you suggested.  Used both fuseblk and ntfs-3g.  In neither case did it work.  In fact, in both cases the /media/EXHD1 disappeared from the Gutsy box.

The blue light on the drive itself was still on, indicating that there is nothing wrong with USB connection.

Any further suggestions.  I carefully triple-checked for typing errors in the fstab, and I don't think there were any.

Thanks again,

P.S.  How do I "Thank" you.

---

### Post by blueridgedog on 2008-01-27
What was the thing that determined to you that id did not work?  It may no longer put an icon on the desktop, due to it being an fstab mount rather than a user mount.

After a reboot, did you attempt to view the files from a terminal or from nautilus?

You will need to double click "file system" then media then EXHD1.

If it is working from a mount standpoint, you can then put a shortcut on the desktop or in nautilus.

But, if you checked the above, then something else is wrong.  I would like to verify before we start digging deeper.

---

### Post by daytimer045 on 2008-01-27
Using nautilus the /media/EXHD1 folder had completely disappeared.  Indeed it had not mounted the drive.

It is now working as I had hoped.  Here  is how I got it to work:

Installed pysdm Graphical Storage Device Manager
Selected sdb1
Used the assistant to create the options (i.e. did not use defaults)
    Settings as follow:  mount file system in read-only mode
    File system is mounted at boot time
    Umask=000
Then used pysdm to Mount the drive.
Then it reliably remounts on restart before login.

This is what I desired.  

The differences in the fstab file (I checked) produced by pysdm, differ from what you suggested as follows:   ntfs  and not using defaults (rather nls=iso8859-1, umask=000)

Thanks for getting me on the right track on this one, blueridgedog.

It has been solved.

---

### Post by blueridgedog on 2008-01-27
Fantastic, by digging in you jumped through a great deal of the trouble shooting that would have been hard in this "iterative" format.

Good work!

---

### Post by daytimer045 on 2008-04-06
Two months after my problem was solved, I unplugged my external drive from the Gutsy box, to use directly with my Vista machine.  Even though I intended to, I must've not waited until the box shut down before removing the drive.

I went about my business, copying files onto the drive using Vista.

Lo and behold when I returned it to the Gutsy box, it no longer mounted (unless I made it read only, which was useless).

AFter hours of frustration, I discovered that i had to force the mounting in the /etc/fstab because it had been improperly unmounted.  On subsequent remounts force was not necessary.

I add this note for others who may be reading the thread.

In short:  it could be an improper unmounting that is causing your trouble.  Try forcing it (at least once).  And use pysdm.

---

