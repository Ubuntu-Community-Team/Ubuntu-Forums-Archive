---
title: "Change default OS in grub"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by seshomaru samma on 2006-05-29
I have Ubuntu in dual boot with XP . It was an XP machine and I recently formated a Windows partition and installed Ubuntu
During installation I lost grub (put it on a floppy cause I originally I didn't want to change the MBR ,but never mind) and just restored it ,now almost everything is cool ,except that Ubuntu is the default OS and I need XP to be default.
The Unofficial guide sais I should :
>    1. Read General Notes
   2.

      sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
      sudo gedit /boot/grub/menu.lst

   3. Find this line

      ...
      default         0
      ...

   4. Replace with the following line

      default         X_sequence

   5. Save the edited file (sample)

I did that and it didn't change anything
What should I do?

---

### Post by tonyr on 2006-05-29
Did you actually use the word "**X_sequence**"?  The argument for **default**
is the order **number** of the XP boot definition, relative to the other
OS boot definitions.  Counting starts at 0, which means that the default
OS is the first one defined.  If, in your **menu.lst**, the XP entry is the second
one, the line should be **default 1**.

---

### Post by seshomaru samma on 2006-05-29
[QUOTE=tonyr]Did you actually use the word "**X_sequence**"?  The argument for **default**
is the order **number** of the XP boot definition, relative to the other
OS boot definitions.  Counting starts at 0, which means that the default
OS is the first one defined.  If, in your **menu.lst**, the XP entry is the second
one, the line should be **default 1**.[/QUOTE]

ha ha
My own stupidy never fails to amaze me...
Thanks

---

### Post by joshrobinson on 2006-05-29
[QUOTE=seshomaru samma]ha ha
My own stupidy never fails to amaze me...
Thanks[/QUOTE]

thats how you learn though :D this forum is great for help

---

