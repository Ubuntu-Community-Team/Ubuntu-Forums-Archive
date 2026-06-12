---
title: "Search path issue"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by in_orbit on 2006-07-13
Good evening

Which file should I edit to add a program to the search path? I want every user on the system to be able to start it.

I did some editing of /etc/environment and that did work out after running the command "source /etc/environment". This is also the case when editing .bash_profile.

I really don't want to write "source /etc/environment" every time I start a bash shell so the question is which file I should append the path to.

Regards
In orbit

---

### Post by halfvolle melk on 2006-07-13
Hi,
[This site](http://www.troubleshooters.com/linux/prepostpath.htm) suggests to put it in /etc/profile. "All users except root | /etc/profile". etc/profile says "#/etc/profile: system-wide .profile file for the Bourne shell" so that makes sense. Never tried it though.

---

### Post by bricedebrignaisplage on 2006-08-03
I added these lines to /etc/profile
```
PATH=$PATH:/usr/realtime/bin
export PATH
```
and when I log in as a regular user the path is modified. When I log in as root too.

However, if I log in as a regular user and that from a terminal I log in as root (su root), the path doesn't contain /usr/realtime/bin anymore! And when I try to call one of the scripts in /usr/realtime/bin with sudo, it's not found.

I tried to modify /root/.bash_profile but that leads to the same result.

Can anybody explain?
And then, how should I do to be able to sudo a script in that directory?


Thanks
Brice

---

