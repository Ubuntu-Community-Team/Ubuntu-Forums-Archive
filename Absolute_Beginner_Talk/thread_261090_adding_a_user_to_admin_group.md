---
title: "adding a user to admin group"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by yeehawjared on 2006-09-19
Is there any way I can add super user priviledges to my user?

only one person logs onto into my ubuntu  - jared
is there any way I can put jared into the admin/SU group?

My goal is to not type sudo every 15 minutes.  Is this possible?  I know I can just log in as root (after enabling account) but I want to stick with jared.

Can I do this under System>Administration>Users and Groups?

---

### Post by LadyDoor on 2006-09-19
Here's the thing--you're forced to use sudo for a reason. Essentially, it's all too possible to accidentally type something that could have very destructive consequences (eg., rm -rdf / home/username/spam instead of rm -rdf /home/username/spam). Therefore, sudo forces the user to type a root password before doing something that could trash the system. In addition, if you were to leave your computer unattended, in theory somebody could use an all-powerful account to do anything they wanted to your computer if you gave them that opportunity.

As to adding yourself to the admin group, I can tell you that it will not give you the ability to do anything that root can. You still need to use sudo--but to do it, you would edit /etc/group and add yourself to the admin group.

Finally, it is possible to su to root if you give root a password. However, this should be done with caution and only used when necessary. And it's *really* not advisable to let root log in to a graphical environment for security reasons--in a shell, even if you've su'd to root and left the terminal open for all to see, someone still has to know what they're doing to do any damage (or at least know just enough to be trying to do something good but screw up).

The moral of the story is:  sudo=good.

--Door

---

### Post by yeehawjared on 2006-09-20
thanks for the info.... I do understand the secuirty risks.  I'll give root a password and use su whenever I need to use a lot of admin commands.

I don't need to be root while using Gnome, I only need it for command line operations.  Thanks for your help :)

---

### Post by aysiu on 2006-09-20
Just type ```
sudo -s
``` and you'll be root.

---

