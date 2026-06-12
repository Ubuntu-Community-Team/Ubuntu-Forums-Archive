---
title: "Moving installation"
date: 2007-04-12
forum: Apple PPC Users
---

### Post by tommoyer324 on 2007-04-12
I was wondering if anyone has ever tried to move a complete installation from one machine to another.  I have a 15" G4 Powerbook, and an 14" iBook G4 and would like to move my installation from the Powerbook to the iBook.  Is there anyway to do this without a complete re-install?  The machines are almost identical.

---

### Post by ssam on 2007-04-13
should mostly work. you may have to poke openfirmware settings to make it boot yaboot.

also you might need to run
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
on the new machine to adjust the graphics settings

it might be easier to just install and copy the home folder across.

---

