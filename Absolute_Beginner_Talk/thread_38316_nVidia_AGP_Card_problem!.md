---
title: "nVidia AGP Card problem!"
date: 2005-05-31
forum: Absolute Beginner Talk
---

### Post by reynoldlariza on 2005-05-31
greetings to al members and developers of Ubuntu linux!

I have received the ubuntu CDs version 5.04

I installed it instantly on my one PC with spec:

PIII 733MHz
256MB RAM (PC-133)
nVidia Riva TnT2 AGP Graphics Card (32 MB)
and others are just fine.

my problem is with the AGP card. Ubuntu is complaining it can't load the X-server.

I tried it too on my AMD Duron 1GHz with 196MB RAM and same AGP card, yet the problem is exactly the same.

I switched to my S3 Savage 3D (PCI, 16MB) and whoa! it works without problems and the X-server loads without problems.

I don't get it? why doesn't it work with my AGP?  ](*,) 
am I missing something? :-? 
please help ;-)

---

### Post by sethmahoney on 2005-05-31
It might not work, but have you tried loading the nvidia drivers?

---

### Post by reynoldlariza on 2005-05-31
you mean like, loading the nVidia glx from the list of packages? 
and then switch to my AGP again?
yes I did, still it complains of inability of loading the x-server

P.S.
I even tried the command about it to the terminal in the recovery mode.

If you're really pointing for a linux driver for nVidia, How do I install one?

sorry, I'm kind'a noob with linux, and ubuntu is my first. ;-)

---

### Post by somuchfortheafter on 2005-05-31
i just had the same problem about 30 mins ago and a reinstall fixed mine for my 5600 ultra however it doesnt seem to help you in your case, have you tried editing the xorg.conf file by hand with
sudo apt-get install pico
whereis xorg.conf
sudo pico -w *insertdirectoriestoxorg.conf*
then typing to use the nv driver and then rebooting?
the third step should look somthing like this
sudo pico -w /etc/x11/xorg.conf *note this is not the real answer so dont use it*

---

### Post by reynoldlariza on 2005-05-31
i think i'm gonna try installing the nVidia driver later, Im at school now ;-) 
I looked on the nVidia website and they have the driver for linux. I'll try download it at home, and then configure it as the readme file is saying.

Sadly I'm have an intuition that I might need to re-install ubuntu to make to recognize the AGP card, I think ;-)

---

### Post by sethmahoney on 2005-05-31
There are instructions for installing the actual nvidia driver on this forum if you do a search.  Good luck!  And if it comes to it, reinstalling Ubuntu isn't the big deal that reinstalling, say, Windows is.

---

### Post by codejunkie on 2005-05-31
you could also try sudo dpkg-reconfigure xserver-xorg and choose vesa as the driver instead of nv that might help you get x up and running until you install the nvidia driver for your card.

---

