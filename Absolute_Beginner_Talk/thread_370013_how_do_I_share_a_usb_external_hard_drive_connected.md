---
title: "how do I share a usb external hard drive connected to my kubuntu pc over a network?"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by benfindlay on 2007-02-25
Hi guys, hoping someone can help me with this. Here's the situation:

I have a usb2 external hard-drive formatted in fat32 plugged into my kubuntu computer. I want to share the contents of this over the network so that the other pcs on the network (Windows, Mac OS-X and ubuntu) can all access it.

However, when I try and share it with samba, I get the error that only local drives can be shared. I have also tried sharing individual folders on the drive, but to no avail.

Does anyone know any way round this at all?

Thanks in advance!

---

### Post by terdon on 2007-02-25
Check out :
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server")

---

### Post by benfindlay on 2007-02-26
Hey, thanks for the reply. I managed to get it shared at last, now the only problem I have is that it doesn't mount automatically at boot; I need to log in and click on the icon to cause it to mount. Anyone have any ideas on this?

Making progress at least...](*,) 

Cheers in advance

---

### Post by terdon on 2007-02-26
I think there is a howto for that in the same guide i posted before

---

### Post by bodhi.zazen on 2007-02-26
> **benfindlay said:**
> Hey, thanks for the reply. I managed to get it shared at last, now the only problem I have is that it doesn't mount automatically at boot; I need to log in and click on the icon to cause it to mount. Anyone have any ideas on this?

Making progress at least...](*,) 

Cheers in advance

You need to add an entry in fstab. The exact entry depends on your file system.

I would use either a label or uuid.

See if this helps :

[http://www.ubuntuforums.org/showthread.php?t=283131](http://www.ubuntuforums.org/showthread.php?t=283131)

---

### Post by benfindlay on 2007-02-26
Thanks for the replies!

I'd seen that article before, but decided to take a closer look at it. I tried using the script mentioned in the auto-mount section which configured my fstab for me. The drives were mounted successfully, but unfortunately when I rebooted they didn't remount themselves. Is this something to do with the pmount command you say is used to mount removable media, or am I barking up the wrong tree? And just in case it makes any difference, I'm using kubuntu 6.06.

Cheers in advance!

---

### Post by terdon on 2007-02-26
Could you post your /etc/fstab file?

---

### Post by benfindlay on 2007-02-26
Here it is:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#Added by diskmounter utility
/dev/sda1 /media/sda1 vfat rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
#Added by diskmounter utility
/dev/sda2 /media/sda2 vfat rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0

Any ideas?

---

### Post by terdon on 2007-02-26
Try adding the option "auto", like so:

```

#Added by diskmounter utility
/dev/sda1 /media/sda1 vfat rw,user,auto,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
#Added by diskmounter utility
/dev/sda2 /media/sda2 vfat, rw,user,auto,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0 

```

---

### Post by benfindlay on 2007-02-26
Hey, cheers for the reply, unfortunately it is still not playing ball! It still requires me to click on the drives once I've logged in.

Have seen a couple of similar articles where the issue of directory ownership has come up as causing problems, would this perhaps have anything to do with my problem?

Cheers for the help!

---

### Post by terdon on 2007-02-27
What do you mean by "click on the drives"? If you can see them on your desktop, they are already mounted.

---

### Post by benfindlay on 2007-02-27
They are on the desktop, but when you click on them for the first time, a dialog box flashes up very briefly and then I can access them. Also once that is done, a little green dot appears next to the icon on my desktop and the dialog box doesn't appear again (until i reboot and click on them again. The title on the dialog box says "Mounting" too, so I had assumed that this meant that they weren't properly mounted, just recognised, until this had happened.

Also, right clicking on the drive icon gives me the option to "Mount", whereas once mounted, said option changes to "Safely Remove"

---

