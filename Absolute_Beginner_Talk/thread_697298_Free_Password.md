---
title: "Free Password"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by aikid14 on 2008-02-15
Hi people, I wanna ask something about log in problem. Besides me, my sister and brother also use the pc for surfing the net. I have made my own log in and passwords. My question is: can I make other users without passwords so anyone can log in easily. Thank you for your help

aikid14
:)):P):P

---

### Post by oedha on 2008-02-15
you can create more user.......system - administration - users and group
for password setting.....system - administration - login windows

---

### Post by hyper_ch on 2008-02-15
Why not letting them choose their own password?

---

### Post by kpkeerthi on 2008-02-15
System -> Admin -> Login Window -> Security -> Auto Login

*** Might pose security threat ***

---

### Post by Trail on 2008-02-15
You can create two new users like the above posters have noted. You can have them login without having to type a password.

Additionally, if the new accounts do NOT belong to the admin and adm groups, they cannot use sudo, and cannot do any administrative tasks. You can set permissions on your files so they can read but not write, or you can make them unable to read or even enter your directories. That way they'll be like guests, if you want.

---

### Post by SOULRiDER on 2008-02-15
Not using a password is a security problem. Just give them a simple password that theyc a remember and remove them from the admin and wheel groups.

---

