---
title: "DVD rom Combo drive won't read DVDs"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by spectrum48k on 2007-06-30
I have a problem with my LG 2140B dvd combo drive. It works fine with CDs but wont read DVD data disks or DVD movie disks.
Can someone help? Im using ubuntu 7.04
Thanks

---

### Post by deadgobby on 2007-06-30
The problem is simple. You will need to install the restricted CODES to able to play DVD's
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
 After you install the codes, You'll be happy
Gobby

---

### Post by spectrum48k on 2007-06-30
> **deadgobby said:**
> The problem is simple. You will need to install the restricted CODES to able to play DVD's
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
 After you install the codes, You'll be happy
Gobby

Sorry I should have mentioned....I have all these loaded!  It won't read any DVD, not just the restricted film ones.

Thnks

---

### Post by Tea4all on 2007-06-30
please post your /etc/fstab file.  Also I would remove gxine, install totem-xine(or something like that), and replace the command for auto opening dvds from gxine to totem %d.

---

### Post by spectrum48k on 2007-06-30
> **Tea4all said:**
> please post your /etc/fstab file.  Also I would remove gxine, install totem-xine(or something like that), and replace the command for auto opening dvds from gxine to totem %d.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=7c2361f8-78b3-4baf-a7c0-0cd24671ad1d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=847e8625-fcaa-4ed7-a42c-98cfe44085cd none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Tea4all on 2007-06-30
Just as I thought!  Enter in ```
cd /etc
```   And then ```
gksudo gedit fstab
```  Edit /dev/hdd 
to read /dev/cdrom

---

### Post by spectrum48k on 2007-06-30
> **Tea4all said:**
> Just as I thought!  Enter in ```
cd /etc
```   And then ```
gksudo gedit fstab
```  Edit /dev/hdd 
to read /dev/cdrom

Thanks....I typed it all in and it ade no difference to the situation.  I tried a reboot to boot but still no progress.

---

### Post by Tea4all on 2007-06-30
You could try to let me to do it.  Go to System>Preferences>Remote Desktop.  Set it so I can view and control your desktop with the password 57gnomer.  Open up port 5900 with firestarter and forward port 5900 on your router.  Then send me your ip address.  Be sure to undo when I'm done.

---

### Post by spectrum48k on 2007-06-30
> **Tea4all said:**
> You could try to let me to do it.  Go to System>Preferences>Remote Desktop.  Set it so I can view and control your desktop with the password 57gnomer.  Open up port 5900 with firestarter and forward port 5900 on your router.  Then send me your ip address.  Be sure to undo when I'm done.

good idea sent pm

---

### Post by Tea4all on 2007-06-30
Now I need to know your routers ip address

---

