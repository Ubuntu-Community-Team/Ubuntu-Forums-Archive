---
title: "Edit Grub?"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by CocheseUGA on 2007-05-12
I'm new to Linux, but I think I am learning quickly.

I am doing an unusual install of Ubuntu, first of all. I have a laptop with a dead CDROM, so the laptop's HDD (I'll refer to it as Fuji) is in an external enclosure connected to my XP desktop machine via USB. Not having a CDROM has caused me a ton of problems, and I've tried to get around those by installing a distro of Linux.

On my XP machine, I have two other internal HDDs. When I ran the Live CD, it numbered those 0 and 1, and the Fuji HDD as 2.

It installed correctly, but I cannot boot from Fuji. I believe because GRUB refers to it as HDD (2,0) and not (0,0). I think if I can edit this to reflect that, Ubuntu should load correctly through the XP machine, and conversely when I re-install it in the laptop. Problem is, I have no idea how to edit it. I can't do it via the Live CD, because it states the files on the HDD are read-only and I don't have privileges.

I think I need a GRUB Boot Disk for me to edit at the command-line level, but I'm not sure. If all of that made sense, I should be on the right track? Any help would be appreciated. I'd just replace the CDROM, but that's pretty expensive for a machine this old. And before anyone asks, the BIOS for the laptop cannot identify a USB drive or Ethernet.

I would appreciate any input anyone has on the issue.

---

### Post by Happy_Man on 2007-05-12
Yeah, a GRUB disk would be best.

---

### Post by RSingh on 2007-05-12
are you trying to edit grub via 'sudo' or not????

---

### Post by CocheseUGA on 2007-05-13
> **RSingh said:**
> are you trying to edit grub via 'sudo' or not????

No, because I have no idea how to do that, or where to find a boot disk image.

I had thought about wiping the HDD in XP, then reinstalling Ubuntu with my internal HDDs disconnected, but that wouldn't fix the sda issue would it?

---

### Post by psyopper on 2007-05-13
Boot from the Live CD again. Once you are up and running open a terminal (Ubuntu Menu> Accessories> Terminal) and type 

```
sudo gedit
```

This will open gEdit with Super User priveliges allowing you to edit grub. Once you have gEdit open you can do a "File" "Open" and browse to the file you want to edit. The SU account on the live cd does not have a password which comes in very handy for things like this!

---

### Post by confused57 on 2007-05-13
> **CocheseUGA said:**
> I'm new to Linux, but I think I am learning quickly.

I am doing an unusual install of Ubuntu, first of all. I have a laptop with a dead CDROM, so the laptop's HDD (I'll refer to it as Fuji) is in an external enclosure connected to my XP desktop machine via USB. Not having a CDROM has caused me a ton of problems, and I've tried to get around those by installing a distro of Linux.

On my XP machine, I have two other internal HDDs. When I ran the Live CD, it numbered those 0 and 1, and the Fuji HDD as 2.

It installed correctly, but I cannot boot from Fuji. I believe because GRUB refers to it as HDD (2,0) and not (0,0). I think if I can edit this to reflect that, Ubuntu should load correctly through the XP machine, and conversely when I re-install it in the laptop. Problem is, I have no idea how to edit it. I can't do it via the Live CD, because it states the files on the HDD are read-only and I don't have privileges.

I think I need a GRUB Boot Disk for me to edit at the command-line level, but I'm not sure. If all of that made sense, I should be on the right track? Any help would be appreciated. I'd just replace the CDROM, but that's pretty expensive for a machine this old. And before anyone asks, the BIOS for the laptop cannot identify a USB drive or Ethernet.

I would appreciate any input anyone has on the issue.
You can use the live cd to install grub to your (hd2) mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Read the link, but it'll be something like this:
```
sudo grub
find /boot/grub/stage1
```
this should return "root (hd2,x)", then you would:
```
root (hd2,x)
setup (hd2)
quit
```

Then set your bios to boot first to the external drive, you should get a grub boot menu, highlight your Ubuntu entry, press "e", change root from (hd2,x) to (hd0,x), then press "b" to boot...this is temporary, but if it works it can be made permanent.

---

### Post by CocheseUGA on 2007-05-13
> **psyopper said:**
> Boot from the Live CD again. Once you are up and running open a terminal (Ubuntu Menu> Accessories> Terminal) and type 

```
sudo gedit
```

This will open gEdit with Super User priveliges allowing you to edit grub. Once you have gEdit open you can do a "File" "Open" and browse to the file you want to edit. The SU account on the live cd does not have a password which comes in very handy for things like this!


Much appreciated. So I should edit out the 0 and 1 entries, and make the external hda 0,1 correct? That will make it work when I reinstall it in the laptop, unless I'm stupid.

Don't think I'll get to it tonight, but I can taste it...

---

### Post by CocheseUGA on 2007-05-13
Success! Thanks guys, now to get the internet working.

---

