---
title: "How can I view/edit/copy contents from the windows HD partition? (Solved)"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by superskiaholic on 2006-11-07
I'm very new to Ubuntu, or Linux in general for that matter.  I just downloaded 'ubuntu 6.06 desktop i386' to try it out on my Windows desktop.  I booted from the CD and it (impressively) recognized my USB key and I had full read/write/copy privileges.  Very cool. I would like to view/edit/copy files on the internal hard drive... is that possible? It shows up in the Computer File Browser, as "116 GB Volume", but when I open it, an error message pops up indicating that it is "unable to mount the selected volume".

Any thoughts or suggestions would be greatly appreciated.

---

### Post by aysiu on 2006-11-07
You won't be able to edit files if it's NTFS, but you can certainly view or copy them.

Open a [terminal](http://www.psychocats.net/ubuntu/terminal) and paste this command in: ```
sudo fdisk -l
``` Make note of the location and filesystem. Let's assume, for this example, it's /dev/hda1 and NTFS.

Make a mount point: ```
sudo mkdir /media/windows
``` Mount your Windows drive there: ```
sudo mount -t ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222
``` Now, you should be able to see and copy all your Windows files from the /media/windows folder.

If it's /dev/hda2 or /dev/sda1 or something else, just substitute in the appropriate location for /dev/hda1. If it's FAT32, substitute in ```
sudo mount -t vfat /dev/hda1 /media/windows -o iocharset=utf8,umask=000
``` for ```
sudo mount -t ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222
``` If the command-line scares you, don't use Ubuntu. You're better off with Mepis, which has for over two years had the ability (with the correct permissions) to mount partitions with a single click.

Ubuntu's getting there...

---

### Post by fasoulas on 2006-11-07
> **aysiu said:**
> You won't be able to edit files if it's NTFS, but you can certainly view or copy them.

Open a [terminal](http://www.psychocats.net/ubuntu/terminal) and paste this command in: ```
sudo fdisk -l
``` Make note of the location and filesystem. Let's assume, for this example, it's /dev/hda1 and NTFS.

Make a mount point: ```
sudo mkdir /media/windows
``` Mount your Windows drive there: ```
sudo mount -t ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222
``` Now, you should be able to see and copy all your Windows files from the /media/windows folder.

If it's /dev/hda2 or /dev/sda1 or something else, just substitute in the appropriate location for /dev/hda1. If it's FAT32, substitute in ```
sudo mount -t vfat /dev/hda1 /media/windows -o iocharset=utf8,umask=000
``` for ```
sudo mount -t ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222
``` If the command-line scares you, don't use Ubuntu. You're better off with Mepis, which has for over two years had the ability (with the correct permissions) to mount partitions with a single click.

Ubuntu's getting there...

Thnx man i was lookin for a way to access MS folders since i installed ubuntu:p

---

### Post by superskiaholic on 2006-11-07
Yeah thanks! That seems to have worked great!

---

### Post by jkvv_1973 on 2006-11-07
thanks this worked for me too >>>aysiu

---

### Post by Whatever6750 on 2006-11-08
Ah thanks just what I was looking for.

---

### Post by holepunch on 2006-11-10
Thank's a lot for that info, I followed it and it worked a treat.  I've got one simple question, how do I create a shortcut to 'My Documents' on Windows and put it on my Ubuntu Desktop?  I found the folder and tried right clicking to create a link but it wouldn't let me.

---

### Post by benjjo on 2007-01-01
Very helpful, thankyou.

---

### Post by shareMenaPeace on 2007-01-01
Hello,
what is the diffrence between this topic soultion and
HOWTO: NTFS with read/write support using the ntfs-3g (easy & safe method) / [http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+read+write](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+read+write)

And is there another way to auto mount from boot beside fstab entry?

---

### Post by tyler_roach on 2007-01-12
This works great, but is there any way i can automatically mount the partition every time i log on?

---

### Post by aysiu on 2007-01-12
> **tyler_roach said:**
> This works great, but is there any way i can automatically mount the partition every time i log on?
Yes.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

