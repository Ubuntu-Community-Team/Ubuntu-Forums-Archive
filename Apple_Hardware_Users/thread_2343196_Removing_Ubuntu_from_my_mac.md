---
title: "Removing Ubuntu from my mac"
date: 2016-11-14
forum: Apple Hardware Users
---

### Post by topmonroe9 on 2016-11-14
Hi. I have installed ubuntu as a second OS on my mac a while ago, but for some reason i don't need it anymore. Can you please help me removing it?

I have installed it using [this guide]("https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick"). As far as i understand, I made Ubuntu's partition the one that boots by default, and to boot MacOS I have to press "alt" when booting. 
Thanks for your help!

---

### Post by gsahli on 2016-11-18
I think you will need to use the Mac installer. (You didn't tell us which Mac OS version for more specifics). You have installed a linux boot loader (refit, yaboot, grub, etc) into a small partition on the drive.
You can use the Mac installer to install over the current one and it won't delete your files and programs. This won't eliminate the linux partition. To do that you'd have to repartition and install, which will lose files and apps.

---

