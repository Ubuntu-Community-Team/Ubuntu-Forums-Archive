---
title: "Root"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by Conquestor1 on 2007-11-02
I set Gutsy up fine. When I set Gutsy up I used the same Password as I used to set myself up. Recently, I needed to add a scanner pacpage, a" rpm". When ever I try to convert this file I get a prompt to login as Root. So, I logoff and enter try to "root" and use the password i used for my self as administrator. and as root, I get nowhere. Can anyone enlighten me.Why won't my root password work?

---

### Post by rudeboyskunk on 2007-11-02
ubuntu is set up so you cannot login as root.  when you try to do that, type "sudo" before typing the command in a terminal.  that's how you get root permissions.

---

### Post by Happy_Man on 2007-11-02
Actually, in Ubuntu, the root account is locked by default. You use the command "sudo" instead. So instead of ```
su
gedit /etc/apt/sources.list
```

You would do ```
sudo gedit /etc/apt/sources.list
```

---

### Post by Maestro23 on 2007-11-02
RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Pumalite on 2007-11-02
There is no password for root in Ubuntu, purposely.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

