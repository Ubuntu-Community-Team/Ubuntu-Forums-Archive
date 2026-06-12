---
title: "Choices on Dual Boot"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by mcwhitelightning on 2007-04-30
Hi, 
I'm dual booting XP and Kubuntu. I tested Ubuntu for a couple days. But I pefered the layout of Kubuntu. I'm a huge noob to linux. I've been using for a couple of weeks. WOW!!! It's like I went from a dump truck to a ferrari. What a better system. I can't believe I waited this long to give it a go. 
I just upgraded to feisty. Now I seem to be having some probs. Why do I now have 3 linux choice (plus recovery for each) and 1 XP choice? Also, If I choose the first or second linux choice I can't get my wireless card to work. If I choose option 3 I have no problems. I'm dual booting on an Averatec 3250.
If anyone has any answers feel free to pm or post.

Thanks in advance!!!

Linux may have changed the way I live!!!

---

### Post by Seisen on 2007-04-30
What are the other two options on grub?

---

### Post by mcwhitelightning on 2007-04-30
I'll reboot and write down my options.

Thanks for the quick reply!:guitar:

---

### Post by sewercake on 2007-04-30
I have the same thing, but I don't think you have to worry about it, if one of the options work, then its all ok.
cheers



-Sewercake

---

### Post by wormser on 2007-04-30
The other options are for older kernels.  It is recommended keeping atleast 2 of them.  If the newer one has issues you can boot into an older kernel.  In order to remove them from the list you can edit /boot/grub/menu.lst.

---

### Post by mcwhitelightning on 2007-04-30
It reads:
Ubuntu, Kernel 2.6.20-15 generic
(recovery)
Ubuntu, kernel 2.6.17-11 generic
(recovery)
Ubuntu, kernel 2.6.17-10 generic
(recovery)
Ubuntu memtest 86+
MS Windows XP

I just tried to connect to my wireless network using all different 3 kernels. I have 3 wireless networks available. I can see them through the connection manager but I can't connect to any of them.
I'm also having a few other minor crashes. Any way to roll back to edgy. It seemed to be much more stable. Any directions around to wipe this linux partition and reload Kubuntu edgy.

Thanks!!!

---

