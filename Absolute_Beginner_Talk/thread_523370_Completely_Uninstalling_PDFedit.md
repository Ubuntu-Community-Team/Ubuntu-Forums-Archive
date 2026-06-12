---
title: "Completely Uninstalling PDFedit"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by mak123 on 2007-08-11
How do I completely remove pdfedit?

I used the following four commands:

> sudo apt-get update
sudo apt-get install alien
wget -c [http://downloads.sourceforge.net/pdfedit/pdfedit-0.3.1-1.i386.rpm](http://downloads.sourceforge.net/pdfedit/pdfedit-0.3.1-1.i386.rpm)
sudo alien -iv pdfedit-0.3.1-1.i386.rpm

I'm using Xubuntu Feisty, and I basically want my system back to how it was before these 4 commands.

THANKS!

---

### Post by dasunst3r on 2007-08-11
When you used *alien* to install the package, it in turn used *dpkg* to install the package.  Therefore, you would want to issue this command in the terminal: *sudo dpkg -r --purge pdfedit*.  This will remove and purge any configuration files having to do with pdfedit.  if you would like to learn more about *dpkg* or any other command, type in *man {command}* (replace {command} with the command you want to learn about.  Press 'q' to exit.

---

### Post by mak123 on 2007-08-11
> **dasunst3r said:**
> When you used *alien* to install the package, it in turn used *dpkg* to install the package.  Therefore, you would want to issue this command in the terminal: *sudo dpkg -r --purge pdfedit*.  This will remove and purge any configuration files having to do with pdfedit.  if you would like to learn more about *dpkg* or any other command, type in *man {command}* (replace {command} with the command you want to learn about.  Press 'q' to exit.

Awesome.

I typed "sudo dpkg -r --purge pdfedit", and it told me that remove and purge were conflicting.

So, I decided to use "sudo dpkg -P pdfefdit".  Looks like it removed everything because when I tried "sudo dpkg -r pdfedit" afterwards, it said pdfedit wasn't even installed.

I should be good now, rite?

Thanks again!

---

### Post by dasunst3r on 2007-08-11
If you got messages that say that the package was "deselected" or "removed," you're all set.  I'll remember that it's either "remove" or "purge" -- I didn't know that the two are conflicting.  Thanks!

---

