---
title: "i386 amd64, how do i know where i am??"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by manojvekaria on 2007-03-13
I like to download the files offline so that i can save them on to a DVD, which will help others to install it as well.

The quesiton is how do i know if someone's comp will get i386 or amd64. why isn't linux like windows, just a flat .exe file.

another quesion, if i install software's with sudo get-apt, where do the .deb files get stored, so i can write them onto a Cd, and save it.?????????

---

### Post by siciliancasanova on 2007-03-13
EXE is proprietary, if my knowledge is correct.

---

### Post by The Iron Curtain on 2007-03-13
SAGE

Other than the many reasons why Linux is not like Windows, the simple fact remains that two OSes (be they Windows, Mac OS, Linux, Solaris, BSD, etc.) will NEVER be exactly alike. Yes, I know it can be frustrating when your MS knowledge doesn't help when you encounter a problem with Linux, but that just means you have to learn the Linux method. It comes down to if you want to use Linux you have to accept the fact that it is DIFFERENT from Windows, Mac OS and others, and learn how to do it the Linux way. It's just like with any other skill, you need to learn.

As for transfering files, AMD64 systems should be able to take x86 programs if you force architechture as per [this thread]("http://ubuntuforums.org/showthread.php?t=191205").
```
sudo dpkg -i --force-architecture packagename_i386.deb
```

I'm not sure how you can retrieve them. I am learning too.

---

### Post by jdong on 2007-03-13
Packages that are downloaded by apt-get are stored in **/var/cache/apt/archives**. You can pick them out, place these in another computer's cache at the same location, and apt will pick them up.

Windows "flat EXE's" are also a false notion -- on 64-bit Windows there is a different binary format, just like Linux. And in addition, Windows is based on a stable binary+source platform model, while the fast-developing, open nature of Linux causes a much faster evolution of the base system.

Windows users, with Vista, are getting the taste of what it feels like when the platform has to change to correct design mistakes. Linux just takes the liberty to undergo that more often instead of accumulating 10 year's worth of grumpy programmers ;-)

---

### Post by kinson on 2007-03-13
> **manojvekaria said:**
> 
The quesiton is how do i know if someone's comp will get i386 or amd64. why isn't linux like windows, just a flat .exe file.

Actually linux is giving you an extra selection here. When you say you install "windows xp", normally it means you're installing the 32bit(i386) version of it. There is a windows xp 64 bit, but less people use it(I personally haven't seen anybody that I know in real life use it).

So here you are presented with 2 options :)

As to your question of how would you know which version you should install on someone's computer. Here's a quote from the download site:
> 
64-bit PC (AMD64) desktop CD:
For computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon). It is not necessary for all (even most) processors made by AMD -- only their 64 bit chips.

link: [http://ftp.linux.edu.lv/pub/ubuntu/6.06/]("http://ftp.linux.edu.lv/pub/ubuntu/6.06/")


So if you're not sure which processor the person is using, just install the i386 version. :) You **can't** install the 64bit version on a 32-bit processor, but you **can** install a 32-bit version on a 64-bit processor.

To be honest, if you're new to linux, I'd suggest you just install the 32-bit(i386) version, regardless of whether you're using a 32/64-bit processor. This is mainly because there are some difficulties when finding programs for the 64-bit architecture(flash, rar etc etc). It might be daunting for a newbie. I first installed the 64 bit version myself, and I'm thinking of switching back to the i386 version sometime soon.

Hope this helped :)

Cheers,
Kinson

---

### Post by manojvekaria on 2007-03-23
Oh thanks man, especially for var/cache/apt/archives.

Is there a DVD iso, which we can download, and it has all the essential stuff in it, like automatix, beryl, e.t.c


That would be helpful

---

### Post by jdong on 2007-03-23
There is no spin with Automatix or Beryl, but there are DVD's on cdimage.ubuntu.com with more packages from the official repositories.

---

