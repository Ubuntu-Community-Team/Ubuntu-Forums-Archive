---
title: "Formatting compact flash disks"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by jlhughes on 2006-04-16
I'm using an old compact flash card that shows up on the desktop as EOS_DIGITAL.

I want to format the disk and rename the card.

I tried the System --> Disks utility, but the "format" option for the card is grayed out.

The Disk utility identifies the current format as Windows Virtual fat.

---

### Post by htinn on 2006-04-16
It should work with gparted/qtparted/fdisk (whatever you use for partitioning/formatting).

---

### Post by hentaidan on 2006-04-16
[QUOTE=jlhughes]I tried the System --> Disks utility, but the "format" option for the card is grayed out.[/QUOTE]

Did you click on "Disable"? The disk needs to be unmounted before it can be formated.

---

### Post by jlhughes on 2006-04-16
Ah, the "Disable" button!  Didn't realize the need. Thanks for the tip.

---

