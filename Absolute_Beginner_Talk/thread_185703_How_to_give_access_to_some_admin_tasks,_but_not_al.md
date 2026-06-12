---
title: "How to give access to some admin tasks, but not all?"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by bluenova on 2006-06-01
Hi Guys,

I tried searching but came up blanks on this one, probably because there are so many posts with 'sudo' in them.

What I would like to do is give a user access to certain admin tasks, but not all. For instance to allow the user to install programs through synaptic, but not access firestarter or nautilus root.

Any ideas how permissions can be set for certain programs/commands?

---

### Post by ProjectGod on 2006-06-01
this is something i would like to know also. i noticed you could give permissions to fdd and cd rom and the like but how might one give away permissions to system administrative tasks? kind of like windows group policies?

---

### Post by aysiu on 2006-06-01
I don't know that this will work, but I do know that each file and folder has permissions for users, groups, and other.

So, theoretically, if you made all the users on your computer part of a group and changed ownership (still root for user, but your special group for group) of the Synaptic launcher and all the folders Synaptic modifies, then they could use Synaptic...

... the danger being, of course, that they'd then have access to all these files and folders without a password.

---

### Post by Nonno Bassotto on 2006-06-01
Have a look here. Maybe one of these two tools could be useful for you.

[http://www.gnome.org/start/2.14/notes/en/rnadmins.html](http://www.gnome.org/start/2.14/notes/en/rnadmins.html)

---

### Post by ProjectGod on 2006-06-01
Thanks for the replys!

i tried that **aysiu**... it doesnt seem to work... what i did was go under /usr/sbin and changed the permissions for the program firestarter to 770

which basically allows root / root group to have full access and others NO access... i then went to change the root password (to something that was different to my own password)... i rebooted then i loged in as me ... i could still start firestarter... all i had to do was put in MY password. :(

... perhaps i could make it so that when the password is prompted everytime i do some administrative tasks... the system requires the ROOT password instead of the USER password... probably that way the users on the ubuntu could be more restricted to whatever permissions given... a very very long winded way to controling user activity!

a friendly GUI tool is indeed the solution! thanks for the link **Nonno Bassotto** i'll give it a whirl.

---

