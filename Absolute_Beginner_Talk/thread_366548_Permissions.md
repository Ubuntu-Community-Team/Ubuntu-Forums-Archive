---
title: "Permissions"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2007-02-21
Ok this is going to be a dumb question I know but I cannot seem to set permission for myself to drag files into the shared folder. Help please

---

### Post by tonyr1988 on 2007-02-21
What do you mean by your shared folder? Is it literally /shared ? If so, you can enable write support for yourself with the following command:

> sudo chmod 766 -R /shared

*chmod* is the Linux command for changing the permissions of a file / folder.
*766* means the owner (root) has full access (read, write, execute) and everyone else has read / write access.
*-R* stands for recursive. It means that it will apply the permission change to /shared and all files / folders within /shared.
*/shared* is the folder to change the permissions for.

You could also change the owner from root to yourself with:

> sudo chown -R *username* /shared

*chown* is the Linux command for changing the owner of a file.
*-R* is recursive.
*username* is the new owner of the files.
*/shared* is the location of the folder.

I actually prefer using chown (depending on the circumstance, ex: who needs to access the files) instead of chmod for shared folders.

One more option is this:

> gksudo nautilus

(repeat for as many as you need to drag / drop). It will look the same as normal, except you should be able to drag files into your shared folder. The only problem is that you'll have to do this every time.

---

### Post by J11Gyro on 2007-02-21
I tried to drag a theme into the folder and the message was I did not have permission to access the folder. I am kinda likw way new and am used to windows so thanks for the help.

---

### Post by J11Gyro on 2007-02-21
Tried all but cannot get the theme to install, heh learning new OS is much fun it truly is.:guitar:

---

### Post by Tomosaur on 2007-02-21
Where exactly is the shared folder? If you're talking about /share - then do not change that directories permissions.

---

### Post by J11Gyro on 2007-02-26
Thanks for the terminal nautilus:guitar:  tip   worked like a champ

---

