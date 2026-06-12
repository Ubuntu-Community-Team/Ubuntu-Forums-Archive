---
title: "[SOLVED] kubuntu, add new user"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by (((X))) on 2008-01-10
Hello

I want to add a new user without administrative rights, have no idea how

---

### Post by JawsThemeSwimming428 on 2008-01-10
Go to K-menu->System Settings->Users and Groups. Does that help?

---

### Post by (((X))) on 2008-01-10
> **JawsThemeSwimming428 said:**
> Go to K-menu->System Settings->Users and Groups. Does that help?

What can I do to add a new user once I am there?
I mean..there are groups: video, scanner, netdev and so on, where to exclude my user from, so that he would not get admin rights..

---

### Post by monte48lowes on 2008-01-10
The main admin rights for a user are in the group 'admin'. This is the group that has access to sudo. Don't assign your new user to that group. You can later change which groups the user is assigned to as necessary.

BTW. I love 'kcontrol' for completing all things KDE related. The search box at the top is an easy way to find the function I need.

Mike

---

### Post by p1r0 on 2008-01-10
You can also do from the terminal:

```
sudo adduser user_name
```

where user_name is the name you want to give to the user.

The to add it to a group:

```
sudo adduser user_name  group
```

where user_name is the same as before and group is a group name to add the
user to for example: admin.

Hope this hepls

---

### Post by disturbedite on 2008-01-10
i have a question a little bit similar to this...
is it possible to rename an existing group?
i changed my username & now i want to change the group name to match it, but i don't see how to do that....

UPDATE:
nevermind, i figured out how:
sudo groupmod -n *desired new group name old group name*

---

### Post by jonwe195 on 2008-06-21
> **JawsThemeSwimming428 said:**
> Go to K-menu->System Settings->Users and Groups. Does that help?

Nope, it doesn't help me...I don't have "Users and Groups" in my System Settings...running KDE4 might be the issue?

---

### Post by ProbablyX on 2008-07-16
I have the same problem...

I had to install gnome-system-tools and use "users-admin"

---

### Post by sathees on 2008-07-17
Hi, 

I am having the problems to test my new designed web site.

Its all working perfectly on Windows IE and Firefox.

But on kubuntu main navigation is coming to the next line.

site is:
[www.todaytranslations.com](www.todaytranslations.com)


I used font family as follows in my CSS.
font-family:Arial, Helvetica, sans-serif;

If anyone could give me the solutions.

Thanks
Sathees

---

