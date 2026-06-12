---
title: "LiveCD password"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by bprof on 2008-01-21
Hi,

I'm testing Ubuntu 7.10, for some tasks I need root privileges, but I'm unable to do any.

I tried to change the password for ubuntu 

```
$passwd ubuntu
```

it asked for current password, I tried ubuntu, or no password, didn't work.

I tried

[HTML]$sudo -s
$sudo -a[/HTML]

None worked.

Any help please?

---

### Post by OffAxis on 2008-01-21
there shouldn't be a password...

try
```
su
```

or 

```
sudo -i
```

---

### Post by skymera on 2008-01-21
no there shouldnt =|

just ```
 sudo <whatever> 
```
and it does it

---

### Post by bprof on 2008-01-21
I tried

```
$su
$sudo -i
```

didn't work

and i tried

```
$sudo <whatever>
```

but it asked for a password

---

### Post by louieb on 2008-01-21
> **bprof said:**
> and i tried...**sudo <whatever>**....but it asked for a password
Usually this is caused by a bad burn. Did you run the check media option?

---

