---
title: "Boot failure"
date: 2005-09-03
forum: Absolute Beginner Talk
---

### Post by nic2 on 2005-09-03
After reinstalling and opening XMMS I added ogg files to the play list and when I tried to play a song XMMS froze.  As XMMS did not want to close I just left it at that and continued with something else.  When I later wanted to shutdown nothing happened and I decided to restart X by pressing ctrl/alt/backspace.  

X restarted but did not go the log on screen – I then rebooted using the command 'sudo reboot', and now find myself in the awkward situation that I cannot boot into Ubuntu using grub's default or recovery modes [kernel 2.6.10-5-386].  

The default boot hangs just after the following:

boot
uncompressing linux ... Ok, booting the kernel.
Audit (1125760517.252:00: initialized
Starting Ubuntu ...

The recovery boot hangs just after the following:

EXT3-fs: hda2: orphan cleanup on readonly fs
kjournald starting. Commit interval 5 seconds

Why is this happening?  What can be done to sort this? 

Ps. Windows boots fine

---

### Post by phen on 2005-09-03
consider that this might be a hardware failure! my linux was totally broken, didn't boot, did not do anything while windows was just fine. it turned out to be the harddisk, which was broken where linux used to be....

if nobody else gives you a better advice, boot a livecd, do fsck.ext3 on your root partition and look for any errors. maybe it works again thereafter. save your important data if possible. make a bios hardware check (this one didn't return any errors on my hdd, but maybe you have more luck).

maybe a file corrupted while you reinstalled xmms. i do not think that this error has anything to do with wrong configuration!

hope i was able to help!

---

