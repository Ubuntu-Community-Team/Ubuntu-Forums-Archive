---
title: "Need help to recover Jaunty PPC system."
date: 2009-10-24
forum: Apple Hardware Users
---

### Post by casbahdk on 2009-10-24
I need help backing up my /home partition to an external hard disk and repairing the system on my G5. I installed gok, which froze my Ubuntu 9.04 PPC64 system. The first couple of times I rebooted, everything seemed to be OK, but now my computer appears to freeze while booting. The system never gets past the splash screen.

My computer is at this time sitting, having booted from the Ubuntu 9.04 PPC live CD. I don't know how to move on to backing up and repairing the system as I have never done this before. Any ideas where to go from here?

---

### Post by albandy on 2009-10-24
type this in a terminal of a live session and paste the results here:
sudo fdisk /dev/sda -l

---

### Post by casbahdk on 2009-10-24
Thanks for the quick reply.

```
$ sudo fdisk /dev/sda -l
/dev/sda
        #                    type name                  length   base      ( size )  system
/dev/sda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/sda2         Apple_Bootstrap untitled                1954 @ 64        (977.0k)  NewWorld bootblock
/dev/sda3         Apple_UNIX_SVR2 untitled            13671876 @ 2018      (  6.5G)  Linux native
/dev/sda4         Apple_UNIX_SVR2 swap                 5900391 @ 13673894  (  2.8G)  Linux swap
/dev/sda5         Apple_UNIX_SVR2 untitled           957198883 @ 19574285  (456.4G)  Linux native

Block size=512, Number of Blocks=976773168
DeviceType=0x0, DeviceId=0x0

```

---

### Post by tiresia on 2009-10-24
Your /home partition should be /dev/sda5. To backup it, first mount it and then copy it. If you booted your g5 from an Ubuntu live CD, just select with your mouse your partition in Places. Ubuntu will mount it on /media, and you will find an icon on your Desktop.

---

### Post by casbahdk on 2009-10-24
> **tiresia said:**
> Your /home partition should be /dev/sda5. To backup it, first mount it and then copy it. If you booted your g5 from an Ubuntu live CD, just select with your mouse your partition in Places. Ubuntu will mount it on /media, and you will find an icon on your Desktop.

OK, I mounted my /home partition and the external drive. Do I just drag and drop my home folder or do I use cp '/media/disk/username' ? What about permissions? How do I find out what my external firewire drive is listed as?

---

### Post by albandy on 2009-10-24
> **casbahdk said:**
> OK, I mounted my /home partition and the external drive. Do I just drag and drop my home folder or do I use cp '/media/disk/username' ? What about permissions? How do I find out what my external firewire drive is listed as?

If your firewire drive is recognized should be listed in the places menu.

The best way to backup a linux filesystem is using tar.

For example:

open a terminal
cd /homepartitionmountpoint

sudo tar zcvf /myfirewiredrivemountpoint/backup.tgz ./

it will create a file called backup.tgz in your firewire drive.

---

### Post by casbahdk on 2009-10-24
Yes, the Firewire drive is in "places" and I have mounted it. I can't figure out what the mount point for the drive is.

---

### Post by albandy on 2009-10-24
> **casbahdk said:**
> Yes, the Firewire drive is in "places" and I have mounted it. I can't figure out what the mount point for the drive is.

ok. 
First click on the drive to open it
then open a terminal and type mount
paste the results.

---

### Post by casbahdk on 2009-10-24
> **albandy said:**
> ok. 
First click on the drive to open it
then open a terminal and type mount
paste the results.

```
$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/hda on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda5 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
```

OK, so I guess this means that I cd to /dev/sda5/home/username ???

Then I need to do a sudo tar zcvf /dev/sdb1/backup.tgz ./ ??? Will this also backup all of the hidden files in my home directory? Then I need to reformat the hard drive on my G5, do a clean install - and then how do I restore my home folder? Do I boot from the live cd or from the newly installed system on my G5, to restore my home directory?

---

### Post by albandy on 2009-10-24
> **casbahdk said:**
> ```
$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/hda on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda5 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
```

OK, so I guess this means that I cd to /dev/sda5/home/username ???

Then I need to do a sudo tar zcvf /dev/sdb1/backup.tgz ./ ??? Will this also backup all of the hidden files in my home directory? Then I need to reformat the hard drive on my G5, do a clean install - and then how do I restore my home folder? Do I boot from the live cd or from the newly installed system on my G5, to restore my home directory?


Now let's go to know what contents are in /media/disk, type ls /media/disk in the console and paste it.

---

### Post by casbahdk on 2009-10-24
```
username  lost+found
```

---

### Post by tiresia on 2009-10-24
The Ubuntu Live CD will mount every disks on /media. Therefore after you left-click with your mouse on the icons under Places, you will find any disk/partition on /media.
Just copy any files you need. If you want to copy also hidden files, press in Nautilus (File Browser) ctrl-H

---

### Post by casbahdk on 2009-10-24
I tried the following:

```
$ sudo tar -cf/media/disk-1/backup.tgz ./
tar: ./.beagle/socket: socket ignored
```

Just dragging and dropping files gives me warnings about not having the proper permissions to copy some of the folders.

---

### Post by casbahdk on 2009-10-24
Actually, I can't drag and drop any folders without this error message.

---

### Post by casbahdk on 2009-10-24
Interesting. Some of the hidden folders look like they have the wrong permissions. Is it possible to repair an Ubuntu PPC64 system? That may be the only thing that needs to be done.

---

### Post by tiresia on 2009-10-24
If you have permission problems, start nautilus from the terminal with this command```
gksu nautilus
```

---

### Post by casbahdk on 2009-10-24
Hehe, thanks, but there are also a couple of thousand files. How do I correct the permissions for that many files in a home directory, from a live cd?

---

### Post by tiresia on 2009-10-24
You don't need to change permissions right now. You will need it later, when you copy back to the new installed system. To change permissions or better owner you can use the command 'chown'. See how it works with 'man chown'
An example for a file on your Desktop, if you want to make the user 'casbahdk' the owner of the file```
sudo chown casbahdk Desktop/name_of_the_file
``` If you want to change the owner of a folder (directory) instead of a file```
sudo chown -R casbahdk Desktop/name_of_the_folder
```

---

### Post by casbahdk on 2009-10-24
Cheers. I assume that when the owner of a folder is changed, then the files and folders residing inside will also  change?

OK, so your assumption is that it is best for me to reformat the drive and install a new system, rather than try to repair the system?

---

### Post by tiresia on 2009-10-24
> **casbahdk said:**
> Cheers. I assume that when the owner of a folder is changed, then the files and folders residing inside will also  change?
Yes, but have a look on that command and in general on permissions in Linux (there is more than just a owner...)

> **casbahdk said:**
> OK, so your assumption is that it is best for me to reformat the drive and install a new system, rather than try to repair the system? It depends, what happened, how much time you have to spend and how many files you need to back up. If you are not so experienced, maybe it's easier to make a new install, and it takes not more than 20 minutes

---

### Post by casbahdk on 2009-10-24
> **tiresia said:**
> Yes, but have a look on that command and in general on permissions in Linux (there is more than just a owner...)

I am having a difficult time wrapping my head around permissions. I understand that there are both a group and a user, but exactly what sets these various permissions... well. I have looked at some man pages and other documentation, but it still doesn't make much sense. 

> It depends, what happened, how much time you have to spend and how many files you need to back up. If you are not so experienced, maybe it's easier to make a new install, and it takes not more than 20 minutes


I just installed gok, ran it, then the system froze and would not respond at all. I had to do a hard restart. The system seemed to be OK, but after around four restarts, the system started getting wobbly and couldn't get past the splash screen.

This is a PPC64 system, so passing arguments to GRUB doesn't work :(

---

### Post by tiresia on 2009-10-25
There are many web-sites about Linux, where you can find all infos you need. You can have a look here [http://www.tldp.org](http://www.tldp.org)
If you want a general overlook you could read 'Introduction to Linux' of Machtelt Garrels to download here [http://www.tldp.org/guides.html](http://www.tldp.org/guides.html)

About your problem, you can try following. When you boot your G5, you get the splash screen. Can you switch again to the first console (ctrl-alt-F1)? Can you login there as normal user?
Second option. At the yaboot prompt, hit TAB. There you can see the different Kernels you can boot from. One must be 'Linux' Try to give to yaboot the option: Linux nosplash. The System should boot without splash screen so you can see what happens when the system boot

---

### Post by casbahdk on 2009-10-25
Wow. That made a difference. As long as there are no Nvidia drivers for Ubuntu PPC64, the best thing to do would be to block that splash screen from loading, so that it is possible to see what is going on.

It turns out that the system was trying to check /dev/sda5 It had been run 28 times without being checked. Another reboot reported that both /dev/sda3 and /dev/sda5 are clean. So when I thought the system had frozen, it must have just been checking the file system.

---

