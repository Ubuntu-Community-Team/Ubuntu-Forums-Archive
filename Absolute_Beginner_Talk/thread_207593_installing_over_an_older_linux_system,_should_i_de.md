---
title: "installing over an older linux system, should i delete partitions?"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by ign on 2006-07-02
i have dual boot pc with xp and mandriva. i'd like to try the new ubuntu, so i need to get rid of mandriva:

- should i delete the whole partition prior to the new installation?
- and what about the swap partition? should i delete it too before installing ubuntu?
- what will happen to GRUB? will it be overwritten automatically?

thanks for your help!

---

### Post by kigina on 2006-07-02
dont delete the mandriva partion
it could result in a grub error
just write over it with the new install

---

### Post by woedend on 2006-07-02
theres no need to delete the partitions unless you want to lay it out differently.  Just mark it to be used and it will automatically be reformatted, then installed on.  Swap is always formatted by default.  I believe Grub is automatically overwritten.

---

### Post by catlett on 2006-07-02
It's up to you. I don't know how mandriba sets up it's partitions but I would say that you can use them no problem.
If you are going to delete and create, I would use gparted [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
As for grub, ubuntu will erase it and install it's own version.

EDIT Disregard. This post is now redundant. Woedend's post wasn't there when I started my reply.

---

### Post by kigina on 2006-07-02
btw mandriva makes you pay for their rpm's but you can find updates and other things pretty easily

---

### Post by ign on 2006-07-02
thanks for all the replies, i'll make the installlation without touching the existing partitions then.
i had problems configuring my wireless card with mandriva, couldn'd finbd the drivers, in ubuntu breezy it worked fine, so i'm coming back :)

---

