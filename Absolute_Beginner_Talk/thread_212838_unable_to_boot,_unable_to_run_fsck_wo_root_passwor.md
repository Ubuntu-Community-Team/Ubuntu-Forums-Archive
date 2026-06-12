---
title: "unable to boot, unable to run fsck w/o root password"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by bartek on 2006-07-10
I installed Breezy a few months ago, things were fine. Something happened upon boot this AM, the machine advised me that inode 1245436 has illegal blocks and that / has an UNEXPECTED INCONSISTENCY and that I should run fsck manually. 
Ok, so at the prompt asking me to enter "root password  for maintenance" I put in my password I normally sudo with (only password I have afaik) and I'm told it is not correct. 
Suggestions?

---

### Post by Paerez on 2006-07-10
I would put your ubuntu cd into the drive and boot it live, then run:
```
# sudo fsck /dev/xxxx
```
where xxxx is your root partition.

It is asking you for the root password, not your password. You can set the root password by running:
```
# sudo passwd root
```
which will ask you for your password for sudo, then the new root password.

---

