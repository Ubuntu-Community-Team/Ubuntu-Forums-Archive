---
title: "[SOLVED] Automount and fstab mount"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by rusty4r on 2007-03-19
Is automounting the same thing as the computer mounting what is in fstab at bootup?

I'm beginning to think not. My operating system mounts exactly as listed in fstab. It also mounts these exact same partitions with another name.

Now that I really think about it, I'm not sure if it isn't just giving me shortcuts, in nautilus, pointing to the fstab mount points and naming those shortcuts by some name it deems appropriate.

These names actually could be labels, but I never gave my partitions labels to my knowledge. I believe this all started after installing SabayonLinux onto one of the partitions. For example hdb1 is my dapper install and I mount it /media/dapper but this shortcut calls it /ubuntu which I don't like because my main distro is hdb3(Edgy).

Here is a screenshot of what nautilus is showing me. Sabayon is actually the "/1" and pclinux is "mediapclinuxos".

If I click on /ubuntu for example it takes me to ubuntu, but if I hit the Up arrow it takes me to media and the dapper icon is highlighted as if that were where I have been. Does that make sense?

I've searched and the few threads I've found seem to point toward relabeling those partitions. But isn't there some little tweak somewhere that will stop nautlus from automatically giving me these shorcuts? 

I know this is long and I apologize, any wisdom would be appreciated

---

### Post by rusty4r on 2007-03-19
OK I think I may have fixed it. I rebooted to windows xp(sorry), I then installed the ExtIFS program(which I had not wanted to do because I didn't want windoze to have any access to Linux) and relabeled all the partitions. Then rebooted to Edgy and this is what it looks like now. Every shortcut or link looks like the mountpoint that I chose.

---

