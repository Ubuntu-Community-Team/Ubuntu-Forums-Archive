---
title: "Ordering the Selection List"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by Shafferalex on 2007-01-25
i'm dual booting Ubuntu XP Pro & have my settings in bios to startup at a certain time but it automatically boots up ubuntu because its the first one on the selection list. I want XP to be the first one on the selection list. How do i change the order of the list so that way XP is first on the selection list?

---

### Post by Tomosaur on 2007-01-25
By changing the default line in the menu.lst file:

Type
```

gksudo gedit /boot/grub/menu.lst

```
into the command line to bring up the file you need to edit.

Alternatively, click the link in my sig :)

If you choose to edit the file manually, do NOT change the order in which the different operating systems are listed (near the bottom of the file). Just change the number shown on the 'default' line (near the top of the file). Grub counts from zero, so the first item in the menu is 0, second is 1, third is 2 etc etc etc. The line which says 'Other Operating Systems' IS included in the count.

---

### Post by spnoe on 2007-01-30
Could anyone help me. I am trying to change the Grub order of boot and have managed to get in to the Grub list via the terminal and changed the 0 to 7; as it is the 7th line where XP is listed. However, despite it being saved, the grub still does not boot to the 7th but stays on the original, first line, which is UBUNTU.
What am I doing wrong? Anyone be of help.

Most grateful.
Steve

---

### Post by meng on 2007-01-30
Are you sure that XP is the 7th ITEM or on the 7th LINE (item is more likely, I'm just checking). Change from 0 to 6, not 7.

---

### Post by spnoe on 2007-01-31
Meng, thanks for your interest. I have just managed to alter the boot-up sequence using Tomosaur´GUI, which he has supplied; I did not notice the link before. I must say that the GUI simplifies the method of changing the grub. A great program. Thanks both to Tomosaur and Meng.

Steve

---

