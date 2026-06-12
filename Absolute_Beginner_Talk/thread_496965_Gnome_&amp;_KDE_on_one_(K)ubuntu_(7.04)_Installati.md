---
title: "Gnome &amp; KDE on one (K)ubuntu (7.04) Installation?"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by akkim on 2007-07-09
Hi there,
i just setup an Kubuntu 7.04 Installtion on my DELL LATITUDE D600 with Radeon R250 graphics hardware which works fine. But when it comes to use a second, external monitor (TeinView), i can't get it to work.
Which drives to me to the question (don#t ask me why, more complicated): is it possible to rn both, Gnome AND KDE on one machine?
Or do i have to install the Ubuntu- OR Kubunto-Desktop on one machine?


Thanks a lot in advance,
Akkim.

---

### Post by stchman on 2007-07-09
> **akkim said:**
> Hi there,
i just setup an Kubuntu 7.04 Installtion on my DELL LATITUDE D600 with Radeon R250 graphics hardware which works fine. But when it comes to use a second, external monitor (TeinView), i can't get it to work.
Which drives to me to the question (don#t ask me why, more complicated): is it possible to rn both, Gnome AND KDE on one machine?
Or do i have to install the Ubuntu- OR Kubunto-Desktop on one machine?


Thanks a lot in advance,
Akkim.

Type:

sudo aptitude update
sudo aptitude install ubuntu-desktop

After this is done you can switch between Gnome and KDE at the login screen.

---

### Post by akkim on 2007-07-09
thanks a lot, i instaled no both and can't switch BUT my real problem (because of which i thought about this) is that i can't make my external monitor working cause i guess my xorg.conf isn't written correctly.

:-(

any ideas?
i'm lost after investigating all day!

thx!!

---

