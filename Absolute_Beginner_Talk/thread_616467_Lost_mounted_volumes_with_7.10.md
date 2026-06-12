---
title: "Lost mounted volumes with 7.10"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by 30mil01 on 2007-11-18
Hi all,

I was running feisty faun for while and then upgraded to gutsy gibbon. Now I have a file sysytem mount problem that I can't seem to fix.

I'm new to Linux but I have been hammering out issues by myself but I'm not afraid of the command line (grew up in DOS). Anyway, this is the short version of what happened. I mention the evil empire only to include it as a possible contributor to the problem.

My wife said something was wrong with Internet Explorer so i took a look. Some Japanese site took over the browser (I only use Firefox, she uses IE much to my displeasure). Bad things ensued once I tried to get rid of the spyware that had embedded itself. I had to re-install XP. Which made the grub loader take a dump. I used the feisty live cd to research and fix the grub boot loader - fixed.

I then set to upgrading Ubuntu to 7.10. done 

However, I have now lost my mounted drives. The original fstab file is still there so I try reloading using the ntfs config tool. but it didn't help at all.

Inside /mnt there is nothing listed. I have an 80 Gig HD with 4 partitions ntfs/ntfs/linux/swap respectively.

Where do I start? Thanks!

---

### Post by puterboy on 2007-11-18
copy and paste the following, please:

cat /etc/fstab
df -h
ls /dev/disk/by-uuid/ -alh

---

### Post by kiepmad on 2007-11-18
Has any parition changed number since you reinstalled Windows XP or upgraded to Gutsy?

---

### Post by 30mil01 on 2007-11-18
Hi guys, as luck would have it a friend at work called about 30 seconds after i posted. He had me remove the NTFS entries in the fstab file and rerun the NTFS config tool. Everything is back to normal. 

I appreciate the time you took to respond (and fast too -- wow)

My wife asked me "So are you going to get Windows caught up on patches and get all the drivers and software reinstalled today?" Ooooh yah baby, I don't ... you know hun, POGO works just fine in Linux and you have a account.....just try it...

Thanks anyway all. :)

---

### Post by kiepmad on 2007-11-18
Hehe. :D
Good luck convincing here! :)

---

