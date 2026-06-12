---
title: "How do I change desktop to another partition?"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by Dafydd on 2006-04-18
Hi

How do I change desktop to another partition? I've repartitioned and want to use hda5 (which is vfat) as the new default desktop location instead of /home/dafydd/Desktop.

Any ideas?

Cheers

Dafydd

---

### Post by pbaehr on 2006-04-18
When you mount the drive in /etc/fstab you would set the mount point to /home/dafydd/Desktop after you rename your old Desktop directory. (Don't delete it yet in case it doesn't work quite right)

Though, if you don't mind me asking, why not put your entire /home folder on a separate partition? That's much more useful in my opinion.

If you do decide to do that instead, this is a nice walkthrough on how to do it right. It would apply to your idea as well, though, I suppose:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by Dafydd on 2006-04-18
[QUOTE=pbaehr]If you do decide to do that instead, this is a nice walkthrough on how to do it right. It would apply to your idea as well, though, I suppose:
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)[/QUOTE]


Cheers. will follow the instructions tomorrow. 

Would it be safe to use a separate vfat (FAT32) partition as home and Desktop for both windows and for ubuntu?

I might give up now if not possible...

Best
Dafydd

---

### Post by fdoving on 2006-04-18
I would not recommend using a vfat partition as home. I would recommend mounting you vfat partitions in a place like /media/ and use that partition for files you want to share with windows.

There are loads of reasons why you should use a linux filesystem for linux files.

- Frode

---

### Post by Dafydd on 2006-04-18
[QUOTE=fdoving]I would not recommend using a vfat partition as home. I would recommend mounting you vfat partitions in a place like /media/ and use that partition for files you want to share with windows. There are loads of reasons why you should use a linux filesystem for linux files.[/QUOTE]

thanks for the info.

does it make the data liable to corruption? Is it very dangerous?

I've just set up a dual boot system for a friend. She needs to access both and I just thought it would be better for her not to have to 'think' about where her Linux or Windows desktop is but just to save the files etc...

Is this so dangerous? Sorry I'm a newb...

Cheers

dafydd

---

### Post by pbaehr on 2006-04-18
I get the feeling you're trying to create a shared desktop between Windows and Ubuntu. It's an interesting idea. As to how feasible it is, I'm not sure. One of the reasons I can think of not to use fat32 for linux files would be permissions. You can't set any in vfat. I'm not sure if that would have an impact beyond the obvious.

My guess is it will be a difficult task, but if you're feeling up to it it can't hurt to experiment. I'm sure you can get some more help here once you're a little further along. Good luck if you decide to continue.

---

### Post by pbaehr on 2006-04-18
Ah, we posted at the same time. Now it's clear what you're up to.

I'd recommend that rather than mount the vfat partition as home or the desktop you mount it somewhere like /media/vfatshare (or whatever you want to call it.) Then put a shortcut to that on the desktop of both OSes and explain that any files that she wants to access from both OSes should reside there.

---

### Post by htinn on 2006-04-18
Using vfat will cause a number of problems:

1) Constant need for defragmenting
2) Files must be < 2 GB
3) Higher risk of corruption
4) Not as much support for file permissions and symbolic linking

I would only use vfat if absolutely necessary and only for storing data that needed to be immediately shared.

---

### Post by pbaehr on 2006-04-18
It should be noted, however, that these are simply flaws in fat32 in general. It has nothing to do with the fact that it is being used by Linux. It is equally inefficient when being used by any operating system. I think it will suit fine for a shared space between the two OSes.

---

