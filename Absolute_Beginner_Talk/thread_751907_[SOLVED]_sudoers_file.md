---
title: "[SOLVED] sudoers file"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by xstation on 2008-04-11
user "andy is part of the admin group

in the sudoers file admin looks like this

%admin  ALL=(ALL) ALL

now if as user andy i do sudo apt-get update NO password is asked for

how do i amend the sudoers file so a password IS asked for?

thanks

xstation

---

### Post by Rocket2DMn on 2008-04-11
It will ask for a password the first time you use sudo, but then that password is good for a short while, like 5 or 10 minutes.  If you don't use sudo for that length of time, you will have to enter your password again.

---

### Post by xstation on 2008-04-11
ok thanks so long as andy  has only sudo privliages and not root.


xstation

---

### Post by joshrobinson on 2008-04-11
root in ubuntu isnt enabled, so it never gets used, sudo just gives you root privileges for a short amount of time, i think its 5 minutes, or if you close the terminal you ran it in

yes you can enable root if you really want to, but its not recommended 
(i personally enable root in terminals, but not in the gui.. sudo drives me nuts)

---

