---
title: "Freezing Ubuntu"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by Gerriec on 2006-08-13
When computer runs a 3D screensaver after a minute or so, it freezes and can only be recovered by a reboot. Why does this happen ???
It occurs with all of the screensavers that come with Ubuntu, my card is a Radeon 9200-120mb, and 1Gb Ram, and copes with 3D screensavers in Windows. Is there a setting in Ubuntu that can cause this to happen

Gerrie C.

---

### Post by Ubunme2 on 2006-08-26
Me Too!

The screensaver locks up the computer.

  I installed 6.06 on an old IBM Pentium II and some of the screensavers lock up the computer.

 (I thought this was a problem with the old computer not having enough power)

 so I installed it on a Pentium 4 2.6 with 512.

  The first thing I did was try to choose a simple screensavers so this would not happen again and it locks up the new computer completely,

 no amount of clicking or control all delete can free it up.  The only way to free it up is to hold the start button in and restart.

Can anyone help please?](*,)

---

### Post by gn2 on 2006-08-26
I had this problem as well, and cured it by selecting the blank screen option

---

### Post by wildseven on 2006-08-26
did u update your video drivers? could be overwhelming ur video card heating up and freezing.

---

### Post by Ubunme2 on 2006-08-26
I would like to choose no screensaver, but when I go to system -- preferences -- screensavers, the computer locks up completely and I cannot make any changes.

Yes all of the ATI video card drivers are updated and it works superbly when I boot into Windows.

I eagerly await any other ideas I am looking forward to using linux.

R

---

### Post by Ubunme2 on 2006-08-26
I just found the answer with a Google search, thank you Washington State University.

This post applies to users with a fairly new ATI video card.

Does your computer lock up while the screensaver is running ever since you updated to Ubuntu 5.10? The solution appears to be updating your video drivers. In the Synaptics package manager, search for and install the package xorg-driver-fglrx or from the command line type:

apt-get install xorg-driver-fglrx

It worked like a charm, I hope this helps others.

R:biggrin:

---

### Post by geezerone on 2006-09-27
Thanks for the fix and glad it worked! :)

---

