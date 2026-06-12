---
title: "Dual-boot torrent synchronization?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Sabretooth on 2007-07-15
This is probably a silly question, but here goes.

I have a Windows XP/Ubuntu set-up. I normally use Windows XP, because thats where my torrents are (they're big, so I have to keep them on as much as possible). But I like using Ubuntu. :(

So, is it possible to synchronize my torrents in Ubuntu and XP, so that the progress made by one OS is recognized by the other and I don't lose progress? I'm using Azureus, and I hear it can be installed on Ubuntu.

---

### Post by Arwen on 2007-07-15
Here's the reasonable part of it: this could be possible if you chose from both azureus installations(XP+ubuntu) to download and store the files in the SAME folder which has to be in a fat32 partition of your hd(cause I think linux cannot write in ntfs partitions)
I've never tried it,just assuming..

---

### Post by xenoph0be on 2007-07-15
You can read/write to NTFS with the [ntfs-3g driver]("http://www.ntfs-3g.org/").  Both ntfs-3g and azureus can be added via synaptic.

---

### Post by Sabretooth on 2007-07-15
I think that is possible, Arwen. But that will mean that Azureus will have to re-check everytime it loads. That'll be a pain. :D

Never mind, I was just curious.

---

### Post by ohzopants on 2007-07-29
I've done this.  The only problem is that it only seems to work one way: the torrents I start in windows are easily continued in Ubuntu, but when I try to continue a torrent I started in Ubuntu from windows it starts fresh and justs adds a (1) to the end of each file name.

---

