---
title: "superuser"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by EtherStriker on 2007-01-29
ok, as far as im aware, su is the command to go into superuser mode in regular terminal, but when it prompts for a password, i dont have one to give it, i just installed, what is the default password, or is there something else i have to configure?

---

### Post by Fasga on 2007-01-29
By default, there is no way to log in as root.  If you want to run a command as root, add the prefix 'sudo'.

---

### Post by istrebitjel on 2007-01-29
Please find the docs here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_set.2Fchange.2Fenable_root_user_password](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_set.2Fchange.2Fenable_root_user_password)

Ubuntu doesn't set a root password, but your default user has sudo permissions, so you can set it.
Btw, it's safer to not use su, but run individual commands with sudo.

---

### Post by taurus on 2007-01-29
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bustanil on 2007-01-29
try with this command:
**sudo passwd**
Password: <enter your **user **password here>
Enter new UNIX password: <enter your new **root **password here>

Then you can use **su** command using your new root password.
Hope this helps :D

---

### Post by EtherStriker on 2007-01-29
thanks for the help, but it seems i now have another problem, whenever i minimize stuff, it just disappears, nothing shows up on the lower taskbar.

---

### Post by aysiu on 2007-01-29
Right-click panel.
Add to panel.
Window list.
Add.

If, for some strange reason, you want to switch to root user, just do ```
sudo -i
``` Otherwise, you can use the GUI with ```
gksudo nautilus
``` to make root changes graphically.

---

