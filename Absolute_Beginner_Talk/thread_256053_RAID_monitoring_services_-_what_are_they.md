---
title: "RAID monitoring services - what are they?"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by Village on 2006-09-12
I'm a bit confused,

This appeared during my (re)install;

RAID monitoring services – failed

 as I was restarting the machine for the first time.
What does it mean? And what is RAID anyway?

Thank you,

Village

---

### Post by mike3k on 2006-09-12
RAID is two or more drives made to work as a single device. 

Two common varieties are RAID 0 where the the two are made to appear as a drive the total of the drive sizes added together and RAID 1 which mirrors two or more drives, which must be the same size. It will appear to be the size of one drive but data will be written to both drives at the same time.

Use the mdadm command to configure and manage RAID devices, which will appear as /dev/md*. You can check the RAID status at /proc/mdstat:

```
[mike@blackbox: ~]$ cat /proc/mdstat 
Personalities : [raid1] 
md0 : active raid1 hda1[0] hdb1[1]
      312568576 blocks [2/2] [UU]
      
unused devices: <none>

```

I'm using RAID 1 for /home on my server for safety. With a RAID 1 setup, if one drive fails you can still keep running with the other drive with no loss of data.

---

### Post by Metacarpal on 2006-09-12
Hi Village,

If you're running a normal desktop or notebook computer, odds are that you don't have to worry about RAID.  During boot and shutdown, my computer also checks for / tries to stop RAID services, even though I don't have any RAID devices in, on, or anywhere remotely near my laptop.

It's part of the boot/shutdown sequence that I haven't yet figured out how to get rid of.  But it's nothing to worry about.

---

### Post by Village on 2006-09-15
Thanks for that, I'm running it on an ever ageing notebook, which to be honest I don't think it can cope with ubuntu. 

Thanks,

Village

---

### Post by Metacarpal on 2006-09-15
Hi Village,

If your comp is having trouble running the Ubuntu/Gnome desktop, try [Xubuntu]("http://www.xubuntu.org") - it runs the xfce desktop environment which is a LOT lighter weight.

If you have a bit of free space in your / directory, you can even put it on without having to do a clean install.  Just open a terminal (Applications > Accessories > Terminal) and type:

```
sudo aptitude install xubuntu-desktop
```

If you like it better, and your machine runs well on it, [here's a page]("http://www.psychocats.net/ubuntu/purexfce") with instructions for removing Gnome from the machine, leaving xfce intact.

Take note, however: the current version of xfce doesn't have a trash can, so what you delete is gone forever(ish).  The next release (6.10/EdgyEft) will have a new version of xfce with trash support.

---

### Post by Village on 2006-09-16
hmm seems like an idea.

To be honest the reason I tried Ubuntu on my old Laptop was to see if I like Liunx/Ubuntu as I'm getting more and more fed up with Windows. 

Trouble is I don't think I'm ready to take the total plunge just yet, as I've got to many things plugged into my Windows computer to justify leaving it, I guess I could do a dual install but then that's just getting complicated and would mean having compatibility problems between saved files. 
Still I was just getting my feet wet. 

Thanks for you advice I'll give it ago. 

Village

---

### Post by abstractcoder on 2007-12-23
[QUOTE=mike3k;1491034]RAID is two or more drives made to work as a single device. 

Two common varieties are RAID 0 where the the two are made to appear as a drive the total of the drive sizes added together and RAID 1 which mirrors two or more drives, which must be the same size. It will appear to be the size of one drive but data will be written to both drives at the same time.

Use the mdadm command to configure and manage RAID devices, which will appear as /dev/md*. You can check the RAID status at /proc/mdstat:

```
[mike@blackbox: ~]$ cat /proc/mdstat 
Personalities : [raid1] 
md0 : active raid1 hda1[0] hdb1[1]
      312568576 blocks [2/2] [UU]
      
unused devices: <none>

```


When I did that command, I got the follow output:

Personalities :
unused devices: <none>


I get the same error during reboot/shutdown "Stopping raid monitor service failed", but since I got that output from that command -- does this mean I don't use RAID Devices? I've been meaning to disable/remove that part from the boot process.

---

