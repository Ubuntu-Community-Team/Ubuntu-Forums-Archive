---
title: "&quot;error loading operating system&quot;"
date: 2005-07-20
forum: Absolute Beginner Talk
---

### Post by geoced on 2005-07-20
Hello all !

Today I finally decided to install ubuntu on my computer but unfortunately I'm now unable to boot any OS ! Immediately after the POST finishes, i get this message : "error loading operating system" . Google had a lot of pages with this error message but so far everything i tried didn't worked.

I had 20 GB of free HDD space on my primary SATA drive. I installed ubuntu on this free space and it automatically created 3 partitions : / home and swap. The problems came when i tried to use lilo instead of grub as a boot loader and installed it on the ubuntu partition, not the mbr. It said that it failed to write it so I abort the installation.
After reboot, that's the first time I got the "error loading operating system" error.

I've tried : 
- reinstalling ubuntu this time using all default settings, said yes when it asked me for replacing the mbr with the GRUB loader. install successfull, no errors 
- under XP SP2 pro recovery console : fixboot, fixmbr, fdisk /mbr
- copying ntldr and ntdetect.com from sp2 cd to windows system partition

NOTHING worked, still the same error.

Does anybody have an idea on how to recover from this error ? 
Thanks in advance...

---

### Post by geoced on 2005-07-20
I was really discouraged when I finally managed to reboot to my Xp partition ! I'm so glad that I wont have to reformat everything again ! Two weeks ago, It took me one week to install all my programs, configure the systems etc... Redoing it just after one month would be a real pain in the a** ! :-?  

Anyway, after hours of googling I found a live linux cd based on gentoo called systemrescuecd which comes with qtparted. At first it also refused to work, same thing for knoppix. By disabling network support and forcing fb1024, I finally managed to get a prompt with systemrescuecd and launch QtParted. Then I change the "Active" partition back to my xp system partition and tataaaaaaaaaam no more error loading OS ! You can imagine how happy and relieved I  was  :grin: 

So everything back to normal... except that my free space is occupied by a "ghost" ubuntu . QtParted showed the following drives for my HDE which is a SATA seagate 250 gb HDD : 

hde1 xp system

hde2 extended xp partition containing hde5->8
hde5 xp programs
hde6 xp games
hde7 xp data
hde8 linux-swap but qt indicated that its size was 0 MB  :-? And why the hell does this linux partition is located into the extended xp partition ????

hde3 linux / partition (ext3)

I still don't know why the ubuntu setup went wrong... Maybe because it didn't set the partitions right. Or maybe I tried sth that cannot be done. Is it possible to dual boot xp-ubuntu with the way my partitions are defined ? The 20 GB free space I left when installing XP are located at the end of my sata drive where xp is installed...

---

