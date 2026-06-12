---
title: "I cannot install"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by LostJot on 2006-09-25
I go through all the partition stuff, the / partition was 5GB, and I had to create a 800MB /swap partition, which ubuntu reformatted (it also reformatted the / partition). 
I get 15% through the installation process and then it just disappears and I go back to the desktop. I try it again, same settings, this time I get 20% through the installation process and the bar and everything just disappears and I'm back to the desktop. No error messages, nothing. 

What now?

---

### Post by Cruz on 2006-09-25
In lack of a better idea I would run some hardware checks first. Diagnose the harddrive and the RAM to make sure there is no troubles with that. Hiren's boot CD has all the tools you need.

---

### Post by bodhi.zazen on 2006-09-25
Try the alternate CD.

---

### Post by CatKiller on 2006-09-25
What filesystem did you use for the / partition?

---

### Post by LostJot on 2006-09-26
On the hardware issues, I could try that, but my hard drive is literally brand new and was ticking away fine on Windows. I am on a laptop, don't know if that causes any issues. In terms of specs it's a 2.7GHz P4 with 512MB DDR RAM so everything should surely run OK. 

I will give the alternate CD a shot. Is it relatively simple to use? I am a newbie. 

The file system I am almost certain was ext3.

---

### Post by LostJot on 2006-09-26
I think I've fixed it :)

Turns out I DIDN@T format it to ext3. It was still NTFS, it just formatted the swap partition and then ended. 

Cheers, sorry for wasting your time

I will undoubtedly be back....

---

### Post by CatKiller on 2006-09-26
No worries. It's actually quite common - especially when you think of people coming across ext3 or reiserfs for the first time and having no idea what they are, and then getting the feeling that they might once have heard of NTFS or FAT.

Welcome to the Ubuntu community!

---

