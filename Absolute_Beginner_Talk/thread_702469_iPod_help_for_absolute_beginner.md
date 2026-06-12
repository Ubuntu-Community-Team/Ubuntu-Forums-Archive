---
title: "iPod help for absolute beginner"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by tommyrock on 2008-02-20
I'm very new to Linux, and don't know much about how to get in and get dirty with the terminal or editing files, but I would love it if someone could help me out.

I'm trying to connect my 3rd Gen Videoo iPod Nano (the newest one), and to no avail. The USB port is recognized if I plug in an adapter and, say, a memory card. But when I connect my iPod, it just says "Floppy 1," can't be mounted, can't be opened, nothing can be done with it. I know this means I probably have to create a mountpoint for my iPod, but I have no idea how to do that. Also, I don't think I have more than one disk, and I'm not sure if that matters.

Any takers? ANY help would be amazing, just let me know what else I need to let you know.

---

### Post by mkoehler on 2008-02-20
You may end up having to edit your fstab file.  By stating that it cannot be mounted, I presume that you've already run the command "sudo mount -a" to no avail.  In that case, can you post the output of the following command:

```
sudo fdisk -l
```

Thanks.

---

### Post by skyjacker on 2008-02-20
> **tommyrock said:**
> I'm very new to Linux, and don't know much about how to get in and get dirty with the terminal or editing files, but I would love it if someone could help me out.

I'm trying to connect my 3rd Gen Videoo iPod Nano (the newest one), and to no avail. The USB port is recognized if I plug in an adapter and, say, a memory card. But when I connect my iPod, it just says "Floppy 1," can't be mounted, can't be opened, nothing can be done with it. I know this means I probably have to create a mountpoint for my iPod, but I have no idea how to do that. Also, I don't think I have more than one disk, and I'm not sure if that matters.

Any takers? ANY help would be amazing, just let me know what else I need to let you know.
See if this link will help you.[http://ubuntuforums.org/showthread.php?t=85489](http://ubuntuforums.org/showthread.php?t=85489)   BTW, I have found a great deal of help by searching the "make new post" items that pop up after you hit "enter" when making a post. (type in ipod nano ask a short question about it, hit enter. Scroll dowm, and there should be posts that are similar if this subject has ever been asked). Hope this helps...

---

### Post by tommyrock on 2008-02-20
Code:
tomas@tomas-laptop:~$ sudo mount -a /media/ipod
mount: can't find /media/ipod in /etc/fstab or /etc/mtab
tomas@tomas-laptop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x818c818c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris


I've been reading this long "How to fstab" post, but am kind of swimming in it.

---

### Post by major_rocks on 2008-02-20
or you could.....

```
sudo apt-get install gtkpod
```

or for video capability
```

sudo apt-get install gtkpod-aac
```

---

### Post by tommyrock on 2008-02-20
I actually have gtkpod. When I try to load the iPod it says I have to create the directory structure. When I attempt to do that, there is no mountpoint aside from the "Floppy 1" I mentioned before, and that won't let me mount to it.

---

### Post by major_rocks on 2008-02-20
ok, i haven't had to edit an fstab in awhile since using Ubuntu regularly, a typical fstab edit would look something like.....

to open fstab...
```
sudo gedit /etc/fstab
```

> /dev/sda1 /media/ipod vfat rw,users,umask=000, auto 0 0

now /dev/sda1 is arbitrary seeing we dont know what your ipod is trying to mount as, /media/ipod is where the filesystem will be mounted, (you will need to create the"ipod" folder in /media)

```
sudo mkdir /media/ipod
```

vfat represents the file system on the ipod..which should be fat32 i believe8-[ 

hopefully some of this will help.....keep workin !!

---

