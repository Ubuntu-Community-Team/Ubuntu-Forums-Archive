---
title: "Problems with b43-fwcutter on iBook G4 || Ubuntu Precise 12.04"
date: 2012-07-23
forum: Apple Hardware Users
---

### Post by abomb07 on 2012-07-23
Hello,

I have been having some trouble installing firmware on my ppc. So far I have tried a variety of things. I have gotten a wired connection and in terminal typed: sudo apt-get install b43-fwcutter

That downloaded but when I go to Additional Drivers I cant activate b43 drivers. Even when I restarted it didn't show up.

I have tried typing: sudo apt-get install firmware-b43-installer
That doesnt do anything.

Please tell me what I need to do. Thanks in advance.

---

### Post by 2blue on 2012-07-23
Have you tried to install the two restricted packages from package manager? If you search for Ubuntu restricted they should appear, and it should activate most firmware. Then a few things from the medibuntu package to make DVDs play.

---

### Post by rsavage on 2012-07-23
@abomb07, uninstall firmware-b43-installer and b43-fwcutter and follow the instructions in the PowerPC FAQ.  Sometimes if you do things in the wrong order (b43-fwcutter) it messes things up.

---

### Post by abomb07 on 2012-07-23
I fixed the problem before I looked at the replies. Thanks anyway.

---

