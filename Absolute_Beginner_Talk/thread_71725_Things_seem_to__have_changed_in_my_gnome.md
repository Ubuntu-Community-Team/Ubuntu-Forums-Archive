---
title: "Things seem to  have changed in my gnome"
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2005-10-04
When i installed ubuntu on my other pc 
i had the following options:
Add applications
terminal
boot options

now i have installed it on my new pc and i have none of these! 
I managed to find the add aplications, it has changed name to sysmantic or something, but what of the others?

Also, if i want to install something like a driver that needs to be installed outside the X environment, how do i do that, as there doesnt seem to be any boot option to not start gnome.

---

### Post by Ampersand on 2005-10-04
Did you install the Breezy release? A few things have moved around since Hoary.

For the terminal, look under Applications - Accessories. I'm not sure about boot options, is it the same as Services (under System - Administration)?

I'm not sure that you'd need to install anything without the X server running, but if you do you can press Ctrl, Alt and F1 to get to a terminal, then log in and type 'sudo /etc/init.d/gdm stop' to close GDM and the X server. When you've finished, type 'sudo /etc/init.d/gdm start' to restart GDM. 

Hope this helps (:

---

### Post by Muhammad on 2005-10-04
If you did a fresh install, then you just need to update. ;)

---

### Post by dgrafix on 2005-10-04
i  used exactly the same cd for both, and just ran the updates (its breezy)

---

### Post by Ampersand on 2005-10-04
The boot manager has been removed temporarily while a few bugs are fixed, it should be back before Breezy's released on the 13th. More on it in this thread: [http://www.ubuntuforums.org/showthread.php?t=70605](http://www.ubuntuforums.org/showthread.php?t=70605)

---

### Post by darkmatter on 2005-10-04
[QUOTE=dgrafix]i  used exactly the same cd for both, and just ran the updates (its breezy)[/QUOTE]

As Amper pointed out, they're still moving things around. These issues should be fixed by the release date.

---

