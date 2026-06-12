---
title: "memtest"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by ShadeOfGreen on 2006-04-03
So my new copy of Ubuntu keeps failing to boot so I went to grub and opened up memtest.

I was shocked to that after 65% completion of the test I get nothing but errors.  Not only that these errors never seem to stop and the test ceases to move past 65%.

So I'm assuming that I need to scrap that RAM.  But is this bad ram the cause of Ubuntu not being able to start?   Cause I got it up once but then it crashed and now I get the same error (explained here [http://ubuntuforums.org/showthread.php?t=154706)](http://ubuntuforums.org/showthread.php?t=154706)).

Thanks for you time.

AMD Athlon 1800+
768 DDR
Asus A78NX mobo
maxtor 120 (brand new)
Audigy 
Radeon 9800 128

---

### Post by Sef on 2006-04-03
> So I'm assuming that I need to scrap that RAM.

Not necessarily true.  Read about troubleshooting on memtest:

(Scroll to 'Troubleshooting Memory Errors')

[http://www.memtest86.com/#philo]("http://www.memtest86.com/#philo")

---

### Post by Bartender on 2006-04-03
Sef -
Thanks for the message.  I never thought to question whether memtest might not work 100% of the time.
Shade -
Can you test one RAM module at a time w/ memtest?  Or can you pull all of that memory out and try memtest'ing it on another machine, again one module at a time?  Memtest is available off the net as a download for PC's that don't have it already.  You just get the download and follow the instructions to make a bootable floppy.

---

### Post by az on 2006-04-03
[http://ubuntuforums.org/showthread.php?t=102254](http://ubuntuforums.org/showthread.php?t=102254)

Since the test is failing at 65 percent, you probably have one of your three 256 meg sticks which is faulty.

You can boot, and edit your kernel line in grub with
MEM=512 
to have the kernel ignore the ram that seems to be faulty (the first 66 percent of 768 is 512) .

Do you have three identical sticks?  Perhaps your last stick has a different timing that you need to set in your bios?

---

### Post by jason.b.c on 2006-04-03
[QUOTE=azz][http://ubuntuforums.org/showthread.php?t=102254](http://ubuntuforums.org/showthread.php?t=102254)

Since the test is failing at 65 percent, you probably have one of your three 256 meg sticks which is faulty.

You can boot, and edit your kernel line in grub with
MEM=512 
to have the kernel ignore the ram that seems to be faulty (the first 66 percent of 768 is 512) .

Do you have three identical sticks?  Perhaps your last stick has a different timing that you need to set in your bios?[/QUOTE]


Yea **AZZ** is right about this->> Do you have three identical sticks?  Perhaps your last stick has a different timing When you have differant types of ram sticks in your computer the odd one sometimes causes an error like that..!;)     If you were thinking about just buying some new ram for your computer, make sure that they are all identical.;)

---

