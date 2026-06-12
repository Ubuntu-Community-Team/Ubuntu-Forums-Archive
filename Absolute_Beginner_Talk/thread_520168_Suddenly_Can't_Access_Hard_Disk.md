---
title: "Suddenly Can't Access Hard Disk"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by SpikeRazorshards on 2007-08-07
[IMG]http://i30.photobucket.com/albums/c315/SpikeRazorshards/Screenshot-1.png[/IMG]
I don't know why, but now when I click on the icon, that message appears.  I didn't do anything to the hard drive, in fact I don't even use it all that often.  I know it used to work though.  It's not even a year old and it was only a couple months ago that I had a friend format it for me.  He's gone now though.  If necessary, can someone tell me how to reformat it?  
Here are the stats for that drive after doing a **sudo lshw -C disk**.

[INDENT] *-disk:1
       description: SCSI Disk
       product: Maxtor 6L200P0
       vendor: ATA
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: BAJ4
       serial: L41QPXSH
       size: 189GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume
          description: Linux LVM Physical Volume partition
          physical id: 1
          bus info: scsi@0:0.1.0,1
          logical name: /dev/sdb1
          capacity: 189GB
          capabilities: primary bootable multi
[/INDENT]

Thank you.

---

### Post by Rovdjur on 2007-08-07
This is just a simple test, but can you mount as super user?

In terminal:

```
sudo mount /dev/sdb1
```

And have you ever been able to access that drive in Linux? It says it is DOS formatted, so is there and Windows installation on it?

If you want to try reformatting it, you can pop in the gparted live cd and format it as ext3, and it should work just fine.

---

### Post by SpikeRazorshards on 2007-08-08
When I put in that command, I got this: 

[INDENT]mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/INDENT]

To reformat it, if I have to, would I be able to use the same disc I used to install Feisty Fawn?

---

### Post by Rovdjur on 2007-08-08
> **SpikeRazorshards said:**
> When I put in that command, I got this: 

[INDENT]mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/INDENT]

To reformat it, if I have to, would I be able to use the same disc I used to install Feisty Fawn?

Well it is saying that it is the wrong filesystem, and there is the very, very small chance it could be corrupt (could possibly just be something simple to fix like a bad sector).

Have you ever been able to mount this drive in linux, and what is on there right now? Is there another OS of some sort?

And if the information on there is not important to you, you should be able to reformat using the Live CD, because I believe GParted is included. If you can not find GParted, then just download the Live CD version of it [here]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828"). Should be pretty straight-forward using the GUI :)

---

