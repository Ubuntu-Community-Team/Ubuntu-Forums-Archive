---
title: "Open Quanta Plus as root"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by jdh01 on 2007-03-04
Hi, is there a way to make Quanta (or any other program) open as root from the menu system?

$ "sudo quanta" works from the terminal so I tried putting "sudo" in front of the command in the menu layout program but it had no effect.

The reason for this is to be able to write html/php pages directly to the apache htdocs folder.  How do other people do this?

Thanks in advance, John

---

### Post by annda on 2007-03-04
you can gksudo quanta or set the permissions on your html/php files - make them writable to your group. admin is a good choice.

sudo chown root:admin *
sudo chmod 775 *

more info on permissions here:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

