---
title: "Make USB-harddrive work"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by hanuman1000 on 2007-04-25
I have an USB-harddrive (NTFS) and now I want it to work in Kubuntu Feisty. It doesn't pop up when I plug it in. I have understood that I'm supposed to "mount" it. But how? I'm a newbie working in the Konsole, though I know the HD is called sdb1 (via sudo fdisk -l).

What do I do?

The same problem goes for my digital camera Samsung. Nothing happens when I plug it in either.


best regards,
Hanuman

---

### Post by bobbocanfly on 2007-04-25
I had a similar problem with my hard drive when i first migrated to Linux. 

As far as i know the Linux Kernel doesn't natively support NTFS and some distros refuse to mount it. I think this can be sorted with third party drivers but i'm honestly not sure, i just reformatted my drives to FAT32.

---

### Post by hanuman1000 on 2007-04-25
Yes NTFS is Win XP, but i think that is a later problem, first i have to mount it. I have a package that makes my kubuntu rw a HD in NTFS.

I just need the command lines for mounting a USB-HD, and please for a digital camera...

---

### Post by bobbocanfly on 2007-04-25
Thread on another linux help forum says 

```
mount -t ntfs /dev/<whatever partition its> /mnt/<destination mount point>
```

should work

for example 

```
mount -t ntfs /dev/hda2 /mnt/win_ntfs
```

---

### Post by Gina on 2007-04-25
Make the directory you want to use (eg. win_ntfs above) before using mount.  Otherwise you'll get a dir not found error.

---

### Post by laidback on 2007-04-25
I'm surprised at the problem you mention. My USB hdd mounts automatically in Ubuntu 6.06 and 6.10 and with many other distros. It originally contained just ntfs patitions but now has some ext3 linux partitions as well. I can read my ntfs partitions but not write to them. But I understand that there now is software to do this. 
Have you tried from the top menu..Places>Computer then look for an icon for the usb-hdd, right click and select Mount. If this works it will be a lot less hassle than using a terminal.

---

### Post by Gina on 2007-04-25
Yes, my USB drive(s) mount automatically and show as an icon on the Desktop.  The mount point can be found in the **/media** directory as well  as Desktop and Places menu.

Another thing I've found useful is to right-click in the top panel, choose **Add to panel **and from the pop-up box choose the **Disk Mounter **from the **System & Hardware** group.  Then all the drives and partitions the system finds will be represented by a drive icon and can be mounted or explored from there.

---

### Post by laidback on 2007-04-26
Gina,
Disk Mounter is a nice idea. I have it now as well.

Thanks

---

