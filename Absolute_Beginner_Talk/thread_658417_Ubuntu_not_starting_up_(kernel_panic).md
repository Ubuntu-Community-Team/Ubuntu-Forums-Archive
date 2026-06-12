---
title: "Ubuntu not starting up (kernel panic)"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by The Stig 90 on 2008-01-04
Greetings people of the internet!

I have used the search and found lots of posts on this problem, but I haven't been able to solve my own problem with the help of them.

I'm not quite sure how I triggered this problem (Im sure it's user error though), but when I try to boot Ubuntu, i get the error: "kernel panic not syncing VFS: unable to mount root fs..". I tried to start up in safe mode, but I got the same error. I'm quite sure the problem related to the splash screen resolution settings. All the related posts on the problem do post a sollution. The thing that makes my situation difficult is that I cant gain/don't know how to access to my ubuntu partition to change the settings. I tried to do so with the live cd to no avail.

I really would be very greatful for any help (I just got used to ubuntu and set it up to my liking after many weeks). I'm not a complete ubuntu noob (even though I have posted my problem here), I have a few months experience with it, but never encoutered a problem as big as this.

Thanks in advance

-Stiggles

---

### Post by Bufke on 2008-01-04
I have no idea what that error is about, but to access your partition you can use gparted from a live CD.  It's labeled as partition editor I believe.  I think gparted is still included on the ubuntu live CD, if not you could always download it with synaptic.  There's even a gparted live CD for just this type of thing.  Here's a link for Gparted live CD [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by PmDematagoda on 2008-01-04
Could you please post some details about your Ubuntu install, how many hard drives you have, how many partitions are present in each hard drive, the lot.

---

### Post by The Stig 90 on 2008-01-05
I have one hard drive that is devided isnto 3 partitions. 1 about 20gig partition for ubuntu, 1 about 200gig partition for Windows Vista and a small recovery partition that came with the computer. My ubuntu install is pretty much standard. No big chages have been made.

---

### Post by PmDematagoda on 2008-01-05
Boot the Live CD, once it finishes booting, could you post the output of:-
```
sudo fdisk -l
```

---

### Post by The Stig 90 on 2008-01-05
Ok I've solved it :guitar: The initrd.img was the culprit. The solution was to make Ubuntu use the backup version of initrd.img via the grub menu. Another problem was that Ubuntu wasn't being directed to the Ubuntu partition (I changed the setting in the setting in grub menu). Once I had done that Ubuntu booted and I was able to edit menu.lst and make the changes permament :)

Thanks for all of your help.

This thread has now served it's purpose

[SIZE="6"]SOLVED[/SIZE]

---

