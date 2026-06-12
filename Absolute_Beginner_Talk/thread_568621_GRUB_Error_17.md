---
title: "GRUB Error 17"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by tuatha1337 on 2007-10-06
I think I did something bad, if someone can help I would be greatly appreciative.

I've been using Kubuntu 7.04 for almost 9 months now, and I am very happy with it. However, I've been experimenting with other distributions and and now in need of Windows XP for school purposes.

I have 2 hard drives on my computer, one 320 GB and one 40 GB. Currently my 320 is master and 40 is slave. At first I had only Kubuntu on my 320 GB with my 40 GB HD unmounted and unused. Then I got my hands on a SUSE linux distro cd and installed it on my 40 GB. This, for some reason or another, altered my GRUB such that it would choose SUSE's version of GRUB, which was more colorful and didn't have as many boot options as Kubuntu's, rather than my original. At first this didn't cause any problems, since I could still choose to boot Kubuntu. 

However, I decided that I didn't want to stick with SUSE, it just didn't appeal to me very much, so I tried installing Windows XP on my 40GB HD, in the process unpartitioning the drive. I never completed the Windows install, as it wanted to create a partition and my 320 HD for some reason (I didn't want to do this because all my goodies are on my Kubuntu system). 

Now, I can't boot at all, unless it's from my Windows XP CD, which continues to demand that I screw around with my Kubuntu partition. Not my SUSE CD, not my burned Kubuntu CD, nor Super Grub. I am currently using my room mate's laptop. Everytime I try booting, from CDs or hard drives, GRUB gives me the following error:
```
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 17

```

All I can access on my computer now is BIOS. Yay. SOS, assist, please help! =)

---

### Post by BetaguyGZT on 2007-10-06
You've hosed GRUB.

[Repair instructions here.](http://ubuntuforums.org/showthread.php?t=114332)

---

### Post by eph1973 on 2007-10-06
That's odd.  What is your boot order in your BIOS?  It should try to boot from your CD first, before your hard drive(s).  It should not even try to check your GRUB if you have a CD in the drive, and the boot order checks the CD drive first.

---

