---
title: "Login Password"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by wedoo2 on 2008-01-17
I have just started upgrading a ver 6 to 7.  The login screen comes on and is asking for my login and password.  Either I have gone brain dead or the start up just cannot recognize my password.  Is there a workaround here.  I'm not trying to bust into someone else's computer.  I have tried several different ways to type it.

---

### Post by p_quarles on 2008-01-17
Which login screen? Are you talking about the package manager? Or the Gnome login manager? 

Anyway, it's easy to set a new password for your user, but I need a clearer idea of where you are in the upgrade process first.

---

### Post by wedoo2 on 2008-01-17
I am at a light brown / tan screen with the Ubuntu logo.  In the bottom left is an options shortcut.

---

### Post by p_quarles on 2008-01-17
So you have already upgraded? 

Anyway, here's what you do. Under "options," choose "restart" to reboot the computer. Next, when you get just past the BIOS screen, hit "escape" to enter the boot menu. From here, choose "recovery mode."

This will give you a root shell, and you can now reset your password by typing:
```
passwd *your-user-name*
```
It will prompt you to type the new password twice, and you're now good to go. Type:
```
shutdown -r now
```
to reboot the computer again.

---

### Post by wedoo2 on 2008-01-17
I appreciate this help.  I rebooted the computer, but it did not actually reboot.  I went back to what I think is the set up routine.  I got line after line of what appears to be error codes  I/O errors, SQUASH... something errors in boot sectors.  As if it is checking the HDD for errors.  Then it goes through all of that.  I got back to a blue screen with a flower on it and the username and password would not work again.  Rebotted from the options and it is going through the same thing.  Uugghh

What now?

---

### Post by p_quarles on 2008-01-17
The setup screen? Do you have an installation disk in the CD drive?

---

