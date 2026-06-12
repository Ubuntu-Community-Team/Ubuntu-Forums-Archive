---
title: "Some Linux Questions"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by Solidad on 2006-05-24
Does linux ever need to be defragmented? looking at ubuntu i dont see any defrag option there?

---

### Post by mority on 2006-05-24
No, it doesn't. The ext2/ext3 filesystem and other filesystems used in unix/linux take care of fragmentation transparently. No need to do it manually.

---

### Post by Solidad on 2006-05-24
another thing. how can i install my Epson LX-300. printer? should i find a linux driver for it?

---

### Post by mority on 2006-05-24
Sorry, I am not very good at configuring printers. I would suggest to search for that printer model in the forums and if you don't find useful information start another topic to get help with your printer.

---

### Post by Solidad on 2006-05-24
heres another. i cant write on my mounted HD(FAT32). it says "You don't have permission" althou i am loged on the admin, (w/c is the only account so far). when i tried to see the properties on the mounted folder it was grey and on the botom it saids "You are no the Owner of this..." or something.

---

### Post by ozPATT on 2006-05-24
are you logged in as root? i had loads of that until i worked out that the default log in wasn't root. :)

---

### Post by mlind on 2006-05-24
[QUOTE=Solidad]heres another. i cant write on my mounted HD(FAT32). it says "You don't have permission" althou i am loged on the admin, (w/c is the only account so far). when i tried to see the properties on the mounted folder it was grey and on the botom it saids "You are no the Owner of this..." or something.[/QUOTE]

see [https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)

---

### Post by Solidad on 2006-05-24
should i type "root" in the username? 

i just type what i typed on the setup "solidad"

---

### Post by mlind on 2006-05-24
[QUOTE=Solidad]should i type "root" in the username? 

i just type what i typed on the setup "solidad"[/QUOTE]

In Ubuntu, using root login is discouraged. See [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Solidad on 2006-05-24
what should i do?

---

### Post by mlind on 2006-05-24
[QUOTE=Solidad]what should i do?[/QUOTE]

did you see that wiki entry about mounting foreign partitions on reply #7 ?

---

### Post by learning on 2006-05-24
I am really new too, but I use gksudo nautilus a lot to get around the permissions when I have to move files or something.

---

### Post by Solidad on 2006-05-24
and how do i do that?

---

### Post by learning on 2006-05-24
In terminal type:  gksudo nautilus

Then it will open a nautilus window for you.

---

### Post by nanotube on 2006-05-24
[QUOTE=Solidad]what should i do?[/QUOTE]
go to the first link in my sig, go to the section about mounting partitions, and it will explain the details.

---

