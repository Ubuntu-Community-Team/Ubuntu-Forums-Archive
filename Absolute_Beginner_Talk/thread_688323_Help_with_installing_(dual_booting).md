---
title: "Help with installing (dual booting)"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Shaun440 on 2008-02-05
Hi

I have a question before I instal ubuntu. In my computer, i have 2 hard drives. One 250gb one that has vista installed (including page file and all that junk) on it, and a 500gb one for general storage. I was wondering if I installed ubuntu on the 250gb hard drive, would both windows and ubuntu then be able to see the 500gb one and be able to read and write on it?

Or would it be better to use the 250gb for windows and the 500gb one for linux? thus having all their respective applications installed and files they use on the same hard drive as the opperating system. (i hear this is faster/better)

For general info, i will be using linux most of the time and for basically everything (word processing, music, chat, internet etc) and will only use vista for the occasional game (unless the game will work under wine :)

Cheers
Shaun

---

### Post by fiddledd on 2008-02-05
If you install Ubuntu on your 250gb Drive and Dual Boot with Vista, then yes, Both Windows and Vista can r/w to the 500gb. Ubuntu can r/w to Fat32 and also NTFS. For NTFS Ubuntu uses the ntfs-3g drivers (If I rememeber right installed by default). You can also, if you prefer, install Ubuntu to the 500gb drive and Partition it so you also have a FAT32 partition that both OS's can share.

EDIT:
Here's a guide:

[http://nighthacker.net/how-to-dual-boot-vista-and-ubuntu-gutsy710/](http://nighthacker.net/how-to-dual-boot-vista-and-ubuntu-gutsy710/)

or just search the Forum here for Dual Boot Vista

---

### Post by rkd on 2008-02-05
Either way will work.  I think there would be very little difference in performance, so don't let that be a big factor in your choice.

One thing to be aware of -- if you are going to install Ubuntu on the same drive as the Vista boot drive, use the Vista disk manager software to shrink the Vista partition to make room for Ubuntu -- don't let Ubuntu try to do that.  The various guides telling you how to install dual boot with Vista should tell you that, but it bear emphasizing.

---

