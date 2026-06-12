---
title: "Hard Drive Problems"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by Ninjas On Fire on 2006-11-29
Hey guys, I installed Ubuntu Linux 6.10 Edgy Eft today on my machine, which was currently running Windows XP Pro...

and i have 2 hard drives in my computer, a 250gb HD, which is my main one, and a 160gb HD, which has all my files backed onto it from XP, which i was on the 250gb HD which i formatted

i cannot find how to get into my 160gb HD at all, so can someone please help me solve this problem?

---

### Post by rlozano on 2006-11-29
> **Ninjas On Fire said:**
> Hey guys, I installed Ubuntu Linux 6.10 Edgy Eft today on my machine, which was currently running Windows XP Pro...

and i have 2 hard drives in my computer, a 250gb HD, which is my main one, and a 160gb HD, which has all my files backed onto it from XP, which i was on the 250gb HD which i formatted

i cannot find how to get into my 160gb HD at all, so can someone please help me solve this problem?


i suggest you visit [www.psychocats.net/ubuntu/](www.psychocats.net/ubuntu/). it will help you in mouting your devices.

you can also post teh result of your

    sudo fdisk -l

to determine if the 160gb is there and was detected.

get your fstab as well at /etc/fstab and post it too.... this way we can understand your current situation better.

---

### Post by Ninjas On Fire on 2006-11-29
i am completely beginner to linux and anything besides windows and a little of OSX, so can you translate that into step by step instructions, please

---

### Post by 56phil on 2006-11-29
Welcome to Ubuntu.

[LIST=1]
[*]Open up a terminal: Applications -> Accessories -> Terminal
[*]Type :```
sudo fdisk -l
```
[*]Post the results in this tread. You can use cut and paste.
[/LIST]

---

### Post by rlozano on 2006-11-29
> **Ninjas On Fire said:**
> i am completely beginner to linux and anything besides windows and a little of OSX, so can you translate that into step by step instructions, please

1. to get your fstab content graphically, press alt-f2 then type gksudo gedit /etc/fstab
2. enter password when prompted.
3. copy the content and post it here

for the fdisk
1. open a terminal
2. type sudo fdisk -l
3. copy the result and paste it here.

hope this helps.

---

### Post by Ninjas On Fire on 2006-11-29
-GamingRig:~$ sudo fdisk -l

Disk /dev/hdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       29765   239087331   83  Linux
/dev/hdb2           29766       30515     6024375    5  Extended
/dev/hdb5           29766       30515     6024343+  82  Linux swap / Solaris

Disk /dev/hdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       19928   160071628+   7  HPFS/NTFS


kk thats it

here is the fstab thing

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=ea31f3b0-5e6e-497e-abb0-629c02fd829e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=131b64a1-61c2-4e6c-96e8-d9b9062ecaab none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0



one major note, the 160gb hard drive is in NTFS format...

---

### Post by rlozano on 2006-11-29
your 160Gb HD is there and the device name is hdc1.

now you can try this.
1. from the terminal, type sudo mkdir /media/any-directory-name-you-want
2. enter the password if prompted
3. then in your fstab, add this line:
/dev/hdc1 /any-directory-name-you-want ntfs nls=utf8,umask=0222 0 0

when you restart your PC it, you maybe able to access your 160gb HD then.

or you can issue the command sudo mount -a instead of re-starting your PC.

---

### Post by Ninjas On Fire on 2006-11-29
when i issue the command sudo mount -a i get this message:

mount: mount point /MyDocuments does not exist

yet i followed your first step, and i can see the /media/MyDocuments folder i created

---

### Post by Ninjas On Fire on 2006-11-29
anyone want to help?

---

