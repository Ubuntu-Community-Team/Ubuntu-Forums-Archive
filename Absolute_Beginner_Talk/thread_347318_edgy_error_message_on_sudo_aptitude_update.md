---
title: "edgy error message on sudo aptitude update"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by dragnazz5.0 on 2007-01-27
well i just got edgy working.  i restarted after upgrading and i got all these errors and had to manually run fsck and everything got fixed so it works now.  the only thing different is there is only two work spaces instead of 4 like on dapper.  but thats not what im worried about.  when i try to sudo aptitude update i get this error message. 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: Couldn't rebuild package cache

how do i fix that?

---

### Post by Iarwain ben-adar on 2007-01-27
Hi there,
well it says that you should run dpkg --configure -a..

What should you do? :wink:

```
sudo dpkg --configure -a
```


Iarwain

---

### Post by dragnazz5.0 on 2007-01-27
> **Iarwain ben-adar said:**
> Hi there,
well it says that you should run dpkg --configure -a..

What should you do? :wink:

```
sudo dpkg --configure -a
```


Iarwain

dang, last time i did that it said i need superuser permission or something like that.  thanks man

---

### Post by Iarwain ben-adar on 2007-01-27
No problem :D

Remember, if you need help, search the forum first, and then ask questions.
(btw, if your pc complains about superuser, try sudo in front of your command :wink: )


Iarwain

---

