---
title: "is my system compatable?"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by ddos on 2007-02-09
hello first! Im a total new starter, but everyones got to start somewhere:) I dont know any programming languages, have only ever used 98/XP and dont really understand linux at all! But here I am. Ive burned the ubuntu 6.10 dvd (PC (Intel x86) install/live DVD) but get an install error when booting, saying the server X cannot start. (vga problems??)Can I just check that my system is compatable?

nvidia 8800GTX
intel core 2 duo e6700
2x 10000rpm western digital raptors in raid 0
2gb ddr2

should I be using the x64 version?

is the 8800gtx even supported?

thanks in advance, gurus!

---

### Post by Zuuswa on 2007-02-09
yes, your system should be compatible.  Not, however, with the 64 bit version.  Maybe you should try using the alternate install disc.  And, since you are new to linux, I would highly reccomend using the 6.06 version, as 6.10 is not as stable and can be trickier to set up.

---

### Post by ddos on 2007-02-09
will try that then, thanks alot!

---

### Post by kelbizzle on 2007-02-09
Yes your computer is compatible. It's just you need to reconfigure xorg.conf. 
After selecting ok. It should eventually bring you to a prompt. Type your user name and password you used during the install. Then type this into the prompt.
```
sudo dpkg-reconfigure xserver-xorg
```

Once you get your video issue resolved. You'll be good.


edit:[ I thought the INTEL core 2 duo was 64 bit?]("http://www.intel.com/personal/our-technology/core2duo/difference.htm")

---

