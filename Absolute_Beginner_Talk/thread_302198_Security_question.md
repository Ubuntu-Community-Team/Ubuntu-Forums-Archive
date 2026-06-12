---
title: "Security question"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-11-18
Hi
I have noticed that all the files I create are read only for group and world.

I would like to create my files that are only read and write for owner only.

I have looked for a configuration file for gedit so I may change the permissions but could not locate one.

Is there some some way to change gedit so the group and world could not have ANY access to my files?

Thanks for any help

---

### Post by taurus on 2006-11-18
You can put this option in ~/.bashrc so everything that you create from now on will have that permission, read/write for owner only.  

```
umask=077
```
Then, you also need to change permissions of your $HOME directory so nobody can view anything in there with

```
chmod 700 /home/kent
(assuming kent is your login name...)
```

---

### Post by kent41 on 2006-11-18
> **taurus said:**
> You can put this option in ~/.bashrc so everything that you create from now on will have that permission, read/write for owner only.  

```
umask=077
```
Then, you also need to change permissions of your $HOME directory so nobody can view anything in there with

```
chmod 700 /home/kent
(assuming kent is your login name...)
```

I figured it was possible because it looks like anything is possible with linux. Thanks

NOTE: Change umask=077  to umask 077

---

### Post by taurus on 2006-11-18
> **kent41 said:**
> I figured it was possible because it looks like anything is possible with linux. Thanks
Yip, especially permissions since it is a multi users system which means security is a big thing in Linux/Unix.

---

