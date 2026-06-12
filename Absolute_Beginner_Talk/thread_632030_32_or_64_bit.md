---
title: "32 or 64 bit?"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by bullon on 2007-12-05
Hi!
I'm going to intall Ubuntu sometime next week on a laptop with a 64-bit processor. My question is, are there considerable software/driver limitations when using the 64-bit version of Ubuntu? 

These are my basic hardware specs:
- Intel core 2 duo T5470 (1.6GHz)
- Intel GMA X3100 (graphics)
- Audio, Wireless are also Intel i think, integrated stuff
- Broadcom network adapter

thanks in advance!

---

### Post by PmDematagoda on 2007-12-05
No, Ubuntu 7.10 x64 is really good and very easy to use, so it should not be a problem to switch to 64 bit.

If you want a full thread on the subject of 32 bit vs. 64 bit, look [here.]("http://ubuntuforums.org/showthread.php?t=368607")

---

### Post by GSF1200S on 2007-12-05
> **PmDematagoda said:**
> No, Ubuntu 7.10 x64 is really good and very easy to use, so it should not be a problem to switch to 64 bit.

If you want a full thread on the subject of 32 bit vs. 64 bit, look [here.]("http://ubuntuforums.org/showthread.php?t=368607")

Agreed- I run 64bit and it runs awesome. The only pain is a java plugin for Firefox.

You have two options here- install the 32bit firefox and use the 32bit plugin (walkthrough as a sticky in the 64bit forums), or download swiftweasel (optimal build of firefox) and use the blackdown java plugin also available from the repos. Blackdown is less than perfect, and certain pages wont work. Most do though, so unless java is your life, it will be fine. I like to use swiftweasel, but either will do. Flash, which used to be a nightmare, is also installed in the repos now.

64bit will give a small but noticeable speed increase, unless you do encoding, where the speed increase will be much better. Almost every package available for 32bit is available for 64bit, and the few oddballs that arent can still be compiled from source. 

64bit is ready for use- if youve got the hardware, use it ;)

---

### Post by jordank on 2007-12-05
vote's up for 64!

---

### Post by tribaal on 2007-12-05
I use 64 bit too, and pretty much everything works flawlessly.
Time has come to move to a modern architecture :)

- Trib'

---

### Post by defenestratos on 2007-12-05
I have used 64 for nearly a year now and although there were some teething problems to do with my  being totally new to linux it rocks my socks now. Sooo much faster than XP or Vista.

---

### Post by GSF1200S on 2007-12-05
Oh god, I just noticed he has a broadcom wireless card.. 64bit doesnt make that any harder- the cards a PITA no matter what version you use!

---

### Post by hyper_ch on 2007-12-05
As mentioned before, there are some tiny issues with some software like java (and maybe also flash) that may not work out-of-the-box but with some research on this forum that's not a big issue ;)

---

### Post by shafin on 2007-12-05
64 bit is now almost completely ready for full adaptation,you'll run into minor java, and/or flash problems,other than that,you should take the plunge now.

---

### Post by natehall on 2007-12-05
I figure since my Ubuntu is a factory install 1420 Dell with a 64 bit processor It has 64 bit Ubuntu. Any way to tell for sure?

---

### Post by Dr Small on 2007-12-05
Try:
```
uname -m
```

---

### Post by bullon on 2007-12-05
> **GSF1200S said:**
> Oh god, I just noticed he has a broadcom wireless card.. 64bit doesnt make that any harder- the cards a PITA no matter what version you use!

when I popped the livecd in the other day i had an internet connection no problem, I figured I wouldn't have to configure it :) (As for wireless, I couldn't test it because I don't have a wireless card at home)

It seems it will be 64-bit then! Thanks for all the help!

---

### Post by natehall on 2007-12-05
> **Dr Small said:**
> Try:
```
uname -m
```I686 was the return.

---

### Post by Puptentacle on 2007-12-06
No, you have the 32 bit install, oddly enough. I get the following return on my 64 bit system. 

> x86_64

Now, why would they do that???

---

### Post by MrKlean on 2007-12-06
I tried 64 and had a problem with flash....; ) so I came back to 32...Is it easier now..in the last month ??

---

### Post by PmDematagoda on 2007-12-06
Yes, it is much easier in Ubuntu 7.10 x64, along with many other things in addition to that.

---

### Post by natehall on 2007-12-09
> **Puptentacle said:**
> No, you have the 32 bit install, oddly enough.  
Now, why would they do that???
 I posted that very question at the Dell Linux forum. Here is the answer:
"There are still a few compatibility issues related to 64-bit Linux primarily because of various closed-source vendors' lag in providing 64-bit versions of their programs. Notable examples of programs include Skype and Java. Taking into consideration the small market share, it will take patience."

---

### Post by sourcemorph on 2007-12-09
i had tried the 64 bit edgy and faced a lot of prob so i abandoned the idea n went to 32 bit... guess now its time to move forward n use my hardware...

is there a significant performance rise while playing games? and i gues i'll have to download and install all my software again for the 64 bit system right??

---

### Post by sourcemorph on 2007-12-09
one more thing.. does wine run fine with the 64 bit ubuntu??

---

### Post by fedex1993 on 2007-12-09
i would use 64 bit version. i use 64 bit verison on my laptop that has a 64 bit cpu and everything works perfect the only thing i had problems with is wireless about 1% of the time and also sound issues at first but i would use the 64 bit version

---

### Post by ptn107 on 2007-12-09
Flash and java work fine with Ubuntu 64-bit, no tweaking needed.   Just install *ubuntu-restricted-extras* and your golden.

---

### Post by MrKlean on 2007-12-13
I switched to 64 bit on my laptop...and with 2 gg memory.. it flies ; )  The flash prob is gone now..so I'm a happy jet ski'er LOL!!

---

### Post by cotcot on 2007-12-13
My 64 bit is working fine. I have checked the difference in speed between 32 and 64 bit especially for video editing and that made me go for 64 bit.
The only issue I have is that the gutenprint driver for my epson Photo Stylus RX640 gives too green and too much ink and that the pipslite driver from Epson is only 32 bit.

---

