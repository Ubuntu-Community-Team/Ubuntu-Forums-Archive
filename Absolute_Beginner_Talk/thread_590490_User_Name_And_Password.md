---
title: "User Name And Password"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Mr. Blake on 2007-10-24
I began using Ubuntu about a year ago on another computer.  We got a new computer and set the old one with Ubuntu aside.  Months later I realize I need to access files that I need for school.  [COLOR="Red"]Problem[/COLOR]:  I forgot my user name and password.  Is there any way to access the files, or create another user that can access them?  Please help, the paper is due soon.

---

### Post by HermanAB on 2007-10-24
Boot into single user mode, then set user to root and change the passwords.  You don't need a password to get into single user mode.

Another option is to boot with the Ubuntu CD, then mount your disk and copy the data off.

---

### Post by Mr. Blake on 2007-10-24
How do I.... umm... boot into single user mode.

---

### Post by aysiu on 2007-10-24
> **Mr. Blake said:**
> How do I.... umm... boot into single user mode.
It's *recovery mode*, usually the second boot option in the list.

Once you're in, you don't have to set user to root. Just booting into *recovery mode* automatically makes you root.

At the command prompt, type ```
cd /home
ls
``` That will tell you what the usernames are on the computer. Then, type ```
passwd *username*
``` where *username* is the actual username. This will allow you to reset the password of the user. Finally ```
sudo reboot
``` to reboot and then select the normal boot mode.

---

