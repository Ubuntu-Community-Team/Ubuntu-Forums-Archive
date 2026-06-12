---
title: "Do I need to do a complete re-install?"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Mallette on 2007-06-16
So no one seems to have heard of mode 0446 or how to get to the apparently preferable mode 0440.  As I cannot do anything without permissions and sudo does not work, about all I can figure is to completely re-install.  OTOH, since I do not know how I got into this pickle I might wind up here again.  

I even use the "lost password" methods to reset at the root level, and still I get authentication failure with su and this mode 0446 business with sudo.

I am clueless...

Dave

---

### Post by PaulFr on 2007-06-16
From the information you gave in your earlier post of mode 446 - there is a file called /etc/sudoers which should have permissions 440 (implying user can read, group can read and others cannot read or write this file). Evidently currently this file has read and write permissions for others on your system. sudo does not like that (it is a potential security breach).

So first you will need to login as root and run **chmod 440 /etc/sudoers** to restore the correct permissions for /etc/sudoers; then you should be okay without having to re-install Ubuntu.

If you have forgotten the root password or cannot login as root (without using sudo), please see **[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_gain_root_user_access_without_login](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_gain_root_user_access_without_login)** .

See [http://ubuntuguide.org/wiki/Ubuntu:Feisty#User_Administration](http://ubuntuguide.org/wiki/Ubuntu:Feisty#User_Administration) section for more pointers. Hope this helps.

---

