---
title: "Freezes at load screen..."
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by Shadonova on 2008-02-22
Ok So IDK if any of you remember me, but I had been having alot of trouble installing the darn 7.04


If you need details, read my other post. So I FINALLY get it installed with the alternate cd...



And now, when I boot it up, It freezes at the load screen. It loads to about the 3rd little block, and then just stops....



What do I do now...I want to pull my hair out...Almost 24 hours of this crap...



PLEASE HELP!

---

### Post by Shadonova on 2008-02-22
Cmon people please....

---

### Post by spiderbatdad on 2008-02-22
So, just to be clear...have you made an installation and now can't boot into it, or are you still trying to load the livecd?

---

### Post by zakirs on 2008-02-22
also whats your config ?

---

### Post by Shadonova on 2008-02-22
Ok i installed the entire thing. I used the alternate cd.

It starts to load normally. You know, UBUNTU comes up and the bar starts to fill up....then just stops...



I have a amd turion 64x2....Nvidia 6150 fx card. 2gig ram....I have installed 7.04 cause 7.10 doesnt really work good with dv9000 laptops...


so cmon people...advice please.

---

### Post by spiderbatdad on 2008-02-22
Try booting into recovery mode or command line, and edit your /boot/grub/menu.lst file like this.```
nano /boot/grub/menu.lst
``` (small "L" not 1st)  Scroll down till you see ####END DEFAULT OPTIONS##### and look at the block of text just below that. On the line that begins with Kernel, go to the end of the  line and delete ro --quiet splash. Replace with noapic nolapic vga=792
save with ctrl-o exit with ctrl-x

See this wiki for an explanation of what's going on with your pc: [https://wiki.ubuntu.com/HP_dv6000_Series](https://wiki.ubuntu.com/HP_dv6000_Series)

And you might want a quick look at a few nano commands, if you've never used nano: [http://mintaka.sdsu.edu/reu/nano.html](http://mintaka.sdsu.edu/reu/nano.html)

---

