---
title: "troubles using useradd"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by pedrotuga on 2006-04-07
hey all, i am trying to add a user to my ubuntu instalation. I only have text, no gui, so... shouldnt 

```
useradd dude
```

create a user called dude?

i whent to /home dir and there was no folder for him :(

what da heck... can anybody tell me very quickly how to use useradd?

---

### Post by black hole sun on 2006-04-07
[QUOTE=pedrotuga]hey all, i am trying to add a user to my ubuntu instalation. I only have text, no gui, so... shouldnt 

```
useradd dude
```

create a user called dude?

i whent to /home dir and there was no folder for him :(

what da heck... can anybody tell me very quickly how to use useradd?[/QUOTE]
Try 


```
useradd -m dude
```

---

### Post by taurus on 2006-04-07
Or
```

sudo useradd -m -s /bin/bash dude
sudo passwd dude

```

---

### Post by black hole sun on 2006-04-07
[QUOTE=taurus]Or
```

sudo useradd -m -s /bin/bash dude
sudo passwd dude

```[/QUOTE]
Isn't the shell automatically set for him?

---

### Post by taurus on 2006-04-07
For /bin/bash, yes.  But some people (and I am one of them) like to use /bin/tcsh instead of /bin/bash...

---

### Post by pedrotuga on 2006-04-07
the ways you guys say... will he be part of the groups tat can use sudo without passowrd? cause i dont want him to be

---

### Post by taurus on 2006-04-07
As long as you don't add him to group adm in /etc/group, he can't sudo...

---

### Post by nanotube on 2006-04-07
[QUOTE=taurus]As long as you don't add him to group adm in /etc/group, he can't sudo...[/QUOTE]

i think its group "admin" that is allowed to sudo. at least, that's what it says in my sudoers file, and i havent changed that line from the default.  

but at any rate... just dont add him to any groups that begin with "adm", and you will be ok :)

---

### Post by taurus on 2006-04-07
[QUOTE=nanotube]i think its group "admin" that is allowed to sudo. at least, that's what it says in my sudoers file, and i havent changed that line from the default.[/QUOTE]
Don't have group admin in my /etc/group but do have group adm though!!!

---

### Post by pedrotuga on 2006-04-07
thank you guys

---

### Post by Mustard on 2006-04-07
[QUOTE=taurus]Don't have group admin in my /etc/group but do have group adm though!!![/QUOTE]

Yeah, I have noticed this inconsistency with the naming of the admin group.  Some people on the forum say they have an 'admin' group and some say they have an 'adm' group.  I've got adm myself.  I wonder whether it was changed from one release to another and it depends on what release someone started with as to what that group is called.

---

### Post by trent dillman on 2006-04-07
Mine is admin. I guess as long as /etc/sudoers has the appropriate group listed, it doesn't really matter. Hell, I'll bet you could change it to group 'fnord' as long as the sudoers was set up...

---

### Post by Mustard on 2006-04-07
[QUOTE=trent dillman]Mine is admin. I guess as long as /etc/sudoers has the appropriate group listed, it doesn't really matter. Hell, I'll bet you could change it to group 'fnord' as long as the sudoers was set up...[/QUOTE]

Well, this is true. :)

---

### Post by nanotube on 2006-04-08
heh yea
curiously, my /etc/group has both adm and admin (but only the admin is listed in sudoers)... i wonder what's up with this inconsistency.

---

