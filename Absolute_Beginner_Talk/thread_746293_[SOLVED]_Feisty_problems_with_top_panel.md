---
title: "[SOLVED] Feisty problems with top panel"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by dpwilson on 2008-04-05
I am not sure what happened, but on my top panel, the applications, places, system and everything on it is useless.  Typically when you mouse over it, a popup appears telling you what it is, but nothing. If I click on it nothing happens.  There is no date/time or shutdown on the left side of the panel.  My desktip does work, but nothing else.  If I boot up using root, its all there and works.  Any advice or ideas whats going on?

---

### Post by Amarsingh0793 on 2008-04-05
Have you tried creating another user account and checking if that is ok? If you canot access your Main Menu, press Alt and F2 and type "gksu users-admin"

Good Luck:)

---

### Post by dpwilson on 2008-04-05
I have tried creating one while under the root account, but couldnt figure out how to do anything under my normal one since I couldnt get anything to work.  I will try what you said and see what happens.

---

### Post by dpwilson on 2008-04-05
Alt + F2 yields nothing.  Nothing at all happens.  Anything else I can try?

---

### Post by Amarsingh0793 on 2008-04-06
At the login screen, log in with your account via a Failsafe terminal and type this command to add a user account: "adduser (newuser)" without the quotes and brackets. To assign a password to that account, type this command in a terminal: "passwd (newuser)", again without the quotes and brackets. Remember to replace (newuser) with an account name!

Hope this helps :)

---

### Post by dpwilson on 2008-04-06
> **Amarsingh0793 said:**
> At the login screen, log in with your account via a Failsafe terminal 


I hate to sound stupid, but how do I log in with a failsafe terminal?  I am pretty new to all this.  Thanks.

---

### Post by ghost_ryder35 on 2008-04-06
should be an option in the Grub boot menu to go to recovery mode

---

### Post by Amarsingh0793 on 2008-04-06
At your lgoin screen, there should be a option named "Session" or "Options".Click on whichever one of those it is and then click failsafe session and then enter your username and password.

---

### Post by dpwilson on 2008-04-07
When I logged into failsafe terminal, it wouldnt let me add a user.  It said I must be logged in as root so I sudo adduser and then it came up with some long message saying use a name matching........via the NAME-REGEX.  

Anyway, when I went to log on I switched back to gnome and voila, everything was working again.

Thanks for your help, and I learned  a little more about the sessions and the options menu.

---

### Post by dpwilson on 2008-04-07
I spoke too soon.  After I got logged in and all was working well.  I tried to download a program and the computer froze up.  No keyboard, mouse, etc.  I had to shutdown and when I restarted it was as before with nothing working on the top panel.  

So, if I try to add a user again, how do I get around the message that I need to add a user listed in the "NAME-REGEX".

---

