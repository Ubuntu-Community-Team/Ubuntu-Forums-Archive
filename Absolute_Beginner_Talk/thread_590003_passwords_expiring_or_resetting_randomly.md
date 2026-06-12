---
title: "passwords expiring or resetting randomly"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by mvanstone88 on 2007-10-24
I've been running Ubuntu 7.04 for about 6 months now, and I had only one user defined on the system, just myself. I resently created a new user for my g/f to logon to the system, but for some reason every couple of days when she tries to login it won't accept her username and password. I've changed it for her a few times, logged out and in again as her and it works fine for a few days, and then she can't login again.

I've checked out all the options associated with her user account when I went to reset the password, and there is no expiry set.

Can anyone help me out here ?

---

### Post by Inxsible on 2007-10-24
> **mvanstone88 said:**
> I've been running Ubuntu 7.04 for about 6 months now, and I had only one user defined on the system, just myself. I resently created a new user for my g/f to logon to the system, but for some reason every couple of days when she tries to login it won't accept her username and password. I've changed it for her a few times, logged out and in again as her and it works fine for a few days, and then she can't login again.

I've checked out all the options associated with her user account when I went to reset the password, and there is no expiry set.

Can anyone help me out here ?
SWEET !!!!!!!!! 
That's an awesome security feature !!
I would love to have that !! Imagine automatically dis-allowing someone from your computer especially your gf :lolflag:

Anyway, are you sure she is using the right passwords or maybe you have set the number of incorrect logins where in if 3 tries are incorrect, it automatically locks the account until and admin resets the passwords?

---

### Post by dca on 2007-10-24
Double check, do:
 
sudo chage -l *username* 
 
at the CLI...

---

### Post by Hospadar on 2007-10-24
try removing her from the "admin" group, she might be accidentally monkeying about with stuff because of her sudo priviledges granted thereof.

---

### Post by mvanstone88 on 2007-10-25
ok, I reset the password one more time and check at the CLI to make sure everything looked right.
We'll see what happens next time she logs in.
Thanks guys.

---

