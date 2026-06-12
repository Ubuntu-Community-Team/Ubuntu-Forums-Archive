---
title: "[SOLVED] Can I install XP after Ubuntu?"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by ring_wraith on 2007-12-21
I currently have a dosbox waiting to have an OS installed on it. Can I install XP after Ubuntu? Because i heard that it was recommended to install it after i installed XP.

---

### Post by Fixman on 2007-12-21
Yes, but you must do some tweaks at the command line.

---

### Post by taurus on 2007-12-21
Yes, you can install XP after Ubuntu BUT XP will overwrite your MBR so you won't be able to boot Ubuntu anymore.  Therefore, you need to reinstall GRUB to MBR if you want to boot both Ubuntu and XP.

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

The best or easiest way is to install XP first and then Ubuntu after that.

---

### Post by dpar on 2007-12-21
Yes, you can install XP after, but be careful. XP will want the whole drive, so make sure you watch out for that. Also you will have to reinstall grub.

It's definately easier to install Ubuntu after XP.

---

### Post by ring_wraith on 2007-12-21
The reason i wanted to install Ubuntu first is that the XP installed picks up only 140 GB of my 160GB hard disk. But the Ubuntu installer picks up the full 160 GB. 

So can I run the Ubuntu installer, create partitions, quit , install XP then install Ubuntu?

---

### Post by taurus on 2007-12-21
Or you can use gparted from the LiveCD and partition your harddrive into two.  Then, install XP on the first partition.  Now, boot from the Ubuntu LiveCD again and tell the installer to install Gutsy on the second partition.

---

### Post by teryowen on 2007-12-21
Yes you can install Ubuntu, and then Windows XP,

after installing windows XP you would need to boot up into a linux live cd and reinstall GRUB by doing the following in terminal:

sudo grub
root (hd0,0)
setup (hd0)
quit

where hd0,0 means the first hard drive and the first partition. if it were hd1,0 it would mean 2nd hard drive and 1st partition and like wise if it were hd0,1 it would mean first hard drive and second partition so change it accordinally.

and then dthe hd0 means onto which hard drive to install it on.

You will also need to edit the /boot/grub/menu.lst file by appending a windows entry to be able to boot into windows.

this is what my windows entry looks like again change the hd0,0 accordingly to where your windows is
```
title                Microsoft Windows XP Professional
root                (hd0,2)
savedefault
makeactive
chainloader        +1
```

---

### Post by ring_wraith on 2007-12-21
Thanks, that's what i wanted to know.

---

### Post by Fixman on 2007-12-21
> **ring_wraith said:**
> Thanks, that's what i wanted to know.

Or you can anyway install XP first, then Ubuntu and, when the Live CD, you go to system->administration->partition editor, create a free space, then install ubuntu and use that free space for your installation

---

