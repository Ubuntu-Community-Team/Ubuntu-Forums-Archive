---
title: "What Type of Computer Do I Have?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Cantabilest on 2007-04-21
Hi, I'm completely new to the world of Linux and am really looking forward to try out Ubuntu. However, I encountered some questions which I need to clarify before I could continue downloading Ubuntu.

I'm trying to download the Desktop Edition "Ubuntu 7.04 - Supported to 2008" from the Download page.

The question I came across was "What type of computer do I have?", and I was given 4 options. They are
1) Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM),
2) PowerPC based Apple computers and OpenPower/Power5 computers,
3) 64bit AMD and Intel computers,
4) Sun UltraSPARC based.

I have no idea which option to choose. I am using an Asus notebook, model A6Jm. Its processor is Genuine Intel(R) CPU T2400 @ 1.83GHz (2 CPUs). This information I got from running "dxdiag" in my Windows XP Home. As far as I know, my notebook runs on an Intel Centrino Duo Core processor (Not Core 2 Duo). I have 2048MB of 667MHz RAM.

Can someone help me with this and advise me which option I should choose? Thanks very much! Please let me know if more information about my computer is needed. Thanks again!

---

### Post by heimo on 2007-04-21
Choose the standard 32-bit x86 version. 64-bit version might work too, but you'll probably have easier time with 32-bit version.

---

### Post by ltk5 on 2007-04-21
the 32-bit x86 should work.

---

### Post by Amorphous_Snake on 2007-04-21
Yes, download the 32bit one. As far as I know, your CPU is not 64bit.

---

### Post by Cantabilest on 2007-04-21
Thanks heimo for your reply! What is 32 and 64-bit?

Anyway, I forgot to add that my Graphics Card is NVIDIA GeForce Go 7600, with Approx. Total Memory of 512.0 MB.

If I choose the standard personal computer option, will my Graphics Card be fully utilised? I'm concerned because I like to play graphic-intensive games.

Thanks!

---

### Post by heimo on 2007-04-21
> **Cantabilest said:**
> If I choose the standard personal computer option, will my Graphics Card be fully utilised? I'm concerned because I like to play graphic-intensive games.

For that, you'll probably need to install proprietary drivers. There is lots of information on these forums how to do that. My nvidia card is working just fine with Feisty, out of the box, but it's not 3D accelerated.

32bit/64bit refers to CPU architecture.

---

### Post by TimJBart on 2007-04-21
> **Cantabilest said:**
> Thanks heimo for your reply! What is 32 and 64-bit?

Anyway, I forgot to add that my Graphics Card is NVIDIA GeForce Go 7600, with Approx. Total Memory of 512.0 MB.

If I choose the standard personal computer option, will my Graphics Card be fully utilised? I'm concerned because I like to play graphic-intensive games.

Thanks!

Yes your graphics card drivers will be installed if you go to  **System>Administration>Restricted Drivers Management**   and enable them.

With regards to games, what ones are you planning on playing?  Have you checked they work on Linux?

---

### Post by amo-ej1 on 2007-04-21
32/64 bit is the size of your bus, these define how many distinct memory addresses are possible (e.g. 2^32 or 2^64). 
You graphics card doesn't chance anything on your cpu architecture. Just use the 32 bit version it'll probably work best for you.

---

### Post by jtraub on 2007-04-21
```
If I choose the standard personal computer option, will my Graphics Card be fully utilised?
```
nVidia make really good drivers for Linux. You may be sure, that your graphic card will be fully utilised

Also you should know that Ubuntu doesn't have a plenty of beautiful games.. Of course, you can use win/cedega, but no all games are well supported in these programs.

---

### Post by heimo on 2007-04-21
Also, when you get your system running, be sure to check gaming forum (under Ubuntuforums), there are lots of Ubuntu gamers who will be able to help you.
[http://ubuntuforums.org/forumdisplay.php?f=93](http://ubuntuforums.org/forumdisplay.php?f=93)

And this is worth checking:
[http://ubuntuforums.org/showthread.php?t=359892](http://ubuntuforums.org/showthread.php?t=359892)

---

### Post by volksolwagen57 on 2007-04-21
yes your graphics card can be utilized and you will have 3d accelerated support. what kinds of games do you like to play? go to [http://www.transgaming.com]("http://www.transgaming.com") where you can play the hottest windows games for a small fee or you can choose something like wine, which is a windows operating system emulator and you can play games too, although at reduced graphics quality.
32bit and 64bit architecture is just the size of a processor. 32bit has a smaller bus size, whereas 64bit is larger, enabling it to handle more information. for a gamer, just look at games such as battlefield 2, which has been out for a while now, and a new game like s.t.a.l.k.e.r. which was just released and can only be played on 64bit machines and has way better graphics.
hope this helps

---

### Post by Xarok on 2007-04-21
> **Cantabilest said:**
> 
I like to play graphic-intensive games.


Because Linux is not that widely used (yet) a lot of people don't develope their games to work on Linux so you may be disappointed that most of your games won't work on Linux.  This is basicly the same thing with the Mac OS or any other OS that is not widely used.

This does not mean that these systems are bad it's just that people don't want to invest their time and funds to develope programs that few people are going to buy.

It's sad, that in order to get people to use a system they want all their apps to work on it, but people arn't going to develope those apps for that system until a significant number of people are using it.  It's a vitious cycle.

---

### Post by Cantabilest on 2007-04-21
Thanks for all the replies and all the help! I'll go get the downloading started. I'll probably keep my Windows XP for gaming. But I'll definitely try out Wine and see how it fares. THANKS!

---

