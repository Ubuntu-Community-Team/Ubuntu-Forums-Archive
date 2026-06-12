---
title: "I have messed up ubuntu something awful :("
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Fraser from Scotland on 2008-01-24
[http://ubuntuforums.org/showthread.php?p=4196687#post4196687](http://ubuntuforums.org/showthread.php?p=4196687#post4196687)

Thats for some background info, anyway I did this > If you feel you need to reinstall, simply put the LiveCD back in and follow the installation process as you did before. This time, you'll see during the partitioning stage that elements of the drive are already partitioned for Ubuntu. Simply format the ext3 partition with a fresh ext3 filesystem and begin installing Ubuntu to that partition. You'll have a fresh installation when you're done.  
I think i did something horribly wrong. Because i did freshly install, and I now think i have about 5 partitions on my laptop. 

What I need to know!
1. How do i delete ALL my partitions WITHOUT touching my windows partition? But removing all ubuntu stuff.

Once i have done that I am going to re-install ubuntu. If nobody can help I'm going to re-install windows then re-install ubuntu.

---

### Post by taurus on 2008-01-24
Boot from the LiveCD.  Then, open gparted (System -> Administration) and delete all the partitions that associate with Ubuntu, including the swap.

---

### Post by Fraser from Scotland on 2008-01-24
I love you so much.

---

### Post by Fraser from Scotland on 2008-01-24
Ok I did that, and now when i restart my lapto I get GRUB error 22 so I can't get into windows now.

---

### Post by jken146 on 2008-01-24
Did you reinstall Ubuntu?

---

### Post by Fraser from Scotland on 2008-01-24
Well no not yet. I thought the grub menu would disapear if i removed all the partitions.

---

### Post by Pandemic187 on 2008-01-24
> **Fraser from Scotland said:**
> Ok I did that, and now when i restart my lapto I get GRUB error 22 so I can't get into windows now.
Yeah, I'm guessing your GRUB loader isn't installed correctly. I think that means that most or all of your Ubuntu system is installed, but GRUB isn't, or it is corrupt at least. I think you need to reinstall Ubuntu to fix that; don't jump to conclusions and do that if you don't need to though, as I could be wrong. That's what I'm guessing though.

---

### Post by taurus on 2008-01-24
Just reinstall Ubuntu on that empty partition and it will reinstall GRUB to MBR so you can boot Ubuntu and XP again.

---

### Post by Fraser from Scotland on 2008-01-24
It's only giving me the option to use the whole hard drive when I go to install.

---

### Post by Pandemic187 on 2008-01-24
> **Fraser from Scotland said:**
> Well no not yet. I thought the grub menu would disapear if i removed all the partitions.
Not true, I don't think. Even though you removed the partitions, you did not format them, which I think means there would still be data on them.

---

### Post by jken146 on 2008-01-24
> **Fraser from Scotland said:**
> It's only giving me the option to use the whole hard drive when I go to install.

Isn't there a 'manual' option?

---

### Post by Fraser from Scotland on 2008-01-24
Yes and it shows the partition as free space but its greyed out.

---

### Post by jken146 on 2008-01-24
You have to create 2 new partitions in the free space, one to be mounted on **/** (formatted ext3) and one for swap (this should be about 1.5 x the size of your RAM, but no bigger than 1G).

---

### Post by Fraser from Scotland on 2008-01-24
I have absolutely no idea how to do that but i went to guided- use the largest continuous free space and it said it was going to format partition# 3 for ext3 and partition#5 for the swap, now i dont know if that is going to do the same thing or not.

---

### Post by jken146 on 2008-01-24
There is an option in the manual partitioning page to create a new partition.

I'd expect that that guided option does the same thing.

---

### Post by seventhc on 2008-01-24
Boot back from the live cd and open gparted again. You should see the partitions that you deleted click in that area and then choose create new then click apply. After that try the installation again, it should see that new space as free space and you can choose the option largest unused free space. That should work.

---

### Post by nofrendo on 2008-01-25
Were you ever able to boot into Windows? If you did the partition deleting correctly, the partitions would no longer have numbers, they would just be one big area that should say unformatted. If you can't boot into Windows, reinstall Ubuntu and then boot from grub into recovery mode for windows

---

### Post by RadiationHazard on 2008-01-25
if i was you i would down load the live version of Gparted [here]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828"). then burn it to a disk, restart computer with disk in cdrom. once it loads and everything delete all the linux partitions. i think there should be two? like a linux and a linux-swap if i'm correct. but anyways just delete the linux partitions and then you should have free space then restart your computer with the ubuntu live disk in it and when you go to install it install it to the largest area of free space or something like that should be one of the installing options.

Hope that helps. Let me know if it did.
RadiationHazard

---

### Post by nofrendo on 2008-02-23
The livecd version of Gparted is actually included in the Ubuntu livecd.

---

