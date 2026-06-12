---
title: "No keyboard in grub with refit"
date: 2007-03-27
forum: Apple Intel Users
---

### Post by jsc1959 on 2007-03-27
I have a c2d macbook. I am using refit 0.9 and the feisty beta. If i let refit boot without a cdrom in the cdrom drive the keyboard will not work after grub comes up most of the time. If I leave a bootable cd in the drive the keyboard will work everytime grub comes up. 

Just thought this might help.

---

### Post by Chrisj303 on 2007-03-28
^ I had the same problem. I uninstalled GRUB, and installed LILO - no problems whatsoever.

In fact it's a lot more elegant soloution, as when i select windows( i triple boot) from the rEFIt menu it boots straight away - no bios-like bootloader to navigate.

Good to know about the cd trick though! It would have saved a LOT of teeth- gritting a couple months ago.

chrisj303

---

### Post by jsc1959 on 2007-03-28
I think maybe your right. lilo is probably the way to go. Ill give that a try.

I was wrong... the cd trick doesnt work 100% of the time... only about 80 % but its alot better than 20%.... lol

Thanks

---

### Post by oskarloko on 2007-03-28
With a triple boot, with xp and a grub egdy:
- Never with grub
- Sometimes with xp

But really, I don't care....

---

### Post by cyberdork33 on 2007-03-28
Mine wouldn't work when i first started dual booting, but after updates and whatnot, it started working fine. Have no idea how.

---

### Post by Azathoth_ on 2007-04-04
Try to press down key a lot of times just after you enter windows or linux in refit. It works most times

---

### Post by The_Giver on 2007-05-05
So is there anything special about removing and installing LILO .... I dont want to mess up since I have everything else working..... What are the steps I need to take?

---

