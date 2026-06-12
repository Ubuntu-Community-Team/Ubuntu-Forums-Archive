---
title: "Installing Ubuntu with Windows on a ready partition"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by alamjadtawfiq on 2008-01-13
Hi there!

I have an 80 GB hard disk. I've installed windows xp on a partition, and emptied -while the installation of XP- a partition for Ubuntu (about 9 GB). Is it possible to install Ubuntu on this partition (which is NTFS and does not have except some small files) directly without harming other partitions?:confused:
Thanks

Amjad

---

### Post by bwhite82 on 2008-01-13
I was a little confused by your question. But I think you stated that you have 2 partitions: 1 with XP and another free partition -- formatted as NTFS. All that you would need to do is pop in the Ubuntu LiveCD, and use gparted to reformat the free partition to EXT3 and then install Ubuntu onto it. The key is to remember the size of the partition that you want to format (9gb right?). That makes it easier to tell the difference between the 2.

---

### Post by bodhi.zazen on 2008-01-13
yes, and you will need a swap partition as well.

size = RAM x1, max 1 Gb

Install guide : [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by alamjadtawfiq on 2008-01-13
> **Soldierboy said:**
> I was a little confused by your question. But I think you stated that you have 2 partitions: 1 with XP and another free partition -- formatted as NTFS. All that you would need to do is pop in the Ubuntu LiveCD, and use gparted to reformat the free partition to EXT3 and then install Ubuntu onto it. The key is to remember the size of the partition that you want to format (9gb right?). That makes it easier to tell the difference between the 2.

Thank you soldierboy. That's right (I also have 2 additional partitions for data). But I have still a small question: will I have to do that manually, right? Will I be able to open the EXT3 partition from windows XP?

---

### Post by alamjadtawfiq on 2008-01-13
> **bodhi.zazen said:**
> yes, and you will need a swap partition as well.

size = RAM x1, max 1 Gb

Install guide : [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Thank you bhodi.zazen, but I quite don't know what you meant by 'swap':confused:

---

### Post by alamjadtawfiq on 2008-01-13
Ahh sorry, I knew what you meant. But does that require me to make an extra partition? And is 9 GB enough?

---

### Post by bwhite82 on 2008-01-13
The size of the Ubuntu partition is up to you, depends on what all you want to install. It will definitely hold a fresh install plus many extras....but if you're a gamer.....

Yes, you'll need to create a swap partition as well. All of this can be accomplished via an Ubuntu LiveCD. Assuming you have one, boot up with it, once in Gnome goto: System>Administration>Partition Editor menu. And manipulate your partitions that way. You can mess around with it all you want, changes won't actually be applied until you click 'Apply' at the top.

---

### Post by alamjadtawfiq on 2008-01-13
Thank you, I'll try it!

---

