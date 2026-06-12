---
title: "Need to recover files from a separate home partition"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by nirpius on 2007-07-12
I'd had PCLinuxOS installed and it had told me to have a separate home folder in case I changed distro so that I could keep all my files. This seemed a good idea to me so when I came back to try Ubuntu again, I didn't worry about them and just formatted my partition where I'd installed all my software and labelled /media/hda6 as /home and it recognised it Ubuntu which was fine.

When I look in GParted, it tells me that there are still 600MB ish of files in there (which makes sense as I had about 200 photos). The only thing is, in Nautilus (and also Konquerer I tried as I've installed Kubuntu-Desktop) I couldn't find them anywhere.

I tried opening up a Terminal and relocating to all the folders and subfolders  then typing ls but I couldn't find any traces of them. I've just got empty folders which apparently take up 600MB of space.

Does anyone know of any apps I need to install to recover these or if there's a way I can browse to find them as I haven't got any other copies of these.

Many thanks in advance

---

### Post by djchandler on 2007-07-12
> **nirpius said:**
> I'd had PCLinuxOS installed and it had told me to have a separate home folder in case I changed distro so that I could keep all my files. This seemed a good idea to me so when I came back to try Ubuntu again, I didn't worry about them and just formatted my partition where I'd installed all my software and labelled /media/hda6 as /home and it recognised it Ubuntu which was fine.

When I look in GParted, it tells me that there are still 600MB ish of files in there (which makes sense as I had about 200 photos). The only thing is, in Nautilus (and also Konquerer I tried as I've installed Kubuntu-Desktop) I couldn't find them anywhere.

I tried opening up a Terminal and relocating to all the folders and subfolders  then typing ls but I couldn't find any traces of them. I've just got empty folders which apparently take up 600MB of space.

Does anyone know of any apps I need to install to recover these or if there's a way I can browse to find them as I haven't got any other copies of these.

Many thanks in advance

Are you sure the partition is mounted? It sounds to me as if the partition is not mounted. You know the partition has not been touched. Did you try to mount it in Gparted?

DJ

---

### Post by ReaderRat on 2007-07-12
This may help:
[***Mounting Filesystems & Disks***](http://users.bigpond.net.au/hermanzone/p10.htm)

---

