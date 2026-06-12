---
title: "Forgotten ROOT password"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Cowdrey on 2007-01-12
Hi

I'm very new to UBUNTU!

I installed it several months ago intending to use it regularly, but have not been able to do so. I have just installed the latest version and need to amend the MENU.LST but have forgotten the ROOT password - I have tried every password I might have used to no avail.

Is there an easy way to assign a new password other than reinstalling Ubuntu?

Thanks

---

### Post by blackened on 2007-01-12
The root password is your regular user password.  Root access is disabled by default. Use sudo or gksudo instead. 
A la
```
gksudo gedit menu.lst
```

---

### Post by Indras on 2007-01-12
Sure, just reboot in single user mode.  In grub, it will be listed as "recovery mode."  You may have to hit ESC when booting to see the list.

Once it boots up in single user mode, just type "passwd root" and assign a new password, then reboot.

(of course, this is assuming you have actually set a root password... in a default Ubuntu install, there isn't one, you just sudo into it using your own login's password to temporarily gain root access)

---

### Post by Tomosaur on 2007-01-12
You can't login as root, you use the 'sudo' or 'gksudo command'. Press alt+f2, then type 'gksudo gedit /boot/grub/menu.lst' to open the gedit text editor as root. The password it asks for is YOUR password which you use to log on.

FYI: The link in my sig is for a graphical grub editor, you may wish to check it out :)

---

