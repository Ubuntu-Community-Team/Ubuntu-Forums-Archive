---
title: "users&amp;groups"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by rensu on 2006-06-02
Could someone tell me why users and groups aren't telling the right information? And how I can check all users and all groups? Is it possible?
Because when im checking users then I don't get all users and get like one name twice. What could be the problem ?:S

---

### Post by tonyr on 2006-06-02
What is it exactly that you are doing to get users and groups? Are you using
a command in a terminal, or a GUI tool?   Show your steps explicitly, and the results.

---

### Post by rensu on 2006-06-03
I am tying in console command [COLOR="red"]users[/COLOR] & [COLOR="Red"]groups[/COLOR].

---

### Post by tonyr on 2006-06-03
I'm not sure what you are trying to do.

The command **users** lists all users currently logged in to the machine you are
working on.

The command **groups** lists all of the groups that **you** belong to.  

All of the userID names are in the file /etc/passwd.  If you have a new installation, all but
one of them (yours) are for 'system' accounts. All of the group names are listed in the file
**/etc/group**. Again, on a fresh install, all but one of them (yours) are standard
'system' groups.  There is a GUI tool for managing users and groups in the
System->Administration menu.

---

