---
title: "Removing A Program?"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by zlegge on 2007-02-22
How do I COMPLETELY remove a program from Ubuntu?  Am I right to just move the file to the trash?

---

### Post by Bachstelze on 2007-02-22
It depends on how you installed it. If you installed it with *apt-get install*, you can remove it with *apt-get remove*..

---

### Post by netkid91 on 2007-02-22
What program, and no.  To remove an app you must either use Synaptic, Add/Remove programs, or apt/dpkg.  If it is an app bundled with the system, run Add/Remove apps in the applications menu, and uncheck the program, it will be removed from your system (minus the config files should you decide to reinstall).

---

### Post by linux_kid on 2007-02-22
If you used Synaptic to install it (or an apt-get install ... command) you can search for the package name and choose to accept a complete removal.

---

### Post by arkangel on 2007-02-22
well depends ,  which program ?, normally deleting the folder does the trick 

most probably you want to remove the configuration files for that program 
normally in your home for example firefox have a folder ~/.mozilla or ~/.firefox
~ is your home where home is (normally) "/home/myuser"  

if this program was installed via synaptic the best way is using synaptic for uninstalling it  (this is graphical gui for apt-get)

hope it helps

---

### Post by tom56 on 2007-02-22
"Applications" - > "Add/Remove"

---

