---
title: "Removing Linux from Bootloader"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by over_score on 2006-03-24
Installed Ubuntu on HD2, Windows was on HD1, so I allowed Linux to install it's bootloader on HD1, the bootable HD with Windows; in order to allow me to boot both OS's. My problem now is that it doesn't work. When booting from HD1 I get an error message involving the word "Grub" and, from memory, the number "8". All I want to do now is remove the Linux bootloader (Grub?) from HD1 so that I can boot into Windows.

I tryed repairing Windows using the Windows disk, of course that checked that the Windows files were 'correct', and did not remove the bootloader (as expected).

Excuse my syntax, any help appreciated,

over_score

---

### Post by dermotti on 2006-03-24
If you boot off your windows cd, theres an option for recovery console (press **R** for recovery console i belive). Boot into the recovery console and run **fixmbr**, this will put the windows bootloader back on (and erase grub).

---

### Post by over_score on 2006-03-24
That sounds extremely logical and I know what you're talking about. I'll try that now and hopefully get back to you from Windows.

(And for the record I only use Windows because of my games :D)

over_score

---

### Post by akiro.yamamoto on 2006-03-24
You can also boot from a win boot floppy and :
```

fdisk /mbr

```
Just remembered that from my old M$ days ;)

---

### Post by over_score on 2006-03-24
Thanks a heap dermotti, it worked and I could load up Windows... unfortunately some idiot ran the automated repair utility from the win2k CD before seeking advice from those more knowledgable... so lots of stuff wasn't working.

So I've reformatted, and reinstalled everything.

Thank you very much for your advice, greatly appreciated.

---

