---
title: "dual booting question"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by dhani99 on 2007-07-08
So I have installed ubuntu 7.04 before and win xp pro. in a same hard drive.
so when i deleted the partition of ubuntu my xp was not able start again as it has to pass with with ubuntu's boot mode.
so i install ubuntu again and in case of i need t delete how do i rescue xp??

---

### Post by Vajra Vrtti on 2007-07-08
Use Microsoft [Recovery Console]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/recovery_console_overview.mspx?mfr=true") to restore the MBR.
Use the **fixboot** and **fixmbr** commands.

---

### Post by dhani99 on 2007-07-08
> Use the fixboot and fixmbr commands.

in recovery console?

because when i deleted that ubuntu i was getting error like grub ubuntu loading  error like that.........

---

### Post by Vajra Vrtti on 2007-07-08
> in recovery console?Yes.

---

### Post by dhani99 on 2007-07-08
okay then i should not worry but i read that i have to type administrator password, but what if i have not password will it still work?

---

### Post by Vajra Vrtti on 2007-07-08
> but what if i have not password will it still work?
I don't remember if I was asked a password or not. I did that process more than a year ago. But I do remember that it was no issue, and the whole thing was very easy to do.

If you are asked a password, I think you own Windows password will do. All Windows users use to be Administrators, don't they? It's why viruses like it so much!  

Anyway, try it while you still have Ubuntu. If anything goes wrong you can [restore grub]("http://ubuntuforums.org/showthread.php?t=224351").

---

