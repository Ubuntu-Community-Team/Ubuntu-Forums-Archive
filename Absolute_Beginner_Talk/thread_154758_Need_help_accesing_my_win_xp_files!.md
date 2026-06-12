---
title: "Need help accesing my win xp files!"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by babelfishi on 2006-04-03
I'm completly new to ubuntu 5.10. :) 
I have installed ubuntu on a seperate disc than my normal win xp hard drive (NTFS). I need to get my files (music, etc) from my normal hard drive.

Can somebody give me a step-by-step detailed instructions to help me?

Thanks.

---

### Post by dreamsINdigital on 2006-04-03
[http://help.ubuntu.com/starterguide/C/ch05.html](http://help.ubuntu.com/starterguide/C/ch05.html)

---

### Post by htinn on 2006-04-03
This one seems pretty good:

[https://wiki.ubuntu.com/MountNtfsOnBoot](https://wiki.ubuntu.com/MountNtfsOnBoot)

---

### Post by babelfishi on 2006-04-03
Hmm.
Following the directions on 
[https://wiki.ubuntu.com/MountNtfsOnBoot](https://wiki.ubuntu.com/MountNtfsOnBoot)

I get the output: 
"@ubuntu:/$ mount -a
mount: only root can do that
@ubuntu:/$ mount
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-9-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
@ubuntu:/$
"

Anyone help?

---

### Post by johnnymac on 2006-04-03
If you have a 32-bit system (or are intested in looking up how to do a chroot environment if your 64-bit) you can try captive ntfs.  Not only will it allow you to read your NTFS file-systems, but you can write to them as well...it's great.  Here's the site on it...

[http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)

GL

---

### Post by RRS on 2006-04-03
[QUOTE=johnnymac]..........you can try captive ntfs............[/QUOTE]

Sounds like answer to my searching also. Checked your link but not sure which package to download and how to install.

Don't mean to hijack the thread but if someone could point me in the right direction I'd be very gratefull.

Also, I used the method recommended by dreamsINdigita, puts an icon on the desktop for ready access but is read only.

Thanks again.

---

### Post by johnnymac on 2006-04-03
so you can do the rpm.......

1.  download the rpm
2.  download alien - sudo apt-get install alien
3.  alien -i <captive_poop.rpm>

Now, if you have a dual boot it should find your drivers quickly...otherwise you should be able to find some directions on that site to help you.

---

### Post by RRS on 2006-04-04
Thanks A lot :)

---

### Post by dreamsINdigital on 2006-04-04
Is it safe to allow writing to NTFS?

---

### Post by trent dillman on 2006-04-04
I've always read that it is not safe. Because of that, I've never tried.

---

### Post by meborc on 2006-04-04
[QUOTE=babelfishi]I get the output: 
@ubuntu:/$ mount -a
mount: only root can do that

Anyone help?[/QUOTE]
welll.. then you should run it in root :mrgreen: 

this is a must-read for all newbuntians: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

and NO, it is NOT SAFE to write to NTFS... make a separate partition of FAT32, that can be read/write by both xp and ubuntu

---

