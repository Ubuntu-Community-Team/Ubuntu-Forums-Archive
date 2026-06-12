---
title: "allow all users on a system to apt-get"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by monkeyking on 2007-06-07
Hi I want to allow all users to install programs,
using apt-get/synaptic.

But I dont want the users to gain all the root priviliges like beeing able reboot and so on.

Is there a way to do that?


thanks in advance

---

### Post by reckless2k2 on 2007-06-07
yeah you just modify the sudoers file and specify for just users or assign them to a group and add the group name:

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

If that's too difficult to understand, let me know and i'll post the conf.

---

### Post by Cypher on 2007-06-07
This is not a smart idea as allowing everyone to install applications means that you could have people install 2 applications that rely on the same library but on different versions. It's also possible that one application expects a particular version while the other wants a newer once, so in the end you're going to have only one of the two applications working.

Additionally, most installation require modifications of files that should only be touched by root, so allowing unchecked installation authority means that someone could easily create a .DEB file that executes and does very random/harmful things.

If you have "users", then have them request an application installatio and have people with proper knowledge do the installation..

---

### Post by warcriminal on 2007-06-07
You can just give everyone access to sudo;

here is the link;

[http://www.goitexpert.com/entry.cfm?entry=Add-SUDO-to-Users](http://www.goitexpert.com/entry.cfm?entry=Add-SUDO-to-Users)

---

