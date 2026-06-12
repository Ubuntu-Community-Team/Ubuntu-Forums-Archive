---
title: "root login?"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by dfa_geko on 2006-08-13
I have a question about ubuntu compared with Fedora Core 5. (Well, other than Fedora and Ubuntu, I haven't used any other linux OSes) With Fedora, I have a seperate "root" account. With Ubuntu, I use the 'sudo' command and it prompts me for the password. Are there no root superuser account in ubuntu? Or did I set up ubuntu wrong? Should I have called the user 'root' instead???

---

### Post by 23meg on 2006-08-13
The root account is disabled by default. You're encouraged to use *sudo *instead.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by stupidkid on 2006-08-13
Hmm bash completion doesn't work with sudo. Or am I missing something? Anyways I believe you can still get a root account using sudo su (I have a root account in my Kubuntu machine).

---

### Post by drtvasudevan on 2006-08-14
well. what i gathered moving around here is that while you can do most things with sudo there are some differences. you can enable a root account if you really know how to handle it.
see  Unofficial Ubuntu 6.06 (Dapper Drake) Starter Guide for directions.

---

### Post by LadyDoor on 2006-08-18
Fire up a terminal and enter the following:

```
$ sudo passwd root
```

After you change the password, you can su to root or log in as root. But be careful.

---

### Post by aysiu on 2006-08-19
```
sudo -s
```

---

