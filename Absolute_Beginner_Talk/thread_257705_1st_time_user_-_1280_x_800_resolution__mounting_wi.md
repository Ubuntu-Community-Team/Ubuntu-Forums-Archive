---
title: "1st time user - 1280 x 800 resolution / mounting windows volume"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by MartyNg on 2006-09-14
I'm trying out linux for the first time via Ubuntu 6.06 Live CD. It seems to work well with my Dell Inspiron 700m laptop, except that I can't get the correct resolution of 1280 x 800, so everything is blurry. Is this a resolution that is not supported? Or perhaps I have to actually install Ubunutu to my hard drive, and then update drivers or something?

Also, I can't seem to get to my hard drive using the Live CD. I can see it there, but when I double-click it, I get a mounting error, saying the drive is not removable. Not quite sure what that means though. 

Any suggestions? Thanks for any help! I'm excited at the possibility of breaking the Micro$oft chains! :)

---

### Post by confused57 on 2006-09-14
You could try opening a terminal(Applications---Accessories---Terminal), enter:
```
sudo dpkg-reconfigure xserver-xorg
```

At the first screen, select "no" for autodetect your video settings, then go with the default for everything else...except choose 1280 X 800 as a resolution to use(you can select with the spacebar)...if you know your video controller, you can select the appropriate driver, e.g. "nv" for nvidia, "ati" for ATI, etc...you might want to start with the "vesa" driver, which is a generic driver that works OK.  Installing the correct drive will better enable you to get 1280 X 800 to display properly.

You may want to read over this link first:
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)


To determine your Windows  partition or the partition you want to mount, you can open a terminal, enter:
```
sudo fdisk -l
```
The -l is a lowercase "L".

You should be able to mount your Windows XP partition with:
sudo mkdir /media/windows

Then type:
sudo mount /dev/hda1 /media/windows -t ntfs -o nls=utf8,umask=0222
If you have SATA, it'd be /dev/sda1...
For a FAT partition, it's:
sudo mount /dev/hda1 -t vfat /media/windows
To unmount:
sudo umount /media/windows

The above mounting instructions for ntfs are read-only...don't try to write anything from Linux to a ntfs partition, Linux does not natively support writing to ntfs.

This link describes how to mount Windows better than I did above:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop)

If you're totally new to Linux, I know all of this is pretty overwhelming..I've been there, done that...my first experience with Linux was back in December and there was definitely a steep learning curve for me...and I couldn't have done it without all the help I've gotten in this forum, so don't hesitate to ask questions, things will start to come together the more you use the OS.

---

### Post by Skia_42 on 2006-09-14
You can manually edit your graphics settings using this command:
> sudo nano /etc/X11/xorg.conf
Find the line that specifies screen resolution and change it.

---

### Post by MartyNg on 2006-09-15
Great! Thanks for the suggestions. I'll give these a whirl next time I boot up Ubuntu!

---

### Post by MartyNg on 2006-09-16
That's kind of scary that I can corrupt my NTFS file system. Is there a way to mount the drive as read-only so I don't have this option? I would think this is a common request from Windows users that are trying to see if their files are truly readable from Linux.

Thanks!

---

### Post by confused57 on 2006-09-16
> **MartyNg said:**
> That's kind of scary that I can corrupt my NTFS file system. Is there a way to mount the drive as read-only so I don't have this option? I would think this is a common request from Windows users that are trying to see if their files are truly readable from Linux.

Thanks!

Read over the link I provided for mounting ntfs, I'm just a rookie myself...I believe the mounting instructions are  read-only.  I mainly wanted you to be aware of trying to write to ntfs from Linux.

---

