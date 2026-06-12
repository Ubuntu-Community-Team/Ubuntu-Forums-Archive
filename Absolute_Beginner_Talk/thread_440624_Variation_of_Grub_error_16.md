---
title: "Variation of Grub error 16"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by ferpadro on 2007-05-11
Hi all! Im posting here coz i dont know what else to do. When i turn on my computer and the several stages of grub start loading, it gets stuck on stage 1.5 and shows on screen "grub error 16". You might say "this is another one of thousands of those errors that can be fixed only changing the "User Type HDD" from LBA to Normal. Not only this isnt worknig, but once i manage to enter Linux or Windows, when i reboot the system it doesnt happen anymore. No matter how many times i reboot my machine, it doesnt happen again. It seems to be a matter of heating or something like that...I really need some feedback here coz i dont know if it is a hard disk problem, a motherboard problem or another kind of problem. 

Thanks in advance. Sorry for my bad english =)

---

### Post by dstew on 2007-05-11
How are you entering Linux? Does it just boot after you wait a while?

---

### Post by ferpadro on 2007-05-11
Not at all... I really dont know what to do, i remember installing hoary somewhat a year ago and i had the same mistake. If i leave my PC turned off all night long, and then at the morning i want to turn it on, it wont display me grub stage 2 till i do a random number of reboots. It can be just one reboot or a lot (one time i had to reboot like 50 times!). The only thing for sure is that the error message always pops in when i want to turn on my computer the day after.

---

### Post by dstew on 2007-05-11
This error is usually one of two things -- a corrupt filesystem, or a bug in grub. To see if it is a filesystem problem, boot an Ubuntu Live CD, start the desktop and run **fsck**. It will look for errors, and possibly correct them. If it is a bug in grub, you might consider seeing if there is a newer version that you could install. To check the version of grub that is on your hard disk linux installation, once you get it booted, enter **grub** at the command line, and look at the title at the top of the screen. The current version is 0.97. However, it is not going to be updated, because the developers are working on grub 2.

---

### Post by ferpadro on 2007-05-12
I booted from a Warty Live CD (coz i didnt had a newer one) and when i executed fsck it doesnt do anything except show the version of the fsck. Does the live CD has to be the same version than the one i have installed in my PC? (I have feisty btw). Second, i checked my grub version, and yes, it is the last one 0.97. I dont think it is a grub version problem coz when i installed ubuntu like 1 and a half years ago i had the same problem, and i assume the grub version was not the same one a year and a half ago that now....so im stuck. I hope its not a motherboard problem or something like that. 

btw, thanks for the feedback i really appreciate it

---

### Post by ferpadro on 2007-05-12
bump

---

### Post by ferpadro on 2007-05-12
bump #2

---

