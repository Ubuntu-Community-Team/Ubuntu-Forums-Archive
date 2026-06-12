---
title: "Alternative Install - CDROM always required?"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by willywilly on 2006-08-17
I just reinstalled Ubuntu via the Alternative Install and now everytime I try to update my packages via the GUI or Synaptic, I get errors stating that not all directories with packets in them could be loaded. -> That means I should reinsert my Ubuntu CDROM every time I update my system.

How can I tell my system that I do not want to install any software from the CD anymore but only want to use the update-packets I can get online?

Thanks for your help. :)

---

### Post by taurus on 2006-08-17
You can modify your /etc/apt/sources.list and comment out by placing a # in front of it the first line (or the first two lines) regarding the CD-ROM...

```

sudo gedit /etc/apt/sources.list

```

---

### Post by willywilly on 2006-08-17
Ah. Now I see. That worked. :) Thank you very much.

---

### Post by DirtDawg on 2006-09-23
Yes, I second that "thank you".

---

