---
title: "allowing sudo to other users..."
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by dupa on 2007-02-06
I create on my ubuntu a new user "newuser"

```
sudo adduser newuser
```

i noticed that logging with it, i was not able to sudo :|
So i have taken a look to the sudoers default file..
It seems to say that the users belonging to the "admin" group are able to "sudo".. 
so i did:

```
sudo adduser newuser admin
```


But.. still newuser cannot sudo itself..

have you any idea?
thanks

---

### Post by taurus on 2007-02-06
You also need to add that new user to group adm as well.

```
sudo adduser newuser adm
```

p.s.  Don't mess around with /etc/sudoers or you could screw up the whole thing.

---

### Post by shareMenaPeace on 2007-02-06
Is this equivalent to the Group & User manager?


thx

---

### Post by dupa on 2007-02-06
> **taurus said:**
> You also need to add that new user to group adm as well.

```
sudo adduser newuser adm
```

p.s.  Don't mess around with /etc/sudoers or you could screw up the whole thing.

This is my sudoers:

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


```

How do you understand from this, that is required to add the user to the "adm" group?
I had just understood i should add them to admin group reading the last line...
But i'm curious about the adm :)
Thanks!

---

### Post by taurus on 2007-02-06
To be able to use sudo, a user needs to belong to both adm & admin in /etc/group.  If he/she belongs to one but not the other, then he/she can't use sudo.  

See if newuser can use sudo after adding that individual to group adm too!

---

### Post by kpatz on 2007-02-06
A user doesn't need to be in the adm group to use sudo, only admin.

My sudoers file looks like the one posted above.  No reference to adm.  I created a user, logged in as that user and tried to sudo, no dice.  Then I added the user to the admin (not adm) group using **sudo adduser newuser admin** and then the user could sudo.

What message does the new user get when they try to sudo?  The nasty one about the incident being logged?  Root (or your primary user account) should receive an email detailing the "violation", there might be some info in there.  Also check /var/log/auth.log.

Did you change anything in your /etc/sudoers file?

---

