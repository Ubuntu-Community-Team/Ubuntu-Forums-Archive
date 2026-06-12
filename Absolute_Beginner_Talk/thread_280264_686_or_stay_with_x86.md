---
title: "686 or stay with x86?"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by BillGod on 2006-10-19
I have been running ubuntu now for 2 months.  My system is configured and running perfectly.  I have a P4 HT processor and was looking to get the most out of it.  I used synaptic packet manager to download and install the 686 version.  When it boots it will not load gnome.  I am assuming this is due to my NVidia driver??  Should I continue to the fight with the 686 version or should I stay with my stable x86 version?  Also is there an easy way to get gnome working?

---

### Post by Grey on 2006-10-19
You need to make sure that you have installed the restricted modules for your kernel as well.  :)  The restricted modules include the nvidia firmware that your video card requires.

---

### Post by mking213 on 2006-10-19
PLEASE install the SMP kernel, i have a 3.2 Ghz HT chip, and i got at LEAST 33% more performance out of an SMP kernel.

---

### Post by BillGod on 2006-10-19
If I install restricted modules and smp will it affect my x86 install?

---

### Post by darrenm on 2006-10-19
> **BillGod said:**
> If I install restricted modules and smp will it affect my x86 install?

No. Everything should work as before except with an SMP kernel image. You will have the 686 kernel as an option on boot.

---

### Post by BillGod on 2006-10-19
ok so just to make sure I have this correct.  I need to install both 686 kernel and smp kernel.  and by booting 686 kernel smp kernel will work also?

---

### Post by mking213 on 2006-10-19
686 is the SMP kernel :)

---

### Post by darrenm on 2006-10-19
Forgotten how Dapper works now but I thought there was a separate SMP kernel aside from the 686 kernel? In Edgy there is a generic kernel that is 686 and SMP, is it now the same with Dapper too?

---

### Post by mking213 on 2006-10-19
Linux malakai 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Linux

As you see, 2.6.15-27-686 = SMP... i believe its called Linux-686.

---

### Post by barkej on 2006-10-19
From my experience the 686 and SMP are the same. I have tried both and cannot tell any difference.

---

### Post by az on 2006-10-19
When you install any kernel, use the linux-whatever metapackage.  For example, linux-686.  That brings in the kernel image and all the restricted drivers.

---

### Post by BillGod on 2006-10-19
I installed the 686 kernel and my gnome desktop will not load.  It comes up to the red and blue X error screen.  should I continue trying to screw with the video driver or am i walking down the wrong path?

---

