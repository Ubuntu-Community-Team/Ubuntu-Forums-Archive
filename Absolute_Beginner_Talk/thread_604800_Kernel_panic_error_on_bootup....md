---
title: "Kernel panic error on bootup..."
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by KimoSaber on 2007-11-06
I recently updated to Feisty 7.10. Everything went smoothly. However, lately I have been getting a
blank screen when booting up. 

I'm booting to a dual boot. I have windows xp. I rarely use xp, only for some programs that I cannot get to work with linux. My hardware: Pentium 4, 1.3 Mhz, ATI Radeon card 9600, restricted drivers enabled, 800 Mb's of Rambus Ram.

I did a search on the forums and found out that other people were having the same problem. Tried the below recommendation.

Re: Long boot time on Gutsy / Black boot screen
Had the same problem - this solved it for me

- editing /etc/usplash.conf to 1024x768 (SET THIS TO YOUR SCREEN RESOLUTION DIMENSIONS)
- running
Code:

sudo update-initramfs -u -k `uname -r'

However, I am getting the following error when booting up:

Starting up...
{24.278188} Kernel panic-not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

How can undo those changes? 

Thank you for your  help in advance

---

### Post by P4man on 2007-11-08
Can you boot one of the older entries in grub ? 

If you google on that error (minus the hour stamp) you get tons of resources. None of them look very straight forward to me though, so good luck :|

---

### Post by Protagonistics on 2007-11-08
I got the exact same error today, made me raise an eyebrow. "Interesting." I said, and preceded to fix the problem by restarting, hitting escape, then changing GRUB to load my typically 32bit version of Gutsy to the Generic version. Worked. I'm wondering if it is RAM related.

anyone else's opinion?

---

### Post by Sadbird on 2007-11-08
Hi.
I had the same problem, the same message about the panic kernel not syncing stuff, and I thought my CD rom was not working, changed it, I even tried to install Windows, just in case my Linux CD was damaged, but the problem was the RAM.  I bought a new one and could install Feisty without any troubles.  Maybe you can check with a new RAM, or if you have two, try removing one or the other to check if there's the problem.  Worked for me.  Hope this helps. ;)

---

### Post by KimoSaber on 2007-11-09
Thanks for the comments. I had to do a fresh install of 7.10. I think Gutsy has a problem with specific computers. It could be the video card, using ATI Radeon Card 9600,I really don't know. Ubuntu is great. It was worth the trouble reinstalling.

Thanks.:)

---

