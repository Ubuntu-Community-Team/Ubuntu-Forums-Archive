---
title: "urgent: mounting ntfs partitions"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by compuboy1010 on 2007-06-19
Hi,

I need to know what is on a particular windows cd. Windows XP won't boot.

How can I mount the partition under the Feisty live CD so I can check what's on it?

---

### Post by finer recliner on 2007-06-19
> **compuboy1010 said:**
>  windows cd

did you mean cd or partition on your harddrive?

if it was the latter, try this link:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
(this will mount windows as read-only)

---

### Post by compuboy1010 on 2007-06-19
Yes, I want to mount the Win XP boot partition.

Isn't there an easier way?

I did just as the example said and now it is telling me that the added line in the fstab was bad.

In my case it was /dev/sda1

I want to mout it temporarily under the live cd just to see whats on there and if I can delete that partition safely.

Is there a quick and dirty way?

---

### Post by gn2 on 2007-06-19
> **compuboy1010 said:**
> 

Is there a quick and dirty way?

Don't know about dirty, but you could try using the NTFS auto-mounter available through Automatix.

[www.getautomatix.com](www.getautomatix.com) Once you've got Automatix installed the NTFS auto-mounter is listed in the "Miscellaneous" category. It will automatically mount your NTFS partition, and make it writeable.
Which is useful.

There are risks associated with using Automatix (apparently) but then again there are risks with everything in life.

You may well be struck by lightning or run over by a car, or have an engine fall off a 747 and crash through your roof, or be trampled by a herd of elephants or abducted by aliens.

Automatix just works. (not sure about under a live CD though...)

---

### Post by neo.patrix on 2007-06-19
Do you need to write something to ntfs partition or just copy something from WinXP to Ubuntu?

If you are using Fiesty, just try from top left of you desktop Places-->Computer. If everything is alright with your ntfs partition it should be visible.  Just click on required drive, and it has work.
The ntfs partition will be mounted as read-only.

For mounting as read- write you will need to install few things, and procedure is bit different. If you need that , I will have to lookup certain things.

---

### Post by defrex on 2007-06-19
Yes.
```
mkdir /media/winxp
mount /dev/sda1 /media/winxp
```

This is assuming your windows partition is /dev/sda1.

---

### Post by bigboy_pdb on 2007-06-19
I'm not too certain about what you're trying to do.

It sounds as though you want to boot Windows XP in order to check the information that is on a CD. If this is the case then I don't think that you need to use windows to do this. CDs have their own specification and format, meaning that the disc that you have should be readable by Linux (mind you any information can be written to and read from a disc so it might be possible that you have a Windows program that can read the disc that isn't available in Linux).

If you want to check the contents of the partition that you installed Windows XP to then you can open a terminal (by going to 'Applications'->'Accessories'->'Terminal'), and type **[edit]**'sudo mkdir /mnt/windows'**[/edit]** to make a new folder that will be a mounting point for your Windows XP partition, and then type 'sudo mount -r /dev/sda1 /mnt/windows' to mount the first partition on your first hard drive (which should be where your Windows XP partition is) as read-only (since linux doesn't properly support writing to ntfs partitions) as the root user. The contents of your windows partition should now be visible under the folder '/mnt/windows'. If you find that this doesn't work and you have more than one hard drive, it might be the case that you installed Windows on another hard drive, meaning you would need to replace '/dev/sda1' with the device for that hard drive partition.

If you are trying to boot from windows then there may be a problem with either the Master Boot Record or with some of your files that are needed to start windows. Doing a search in a search engine (such as Google) using terms like 'fix', 'XP', 'MBR', and other similar terms should help you to find more information on this fixing these problems (I would give you more information but I don't know enough about the files that are required for starting Windows or the master boot record to help you with those problems).

---

