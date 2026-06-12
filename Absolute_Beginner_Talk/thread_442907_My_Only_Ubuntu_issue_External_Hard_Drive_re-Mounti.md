---
title: "My Only Ubuntu issue: External Hard Drive re-Mounting"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Sethalos on 2007-05-14
Heya,

I have an external hard drive, connects to my PC via a usb cable. I use it as a storage medium for my 180gig+ mp3 collection, documents, photos, etc.

The problem is that everytime I turn on the computer, it apparently has to be re-mounted or something, and after the 20th mounting when the system boots up, it pauses and does this long disk check of some sort.

Just wondering if there was anyway to get around this or not.  Hope this makes sense, I'm a noob.

Other than this, I've had almost no issues with my switch from XP to Ubuntu.

Seth

---

### Post by freebird54 on 2007-05-14
I believe the disk check occurs after 30 mounts.  Happens to your main drives too, but I guess they're faster!  If you don't want the drive checked except by your order (but don't forget to do it once in a while), you can change the entry for that drive in your /etc/fstab file:

make a backup before you commit any changes!

```
sudo cp /etc/fstab /etc/fstab.backup_20070514
```

now to edit the file

```
gksudo gedit /etc/fstab
```

You will see entries like this

```

# /dev/hde3
UUID=e9c82550-a09f-4d28-8419-4c572a058f80 /home    ext3  defaults      0       2
```

Change the last number at the end of the line to 0, which means "don't check".

```

# /dev/hde3
UUID=e9c82550-a09f-4d28-8419-4c572a058f80 /home    ext3  defaults      0       **0**
```

Hope this helps....

---

### Post by Sethalos on 2007-05-14
Thanks very much, that did the trick.

Seth

---

