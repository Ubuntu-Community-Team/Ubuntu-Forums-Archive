---
title: "cannot delete old or ad new users"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-10-14
so, as usual I was trying to fix a simple problem and have dug myself into a deeper hole.


on Feisty and I want to add a new user called ancsi

I tried it via syst/admin/user group but was not able to log in. I deleted it there.

tried it at the command line...

and was still not able to login.

This is what I have 

```
rob@rob-desktop:/home$ ls -la
total 36
drwxr-xr-x  9 root root 4096 2007-10-14 16:44 .
drwxr-xr-x 22 root root 4096 2007-10-01 19:54 ..
drw-------  2 1002 1005 4096 2007-10-02 18:11 ancsi
drwxr-xr-x  2 1002 1005 4096 2007-10-14 16:44 anna
drwxr-xr-x 28 aron aron 4096 2007-10-14 16:40 aron
drwxr-xr-x 12 evi  evi  4096 2007-10-14 16:40 evi
drwxr-xr-x  9 1002 1003 4096 2007-09-28 19:54 laci
drwxr-xr-x 34 rob  rob  4096 2007-10-14 17:43 rob
drwxr-xr-x  9 aron 1002 4096 2007-09-28 19:55 zsolt

```

not quite sure why i cannot log into ancsi... hence wanting to delet it and set it up anew.

this is what I tried

```
rob@rob-desktop:/home$ sudo deluser ancsi
Removing user `ancsi' ...
Done.
```

but when I checked
```

rob@rob-desktop:/home$ ls -la
total 36
drwxr-xr-x  9 root root 4096 2007-10-14 16:44 .
drwxr-xr-x 22 root root 4096 2007-10-01 19:54 ..
drw-------  2 1002 1005 4096 2007-10-02 18:11 ancsi
drwxr-xr-x  2 1002 1005 4096 2007-10-14 16:44 anna
drwxr-xr-x 28 aron aron 4096 2007-10-14 16:40 aron
drwxr-xr-x 12 evi  evi  4096 2007-10-14 16:40 evi
drwxr-xr-x  9 1002 1003 4096 2007-09-28 19:54 laci
drwxr-xr-x 34 rob  rob  4096 2007-10-14 17:43 rob
drwxr-xr-x  9 aron 1002 4096 2007-09-28 19:55 zsolt

```

it was still there....

i would also like to delte zsolt and laci

help....

thanks

robi

---

### Post by finer recliner on 2007-10-14
just because there is a folder in /home doesnt mean they are a user. 

all user accounts set up on your computer can be found in the file /etc/passwd

i would google this file to learn how to read it correctly becuase there is a lot of information stored here.

also, despite the name, the passwd file does not store any passwords in it. 

ALSO, you will find many accounts in your passwd file that were automatically created by software you have installed. it is probably best you leave these alone.

---

### Post by beanco on 2007-10-16
Thanks for the tip!

I will google for it now that I have an idea what to look for...

what I still do not understand is why I cannot create any new users... could I have messed up my own permissions and now I do not have the rigths to create new ones?

I do not tink thi sis what happened because when I tried to create a new user via the user-group manager thingy i can do it, but then not log on as that user...

oh, so confusing this is!

rob

---

### Post by BaffledMollusc on 2007-10-16
> **beanco said:**
> Thanks for the tip!

I will google for it now that I have an idea what to look for...

what I still do not understand is why I cannot create any new users... could I have messed up my own permissions and now I do not have the rigths to create new ones?

I do not tink thi sis what happened because when I tried to create a new user via the user-group manager thingy i can do it, but then not log on as that user...

oh, so confusing this is!

rob
When you create a new user (under System->Administration->Users and Groups) you have to set the password for that user. When you try to log in as the new user you have created, are you using your own password or the new one you've given to the new user?

---

### Post by beanco on 2007-10-16
using the new user's pass word!

rob

---

