---
title: "root user problem"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by finch on 2006-04-10
Hi there.
First of all i must to tell you i`m new in linux. I installed ubuntu 5.10, but can make root user.
Here what i try:
```

Applications &#8594; System Tools &#8594; Run as different user
As user: root -> OK

```
but no ask for password. Can you help me to create root acc.
Thx in advance

---

### Post by htinn on 2006-04-10
The installer-made user is set up as an admin by default. That user can just use sudo <command> (or sudo -i if you need a root shell).

---

### Post by steve.horsley on 2006-04-10
The root account is locked by default (but it exists). See this explanation:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by finch on 2006-04-10
I try to back my root acc
```

sudo passwd root

```
but nothing`s happen

---

### Post by taurus on 2006-04-10
What group do you belong to?  Log in as your normal account and open a terminal by clicking Applications -> Accessories -> Terminal.  Then type the following command and paste the output here...
```

id

```

---

### Post by finch on 2006-04-10
```

finch@ubuntu:~$ id
uid=1000(finch) gid=1000(finch) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(lpadmin),105(scanner),1000(finch)

```

---

### Post by Bishop Hill on 2006-04-10
I have a similar problem. Even though I am in the group "root", I cant get access to my windows folder>_<

---

### Post by htinn on 2006-04-10
You have to be part of the "admin" group to use sudo (the way that sudoers is set up by default, that is).

---

### Post by CTF on 2006-04-10
Well, this is not a good way to get started. If you load Ubunto in a multi-partition environment but the Win partitions are disabled AND you need help files to figure out some strange new linux command (SUDO??) to get access to YOUR OWN DRIVES, then someone didn't think through things very well. Developers take notice... If you want to compete in the real world then things have to work! Another wasted implementation of a Linux distro.

---

### Post by steve.horsley on 2006-04-11
And windows shows you your Linux drive contents, does it?

---

