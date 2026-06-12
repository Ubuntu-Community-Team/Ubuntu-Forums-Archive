---
title: "help making ubuntu &amp; windows dual boot"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by hondaboi on 2007-03-15
can anyone help me one here about making linux (ubuntu) and windows xp dual boot?!? 
i installed ubuntu and then after rebooting it, it will load straight up to XP. i wonder how to make this as bootable.

---

### Post by Drakkor on 2007-03-15
prolly cause you installed grub to the ubuntu partition, you want to install it to the mbr,so that youll have a choice upon booting. :)
Edit: grub is the bootloader .

---

### Post by siciliancasanova on 2007-03-15
[This thread]("http://www.ubuntuforums.org/showthread.php?t=378246&highlight=dual+boot") might help some.  If it's not specific enough, first search "dual boot" in the forum search and browse some topics.  You're not the first to have this happen.  Hope it helps, :)

---

### Post by tommcd on 2007-03-15
Did ubuntu seem to install ok? Did you choose to install grub to the master boot record at the end of the install? If ubuntu did indeed install you should see that your C drive in windows is now smaller, and you should see partitions in windows disk management utility labeled "unknown partition".

---

### Post by hondaboi on 2007-03-15
yah i installed in a right way. 

i installed it in my spare HDD which is 80 Gig, so Linux & XP are two different HDD. because i don't want anything in my Drive C except XP OS.

so if i didn't install it in a dual boot mode should i reinstall ubuntu again?

thank you guys for the help.. i'm really NOOB about Linux and i'm so eager to learn Linux coz it's lots of people like this in so many ways. :D

---

### Post by DaveyG on 2007-03-15
if you`v got two Os on separate HHDs why not dual boot them via having one master on each bus? i posted something about this earlyer on a similar thread but got a reply saying "how would that work" if you`v got grub then it should let you chose wich one to boot from??

Davey

---

### Post by yllorco on 2007-03-15
I installed WinXP and Ubuntu 6.10 last Monday in one harddrive and it was successful. I reformated the 20GB harddrive first with only one partition and installed WinXP. Then I installed Ubuntu 6.10 by giving it about half of the total space. It successfully worked.  If you installed dual booting in two separate drives, it may likely boot up with the hardisk set as Master or primary.  I don't know if both Hard drives can be set as Master with both each having separate OS. Perhaps it has something to do with your CMOS setting whether the boot up is set to only one hard drive for boot up without any other option.  Try checking your CMOS. 



Quoted:

can anyone help me one here about making linux (ubuntu) and windows xp dual boot?!? 
i installed ubuntu and then after rebooting it, it will load straight up to XP. i wonder how to make this as bootable.

---

### Post by confused57 on 2007-03-15
> **hondaboi said:**
> yah i installed in a right way. 

i installed it in my spare HDD which is 80 Gig, so Linux & XP are two different HDD. because i don't want anything in my Drive C except XP OS.

so if i didn't install it in a dual boot mode should i reinstall ubuntu again?

thank you guys for the help.. i'm really NOOB about Linux and i'm so eager to learn Linux coz it's lots of people like this in so many ways. :D

Maybe this thread will help:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

Does Ubuntu boot, if you select the drive it's installed on to boot before your Windows drive?

If it doesn't & you get a grub menu at boot, highlight your Ubuntu entry, press "e" to edit, then change the line with root from (hd1,0) to (hd0,0), or whichever is your root partition, then press "b" to boot.
If Ubuntu does boot, then all you'll need to do is add an entry similar to the one in the thread I provided to boot Windows.

You can determine your root partition by booting up the live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
the -l is a small "L"

---

