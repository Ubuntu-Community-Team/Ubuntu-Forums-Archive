---
title: "'User' problem..."
date: 2005-10-22
forum: Absolute Beginner Talk
---

### Post by vlady12 on 2005-10-22
I have a problem with loging with the root account on ubuntu!!!Why??
I even tried to create new users front roots' console, but no use......But there is another problem!the new users do not login....and in console it says something like "vlady12 is not in the sudoers file"!!!!!!!!!!  :confused: 
Can u help me???? pls. In the atachement there is a screenshot that shows the desktop with the error in gnome.....
I THINK ITS A BIG PROBLEM!I EVEN TRIED 2 REINSTALL UBUNTU, BUT NO RESULT.

---

### Post by aysiu on 2005-10-22
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by codejunkie on 2005-10-22
[quote=vlady12]I have a problem with loging with the root account on ubuntu!!!Why??
I even tried to create new users front roots' console, but no use......But there is another problem!the new users do not login....and in console it says something like "vlady12 is not in the sudoers file"!!!!!!!!!! :confused: 
Can u help me???? pls. In the atachement there is a screenshot that shows the desktop with the error in gnome.....
I THINK ITS A BIG PROBLEM!I EVEN TRIED 2 REINSTALL UBUNTU, BUT NO RESULT.[/quote] the reason you can't login as root in ubuntu is because it's disabled by default. ubuntu uses sudo for example if you wan't to login as root in a terminal you would use ```
sudo su
``` and then enter your password. if you wan't to login as root through gdm though you first have to enable the root account with this command ```
sudo passwd root
``` it will ask for an admin password, use the password of the first user you created when you installed ubuntu, then it will let you enter a new password for the root user. then go to System/Administration/Login Screen Setup and under the security tab check the box that says allow root to login through gdm now you should be able to login as root. if you have any trouble getting it to work let me know and i'd be glad to help you.

---

