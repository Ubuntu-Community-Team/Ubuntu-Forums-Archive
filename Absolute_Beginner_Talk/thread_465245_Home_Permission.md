---
title: "Home Permission"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by DSAKA on 2007-06-05
I have a rather easy question, but I can't find an answer in the forum. 
I'm trying to copy files from a CD into the home folder, but only root has the permission.
After trying

dsaka@UUUbuntUUU:~$ chown dsaka /home
chown: changing ownership of `/home': Operation not permitted

it still doesn't work. 
By the way: where are programs installed to?
Sorry for those silly questions, but you're facing an absolute noob ;-)

Thanx a lot already

---

### Post by steeleyuk on 2007-06-05
You'll need to run:

sudo chown dsaka /home

---

### Post by Rocket2DMn on 2007-06-05
> **DSAKA said:**
> 
dsaka@UUUbuntUUU:~$ chown dsaka /home
chown: changing ownership of `/home': Operation not permitted


Try using
```
sudo chown dsaka /home
```
If root owns it, you need to be root to change it.

---

### Post by taurus on 2007-06-05
Root should own /home but you should be the owner of your own $HOME, /home/dsaka.

```
ls -la /home
```

---

### Post by DSAKA on 2007-06-05
Unfortunately it gives me:

dsaka@UUUbuntUUU:~$ chown dsaka /home
chown: changing ownership of `/home': Operation not permitted

Any idea?

---

### Post by DSAKA on 2007-06-05
> **taurus said:**
> Root should own /home but you should be the owner of your own $HOME, /home/dsaka.

```
ls -la /home
```

AHHHH...that explains a lot. Thank you guys, very nice of you :p

---

### Post by Rocket2DMn on 2007-06-05
as taurus said, your home folder is /home/dsaka/ not /home/
if you had other users for the computer they would have their own "home" directory under /home/
ex: /home/user2/

---

### Post by steeleyuk on 2007-06-05
edit: never mind...

---

### Post by linux noooob on 2007-06-05
please how do i post a thread!!

---

### Post by Rocket2DMn on 2007-06-05
@noob:
under the [forum]("http://ubuntuforums.org/forumdisplay.php?f=73") (not a thread), click the Make New Post button at the top left

---

