---
title: "I need some help getting a dual boot to work"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Donnie Darko on 2007-06-11
Ok first off, I'm running Feisty Fawn, but I would like to reinstall Xp on a partition. I've tried to run gParted to place some space for Xp, but the gparted isn't working for some reason. 

[IMG]http://img.photobucket.com/albums/v451/ska7245/Screenshot--dev-sda-GParted.png[/IMG]


Here's the image I get when I run it.
any help would be appreciated
Cheers

---

### Post by cotcot on 2007-06-11
I think you are trying to work with gparted on a mounted partition. That will not work. You can do that with a liveCD. I recommend the GpartedLiveCD.

It is further better to install XP first and than ubuntu. (easier to install the bootloader)

---

### Post by Ferri on 2007-06-11
#

---

### Post by Nythain on 2007-06-11
im REALLY no expert on partitioning, and how ext3/swap/ntfs/fat work and the differences between logical, primary and extended partitions, but if i had to take a guess i think i might say it could possibly have something to do with swap residing in an extended partition after the / ext3 partition... or i could be completely retarded on this one (more than likely the case)

edit: yep, went way the wrong way on that one, didnt occur to me that you cant edit mounted partitions :)

---

### Post by Ferri on 2007-06-11
Sorry,I deleted the message because I was wrong.

---

### Post by Donnie Darko on 2007-06-11
ok, so where do I go about getting the GpartedLiveCD? 

thanks

---

### Post by durrell on 2007-06-11
It won't let you edit because you're using that partition when you're in Linux. And whoever said about the swap residing in the same partition, that doesn't matter..I think pretty much everyone dual booting is running an NTFS partition for Windows and then one big extended partition with Linux, Linux Swap, and FAT32.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

That's the Live CD. Be prepared to reinstall GRUB if you install Windows after you've installed Linux, because Windows is going to rewrite your boot sector and make it where you can't boot into Linux. Just search "reinstall grub" on the forums to find instructions on that.

Good luck.

---

### Post by HereInOz on 2007-06-11
You can download the ISO of gparted from here:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Then burn it to a CD, using the "burn ISO" function, and you will have the Gparted live CD.

---

### Post by Donnie Darko on 2007-06-12
Ok, I'm about to embark on placing XP on a roughly 65 GB partiton, how do I reinstall GRUB?

---

### Post by Hobo Joe on 2007-06-12
You'll find lots of threads if you just search for re-installing grub.

Alternatively, there is a grub magic CD which installs it autmatically.

---

### Post by Donnie Darko on 2007-06-19
Ok, I partitioned the drive with the Gparted CD, and I tried to install windows. But it only found the ubuntu partition, not the one I formatted for it. What could have happened?

---

