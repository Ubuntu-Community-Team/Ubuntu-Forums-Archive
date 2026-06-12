---
title: "EXT HDD bootable BIOS"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by patchido on 2007-12-29
my bios does support usb booting.. if i plug a 1 gb flash drive in the boot menu it appears but when i insert my 60 gigas ext HDD my boot menu wont show it. wierd huh? 
my bios is phoenix notebios 4.0 release 6.1

---

### Post by patchido on 2007-12-30
plz.... this is urgent

---

### Post by patchido on 2007-12-31
bump

---

### Post by LinuxIsInnovation on 2007-12-31
Looks like your external HDD is a SATA or SATA-II. Your BIOS may/may not support SATA drivers. Is you primary HDD SATA or is it an IDE?

---

### Post by patchido on 2007-12-31
it is SATA... anything i can do?

---

### Post by patchido on 2007-12-31
come on plzzzz help this is so urgent
|

---

### Post by patchido on 2007-12-31
is there a way to make it work with super grub?

---

### Post by patchido on 2007-12-31
im so desperate cause i just baught this HDD for this especific purpose and now it wont work

---

### Post by petteriIII on 2008-01-01
Without knowing the specific type of BIOS it is impossible to give exact advice, but so it goes generally:

Enter the BIOS by pressing Delete, f2 or what the knob might be in your machine.

When bios opens your drive must appear there somewhere in the opening page; if it doesn't appear in that first page situation may be desperate. The first page is generally titled: 'Main' 

To make it to appear in the list of bootable drives you must sometimes choose it to be the first hard-disk. You may make this happen via sub-leaf 'Hard-drives' - that sub-leaf is generally situated in leaf 'Boot'.

---

### Post by patchido on 2008-01-01
i know that but plz read my posts

---

