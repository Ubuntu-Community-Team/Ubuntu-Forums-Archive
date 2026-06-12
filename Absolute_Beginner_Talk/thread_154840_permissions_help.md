---
title: "permissions help"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by obey43 on 2006-04-03
so for some reason when i rebooted my X would circle between a failing X server on tty7 to the tty1 login after i installed a wine program and tried to run it in fullscreen and a .sh script that tried to install a printer.

neither worked.

anyway when i restarted i was unable to start X. so i thought maybe permissions had changed from the .sh script so i tried to chmod 777 certain directories like /usr/bin and /etc or something and now i am really screwed.

how do i change all the important permissions back to their normal state?

---

### Post by johnnymac on 2006-04-03
ewww....oopsie.

That's okay - boot with your CD and go into rescue mode.  This will allow you to change the permissions.  The xorg.conf should have 

-rw-r--r--

permissions

GL

---

