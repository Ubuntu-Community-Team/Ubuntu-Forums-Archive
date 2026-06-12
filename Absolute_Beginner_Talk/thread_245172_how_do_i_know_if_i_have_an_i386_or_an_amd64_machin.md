---
title: "how do i know if i have an i386 or an amd64 machine?"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by sbrody88 on 2006-08-27
To install the Java plugin for Firefox, the Ubuntu desktop guide says to "install the sun-java5-plugin package (for i386 machines) or the j2re-1.4-mozilla-plugin package (for amd64 machines) from the Multiverse repository."  How do I know if I have an i386 machine or an amd64 machine?

---

### Post by Bachstelze on 2006-08-27
Hi and welcome to Ubuntu :)

In a terminal, type

```
uname -r
```

---

### Post by sbrody88 on 2006-08-27
it said "2.6.15-26-386"  Should I assume that means I have an i386 machine?

---

### Post by westie on 2006-08-27
mine prints out

2.6.15-26-amd64-generic

as mine is an amd64 so i'd say yes its a i386

---

### Post by encompass on 2006-08-27
That will only show what kernel you have installed... you computer may be different...
By default I think the 386 kernel is installed.  And it works fine for most.  But it may be nice to get something nice like 686 if you have a pentium 2 or better.  and then 686-smp for any processor with HT technology.  Then there is the AMD brand.  They have K6 and K7 kernels. And after all that... there is 64 bit too.
So that would be the processor you have.... I think you can look for those words in the device manager.
Hope it helps.
PS look at your computer... you may have a sticker on it telling the processor. Like mine is a celeron. That is the 686 32bit kernel.

---

### Post by encompass on 2006-08-27
You don't have a 386.  haha... never... you have a 386 based machine... it support multitasking... they have that in about 1984.  Refer to my other post.

---

### Post by Bachstelze on 2006-08-27
encompass, nice explanation but I think it will confuse him more than it wil help. He has a 386 kernel, thus he must install the sun-java5-plugin pckage. Kernel optimizations for different CPUs is another matter :)

---

### Post by sbrody88 on 2006-08-27
Okay, uname -m told me I have i686, so then going back to the original reason I needed to know this, which java plugin should I get, the sun-java5-plugin for i386 based machines?

---

### Post by sbrody88 on 2006-08-27
Ha ha, in the time I was typing my last post, my question was answered.  =P  Thanks for all your help everyone!

---

### Post by Bachstelze on 2006-08-27
Short answer : Yes.

But intalling a 686 kernel won't hurt :) (Just a tip, it has absolutely nothing to do with Java)

---

### Post by 6.*-freak on 2006-08-27
Yes, the important difference is 32- or 64-bits linux. i686 is 32-bit, so is i386.

---

### Post by b_martinez on 2006-08-27
No , it means that you have the i-386 kernel installed and need to select the -i386 java to install. I have the amd64 processor, but I am learning Xubuntu -i386 to be able to help my Grandchildren and some friends convert from MS to Linux. All the applications that you will ant to install will be based on the kernel, not necessarily the processor. 
 To learn what processor you have, you will need to know who made your box, the model and serial number. Go to the manufacturer's web site with that info, and look up the specifications. If you have an AMD 32 bit processor , you may get a bit of a boost in processing by installing the K-7 kernel.
 Hope thet I didn't confuse you too much, and that this maybe helped a bit.
Bill

---

### Post by 6.*-freak on 2006-08-27
lol i'm reading to slow:)

---

### Post by oliverb on 2006-08-27
Does that mean I can just replace the 386 kernel with the one optimised for my processor (AMD Athlon XP)?

---

### Post by Bachstelze on 2006-08-27
Yes, for an Athlon XP it would be the k7 kernel.

```
sudo apt-get install linux-k7
```

---

### Post by yossarain on 2006-08-27
i have got the following one when i typed "uname -r"
2.6.15-26-386

someone told me that my computer is a 64-bit processor one and my make is of Intel. Is it true or somone said in the posts above is it  a 32-bit one? 

just curious to know

---

### Post by Bachstelze on 2006-08-27
386 definitely is a 32 bits kernel so even if your CPU is 64bit-capable, you'll have to reinstall if you want a 64 bits system.

---

### Post by encompass on 2006-08-27
That if you want to make the effort.  Personally I don't mind the 32 bit.  But if you want to squeeze all the speed you can out of it.  Go 64.  But less software and drivers work in 64.

---

### Post by Kilz on 2006-08-28
> **encompass said:**
> That if you want to make the effort.  Personally I don't mind the 32 bit.  But if you want to squeeze all the speed you can out of it.  Go 64.  **But less software and drivers work in 64.**
Sounds like FUD to me. Drivers for all common hardware is available in the 64bit version. If you have problems with the hardware in 64bit , odds are you will have problems with the hardware in 32bit.
The same can be said of software. If you are surfing, writing emails, copying cd's, playing a few games, and listening to media. Nothing is missing. For the most part the only thing missing are some development applications. But since there are work arounds , technically nothing is missing. It just may take a little bit more setup.

---

### Post by KGH on 2006-08-28
I have a AMD Athlon64 3200+. I could not boot amd64 live CD. The 686 version booted fine.

---

