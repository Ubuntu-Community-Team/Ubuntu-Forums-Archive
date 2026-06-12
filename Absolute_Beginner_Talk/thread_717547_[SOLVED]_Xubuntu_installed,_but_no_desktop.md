---
title: "[SOLVED] Xubuntu installed, but no desktop??"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by monsieurdl on 2008-03-07
I installed xubuntu using the alternative installer, and I get the logon screen. I logged on using oem and my password- is that right?

I get the prompt oem@del..$... how do I get to the desktop? :(

---

### Post by Paqman on 2008-03-07
Were you trying to do an oem install? Or do you want to use the machine for yourself? If it's for your own use you should enter your own user name and password.

---

### Post by Arthur Archnix on 2008-03-07
I did an oem install the other day, and when I rebooted it simply took me to the desktop.

If you're at a terminal prompt try typing "startx" without quotes. If that doesn't take you directly to the desktop, and your greeted with a login prompt just trying entering without a username and password. If that fails then try oem and the password you used during setup.

---

### Post by MasterJS on 2008-03-07
Try typing ```
startx
``` or```
sudo apt-get install xubuntu-desktop
```just in case it was installed.

---

### Post by monsieurdl on 2008-03-07
I know this is silly, but what is my own username? Is it the hostname I entered? It never asked me for a username during the install...

When I logged on as oem it said it didn't recognize xstart.

---

### Post by jken146 on 2008-03-07
You can reboot in Recovery Mode and type ```
ls /home
``` to find out the names of the user(s).  You can then type ```
passwd someUserName
``` to change the password of the user someUserName.

---

### Post by perixx on 2008-03-07
Hi monsieurdl,

your username is whatever name you prefer to use. Same goes to 'password'. If you entered 'oem' for username during the installation, then it's 'oem' for username at the login screen you must enter, and the password (should you dislike that username, you can always create another user account - I don't know a way how to change the username). 

What do you exactly see, after you've logged in?

perixx

---

### Post by monsieurdl on 2008-03-07
Thanks all. Much better :)

---

