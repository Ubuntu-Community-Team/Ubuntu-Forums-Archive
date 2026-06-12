---
title: "Error 17"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by yellowpagesguy on 2007-07-20
:( hey there i deleted the ubuntu partition and i restarted it and it says error 17 and nothing happens..it doesnt load or anything....  :(  :(  :(  :(   :(  :(

---

### Post by dca on 2007-07-20
Wait a sec, you deleted Ubuntu?  Is this a dual-boot?

---

### Post by grishenko2000 on 2007-07-20
if its grub error 17 then it means that it cant find the partition (which you just deleted) to boot from.

press esc to get to the grub menu and select a different OS

---

### Post by yellowpagesguy on 2007-07-20
yea

---

### Post by yellowpagesguy on 2007-07-20
> **grishenko2000 said:**
> if its grub error 17 then it means that it cant find the partition (which you just deleted) to boot from.

press esc to get to the grub menu and select a different OS

esc doesnt do anything :(

---

### Post by grishenko2000 on 2007-07-20
i assume your using grub (default with ubuntu installations)

what other OS(es) do you have on there?

---

### Post by yellowpagesguy on 2007-07-20
windows 98 i think :confused:

---

### Post by Campingman on 2007-07-20
When you installed Ubuntu grub overwrote the mbr on your drive, now you have deleted the partition grub cannot find the files it needs to complete the boot sequence.  If you want to have just a windows boot you will have to repair the mbr with your original windows installation cd.  When you boot with your windows disk there should be an option to repair the mbr.

---

### Post by grishenko2000 on 2007-07-20
depending on how grub is set up on your system you should be presented with a menu which you can select your OS or it says something like "Press Esc to enter grub menu..."

---

### Post by alienexplorers on 2007-07-20
Load your Windows Install disk and go into recovery mode and type in fixmbr.  Reboot your computer and windows should load.

---

