---
title: "[SOLVED] Can we replace Grub 1.5 with Grub 2?"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2008-04-20
I've seen that Grub 2 has more advanced features than Grub 1.5, especially when it comes to handling custom resolution (aka 1280x800), so I was wondering if I could just switch? Are there any risks or best method?

---

### Post by Rhubarb on 2008-04-20
Grub 2 is still under development.
It's missing some features that I think is rather important, such as support for reiserfs3 and 4, ntfs, support for booting into the BSDs, and a few other things such as a graphical boot screen.

More information can be found here:
[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

It indeed would be great to see grub 2 finally released and working well :)

---

### Post by sayakb on 2008-04-20
```
sudo apt-get install grub2
```

Though +1 to what Rhubarb said. Wait for the final version to be released.

---

### Post by the8thstar on 2008-04-20
> **Rhubarb said:**
> Grub 2 is still under development.
It's missing some features that I think is rather important, such as support for reiserfs3 and 4, ntfs, support for booting into the BSDs, and a few other things such as a graphical boot screen.

More information can be found here:
[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

It indeed would be great to see grub 2 finally released and working well :)

Mega-bummer. I need support for NTFS (check my sig). I guess I'll wait then. 

Thank you both very much!

---

### Post by Sef on 2008-04-20
> Mega-bummer. I need support for NTFS (check my sig). I guess I'll wait then. 

You can download NTFS configuration tool from Add/Remove, so you will be able to read and write to NTFS.

Applications > Add/Remove > Change the top right box to 'All Available Applications' > Search > type in NTFS > chose NTFS Configuration Tool > Click Apply Changes > Click Apply > Click Close.

---

### Post by sayakb on 2008-04-20
```
sudo apt-get install ntfs-3g
```

---

### Post by Sef on 2008-04-20
> 
Code:

sudo apt-get install ntfs-3g



Before you do that, do this:

> sudo apt-get update

Then do the first command.

---

### Post by the8thstar on 2008-04-20
Thanks guys, but I can already identify NTFS partition within Ubuntu. My point is to LAUNCH NTFS formatted OS with Grub 2.

---

### Post by Fixman on 2008-04-20
> **the8thstar said:**
> Thanks guys, but I can already identify NTFS partition within Ubuntu. My point is to LAUNCH NTFS formatted OS with Grub 2.

Thats still impossible, so you will have to stick to Grub 1.5

---

### Post by revertex on 2008-07-02
you can't boot windows from grub2, but you can boot windows from a livecd that contain smart boot manager, like systemrescue cd or ultimate boot cd.

take a look here.

[http://grub.enbug.org/TestingOnX86](http://grub.enbug.org/TestingOnX86)

There is a patched version of grub2 that support ntfs.

If you use windows eventually i guess it's not a big issue.

Until grub2 is finished, I don't recoment use it, unless you have a very good reason.

The only reason I see you should want to use grub2 is to use a gpt partition table.

There is a grub legacy patched to support gpt disks that comes with systemrescuecd. 

[http://www.sysresccd.org/news/2008/01/26/gpt-disklabel-support-guid-partition-table/](http://www.sysresccd.org/news/2008/01/26/gpt-disklabel-support-guid-partition-table/)

Bear in mind that only vista and win2003 can use gpt disks, but only to store data, it cannot boot from a gpt partition.

cheers.

---

