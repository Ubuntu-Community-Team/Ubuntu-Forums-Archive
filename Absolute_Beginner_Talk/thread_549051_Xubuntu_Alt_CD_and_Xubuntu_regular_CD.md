---
title: "Xubuntu Alt CD and Xubuntu regular CD?"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by mashtdi on 2007-09-12
Sorry for Noobing it up here.

Ive installed Ubuntu and xubuntu about 20 or so times now just messing around with the configs and seeing which flavor I like better.

I have lots of questions....

My question is....   What is the difference between Xubuntu from the ALT CD and regular Xubuntu?   I know one is supposed to be used for PC's that are low in the Ram Department....  But exactly what has been changed to make it preform better.

Another question is,  When Ubuntu is installed i get sound out of the box and the volume controls on my laptop work.  In Xubuntu, i have to go through a long process of editing the modprobe file and re-configing "alsi" (i think thats the program)  what is the difference between the versions?  Can anyone give suggestions on what I can do to fix this little annoyance?

My ultimate goal is to load the laptop with Xubuntu (for performance) but have all of the convenience of regular Ubuntu,  e.g. Sound, DVD playback, and all other multimedia...    Once i get a good configuration I can ghost an image and ill never have to worry about config again....... untill the next version comes out!  LOL

Thanks,
Mash

---

### Post by hyper_ch on 2007-09-12
Well, the Desktop CD is a live cd... that first start a graphical interface where you can live-test how well it works... the alternate cd does just install from a text installer... so no gui loaded and hence less resource-consumpting for an install... furthermore the desktop cds more often has problems with hardware running and hence an install is more likely to fail.

Well, the sound also works out of the box in Xubuntu but you do have to configure the keys for the volume controls...
Hardware running and the base system is identical... only the desktop environment - meaning how different things interact - is different...

---

### Post by K.Mandla on 2007-09-12
hyper-ch is right, the end result is the same for both. You'll get basically the same product. The only real difference is that the installation procedure is text-based for the alternate CD, and the desktop CD does it with a GUI.

Personally, I always use the alternate CDs, but that's because I don't really need to know if the desktop will work or not. On the other hand, if you're using a machine you're not familiar with, or if you need a CD-based operating system for some reason (like rescuing files), then the desktop CD is a better option.

---

### Post by mashtdi on 2007-09-13
Ahhhhhh....   Question.... Is it possible to have both XFCE, GNOME and KDE installed on the same computer... and maybe an option of which GUI you want to run at start up?  Since your using the same Kernel anyway?

---

### Post by hyper_ch on 2007-09-13
yes, just do:

```

sudo aptitude install ubuntu-desktop

```

or 

```

sudo aptitude install kubuntu-desktop

```

or

```

sudo aptitude install xubuntu-desktop

```

or

```

sudo aptitude install edubuntu-desktop

```

---

### Post by chrome307 on 2007-09-13
'oops' thought we were discussing the merits of the 'Minimal Install CD'

---

### Post by mashtdi on 2007-09-13
yeah, got a little off topic there, im just eager to learn i guess.....

Thanks all

---

