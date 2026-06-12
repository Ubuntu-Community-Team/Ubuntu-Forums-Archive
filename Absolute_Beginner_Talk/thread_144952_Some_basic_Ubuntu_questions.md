---
title: "Some basic Ubuntu questions"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by mlind on 2006-03-15
I'm planning to install Ubuntu on my parents computer in near future.

Does Ubuntu shipped GDM have login screen(s) where you could select a
userprofile instead of typing the name. 

I know It sounds kinda lame and unsecure, but hey. Old folks forget things.

And other thing would be possibility of disabling login password which is lame
aswell. But I'm going to otherwise trapwire the system. I would just need to
somehow tone down unnecessary password prompting. Adminstrative tasks
would require password ofcourse.

---

### Post by Koybe on 2006-03-15
You can have a look at Gnome-look for GDM theme matching your needs. And in the gdm config you can also specify a user that logs in directly without prompting for password. Anyway it'll always be the same and you can't set a user password to nothing.

---

### Post by mlind on 2006-03-15
Thanks, I'll check this right away.

That user without password thingy is a single user only?
meaning one useraccount with a password gdm knows/hides ?

I would need that profile selection. I recall that Suse something like this
implemented on kdm.

---

### Post by Koybe on 2006-03-15
Yes, it's a simple user account. You just specify the login/pass in gdm configuration. I don't have it in english in english in front of me but i suppose : Desktop -> Administration -> login screen or something like that.

---

### Post by jjf on 2006-03-15
There's always the old standby: password = "password"  :)

---

