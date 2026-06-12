---
title: "PCI bus points to wrong place"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by Namingishard on 2006-07-26
I just installed Ubuntu but i get the stupid Xserver problem but i know why its happening, the PCI bus points to PCI:0:2:0 and my video card is on PCI:1:10:0 i used the LiveCD afew days go and i was able to change it to 1:10:0 but now that iv installed it when it fails and i type sudo dpkg-reconfigure xserver-xorg it says its unable to bring it up, 0_o, how can i change it so that it points to PCI:1:10:0.
Btw i have to login befor i can get to terminial (Course)

---

### Post by trent dillman on 2006-07-26
Use the live cd and edit your /etc/X11/xorg.conf file, and replace the PCI address there.

---

### Post by Namingishard on 2006-07-26
Hmmm

---

### Post by Namingishard on 2006-07-27
Hmm k, but im kinda new...well really new to linux so how exactly would i do that >_<

---

### Post by noham on 2006-07-28
Sorry, I'm still very new to all of this but I was wondering if you could explain the PCI bus address a little more.  I think I may be having this same problem.  I installed Ubuntu without any problems, but it seems that my PCI Bus is not being detected, none of my PCI cards are showing up.  How would I know what address Ubuntu is pointing to and more importantly, how do I find out what the correct address is that Ubuntu should be directed toward for my PCI Bus?

Thanks, I appreciate the help!!

---

