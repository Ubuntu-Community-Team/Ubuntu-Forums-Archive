---
title: "WINE Question- Permissions?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by 3pinner on 2008-02-11
I installed the latest version of WINE on Ubuntu 7.10, then installed two programs in WINE. I did thislogged on as administrator.
If I install a program in WINE, shouldn't I be able to access it as a regular user?
When I log on as a regular user, I don't even see the programs listed in WINE, nor is there a folder for either of them in my home directory. (I do see the folders for them if I log on as admin)

1) how can I install a program in WINE and make it available to all users?
 
OR

2) Do I have to install the program in WINE for each user?
I can't even scan the C/ drive as a regular user.

Thanks for the help!

---

### Post by PeterJS on 2008-02-11
> **3pinner said:**
> I installed the latest version of WINE on Ubuntu 7.10, then installed two programs in WINE. I did thislogged on as administrator.
If I install a program in WINE, shouldn't I be able to access it as a regular user?
When I log on as a regular user, I don't even see the programs listed in WINE, nor is there a folder for either of them in my home directory. (I do see the folders for them if I log on as admin)

1) how can I install a program in WINE and make it available to all users?
 
OR

2) Do I have to install the program in WINE for each user?
I can't even scan the C/ drive as a regular user.

Thanks for the help!

Wine is designed to be run as a regular user not as admin, you first want to track down where it installed and then set the permissions to something more appropriate for that user.

Also wine expects each user to have their own fake windows set up in ~/.wine/drive_c/, so by default each user will be completely separate from all the others. To set up a common wine install you're going to want to stash a folder some where (might I suggest /opt/wine/) and copy/move the registry and drive_c folder from the user that currently has the applications installed to the common location, make it world readable and writable, and then symlink the common install in to each individual users ~/.wine file. It's important that each user own there own ~/.wine directory, but it's contents don't have that same requirement, so you'll want to set the links to the elements in ~/.wine, rather than the directory itself. Good luck.

---

