---
title: "Problem with upgrade to Feisty from Edgy[Resolved]"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by FotiX on 2007-05-01
I had Kubuntu 6.10. I recently upgraded it to Feisty, but after rebooting, as it is required for the upgrade, Kubuntu loads in a command line mode ( i don't know if i am making any sense, i hope you understand what i intend to say). How can i make it load in the normal mode?

---

### Post by Seisen on 2007-05-01
Did you finish installing all the updates?

---

### Post by starcraft.man on 2007-05-01
Did you remove your 3D drivers before you upgraded? If not, theres your problem right there.

If you can boot into recovery mode, switch to your default 2d drivers for your card.

EDIT: I should add the command to do this, you might not have done it before via terminal.

sudo dpkg-reconfigure xserver-xorg

Make sure that you pick nv or the ati 2d drive instead of yours.

If that doesn't work, I think [this]("http://ubuntuforums.org/showthread.php?t=422918") will fix you.

You may have to change certain things, I know its not gdm in kubuntu and if you have ati its obviously different where they specify nvidia.

---

### Post by FotiX on 2007-05-01
Seisen: Yes, i did.

starcraft.man: That seemed to do the trick. Thanks. Everything's fine now. :D

---

