---
title: "do not have login window at all :cry:"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Tanya on 2007-07-02
Hi!
I had almost "ok" Ubuntu with one User.
Today I changed in tools>users and accounts>  part about Administrative rights of the User.
After I disable the admins rights I coudn't get to the same menu etc.

I logged out and now I can not get back at least to the User account. I see after initial booting just loading sign ring....

:cry:

What can I do in this case? Please, help!!!
I just can get to recovery mode/:cry::cry::cry::cry::cry::cry::cry:

---

### Post by enopepsoo on 2007-07-02
you could log in to a terminal and give the rights back to the account I think.  I am not really sure what you changed though.

---

### Post by Rocket2DMn on 2007-07-02
maybe try logging in from terminal (CTRL+ALT+F1) as "root" user, then starting the x-server with 
```
startx
```
If the x-server loads, you should be able to access the users and accounts.

---

### Post by Tanya on 2007-07-02
i can boot only in recovery mode(

---

