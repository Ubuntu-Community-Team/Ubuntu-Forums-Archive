---
title: "Weird I/O error message when trying to use LIVE cd"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by ErichWK on 2008-04-16
First. . my specs. Asus M2n32-SLI deluxe 
64 bit Dual Core 4800+
8800 GTS
2 Gigs Ram
1x500 gig samsung (my backup)
1x500 gig Maxtor (my main)

So I am absolutely new to Linux. I've done a bunch of reading and research and decided to try out Ubuntu and see how I feel about making the jump. So I downloaded the destkop amd64 and mounted it on a cd (slowest write speed). So I get the main screen and when I would run it my screen would turn off. . . okay. Did some research and found out about deleting the "quiet splash--". I did that. 

So my screen stopped turning off but now I just get a bunch of random data coming up and after a couple of seconds I keep seeing a reoccurring phrase. "Error" and "I/O error device fd0" or "I/O error /dev fdo, secor 0"

this way bums me out because I really want to get into Linux. Any idea? Maybe I should just partition my HDD and install it. . . well. If I knew how to do that. haha.

---

### Post by Gen2ly on 2008-04-16
dense, lacks originality, totally transparent, try again indoctrinated, eh ehmm, erich

---

### Post by ErichWK on 2008-04-16
Pardon? I'm sorry, Dirk. . . I don't seem to follow. . I usually try to avoid asking questions and bothering people. But I've been searching and trying for a little over six  hours and still can't seem to figure it out.

---

### Post by kesman on 2008-04-16
> **Dirk.R.Gently said:**
> dense, lacks originality, totally transparent, try again indoctrinated, eh ehmm, erich

What? I think the post is very appropriate.

For ErichWK:

Boot back to windows and check the Md5 sum of the downloaded ISO-file and compare it to the given value in ubuntu's download section where you downloaded it in the first place. You'll find info about this in google and here in the forums too, search for md5sum check. After you've confirmed that the ISO-file is not corrupted during the download, burn it again at VERY low speed. Then try again and select the "safe graphics" mode and remove the splash and quiet as you did last time.

I/O errors can be a mark of a broken HD also.

---

### Post by kesman on 2008-04-16
Also you could try the 32-bit version, I personally think it's better for starters.

---

### Post by ErichWK on 2008-04-16
Okay! Thank you very much. I heard of the Md5sum when searching the forums but it made little sense to me how to use it. But I will sit down and learn. Also, I will try to use the 32-bit version. What is the main difference between the 32 and the 64?

---

### Post by NightwishFan on 2008-04-16
Burn cd at slow speed. Check for errors in download and burn always.

---

### Post by st33med on 2008-04-16
Main difference between 64-bit and 32-bit is that 64-bit enables more memory for use on 64-bit CPUs (32-bit computers have a limit of 4 Gigs of memory). However, there are a few hiccups with 64-bit Ubuntu because there are some apps (Like flash) that do not work natively. There are a few howto's somewhere in these forums, though.

---

### Post by NightwishFan on 2008-04-16
The general lack of compatibility of 64bit is in the past. The main difference is that more data is processed at a time than 32-bit, leading to huge performance gains in cpu intensive applications, and for general applications designed for 64, which is many of them.

---

### Post by st33med on 2008-04-16
> **NightwishFan said:**
> The general lack of compatibility of 64bit is in the past. The main difference is that more data is processed at a time than 32-bit, leading to huge performance gains in cpu intensive applications, and for general applications designed for 64, which is many of them.

I do not want to start an argument here, but there is still some incompatibilities with some software, like Flash and a few other programs. 64-bit does add a little bit of performance, but that is if you have at least 3 GB of memory.

---

### Post by NightwishFan on 2008-04-16
I do want to start an argument here. You can use more than 3gb with 32 bit anyway so that is simply not realistic reason. It is that more data is processed at the same clock rate. Sort of like adding a few more lanes to speed the flow of the same amount of cars. Also the flash plug-in is not "incompatible" it is just not made for 64bit Linux without the plug-in wrapper, and it can be used in 64bit Firefox. Also 32bit applications can be used in any case, they just will not get the bonuses for 64bit. I have 895mb of ram and I notice improvement in general performance, and great improvement in encoding audio/video. 64bit will almost always use more ram due to swollen pointers and such but it is not to the point where it would make a difference unless you have very minimal hardware, in which case you likely could not use 64 in anycase. Hardy 64 sits comfortably at 280mb of ram.

---

