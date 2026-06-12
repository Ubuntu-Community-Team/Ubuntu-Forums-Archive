---
title: "Sudoers file corrupted"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by Tom9999 on 2005-11-26
Help please!!  I managed to corrupt the sudoers file whilst trying to give another user sudo priviliges.  Now none of the users can use sudo so I can't change the file back, or do anything else.  Can anyone help me out - I'm an (almost) complete linux newbie.

---

### Post by Xian on 2005-11-26
Reboot into Ubuntu using the recovery mode (available from the grub menu). This will drop you into a command prompt with admin priviledges. Then you just need to issue the 'visudo' command and edit your sudoers file to fix the errors.

---

### Post by teaker1s on 2005-11-26
use live cd to access your harddisk and edit damaged file-[here]("http://ubuntuforums.org/showthread.php?t=90433")

---

### Post by Tom9999 on 2005-11-26
Thanks both, I'll try what you suggest :D

---

### Post by Tom9999 on 2005-11-26
Xian - if I go into recovery mode and get a command prompt, will a windows based application like visudo work or will I need to use something like nano?  

Anyway thanks for the help - I'm going to go and sleep on this one now before I cause any more damage tonight.

Tom

---

### Post by Xian on 2005-11-26
[QUOTE=Tom9999]Xian - if I go into recovery mode and get a command prompt, will a windows based application like visudo work or will I need to use something like nano?  [/QUOTE]
It's not exactly like that. :)

When you get a command prompt you just want to type in the command 'visudo' and then you will get a screen that will be very familiar if you have used nano before. It will take you directly to the sudoers file where you can make the needed changes.

---

