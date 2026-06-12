---
title: "Grub"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Tyscorp on 2007-03-30
> **Tyscorp said:**
> Also, when I get my computer, I will take my HDD with me. And when my HDD is removed the computer doesnt boot in XP. (My HDD is currently slave) Is there any way to fix it so it boots in XP with my HDD removed? I think its called 'grub'...

A while ago I asked this, I just got my PC and need to fix it so it boots and I can remove my HDD. Can someone please help me?

---

### Post by eljalill on 2007-03-30
It seems like you have to take care of the MBR here. 
Grub is a bootloader, which will let you boot several systems. So if you take out the ubuntu Hard drive, and if, as it seems, grub is partly on that (as the assigned MBR is apparently often too small), you ave to fix the mbr on the windows hard drive. You can do that with your windows CD and "fixmbr".

Fot that you have to boot from the CD in recovery mode... there should be more information here [http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058) .

OF course you could also reinstall grub on the lone left windows hard drive, but if you are not dual booting, there is not much sense in that execpt of course, if you don't have a windows CD ;) .

---

### Post by Tyscorp on 2007-03-30
The Recovery Console provides system repair and recovery functionality.
Type EXIT to quit the Recovery Console and restart the computer.

1: C:\WINDOWS

Which Windows Installation would you like to log on to
(To cancel, press ENTER)?


No idea what log on to use... Thanks for your help so far.

---

### Post by Tyscorp on 2007-03-30
Bring
My
Post
Up...

---

### Post by Tyscorp on 2007-03-30
Well... I used 1 and it worked. It then prompted for a password. Problem, there is no admin password. I am lost... Please help.

---

### Post by Tyscorp on 2007-03-30
Sorry about all these posts, but I'm getting frantic. My dad forgot the admin password -_- Is there any other way to do it?

---

