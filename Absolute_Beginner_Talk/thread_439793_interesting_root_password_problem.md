---
title: "interesting root password problem"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by nn2004 on 2007-05-11
im having a very (imo) wierd problem with my root password, if i use the terminal and type su and give my root password everything works fine, if i type sudo and give the same root password it tells me that its the wrong password, if i try and open synaptic, when it asks for my password i type the root pass and it tells me its wrong, im typing the correct root pass and it still wont let me in, any suggestions?

---

### Post by rillip on 2007-05-11
Sudo uses the advanced user password, not the root password.  By default this is the one you set up when you first installed ubuntu.

Su is actually switching you to root, so the root password is fine.  But Sudo is trying to use advanced privelages on your default user account, as I understand it.  Could be wrong though.

---

### Post by aysiu on 2007-05-11
Forget the root password.

Use your user password for everything. If you need to log in as root, use ```
sudo -i
``` instead of ```
su
```

Read more here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by adam93250 on 2007-05-11
so you just have to type ```
sudo {command}
```
and when it asks for the password type YOUR password. The one you login with.
and when an application wants a password type YOUR password.

---

### Post by Atomic Dog on 2007-05-11
sudo su will make you root.  It will prompt you for your password (not root pass).  I can;t remember the last time I had to use that command though.

---

### Post by nn2004 on 2007-05-11
see thats the thing, if i use sudo, and use my own password it still doesnt let me, i have to su and enter the root password, and then i can use terminal for what i need, the main problem is that when i click on anything that needs super user credentials (synaptic, update manager..etc) neither my password or the root password lets me in, any other ideas would be greatly appreciated.

---

### Post by Bachstelze on 2007-05-11
Not all users are allowed to use sudo. Are you in the admin group ?

---

