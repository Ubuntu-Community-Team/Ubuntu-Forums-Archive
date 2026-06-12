---
title: "mounting hard drive"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by dr.silly on 2007-03-30
I have no idea how to do this but I know I can't access my other drive till I do it. Any help?

---

### Post by taurus on 2007-03-30
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by cowlip on 2007-03-31
Also, if you're trying to mount a windows drive with ntfs-3g, google 'ntfs-config' and use it to mount with a GUI

---

### Post by brennydoogles on 2007-03-31
Disclaimer: This post is written assuming that your other partition is an NTFS partition. You do not want to write to an NTFS partition without first downloading software for it from Synaptic. If you write to your windows partition without software help, windows may freak out and crash.

You will need to find out the name of your other drive/partition. If you only have one hard drive it will be hda+ a number (if it is the first partition on the disk it will be hda1, if it is the second it will be hda2 and so on and so forth), and if you have two hard drives it will be hdb+ a number (following the same pattern as before). After you know what the drive name is you could put into terminal

```
sudo mount /dev/[COLOR="Red"]hdb1[/COLOR] ntfs /media/[COLOR="Red"]hdb1[/COLOR]
```

with the red text being changed to the name of your drive. This would mount the hard drive to /media/hdb1, and would also create a link on your desktop. Once again, you don't want to write to an NTFS partition without software help. This should help get you started, but if you have any questions feel free to ask again!

---

### Post by dr.silly on 2007-03-31
I typed ```
sudo mount /dev/hda1 ntfs /media/hda1

``` and I don't notice any difference in filebrowser

---

### Post by dr.silly on 2007-03-31
I typed ```
sudo mount /dev/hda1 ntfs /media/hda1

``` and I don't notice any difference in filebrowser

---

### Post by dr.silly on 2007-03-31
thanks this did the trick
[http://flomertens.free.fr/ntfs-config/](http://flomertens.free.fr/ntfs-config/)

---

### Post by dr.silly on 2007-03-31
I now restart my computer and the windows folder is empty? I try using ntfs-config but that doesn't work either!

---

