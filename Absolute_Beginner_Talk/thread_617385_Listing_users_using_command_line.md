---
title: "Listing users using command line"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by mohalfares on 2007-11-19
Helllo,

I'm using ubuntu, last version, updated

I wonder how to list users using command line? I've added the users through the command line, and I can see them by going to Users And Groups GUI , but when I user the command: ls /home in the command line, it lists only one user, which the sudo user

Thanks

---

### Post by steveneddy on 2007-11-19
Maybe in terminal

```
users
```

is that what you wanted?

---

### Post by mohalfares on 2007-11-19
"users" command listed only one user, repeated two times, like" xxx xxx"

---

### Post by lvleph on 2007-11-19
The user folders are not created until their first log in (I believe).

---

### Post by hyper_ch on 2007-11-19
Users are listed in the /etc/passwd file:

```

cat /etc/passwd

```

---

### Post by vambo on 2007-11-19
```
who
```

Also see:
```
man who
```

---

### Post by nick_h on 2007-11-19
Or if you just want the user part of /etc/passwd try:
```
cat /etc/passwd | cut -d: -f1
```

---

