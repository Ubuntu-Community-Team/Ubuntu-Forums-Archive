---
title: "How do I get Guarddog to run at startup on Ubuntu?"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by kevdog on 2007-08-22
Using guarddog as my firewall.  Im noticing however on Gnome (not with KDE), that I have to manually start this program everytime to modify the iptables before I can run any server off my computer.  Is there a way to make this run or load the iptables at startup so I can automate this process at boot?

---

### Post by Dave54 on 2007-08-22
> How do I get Guarddog to run at startup on Ubuntu?

If the command "guarddog" in terminal runs guarddog, then:
Go to "System > Preferences > Sessions"
Add a new startup program, name it, and enter for the command "guarddog".

---

### Post by kevdog on 2007-08-22
I dont want the gui to popup, I just want it to run to set the iptables in the background and then exit (that is what I do manually).  In addition I think it needs to be run as root to set the iptables based on permissions.

---

