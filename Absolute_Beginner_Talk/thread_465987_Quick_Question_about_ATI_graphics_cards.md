---
title: "Quick Question about ATI graphics cards"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2007-06-06
I am about to carry out the kernel update on a friends computer, they have an ATI card which I am not familiar with. In the xorg.conf file under Section Device the driver that is being used is fglrx. If I update the kernel will it break the x server?

---

### Post by Mark_in_Hollywood on 2007-06-06
I have an ATI card (Rage Pro 128). I have updated my kernel (Feisty 7.04). Everything is working. I have not, updated to the 686 kernel, I believe this computer boots as 386 generic.

---

### Post by Nekiruhs on 2007-06-06
Not to my knowledge, the kernal shouldn't touch the xorg.conf. Did your friend have to doanything special to get it working? Just make a back up and restore if it doesnt work.  If not, worse case scenario just run
```
sudo dpkg-reconfigure xserver-xorg
```
to fix the xorg.
I'd wait for a more knowledgeable response to make sure I'm right though.

---

### Post by PartisanEntity on 2007-06-06
I am the one who installed Ubuntu for them, and I am the one who maintains their laptop :) I don't remember having had to do anything special to get the card to work, I think it worked right away, but I just thought I would double check since I am not familiar with ATI cards at all.

---

