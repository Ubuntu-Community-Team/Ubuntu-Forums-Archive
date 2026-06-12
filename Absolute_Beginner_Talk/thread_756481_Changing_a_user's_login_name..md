---
title: "Changing a user's login name."
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by michael walker on 2008-04-15
I've been using ubuntu/linux for just one week so please bear with me here. My question is with regard to changing the login name for a user.

When I go to System -- Administration -- Users and Groups and select the user whose login name I wish to change then open the properties associated with that user the "Username" section is grayed out -- even after I "Unlock" the User Settings. Does this mean that it is not possible to change the username for a specific account? Or am I going about this the wrong way?

Please note that I am logged in with the user of which I wish to change the login name.

-michael

---

### Post by Inxsible on 2008-04-15
You can create a new username with whatever name you want. Give the new username admin privileges and then reboot.
Login with the new username and then simply delete the old one.

---

### Post by spiderbatdad on 2008-04-15
Change jerry to tom:

```
# usermod -l jerry tom
# id jerry
# id tom
```

```
# id tom
# usermod -u 10000 tom
# id tom
```

[http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/](http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/)      :)

---

### Post by Inxsible on 2008-04-15
I didnt know we could do that. Useful, if you ever want to change usernames. Thanks spiderbatdad :)

Ubuntu gives a default UID of 1000 to the first user created 1001 to the next and so on.

---

### Post by MeTylerDurden on 2008-04-15
System - preferences - about me  / then look for changepassword in upper right corner ..  :popcorn:

  The Liberator who destroyed my property has realigned my perception

---

### Post by spiderbatdad on 2008-04-15
> **Inxsible said:**
> I didnt know we could do that. Useful, if you ever want to change usernames. Thanks spiderbatdad :)

Ubuntu gives a default UID of 1000 to the first user created 1001 to the next and so on.

I believe the second command in the series: # usermod -u 10000 tom
is intended to make the original users home directory associated with the new UID. I do not know if that changes the path name...that may have to be done separately.
And I'm not going to try it now because I have a rule about breaking my system only once a week...and my quota is met for this week.

---

### Post by Inxsible on 2008-04-15
> **spiderbatdad said:**
> I believe the second command in the series: # usermod -u 10000 tom
is intended to make the original users home directory associated with the new UID. I do not know if that changes the path name...that may have to be done separately.
One thing that concerns me though, is that the commands will only change the username. But in linux the group name is almost always the same as the username (at least it is in Ubuntu) and if you are not in the "first" usernames group, you don't have admin privs. All the folders owned by the "first" user will suddenly be inaccesible.

The op might want to be careful about all that before changing his username.

---

### Post by VyperX on 2008-04-15
just create another account

---

### Post by anjilslaire on 2008-04-15
> 
One thing that concerns me though, is that the commands will only change the username. But in linux the group name is almost always the same as the username (at least it is in Ubuntu) and if you are not in the "first" usernames group, you don't have admin privs. All the folders owned by the "first" user will suddenly be inaccesible.

You can do a sudo nautilus and change permissions on the "first" user's folders, and all groups as well. Tedious, but it can be done.

---

### Post by spiderbatdad on 2008-04-15
> **Inxsible said:**
> One thing that concerns me though, is that the commands will only change the username. But in linux the group name is almost always the same as the username (at least it is in Ubuntu) and if you are not in the "first" usernames group, you don't have admin privs. All the folders owned by the "first" user will suddenly be inaccesible.

The op might want to be careful about all that before changing his username.

I think changing the UID to 1000 solves the problem...dangit...you're gonna persuade me to foul up my system in a minute.:)

---

### Post by Inxsible on 2008-04-15
> **spiderbatdad said:**
> I think changing the UID to 1000 solves the problem...dangit...you're gonna persuade me to foul up my system in a minute.:)Boy am I glad I am not near my Ubuntu machine right now. Or I would surely try that out and screw something up ;)

---

### Post by rusty4r on 2008-04-15
I'm not trying it. Get Mikey to try it!

---

