---
title: "Very big problem, huge uninstallation mistake"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by guitarfreak2765 on 2007-12-29
I was uninstalling Ubuntu, and being the idiot I am, I deleted the Partition, expanded the Windows one, and only had the Windows OS running (I was on a dual boot system). I didn't even think about GRUB causing problems. I restarted my computer, and got this:

GRUB Loading stage1.5

GRUB loading, please wait...
Error 17


And that's it, can't do anything from this point. Is there anyway to fix this? I can get iso files off this comp if I need to, and I'm almost positive I have my Vista CDs here (if not here, at college for sure). What's the best way to fix this thing?

---

### Post by CCNA_student on 2007-12-29
You would have to restore the MBR. I am not sure as to how to do that but I will look.

        Sin Cere,

        CCNA

---

### Post by guitarfreak2765 on 2007-12-29
Thanks.

I've searched around, but all I've found are downloads to run BEFORE the restart, so this doesn't happen =/

---

### Post by CCNA_student on 2007-12-29
I found this web page on how to restore the MBR,[https://www.redhat.com/archives/blinux-list/2006-February/msg00104.html]("https://www.redhat.com/archives/blinux-list/2006-February/msg00104.html"). I hope that this works for you.

        Sin Cere,

        CCNA

---

### Post by Keen101 on 2007-12-29
From what I've read the **Super Grub Disk** should help you fix your problem. But, I've never actually used it myself. The website say's it can help you restore grub, to boot into Windows.


[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Sef on 2007-12-29
The code you need is ```
fdisk /mbr
```.

---

### Post by Gone fishing on 2007-12-29
Just boot from the XP recovery disk, start up the recovery console and type fixmbr. This will overwrite grub with the standard XP mbr.

I suppose a word of caution this assumes you had a standard XP mbr if it was modified by, for example a virus (ah! the joys of the Windows world) this would be bad so backing up first would be good this could easily be achieved by booting from a Ubuntu live disk and then copying your important files onto a flash disk.

---

### Post by guitarfreak2765 on 2007-12-29
I'm in the console, and this is what it says:

X:\Sources>

I typed in fdisk /mrb and it gave me:

'fdisk' is not recognized as an internal or external command, operable program or batch file


Now what? This can't be right.

---

### Post by CCNA_student on 2007-12-29
Windows XP does not have fdisk. You have to try one of the other ways we suggested.

---

### Post by guitarfreak2765 on 2007-12-29
Wow, stupid me, I was panicing and completely forgot to say I was using Vista, sorry guys =(

---

### Post by Keen101 on 2007-12-29
you could try it on the Live-CD.

---

### Post by CCNA_student on 2007-12-29
Vista also does not have fdisk.

---

### Post by Gone fishing on 2007-12-29
Try FIXMBR

look at this: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

also consider my comment about backing up first

---

### Post by guitarfreak2765 on 2007-12-29
Awesome, thanks a ton guys! Got it to work.

FixMbr was in there, I just had to type it as 'Bootrec.exe/FixMbr

It did it though, everything's working normally again. Sorry for the trouble =p

---

### Post by meindian523 on 2007-12-29
Then please mark the thread solved.

---

### Post by CCNA_student on 2007-12-29
No problem, just mark this thread as solved.

---

