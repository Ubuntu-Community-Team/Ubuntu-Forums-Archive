---
title: "XFree 86 4.3"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by crazy757 on 2007-05-17
I am trying to install the latest driver for my video card from ATI's website.  They have a file that says it will work with Linux, but it needs XFree 86 4.3 or X.org 6.7, 6.8, 6.9, 7.0, 7.1.  I looked at both of these websites and tried to download both of them, but the download link brings me to a bunch of different packages of programs that I don't know what to do with.  Do I need to download it all?  I just don't understand what to do to install either one of these programs so I can install the latest ATI driver for my ATI Radeon X1600.

---

### Post by Bachstelze on 2007-05-17
Changing the X server your distro uses is a very complicated process. Especialy in Ubuntu, it will give you many headaches. I'd recommend either waiting for the Ati drivers to support Xorg 7.2 or diwngrade your Ubuntu to a release that runs 7.1.

EDIT : ...or buy a nvidia :p

---

### Post by crazy757 on 2007-05-17
What version does Ubuntu come with?

---

### Post by crazy757 on 2007-05-17
Is there a way to make the desktop effects run in Ubuntu with my video card?

---

### Post by Bachstelze on 2007-05-17
Feisty comes with Xorg 7.2. Edgy has Xorg 7.1 though...

I know very little about ATi cards buth this should get you started : [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by crazy757 on 2007-05-17
Okay.  I have gotten pretty far and am almost done, but I can't depackage.  What does superuser privileges mean?
This is the message it gives.  I've seen this before.
dpkg: requested operation requires superuser privilege

---

### Post by Bachstelze on 2007-05-17
Add "sudo" before your command to execute it with superuser privileges.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

