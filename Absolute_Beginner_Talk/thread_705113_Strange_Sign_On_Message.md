---
title: "Strange Sign On Message"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by ImThatNerd on 2008-02-23
I keep getting this when I log on, what exactly does it mean?

---

### Post by kesman on 2008-02-23
find this file with your file browser, right click on it and set the permissions to 644 or the owner being you, this should solve the problem.

---

### Post by PeterJS on 2008-02-23
Exactly what it says. ~/.dmrc has the wrong permissions, so it is not secure, and as a result of this it is being ignored. As the error message says the proper permissions for ~/.dmrc are owned by the owner of the home directory it resides in, with permissions 644. To fix this:
```

sudo chown *username*:*username* ~/.dmrc

```
To set the owner ship to the required settings.
```

chmod 644 ~/.dmrc

```
To set the permissions

---

### Post by ImThatNerd on 2008-02-23
> **PeterJS said:**
> Exactly what it says. ~/.dmrc has the wrong permissions, so it is not secure, and as a result of this it is being ignored. As the error message says the proper permissions for ~/.dmrc are owned by the owner of the home directory it resides in, with permissions 644. To fix this:
```

sudo chown *username*:*username* ~/.dmrc

```
To set the owner ship to the required settings.
```

chmod 644 ~/.dmrc

```
To set the permissions

```
ryan@ryan-desktop:~$ sudo chown username:Ryan ~/.dmrc
chown: `username:Ryan': invalid user
ryan@ryan-desktop:~$ sudo chown username: Ryan ~/.dmrc
chown: `username:': cannot get the login group of a numeric UID
ryan@ryan-desktop:~$ sudo chown username:ryan ~/.dmrc
chown: `username:ryan': invalid user
ryan@ryan-desktop:~$ sudo chown username: ryan ~/.dmrc
chown: `username:': cannot get the login group of a numeric UID
ryan@ryan-desktop:~$ 

```


Am I doing something wrong? lol

---

### Post by yabbadabbadont on 2008-02-23
sudo chown Ryan:Ryan ~/.dmrc

;)

---

### Post by PeterJS on 2008-02-23
Yeah, the first user name isn't a description of what's being set, it's the username twice so yours would be:
```

sudo chown ryan:ryan ~/.dmrc

```

---

### Post by yabbadabbadont on 2008-02-23
But is your actual username Ryan or is it just ryan?  Linux is case sensitive.

---

### Post by ImThatNerd on 2008-02-23
> **PeterJS said:**
> Yeah, the first user name isn't a description of what's being set, it's the username twice so yours would be:
```

sudo chown ryan:ryan ~/.dmrc

```

When I put that in this is what happens: 

```
ryan@ryan-desktop:~$ sudo chown ryan:ryan ~/.dmrc
[sudo] password for ryan:
ryan@ryan-desktop:~$
```

Is that right? And below is the permissions tab of the file.

And it says my username is lowercase ryan

---

### Post by PeterJS on 2008-02-23
The ownership is right, but the permission's aren't. If you look at the other permissions currently it's set to read and write for the world, so the permissions are 6 (owner read (4) + write (2)) 4 (group read(4)) 6 (world read (4) + write (2)).

To set the permissions to what it wants in nautilus change the world permission to read only.

---

### Post by ImThatNerd on 2008-02-23
> **PeterJS said:**
> The ownership is right, but the permission's aren't. If you look at the other permissions currently it's set to read and write for the world, so the permissions are 6 (owner read (4) + write (2)) 4 (group read(4)) 6 (world read (4) + write (2)).

To set the permissions to what it wants in nautilus change the world permission to read only.

I am guessing I do not know what to do since I am still getting it. I apologize for not knowing. I have only had Ubuntu for about 4-5 days and before that Windows for 10 years. Also it is too late and I have a cold. :?

Anyways here is a screen of what I thought I knew what I was doing...

---

### Post by yabbadabbadont on 2008-02-23
Top one should be read-write.  The other two read-only.

---

### Post by ImThatNerd on 2008-02-23
> **yabbadabbadont said:**
> Top one should be read-write.  The other two read-only.

Still coming up when I did that...

Hmm, I am not sure why it has been coming up all of a sudden.

---

### Post by ImThatNerd on 2008-02-23
Bump.

I am still getting it.

---

