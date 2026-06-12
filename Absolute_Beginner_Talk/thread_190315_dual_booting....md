---
title: "dual booting..."
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by r3st on 2006-06-06
I have decided i am going to dual boot with ubuntu and windows xp

first of all will my video and sound card be supported?

this is my video card
[http://www.newegg.com/Product/Product.asp?Item=N82E16814127180](http://www.newegg.com/Product/Product.asp?Item=N82E16814127180)

and my sound card is a audigy 2 zs

and second, i have a 200GB hard drive with xp installed on a 20GB's of it.  the rest is unformatted.  how much should i use for ubuntu and should i partition the drives i want to use for windows first then install ubuntu?

---

### Post by r3st on 2006-06-06
another thing. can linux read NTFS?

---

### Post by Phasmagon on 2006-06-06
Linux can read NTFS and in some cases (with a little effort) it can write too. The best way to go though is a mutual fat partition.

A typicall installation of dapper takes a little less of 2GB. But you should have some space left for files and extra programs added after installation.

you can partition the remaining unpartitioned space any time from either windows or linux.

As for your hardware I cannot say if it is going to have the same capabilities as in windows, but in general I suspect that it is supported

---

### Post by hotbrainz on 2006-06-06
You can use the Live CD first to make sure all your hardware is Ok with Ubuntu before going for an install. Will give you a fair idea as to what isuues you might have to sort out later :)

---

### Post by Phasmagon on 2006-06-06
That is fairly true. One issue that you might encouter is that you will have to boot in safe graphics mode since ati graphics cards have proprietary drivers that do not ship with ubuntu. You will have to install them after installation using this:

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

---

### Post by r3st on 2006-06-06
what version should i use if i have an amd dual 64-bit processor?

would this work? mine is amd FX

64-bit PC (AMD64) desktop CD 
For computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon). It is not necessary for all (even most) processors made by AMD -- only their 64 bit chips.

source: [http://mirror.cs.umn.edu/ubuntu-releases/6.06/](http://mirror.cs.umn.edu/ubuntu-releases/6.06/)

---

### Post by r3st on 2006-06-06
if i wanted to remove ubuntu from my computer or reinstall it would that effect my XP install

---

### Post by carlosqueso on 2006-06-06
no, as long as you are careful not to mess with your winXP partition.  You will have GRUB still show up, but there are numerous threads out there with how to take care of that.

---

### Post by Phasmagon on 2006-06-06
> what version should i use if i have an amd dual 64-bit processor?

would this work? mine is amd FX

64-bit PC (AMD64) desktop CD
For computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon). It is not necessary for all (even most) processors made by AMD -- only their 64 bit chips.


Yes it would do just fine.
Although you should keep in mind that there are some issues with amd64 release.
As in every technonology break (e.g 16 to 32 bit processors) there is a lack of compatibility between programs, drivers, hardware and every other little thing that forms a complete working environment.
Keeping that in mind I have to say that, Flash plugin for instance is not fully supported in amd64 releases. That is because adobe has not yet released a new plugin for 64-bit environments. There is an equivalant in Ubuntu, but it is not exacly the same (some bugs may rise). Wine (win32 API to Linux API) also is not supported in amd64. Also some hardware drivers do not fully suport 64-bit.

Having said that if you are not into digging and solving problems, I would recommend for now the i386 release. Hopefully 64-bit issues will be solved soon enough. I am really looking forward to it since I only have 64-bit processors in my computers and I really hate to waste them on a 32-bit environment.

---

