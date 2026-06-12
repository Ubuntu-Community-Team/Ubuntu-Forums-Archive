---
title: "Remove Grub"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Mizbaby on 2007-06-12
How do I remove Grub completely so that my Windows XP will start normally instead of giving me that grub error message.  I have Ubuntu on 2 computers and tried to remove it from this computer but when I did I just deleted the Ubuntu partitions with Norton Partition Magic thinking it would then start up Windows normally.  But instead I get a grub error message and I can't get to Windows.  So I had to re-install Ubuntu.  Thanks

---

### Post by cawill on 2007-06-12
Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

Hope this works.

---

### Post by Mizbaby on 2007-06-12
Removed Grub successfully.

---

### Post by Inxsible on 2007-06-12
Mark the post as resolved, for someone else who needs to do the same thing

Thanks !

---

