---
title: "amarok doesn't connect to ipod"
date: 2005-12-24
forum: Absolute Beginner Talk
---

### Post by qiemem on 2005-12-24
iPod mounts automatically as it should, it is read fine by Rhythmbox (but Rhythmbox can't write to it, so that's why I'm using amarok; also, just cause amarok kicks ass). amarok (1.4) seems to be working fine in all other regards. Its just doesn't detect the ipod. I already tried linking /media/ipod to /mnt/ipod because I heard that's where amarok looks (from other posts) using:
```
sudo ln -sf /media/ipod /mnt/ipod
```
this only worked when the ipod was disconnected (just out of curiousity, why is this? I'm obviously new to this stuff as I'm posting in the beginners section.)
Here's my /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb        /media/usb0     auto    rw,user,noauto  0       0

```

It doesn't list the ipod, which is weird, but the ipod does mount fine and I can cd to it and everything.
Anyway, any ideas?

(I'm not using gtkpod because I couldn't get it to work with .m4as, couldn't find the right libraries or something when trying to compile from source with aac support.)

oh, ps, I know there's a forum on this in the hardware section (not my thread) , but that was kinda over my head slash it didn't work or come to a conclusion.

---

### Post by qiemem on 2005-12-24
bounce

So, I found some articles on how to get amarok to recognize the ipod. Following them, I added "/dev/sdd2       /mnt/ipod       vfat    noauto,user     0       0" to /etc/fstab, but alas, it still does not work.

Any ideas on this? I deleted the link ?file? /mnt/ipod by just "sudo rm /mnt/ipod" so I could create a directory of the same name. Anyway, anyone know what I should do? I'm screwing things up big time? Help?

---

### Post by zentus on 2006-09-16
im having the exact same problem but i don't have any issues with gtkpod.  id much rather use amarok though.

anyone any ideas?

---

### Post by lemboy4 on 2008-07-19
Well, I had the same problem as described above -- Ubuntu seemed to recognize my iPod, and Rhythmbox could read from it, but Amarok couldn't find it.  I solved the problem on my computer, however, and I think the issue is just that one has to extremely careful when defining the location at which the iPod is mounted.

I opened Properties for the iPod icon that appears on my Desktop and saw the Mount Point was listed as /media/CHRIS'S IPO.  I did the following things, though I don't know if the first is necessary (it can't hurt, though, and some sites seemed to indicate a deficiency on Amarok's part might mean it has to be done):

1) I soft linked /mnt/ipod with

```
sudo ln -sf "/media/CHRIS'S IPO" /mnt/ipod
```

2) Under Settings -> Configure Amarok -> Media Devices -> Add Devices, in Amarok, I entered as the mount point 

```
/media/CHRIS'S IPO
```

And, of course, selected to use the iPod plugin.

---

### Post by polytropos on 2008-07-19
i had the problem described on this thread when i upgraded from gutsy to hardy, but lemboy4's instructions got my nano working.  thanks for that.  for anyone deciding which media player to use with an ipod, i highly recommend amarok.  organizing files is easy and intuitive with it.

---

