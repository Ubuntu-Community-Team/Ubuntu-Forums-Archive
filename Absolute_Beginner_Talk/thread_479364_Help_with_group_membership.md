---
title: "Help with group membership"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by teamanx on 2007-06-20
Hello. I am a newbie on linux administration, and trying to move from windows.
I have joined my Ubuntu machine into a windows Active Directory domain. I have created an AD group called "unixadmin", and added it to sudoers, so the members of this group can use sudo.

My problem is the following: Is there any way of making these users (the members of "unixadmins") become members of the unix group "admin", so they have the administrative menu entries?

Thanks a lot.

---

### Post by yagood on 2007-06-20
Have you tried going to System > Administration > Users and Groups > Manage Groups > (select group) > Properties > Group Members?

---

### Post by teamanx on 2007-06-20
Well, the problem is that in the "Group members" dialog only appear the local users. I have manually added a domain user to the group "admin", by entering his name on the file "/etc/group/". Here is the line:

admin: x:117:lxadmin,jmcorral

Where "lxadmin" is the local user, and "jmcorral" the domain user. It works well, but the domain user still doesn't appear at the "Group members" dialog. And, what is worst, if I put the domain group "unixadmins" on the same line, the members of the group don't get the admin menu entries.

I'd like to automatically add all of the members of the domain group "unixadmins", without having to enter the names on each computer, so I can have a centralized control of the administrative users.

---

