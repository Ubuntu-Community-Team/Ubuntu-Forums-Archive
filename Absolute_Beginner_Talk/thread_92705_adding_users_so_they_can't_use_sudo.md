---
title: "adding users so they can't use sudo"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by marks_linux on 2005-11-20
The message title kind of says it.

I want one user account with sudo access (the user I specified when installing) and that all other users I add cannot use sudo.

(I do most of my work in shell not the GUI desktop)

Thanks
Mark

---

### Post by frodon on 2005-11-20
Just go to System > Administration > users & groups, then when you create a new user click on it then on the property button and you will be able to manage the exact rights for each user (by default a new user have no sudo rights).

---

### Post by marks_linux on 2005-11-20
Thanks for the quick reply - you don't by chance know how to do it without the desktop?

Thanks
Mark

---

### Post by Kyral on 2005-11-20
IIRC, new users don't have sudo power by default

---

### Post by marks_linux on 2005-11-20
:oops: blushes. I logged in as the new user did sudo ls and was asked for password, but the ls returned no results. I thought that was because there were no files.

Did sudo apt-get update as the new user and got
**** not in the sudoers file.  This incident will be reported.

which is what I expected and wanted. My mistake on a cold but sunny Sunday afternoon!

thanks for the help
Mark

---

### Post by frodon on 2005-11-20
[QUOTE=marks_linux]Thanks for the quick reply - you don't by chance know how to do it without the desktop?

Thanks
Mark[/QUOTE]To create a user in command line (minimum rights by default) : ```
sudo useradd username -p password_for_this_user -d his_home_directory_path -s /bin/bash
```Type "man useradd" in the terminal if you want more details.

---

