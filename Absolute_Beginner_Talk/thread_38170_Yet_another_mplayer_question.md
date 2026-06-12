---
title: "Yet another mplayer question"
date: 2005-05-30
forum: Absolute Beginner Talk
---

### Post by Error_Msg on 2005-05-30
When installing mplayer per the Ubuntuguide, the terminal prompts:
Media change: please insert the disc labeled
'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
in the drive '/cdrom/' and press enter
but I don't have a CD. 
Is there a way to get around this?

E_M

---

### Post by SGC on 2005-05-30
[QUOTE=Error_Msg]When installing mplayer per the Ubuntuguide, the terminal prompts:
Media change: please insert the disc labeled
'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
in the drive '/cdrom/' and press enter
but I don't have a CD. 
Is there a way to get around this?

E_M[/QUOTE]
 open the following file:
/etc/apt/sources.list

and then add # to  the first line, like this:
# deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)] / hoary main restricted

finally type the following in the terminal:
apt-get update

Now apt-get or synaptic will download the packages from the internet instead of using the cdrom.

---

