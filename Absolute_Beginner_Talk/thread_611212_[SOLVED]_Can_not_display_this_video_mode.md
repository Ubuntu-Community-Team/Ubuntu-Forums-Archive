---
title: "[SOLVED] Can not display this video mode"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by maninsitu on 2007-11-12
I get this message just after I select Ubuntu to boot when starting my computer. The message stays active for about 15 seconds on a black background before the Ubuntu login screen for Username shows. Occasionally the whole system crashes necessitating in a hard boot. Could the message at the beginning have a relation to the system freezing?

Also, is there an equivalent to the Task Manager that will work when the system freezes and  you can "end task" without having to re-boot?

Thanks for any help anyone can give...really like Ubuntu. :)

I have no developer skills nor programming, but like the way users can have control over software and the OS. I use to enjoy being able to take care of issues in Windows 3.1, but over time Microsoft shut out the user. :(

---

### Post by ubnewbie2 on 2007-11-12
I can help with the first problem.  It sounds like the problem I had. The graphical boot splash screen works in a video mode that my screen didn't like.  Initially I used a program called startupmanager to configure the grub /boot/grub/menu.lst file to use a screen res of 1024x768.  That fixed the boot splash, but after I found I couldn't use ctrl-alt-F1 as the full screen console was blank.

Instead, I manually edited the kernel line for the menu.lst entry that starts ubuntu, and removed the "splash" option.  Now ubuntu boots with text messages onscreen instead of the boot splash, but it works, and ctrl-alt-F1 works as well.

---

