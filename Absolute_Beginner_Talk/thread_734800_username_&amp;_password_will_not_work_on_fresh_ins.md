---
title: "username &amp; password will not work on fresh install"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by crbutcher on 2008-03-25
fresh install but it says my username or password is wrong what do i do?

---

### Post by kesman on 2008-03-25
In what part? Note that usernames and passwords are case-sensitive.

---

### Post by joshrobinson on 2008-03-25
restart your computer, when it says hit whatever button to enter grub menu, hit it, then click recovery mode

when you get to the command prompt put in this code

```
grep x:1000 /etc/passwd | cut -d: -f1
```
this will print out your username

now use this command
```
passwd username
```
where it says username, put the username that the first command put out, and this will let you set a new password

then restart the computer, and boot up normally and try to login
to reboot the computer from the command line type this

```
reboot now
```

---

