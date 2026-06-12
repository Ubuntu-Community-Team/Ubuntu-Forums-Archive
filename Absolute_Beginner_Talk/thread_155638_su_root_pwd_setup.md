---
title: "su root pwd setup"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by erhunter on 2006-04-05
I just completed the install and I created my own account, but I don't recall setting the su password, did I miss something or is that first user I create root?

---

### Post by IYY on 2006-04-05
For security reasons, Ubuntu doesn't use root in the traditional way. Every user in the admin group can run processes as root by using the sudo command and their own password.

---

### Post by Rumor on 2006-04-05
The first user you create has sudo privileges. You *can* set a root password if you think one is absolutely necessary. One has already been randomly generated on your install.

---

### Post by erhunter on 2006-04-05
Thanks folks, that makes sense.

---

### Post by cega on 2006-04-05
But any way, how can I set up root passw or change it. I tried with sudo, he asks anyway for root.

thnx

---

### Post by Ian Maxwell on 2006-04-05
With Ubuntu out of the box, there is no valid root password unless you set one up--the hash is set to an impossible value. Instead, the first user created can run admin commands through sudo, which will ask for that user's password.

If you feel that you need a root password, you can use ```
sudo passwd
``` to create one.

---

### Post by take_one on 2006-04-06
I know this way, it works, but it doesn't seem like everyone uses it. Maybe someone can tell me.

sudo -s
then it goes to root, then
passwd
to create new password

I found sudo -s accidently, but it worked you know...

---

