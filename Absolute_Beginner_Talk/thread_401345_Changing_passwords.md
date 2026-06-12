---
title: "Changing passwords"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-04-04
I've read a number of post here about folks having login/root access problems after changing their password. I'd like to change my user password and root password to two different passwords. 

Doable? Not doable? Issues that might arise? Cautions that should be taken before/after changing passwords? Anything else?

---

### Post by sargeras on 2007-04-04
I do not know all the pitfalls, but when I want to change the passwords, I just use "passwd" command in a console.  To change the root password, just type "sudo passwd" and you can change that.

Regards

---

### Post by Patrick K on 2007-04-05
Thanks for the tips. 

Anyone else have any thoughts on this?

---

### Post by Patrick K on 2007-04-07
Bump

---

### Post by Hieronymus on 2007-04-07
I don't see what problems could arise, unless you twice type a different password then you think you type :confused: sounds odd doesn't it?

So just go to your terminal and do:

```

jeroen@laptop:~$ sudo passwd
Password:
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
jeroen@laptop:~$ 
```

This will change your root passwd.

if you want to change you normal users password do the same but without the sudo. I really don't see any bears on the road (maybe thats because there are no bears in the Netherlands though?)

Jeroen

---

### Post by zvacet on 2007-04-07
I think it will be smart not to mess with root password.Herre it is how to change adduser password
[http://www.linux.org/lessons/beginner/l3/lesson3b.html]("http://www.linux.org/lessons/beginner/l3/lesson3b.html")

---

