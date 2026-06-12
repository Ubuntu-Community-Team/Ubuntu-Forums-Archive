---
title: "[SOLVED] Clean install with separate /home"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by BoJon on 2008-01-17
I want to confirm my understanding from reading prior threads.  I have 7.04 with /home in a separate partition.  If I install 7.10 and not format /home then all my data, inc. bookmarks, address book etc. will be untouched, right?  Same process to go from 32bit to 64bit or vice versa.  If this is OK then think I finally understand the Ubuntu's file system, mostly thanks to you all here.  Taken a while, but I'm old and slow.  Texas size thanks.

---

### Post by pytheas22 on 2008-01-17
Yes, I've had /home on a separate partition for a long time so that I can do a clean install of the system without having to backup all my personal data.  When you're doing the new install, just be sure to specify /home as the same partition that it is now (and DON'T check the format box) and you'll be fine.  You can even create the same user account in the installer for the one you use now and it won't overwrite anything.

On the downside, you won't be able to login to Gnome because it will complain about lack of permission for a file called .dmrc or something like that.  To solve that, run these commands:
```

cd /home/YOUR-USER-NAME
chmod 644 .dmrc
chown YOUR-USER-NAME .dmrc
chmod 755 /home/YOUR-USER-NAME
chown YOUR-USER-NAME /home/YOUR-USER-NAME
chown -R YOUR-USER-NAME /home/YOUR-USER-NAME
chmod -R 755 /home/YOUR-USER-NAME
```

those lines may be redundant, but they will get it working and your account on the new system be exactly the same as it was before the reinstall.

And as far as your /home partition is concerned, it could care less whether you're using a 32-bit or 64-bit build.

---

### Post by pytheas22 on 2008-01-17
by the way, since you won't be able to log in to Gnome, you can run those commands (which you should run as ROOT) by selecting the "failsafe terminal" option at the sign-in screen

---

