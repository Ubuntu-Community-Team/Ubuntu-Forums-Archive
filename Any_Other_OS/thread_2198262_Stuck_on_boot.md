---
title: "Stuck on boot"
date: 2014-01-07
forum: Any Other OS
---

### Post by linuxn00b1 on 2014-01-07
2 days ago I did a fresh instal of windows xp, and linux mint 15 on different partitions on my laptop HD. For Mint I have a root partition, home, and swap partition. This laptop does not charge the battery. I moved and lost power while I was in the linux partition (reading another thread on this forum lol) and now I get the screen that shows linux mint, memtest, repair, and XP like normal.When I select Linux Mint it's stuck at a script that says busy box v1.20.2 built in shell (ash) under that it says initramfs with a blinking cursor. It's wierd b/c I lost power before when I ran ubuntu 10.04, 12.04, live mint (which I accidentally made persistant) and never had this problem.

I installed XP first, then linux mint from a thumb drive. I used "other option" to install/create partitions, then installed all updates. I assume I need to reinstall grub?  I found a tutorial but it seems like if you used a WUBI it's different process than a live install. Does anybody have a dummy proof tutorial for my situation, that is current? b/c I believe mint 15 doesn't support WUBI. 

Thanks in advance.

---

### Post by sammiev on 2014-01-07
Myself, I would just do a fresh install of Mint over the first one or you can use gparted to wipe the Mint install and start over with installing Mint again. I assume your XP is working at this time.

---

### Post by linuxn00b1 on 2014-01-07
XP is working , but doesn't have any of my files. I didn't wan't to have to reinstall b/c it was a pain to setup serviio and ffmpeg. I assume I can just install over the root folder and use the existing home and swap ? Is there a trick to manually installing ? b/c this is the first time I had this problem with linux, it is also the first time I didn't do 1 click install.

---

### Post by oldfred on 2014-01-08
Often after abnormal shutdowns fsck is needed like chkdsk would be needed with Windows.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by linuxn00b1 on 2014-01-08
Oldfred you are awesome!!!! Thank you so much! saved me a lot of frustration.
To anybody that might have this problem First one didn't work, 2nd worked like a charm. 
 
Question though, my root partition was dev/sda5. Is this bad? If I lose power again will this definiately happen again?

---

### Post by oldfred on 2014-01-09
That your / is sda5 is common and Linux works just as well from logical partitions as primary. But anytime system is writing something and you have a power failure, you may then have file corruption. Those really concerned add battery backup.
And issue is similar for all operating systems, Windows, Linux, and Macs. Of couse laptops have batteries, but some post same error when battery runs down.

I just assume I can run repairs, do not run system during lighting storms and try to have decent backups so I can re-install when (not if) hard drive totally fails.

---

