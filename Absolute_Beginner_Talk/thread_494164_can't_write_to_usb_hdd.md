---
title: "can't write to usb hdd"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Ripfox on 2007-07-06
I just want to wipe it out and format it with fat32 so i can use it on both windows and ubuntu. I searched and all I can't seem to understand. Any help here?

Peace

---

### Post by twiceasworn on 2007-07-06
I cant remember if you are able to do this, but I am pretty sure you can.  You should just be able to right click the icon for the thumbdrive and select format (similar to how you would do it in windows).

---

### Post by tartarian on 2007-07-06
I'm not sure about actually doing it, but before you format it as fat32 check out.....
[http://www.fs-driver.org/]("http://www.fs-driver.org/")
Means you can format it as the native linux type and windows can read/write from it

---

### Post by Ripfox on 2007-07-06
Nah I know it's more complicated than that, but thanks for the quick reply...

---

### Post by Ripfox on 2007-07-06
Fat 32 is  what I want b/c it's for sure compatible

---

### Post by Ripfox on 2007-07-06
> **tartarian said:**
> I'm not sure about actually doing it, but before you format it as fat32 check out.....
[http://www.fs-driver.org/]("http://www.fs-driver.org/")
Means you can format it as the native linux type and windows can read/write from it

Actually I have used that software and it works great. :p

---

### Post by avik on 2007-07-06
Did you install gparted?

```
sudo apt-get install gparted
```

You'll find it in System->Administration as GNOME Partition Editor.  Make sure the HDD in question is not mounted, then right click and format it to FAT32.

And you're right, a USB HDD that you'll be transferring between OSes and possibly different computers should be FAT32.  It's always compatible.

---

### Post by shrift on 2007-07-06
You can do this in Ubuntu with the application called "gparted". If it is not already, install it, and launch it. gparted requires root access, so you need to launch it with "sudo gparted". Once launched find your device in the drop down list. If you don't know which device yours is, unplug it and plug it back in, type dmesg in a terminal and look at the bottom to see what device Ubuntu assigned it. That's the device you want to use in gparted. Gparted from there should be fairly straightforward.

Another good way to do this is simply create the partition in windows.

---

### Post by shrift on 2007-07-06
> **avik said:**
> Did you install gparted?

```
sudo apt-get install gparted
```

You'll find it in System->Administration as GNOME Partition Editor.  Make sure the HDD in question is not mounted, then right click and format it to FAT32.

And you're right, a USB HDD that you'll be transferring between OSes and possibly different computers should be FAT32.  It's always compatible.

Ha, : ) Great minds think alike.

---

### Post by Ripfox on 2007-07-06
mkfs.ext3 -j /dev/sdb

I got an ext3 with this command.

I didn't know you had to unmount the drive to use gparted. That explains it, as I have had gparted on my system from a long time ago, but was unable to make it work.

Thanks guys for all the help!!

---

### Post by avik on 2007-07-06
> **ripfox said:**
> I didn't know you had to unmount the drive to use gparted. That explains it, as I have had gparted on my system from a long time ago, but was unable to make it work.

You don't need to unmount a drive to *use* gparted, just to format that drive, resize partitions, etc.  You can go into gparted and unmount a drive from there (right click and click unmount).

---

### Post by Ripfox on 2007-07-07
Good info as well...don't know how I missed that...

---

