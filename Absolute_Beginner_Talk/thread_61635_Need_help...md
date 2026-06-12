---
title: "Need help.."
date: 2005-09-01
forum: Absolute Beginner Talk
---

### Post by DMD on 2005-09-01
Ok so i read a few things on mounting a second hard drive.. I can see it in the Device manager but not in my drive's.. Ive used sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

and
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000... 

Im not to sure what format the drive is in.. But nether give's anything.. Just says that the drive is there.. Then i tryed /dev/hdb.. that says permission denied
the only thing on the drive are music files and pic. files.. If anyone can help me get this drive up and running that would be amazing.. thanks..

Dustin

---

### Post by aysiu on 2005-09-01
[QUOTE=DMD]
Im not to sure what format the drive is in..[/QUOTE] Type *sudo fdisk -l* in a terminal. It'll tell you what format the drive is in.

---

### Post by DMD on 2005-09-01
fdisk -1 shows 1 is invalid.. also used -u and that worked but its only reading 1 hd on the ide chan... But like i said under the D/M. it shows the second h/d

---

### Post by aysiu on 2005-09-01
[QUOTE=DMD]fdisk -1 shows 1 is invalid.. also used -u and that worked but its only reading 1 hd on the ide chan... But like i said under the D/M. it shows the second h/d[/QUOTE] It's a lower-case L, not a one. Did you type *sudo* in front?

Just copy and paste into a terminal what I type below:

sudo fdisk -l

---

### Post by DMD on 2005-09-01
Its is a ntfs.. but when i type in ... sudo mont /dev/hdb /media/windows/ -t ntfs -o nls=utf8,unmask=0222... it says its mounted.. I still only see my system folder on hda

---

### Post by aysiu on 2005-09-01
Open up a terminal and type this

*cd /media/windows*

Then type this

*ls*

What happens?

---

### Post by DMD on 2005-09-01
well nothing.. i type in the cd /media/windows.. then bumps me to the next line.. type in ls and just bumps me to the next line agan.. nothing happens.. :(

---

### Post by aysiu on 2005-09-01
When you mounted the partition, did you really type this exactly?

[QUOTE=DMD]sudo mont /dev/hdb /media/windows/ -t ntfs -o nls=utf8,unmask=0222[/QUOTE]
Or did you type this?

```

sudo mount /dev/hdb1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

```
First of all, the command should be *mount*, not *mont*, and, as far as I know, there's never an /dev/hdb. Even when I hadn't partitioned my hard drive (i.e., it was just one big space), it was called hda1, not just hda. You also typed *unmask* instead of *umask*.

Just a little hint from one newbie to another: it's always better to copy and paste what people tell you to "type" than to type it in yourself.

Personally, I've never found it that great to manually mount the Windows partition each time. I just have it automount at boot-up every time.

[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

Can you please type in *sudo fdisk -l* in the terminal and copy and paste the output into a post here?

---

### Post by DMD on 2005-09-01
Im just going from one computer to the next so i dont have copy and past going on.. so sorry for the miss spelling. But i had the command right..


Disk /dev/hda: 13.6 GB, 13676544000 bytes
255. heads 63 sectors/ track, 1662 cylinders
units= cylinders of 16065 * 512= 8225280 bytes

Device Boot        Start           End              Blocks            id         system
/dev/hda1*        1                   1590          12771643    +83         linux
/dev/hda2          1591            1662          578340           5          extended
/dev/hda5          1591            1662          57308           +82        linux swap/ solaris


Disk /dev/hdb : 61.46 GB. 61492838400bytes
255 heads, 63 sectors/track, 7476 cylinders
Units= cylinders of 16065* 512=8225280 bytes

Device Boot         Start                 End             Block          ID             system
/dev/hdb1            1                      7475           60042906    7          HPFS/NTFS

---

### Post by aysiu on 2005-09-01
[QUOTE=DMD]so sorry for the miss spelling. But i had the command right..[/quote]

Including using hdb1 instead of just hdb?

> 
/dev/hdb1            1                      7475           60042906    7          HPFS/NTFS

---

### Post by DMD on 2005-09-02
Oh man.. That works.. Thank you.. I would like to have it boot up every time.. But not to sure if i wanna go through all that.. lol.. It says that it is read only.. Now that means that i cant add files to that? Is there a way to be able to add files?

---

### Post by xmastree on 2005-09-02
> Oh man.. That works.. Thank you.. I would like to have it boot up every time.. But not to sure if i wanna go through all that.. lol..Edit your /etc/fstab file to have it mount automatically at boot up [here's how](http://www.ubuntuguide.org/#automountntfs) 
>  It says that it is read only.. Now that means that i cant add files to that? Is there a way to be able to add files?Linux can't write to an ntfs partition. If you want to be able to write to it, you need to reformat it as Fat32.

---

### Post by DMD on 2005-09-02
cool.. Sounds good.. thank you..

---

