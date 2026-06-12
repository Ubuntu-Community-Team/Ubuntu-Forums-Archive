---
title: "Suspend to RAM not working on Mac Book Pro 10,1"
date: 2013-08-14
forum: Apple Hardware Users
---

### Post by Ashish_Bhatia on 2013-08-14
$ uname -a
Linux ashishb-MacBookPro 3.11.0-2-generic #5-Ubuntu SMP Mon Aug 12 16:09:51 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
$ dmidecode -s system-product-name
MacBookPro10,1

I am using Ubuntu 13.10
I have installed gfxcardstatus on Mac and changed my graphics card to Integrated.

When I resume from suspend, I see the login screen and then immediately it converts to a black screen with (responsive) mouse on it.
I can move the mouse around but key presses (including ctrl+option+fn+F2 etc.) does not seem to respond.
Any idea what could be going wrong here?

---

### Post by Ashish_Bhatia on 2013-08-15
Using 13.10 was a bad idea.
Just using 13.04 fixed this issue.

---

### Post by Quackers on 2013-08-21
Interesting. I have the same MBP 10,1 and am using 13-04 and although the laptop suspends when closing the lid, on opening it up again one of two things happens. The desktop appears but is totally unresponsive (but the pointer moves) or the desktop remains black (with no pointer) and I have to force close the system to get it back.
Did I miss something somewhere?
Thanks.

---

### Post by unsichtbarkeit on 2013-10-20
can anybody please confirm if macbook pro 10,1 can suspend under ubuntu? and how?
thanks

---

### Post by Quackers on 2013-10-21
I had more success when the Nvidia driver was installed. Nouveau (last I heard) did not allow for sleep/waking.
It worked better for me by selecting sleep from the menu rather than just closing the lid.

---

### Post by Infra on 2013-11-14
Hello,

I just yesterday installed Ubuntu 13.10 to my MacbookPro Retina (MBP 10,1). Everything went pretty smoothly but now I have a strange problem which i can't figure out.

My ubuntu install works fine, but if I leave my MBP idle for a long time, for example night time. This morning i went to my mbp and the screen was blank (as it should be) but then I could not get the system to wake up again. I had to force shutdown the machine and start it again to get to the desktop.

Anything I could do to get this fixed?

I installed the ubuntu with refind and used the normal 13.10 desktop iso, i couldn't find the mac version of it. Should I have done it with the mac version ISO file or does it matter anymore. I read some tutorials and others sais (they were based on 13.04 though) that you should use the mac iso, and others said to use the normal desktop ISO file.

I have a pretty fresh install so I haven't installed any software or changed any drivers.

If anyone has a solution to this.

---

