---
title: "[SOLVED] cannot copy cd!"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by bhadotia on 2008-03-27
I'm trying to copy a CD with Gnome Baker but am not able to do that, the following message is coming:

     readcd: Permission denied. Cannot open '/dev/sg0'. Cannot open or use SCSI driver.
readcd: For possible targets try 'readcd -scanbus'. Make sure you are root.
readcd: For possible transport specifiers try 'readcd dev=help'.


 Can any body help?:confused:

---

### Post by thane1 on 2008-03-27
Just a shot in the dark here...  Are you sure your cd burner doesn't show up as /media/... instead of /dev/... ?  My drives show up as /media/ .  Also it sounds like you may need to do a sudo type command, judging by the prompts for root, permission denied, etc.  Did you install gnomebaker through Synaptic or did you use another method.  Mine works like a dream and all I did was install it through Synaptic.  Hope you find your answer.  Cheers.

---

### Post by DBrocks on 2008-03-27
> **bhadotia said:**
> I'm trying to copy a CD with Gnome Baker but am not able to do that, the following message is coming:

     readcd: Permission denied. Cannot open '/dev/sg0'. Cannot open or use SCSI driver.
readcd: For possible targets try 'readcd -scanbus'. Make sure you are root.
readcd: For possible transport specifiers try 'readcd dev=help'.


 Can any body help?:confused:

It seems like you don't have permission to do that. 
Open a terminal and type:
```
gksudo
```
Which will give you root access in the GUI. Give it a shot, and get back!

Good Luck!

---

### Post by bhadotia on 2008-06-22
Think I've got it thanks.

---

