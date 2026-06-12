---
title: "Grub Loading Stage1.5, Error 21"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by lutherhert on 2007-05-19
I installed Ubuntu 7.04. When the install finished, at the end of the booting session, I received an error message: Grub Loading Stage 1.5. Grub loading, please wait....
Error 21. 

After using the disk partitioner in the manual mode, I installed Ubuntu on the 2nd of my two hard drives. The boot loader did not install and I cannot boot to WIN XP or Ubuntu using my hard drive. I can only boot into Ubuntu using my Ubuntu disk. 

Is there a a configuration file that I can modify using a text editor to fix this situation? How can I correct this without having to completely re-install everything and possibly ending up with the same problem again? 

I have read about the problem and some of the solutions posted in the forums, but it does not appear that those solutions will work for me. I need help getting started on a resolution, prior to reformatting and starting from scratch.

---

### Post by justin whitaker on 2007-05-19
Did you try Hardware's workaround?

> 

I have a cheeky little fix for the grub Error 21 problem.

I was trying to install Ubuntu on my Dell Inspiron 3500 as I herd it had better wireless support. When I ran into the same problem. Since Ubuntu's Grub is a bit rubbish use another version instead!

The fix is, boot your laptop with a recuse cd , I this case I used one I had for fedora core 5 (I did try knoppix but that wouldn't work). When you boot up let it mount the drive, once your at prompt, type grub , then setup as normal. This takes account that you have /boot.. setup and you grub.conf/menu.1st setup. (go here to find that out - [https://help.ubuntu.com/community/Installation/FromKnoppix](https://help.ubuntu.com/community/Installation/FromKnoppix)) ie ->

grub> root (hd0,0)
-> or what every disk you want to install grub on.
then

grub> setup (hd0)

then "quit" grub and reboot.

I did say it was a cheeky fix, but it works!
Job done!


It seems that this could be a longstanding issue. The Launchpad tread goes back to 2004. 

[https://launchpad.net/ubuntu/+source/grub/+bug/8978](https://launchpad.net/ubuntu/+source/grub/+bug/8978)

---

### Post by lutherhert on 2007-05-19
> **justin whitaker said:**
> Did you try Hardware's workaround?



It seems that this could be a longstanding issue. The Launchpad tread goes back to 2004. 

[https://launchpad.net/ubuntu/+source/grub/+bug/8978](https://launchpad.net/ubuntu/+source/grub/+bug/8978)

I have a cheeky little fix for the grub Error 21 problem.

I was trying to install Ubuntu on my Dell Inspiron 3500 as I herd it had better wireless support. When I ran into the same problem. Since Ubuntu's Grub is a bit rubbish use another version instead!

The fix is, boot your laptop with a recuse cd , I this case I used one I had for fedora core 5 (I did try knoppix but that wouldn't work). When you boot up let it mount the drive, once your at prompt, type grub , then setup as normal. This takes account that you have /boot.. setup and you grub.conf/menu.1st setup. (go here to find that out - [https://help.ubuntu.com/community/In...on/FromKnoppix](https://help.ubuntu.com/community/In...on/FromKnoppix)) ie ->

grub> root (hd0,0)
-> or what every disk you want to install grub on.
then

grub> setup (hd0)

then "quit" grub and reboot.

I did say it was a cheeky fix, but it works!
Job done! 

Justin, thank you for quickly coming to my aid. I am going to try your solution this evening. What is the recuse cd that you mention above and how do I go about obtaining one? I may have some older veersions of Linux around, but I can down load a version other than Ubuntu to make the fix. Please let me know what version or exactly what it is that I need to obtain. 
Thanks

---

