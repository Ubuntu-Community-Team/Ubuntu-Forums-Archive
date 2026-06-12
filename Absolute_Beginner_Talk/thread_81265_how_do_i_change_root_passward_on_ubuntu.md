---
title: "how do i change root passward on ubuntu"
date: 2005-10-24
forum: Absolute Beginner Talk
---

### Post by lorelly on 2005-10-24
pls tell me how do i change root passward on ubuntu without knowing the old passward. I recently installed ubuntu, but on installation, it didn't ask me for a root passward, only for the user passward.

Thanks

---

### Post by cbudden on 2005-10-24
In Ubuntu you use sudo to run super user commands, which uses your user password.

---

### Post by lorelly on 2005-10-24
yes, i know that, but i want to enter as root. With fedora i knew how to do it.  Thank u anyway

---

### Post by 23meg on 2005-10-24
```
sudo passwd root
```

will do it.

---

### Post by patrick295767 on 2005-10-24
[QUOTE=23meg]```
sudo passwd root
```

will do it.[/QUOTE]

U can also boot ur pc with knoppix or liveCD, 
mounting ur partition, 
then go into the shadow file of the /etc/
and copying the encrypted password of an user (password known)
or resetting the password of root ...(i guess 0:0 should work, ...I have to check)
  
Then, u reboot normally ur pc, and once root !
type to redefine ur root password:
passwd 
  
Good luck, please let me know about ur results !!!
('cos I forgot a bit)
  
Patrick

---

### Post by paddyg on 2005-10-24
[QUOTE=lorelly]yes, i know that, but i want to enter as root. With fedora i knew how to do it.  Thank u anyway[/QUOTE]

Try this:

1. give root a password:
system-->administration-->users and groups (show all users and groups)--> root -->properties

2. select:
system-->login screen setup -->security-->allow root to login with GDM

---

