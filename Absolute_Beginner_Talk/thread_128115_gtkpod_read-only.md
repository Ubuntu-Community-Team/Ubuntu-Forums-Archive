---
title: "gtkpod read-only?"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by hamsaladsandwich on 2006-02-10
Hi - trying to sync mp3's to my ipod using gtkpod, i get the following error:

Error opening '/media/ipod/iPod_Control/Music/F11/gtkpod801903.mp3' for writing (Read-only file system).

The songs appear on my ipod but are 0 seconds long.

I guess I just need write privileges? I'm pretty new to ubuntu but anything you guys could tell me would be great.

---

### Post by majikstreet on 2006-02-10
sudo gtkpod
(or if you do it from gnome run, you can do gksudo gtkpod)
that may work..

also: I had somehow fixed it so I don't have to do that... if you could do this is terminal and show me the output I may be able to help you:
```

cat /etc/fstab

```

majikstreet

---

### Post by hamsaladsandwich on 2006-02-10
here's the output:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/sdb1       /mnt/ipod       auto    noauto,user,rw  0       0

---

### Post by majikstreet on 2006-02-10
hmm... that's strange.. but does sudo gtkpod work? that may be the only solution that I can thing of.. my cat /etc/fstab gives similar output.

---

### Post by hamsaladsandwich on 2006-02-10
yes, wow! it seems to be working now. muchas gracias

---

### Post by hamsaladsandwich on 2006-02-11
OK, new problem (i think): Now when I open with sudo gtkpod and try to sync, i get this error in the terminal:

/usr/bin/eject: unable to find or open device for: `/dev/sdb1'

mounting error? The ipod icon is on my desktop and i can browse it...

---

