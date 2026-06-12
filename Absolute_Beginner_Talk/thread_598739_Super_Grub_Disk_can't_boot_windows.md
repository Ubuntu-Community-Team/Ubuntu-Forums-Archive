---
title: "Super Grub Disk can't boot windows"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by Onay on 2007-10-31
I downloaded Super Grub Disk and burned it like the guide said, since I cannot boot into my Vista install (dual boot Vista and Ubuntu 7.10). I tried using "boot windows" option, and it still boots only into the "rescue and recovery" partition. I also tried doing the "fix boot" options. No success there either.

How can I restore the NTLDR without the vista DVD? Is there something I don't know that's preventing me from booting windows?

---

### Post by gsiliceo on 2007-10-31
Super grub does not support vista, just xp.

---

### Post by meierfra on 2007-11-01
Since you resized  vista with "gparted" your vista might be corrupt. Are you able to access you vista partition from ubuntu?

---

### Post by adrian15 on 2007-11-06
> **Onay said:**
> I downloaded Super Grub Disk and burned it like the guide said, since I cannot boot into my Vista install (dual boot Vista and Ubuntu 7.10). I tried using "boot windows" option, and it still boots only into the "rescue and recovery" partition. 

Did you try the **Boot Windows from second partition** option which if it is not found on the GNU/LINUX menu it is found in the GNU/LINUX (Advanced) menu?

If it stills does not boot try to activate the second partition from **Boot & Tools -> Activate partition** menu and redo the **Boot Windows from second partition** again.

adrian15

---

