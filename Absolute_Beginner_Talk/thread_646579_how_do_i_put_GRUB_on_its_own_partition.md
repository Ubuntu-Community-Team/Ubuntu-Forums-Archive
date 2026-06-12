---
title: "how do i put GRUB on its own partition?"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by chips24 on 2007-12-21
i want to put GRUB on its own partition.

---

### Post by bowsercake on 2007-12-21
Is there a reason?  I don't see why you would want to.

---

### Post by chips24 on 2007-12-21
i want to remove ubuntu because im getting a cheap computer to install it on, i dualboot vista and ubuntu

---

### Post by thelatinist on 2007-12-21
If you're going to single-boot vista, why not boot to the recovery console and use fixmbr to restore ntloader?

---

### Post by chips24 on 2007-12-21
well, first i have no clue what youre talking about, and i want the easiest way to singleboot vista

---

### Post by ReverendJ1 on 2007-12-21
What thelatinist is talking about is the recovery console on your Windows CD. Put your Windows cd in your cd-rom drive, reboot your computer and it should allow you to bring up the recovery console. Then type in:
```
fixboot
fixmbr
```I am not entirely sure if this is the same process for Vista, but thats what you do in XP. It should be similar.

---

### Post by ReverendJ1 on 2007-12-21
That won't get rid of Ubuntu, it will still be sitting there taking up space, but you won't see it and your computer will boot right into Vista. Then you can either reformat the Ubuntu partition in Windows or use a partition editor and grow your partition.

---

### Post by meierfra on 2007-12-21
Click on FixMBR in my signature for three different ways to  fix the MBR. Any of those will let you boot directly into Vista,

---

### Post by thelatinist on 2007-12-21
Actually, it seems that Windows Vista is a little different.  Still, the easiest way to singleboot vista is to use Vista's native boot loader.  You can easily restore this by entering the Windows Recovery Environment (you can boot into this from and install DVD...if you don't have a DVD your OEM should have installed it on the hard drive.  Check your OEM's website for information).

1.	Put the Windows Vista installation disc in the disc drive, and then start the computer.
2.	Press a key when you are prompted.
3.	Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4.	Click **Repair your computer**.
5.	Click the operating system that you want to repair, and then click Next.
6.	In the **System Recovery Options** dialog box, click** Command Prompt**.
7.	Type** Bootrec /FixMbr**, and then press** ENTER**.

This should replace grub with the native Vista boot loader.

---

