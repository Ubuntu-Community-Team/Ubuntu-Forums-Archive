---
title: "what other OS's are good for AMD64/ ATI200m"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by johnmxg12 on 2006-12-07
so it's been confirmed that with these specs:

AMD 64
ATI 200M express video card

you wouldn't be able to run Ubuntu to it's full potential.  there's no solid support for our drivers and its pretty much impossible to get it to 3d-render.  So my question is: what other free operating systems are out there in which i'd be able to run my computer to its full potential? 

my plan is to dual boot ubuntu with another free OS so that i can run my computer to it's full potential but still work on developing my computer with ubuntu.  

so anyone else running a solid OS with my specs?

---

### Post by igknighted on 2006-12-07
Sabayon Linux (based on gentoo, but its friendly, don't worry) is a great choice.  It has the best 64bit implementation I have found, and proprietary drivers are installed with the base system (for your ATI graphics card).  I don't know if you have any experience compiling, but you will love it in 64 bit... so much faster!  OpenSuSE also has terrific 64 bit implementation, and is also a great choice.  The new OpenSuSE 10.2 just came out today and from playing with it this afternoon it seems terrific, much better than 10.1.  Aside from these two distro's, I have found 64 bit to be very much lacking (especially in Ubuntu... I love Ubuntu, but 64bit has a long way to go here).

Edit:  I am posting from 64 bit Sabayon right now

Edit #2:  I am sorry about the ATI 200M... that is one of those cards that just performs poorly in Linux in general.  If you have interest in XGL/Beryl give sabayon a shot... it'll do the ATI driver setup and beryl setup for you

---

### Post by johnmxg12 on 2006-12-07
oh ok thanks a lot, i'll check those out, so with sabayon linux, would this operating system offer the same free software packages as Ubuntu? i love that aspect of Ubuntu, is that they give a lot of free software

---

### Post by igknighted on 2006-12-07
Sabayon offers the same basic selection as Ubuntu (actually if you download the DVD version it offers a lot more), but they also include a lot of non-oss stuff (like mp3/DVD support and binary video drivers) out of the box as well.  The difference is that Sabayon uses portage, Gentoo's package management, which tries to find the source code for programs you want to install unless you specify a binary.  Compiling from source customizes software for your PC, and it might run a little faster, but takes a long time (could be a couple hours for a large program).  Either way, portage and apt are (IMO) the best package tools in linux.  SuSE uses RPMs, which I don't really like, but I dont deal with packages too much and I really like the rest of SuSE so I live with it.

---

### Post by johnmxg12 on 2006-12-07
holy crap, the sabayon linux download is 3 gigs!!!! wow.

---

### Post by johnmxg12 on 2006-12-07
it seems like both the opensuse10.2 and the sabayon linux are both huge downloads, do you know of any alternatives that are under 700mb? like ubuntu?

---

### Post by igknighted on 2006-12-07
Sabayon has a "mini edition" which is one CD, anything else you would want is on portage.  You may need to get Sabayon 3.1 mini, as I don't think 3.2 mini is out yet (should be very soon if you want to wait).  SuSE is a big distro, if you just want to install you could just get the first three CDs, thats all you need for a standard install.

---

