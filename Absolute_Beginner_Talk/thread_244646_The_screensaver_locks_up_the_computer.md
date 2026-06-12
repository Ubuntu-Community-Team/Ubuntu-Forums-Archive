---
title: "The screensaver locks up the computer"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by Ubunme2 on 2006-08-26
The screensaver locks up the computer.

  I installed 6.06 on an old IBM Pentium II and some of the screensavers lock up the computer.

 (I thought this was a problem with the old computer not having enough power)

 so I installed it on a Pentium 4 2.6 with 512.

  The first thing I did was try to choose a simple screensavers so this would not happen again and it locks up the new computer completely,

 no amount of clicking or control all delete can free it up.  The only way to free it up is to hold the start button in and restart.

Can anyone help please?](*,)

---

### Post by Ubunme2 on 2006-08-26
I have an ATI radeon 9800 installed on the new comp.

Does anyone know which packages I could try to uninstall in the synaptic package manager so at least I could keep the computer from freezing up completely?

Thanx
R

---

### Post by Ubunme2 on 2006-08-26
I would like to choose no screensaver, but when I go to system -- preferences -- screensavers, the computer locks up completely and I cannot make any changes.

Yes all of the ATI video card drivers are updated and it works superbly when I boot into Windows.

I eagerly await any other ideas I am looking forward to using linux.

R](*,)

---

### Post by Ubunme2 on 2006-08-26
I just found the answer with a Google search, thank you Washington State University.

This post applies to users with a fairly new ATI video card.

Does your computer lock up while the screensaver is running ever since you updated to Ubuntu 5.10? The solution appears to be updating your video drivers. In the Synaptics package manager, search for and install the package xorg-driver-fglrx or from the command line type:

apt-get install xorg-driver-fglrx

It worked like a charm, I hope this helps others.

R:biggrin:

---

