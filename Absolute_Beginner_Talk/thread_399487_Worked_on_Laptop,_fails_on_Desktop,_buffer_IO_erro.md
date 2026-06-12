---
title: "Worked on Laptop, fails on Desktop, buffer I/O error hdc"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by dptxp on 2007-04-02
When I try to run the live CD on AMD Sempron 64 bit desktop with SATA drive and 256 MB ram with tested 64 bit CDs of 6.10 or 7.04, I have problems. The later does not load the KERNEL, the former loads the KERNEL but then gives Buffer I/O error on hdc, lines come with numbers, one after one.

The CDs run well on my laptop, I have eve installed 6.10 from the CD.

---

### Post by Kobalt on 2007-04-03
You can try to boot with noapic/nolapic options : when your computer boots and gets to the LivdCD boot menu (start ubutu, mem test, etc.) press F6 to access boot options and add at the enof the line, after a space > noapic nolapic

---

### Post by dptxp on 2007-04-03
Tried. Did not work. Same problems (Kernel does not load in Fiesty, Buffer I/O error Device IDC in 6.10).

I read somewhere that the 80 core cable gives problems and replacement with 40 core solves it. I am looking for a 40 core cable. My CD drive is Secondary Master, HDD is SATA, SATA mode, not RAID.

We got to have these routine problems listed and the solutions at some place. I have been assembling my computers, one in 2 or 3 years, installing Windows w/o problems. 

Thanks.

---

### Post by pixeldotz on 2007-04-10
wouldn't you lose speed and reliability by switching to a 40 cable?

reason i ask is because im going  through this same problem. im trying 6.06 currently on my desktop to see if that works. 6.10 and fiesty failed.

---

### Post by pixeldotz on 2007-04-10
so i got the LIVECD! of 6.06 to install. a little slow of course but no problems with the install. i'm currently upgrading to 6.10 EDGY using the wiki instructions. it's about 1/2 way done. if this works  then i'll be happy. try it like that see if it works for you.

---

### Post by houstonbofh on 2007-04-11
If you can set the SATA for IDE Mode in the BIOS, that can help.  Same for Windows, by the way.

---

