---
title: "Mounting external USB Drives - what worked for me"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by Gary.M on 2007-07-21
I see plenty of people having trouble with this.

I have an external USB drive with a NTFS partition on it. I don't want to change the file format.

After a bit of playing I found if I installed ntfs-3g and added the following to my /etc/fstab file
This mounts the volume I call data to a location called USB/data in my home folder. The volume also appears on my desktop.

You will need to substitute /dev/sdc2 and the user name etc with whatever you have on your system

I now have full read/write access

# USB DATA VOLUME
/dev/sdc2 /home/gary/USB/data ntfs-3g defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 0

(edit, for some reason when I view this in the forum the nouser appears as n ouser, I hope if you cut and paste this doesn't happen)

---

### Post by GMachine_24 on 2007-07-22
hey - thanks a lot. i'd all but given up getting my usb external hard drives to work with linux.

good job.

gm

---

### Post by tombayo on 2007-07-26
> **Gary.M said:**
> I see plenty of people having trouble with this.

I have an external USB drive with a NTFS partition on it. I don't want to change the file format.

After a bit of playing I found if I installed ntfs-3g and added the following to my /etc/fstab file
This mounts the volume I call data to a location called USB/data in my home folder. The volume also appears on my desktop.

You will need to substitute /dev/sdc2 and the user name etc with whatever you have on your system

I now have full read/write access

# USB DATA VOLUME
/dev/sdc2 /home/gary/USB/data ntfs-3g defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 0

(edit, for some reason when I view this in the forum the nouser appears as n ouser, I hope if you cut and paste this doesn't happen)


Looks cool, but I don't know what to put instead of:
/dev/sdc2

---

### Post by ghandi69_ on 2007-07-26
> **tombayo said:**
> Looks cool, but I don't know what to put instead of:
/dev/sdc2

Ok, in order to mount something, it first has to be detected by the system.  When it is detected by the system, it shows up in your /dev directory I believe..  here are some commn things in there, to the best of my memory

hda/hdb/hda1       <<< IDE based hard drives
CDRW/DVDRW   <<<Disk drives
Sda/Sdb/               <<<Sata based hard drives...

I'm not at my computer to look here, but you will have to look through that directory, and see if you can figure it out...

You might want to look for some commands where you can do like a {command} sdb, which might output some specific information about that device.

So, when he said you need to substitute /dev/sdc2 to /dev/whatever your device shows up as in that directory.

Hope that can get you started.

---

### Post by tombayo on 2007-07-26
> **ghandi69_ said:**
> Ok, in order to mount something, it first has to be detected by the system.  When it is detected by the system, it shows up in your /dev directory I believe..  here are some commn things in there, to the best of my memory

hda/hdb/hda1       <<< IDE based hard drives
CDRW/DVDRW   <<<Disk drives
Sda/Sdb/               <<<Sata based hard drives...

I'm not at my computer to look here, but you will have to look through that directory, and see if you can figure it out...

You might want to look for some commands where you can do like a {command} sdb, which might output some specific information about that device.

So, when he said you need to substitute /dev/sdc2 to /dev/whatever your device shows up as in that directory.

Hope that can get you started.

Thanks.. by using
```
sudo fdisk -l
```
I get the path :)
But nothing happends when I reboot my computer after changing the fstab file..

---

### Post by dannyboy79 on 2007-07-26
feisty automatically mounts external devices read/write without having to install ntfs-3g. unless it's just my feisty that it works for but I doubt it.

---

### Post by tombayo on 2007-07-26
> **dannyboy79 said:**
> feisty automatically mounts external devices read/write without having to install ntfs-3g. unless it's just my feisty that it works for but I doubt it.

Sorry but no, it seems like external devices with NTFS formatting DO get mounted automaticly, but it does not allow you to write to it..
Atleast that was my problem, after replugging the device, nothing happend at all..
Read somewhere that I need to run a scandisk on windows on the device.. doubt that is going to help, but I'll give it a shot..

---

### Post by dannyboy79 on 2007-07-26
it's because you didn't properly "eject" the usb device before you unplugged it so the NTFS journal is screwed up and Ubuntu can't fix that for you. SO you need to simply plug it into a windows box and use the little icon in the lower right corner to "eject safely" first. then it should work fine in Feisty. I just plugged in a 500gb Seagate last night and it got auto mounted with rw capability and I transferred my entire mythtv recordings (over 200gb) so I know it works rw without installing NTFS-3G.

---

### Post by Neovos on 2007-10-31
I posted a similar question a couple days ago and found a solution. Check it out and see if it helps at all. 

[http://ubuntuforums.org/showthread.php?t=590784](http://ubuntuforums.org/showthread.php?t=590784)

My problem was that it auto-mounted fine, but I couldn't read/write. The solution was in the default ntfs-3g mount options.

Using fstab for external drives doesn't work because fstab I *think* is used at boot time and assumes the drives are always connected. USB drives are obviously not.

---

