---
title: "Terminal Help"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by beaNN on 2006-01-15
Hi, first post so go easy =D I'm trying to download some programs via the terminal but when I do the command "su" it asks me for the password. So I enter the password for my usersccount and it auth failed. I then do the command su richard and it works, but if I do the following command:

apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev msttcorefonts libfontconfig1-dev

I get the folllow errors:

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list director

Does that mean that my user account isn't allowed to do that?

Cheers

Rich

---

### Post by Zelut on 2006-01-15
Yes.  That is telling you that you do not have permissions, as that user, to run those commands.

By default the first created user is the user that has permissions to do commands as sudo.  Anyone else must be added by someone with persmissions.

Other users can use 'su' (like you've done above) but must have the root password and the root password must be set.  To set this password, login as an administrator and use 'sudo passwd root'.

I hope that wasn't too confusing..

---

### Post by beaNN on 2006-01-15
Well as far as I know that account is the admin account. It was the first one that was created on the system.

---

### Post by Zelut on 2006-01-15
If your account was the first created you should be able to:

sudo <command>
[password]

This will let you run commands as admin.. after re-reading your original post it looks like you tried using 'su' which requires the root password to be defined.  Again, 'sudo passwd root' will do that (but sudo should be fine for you)

---

