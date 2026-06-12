---
title: "[SOLVED] Nautilus - Restricted-Manager Message when starting desktop"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by Perpetual on 2007-09-25
New user question/observation.  I noticed (and it doesn't happen every time but sometimes) when I boot in to Ubuntu during the splash screen that shows Nautilus starting, services, peripherals, desktop etc. that sometimes I see the words 'Restricted-Manager'.  It happens so fast that if I am not expecting it, I don't see what it says.  It says nothing more and continues on to the desktop and all SEEMS to work as expected.

Can someone explain what this message means and is it part of an underlying issue?  Is there something not loading as expected which puts the OS in 'restricted-manager' mode?

Thanks!

---

### Post by Nikitas350 on 2007-09-25
The restricted manager is the "restricted drivers manager" (system--->administration--->restricted drivers manager). It handles the proprietary drivers for your system. It is not something unsafe :) You can open the restricted drivers manager and check what drivers you may can download to full utilise your system....

---

### Post by Perpetual on 2007-09-25
Ah, thanks Nikitas350.  I knew it was going to be something simple.  I did some googling and couldn't come up with a solid answer.

Now that you say that though, it makes perfect sense.

Thanks for the fast response!

---

### Post by mcduck on 2007-09-25
In case you don't need any restricted managers, or you have already installed them, you can just go to System/Preferences/Sessions and remove the restricted drivers manager from your session so it won't start any more.

---

### Post by Perpetual on 2007-09-25
> **mcduck said:**
> In case you don't need any restricted managers, or you have already installed them, you can just go to System/Preferences/Sessions and remove the restricted drivers manager from your session so it won't start any more.

Thanks.  I do not need any restricted drivers so I will make that change.

---

