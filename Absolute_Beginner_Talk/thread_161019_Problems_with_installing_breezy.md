---
title: "Problems with installing breezy"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by tombo on 2006-04-16
Hi
A new install of ubuntu left me with a machine I can hardly use, only a brown screen + logo after I log in with original user.

I partitioned two hard drives..... hda with / and swap, hdb with /home.

I changed 'nv' to 'vesa' in xorg.conf. and added a new user with add adduser but I have no privilges.

I did useradd -m -g admin 'newusername' and got a new account with priveliges but it only lasts for one log in it seems, and then I get the brown screen and it freezes

I can only log on to the original user thru failsafe terminal and can get minimal gui by typing in the name of the a prog.

I partitioned two hard drives..... hda with / and swap, hdb with /home.

Something pretty major is wrong but I do not know where to look.

Any help gratefuly received

---

### Post by JoshHendo on 2006-04-16
Have you installed your graphics driver? If it a graphical problem, that may help.

---

### Post by htinn on 2006-04-16
So, I take it you do *not* have an nVidia card?

---

### Post by tombo on 2006-04-16
I really do not know

When I opened up xorg.conf "nv" was there.  
I have no internet connection and do not know how to install video drivers

---

### Post by htinn on 2006-04-16
If you know you have nVidia as your video card, you really should leave "nv" there (as there's really no telling what "vesa" will do to your monitor).

---

