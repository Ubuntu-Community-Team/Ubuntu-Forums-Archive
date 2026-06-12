---
title: "[SOLVED] Super user access"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by aad10000 on 2008-02-09
HELP!! I am new to Linux (Ubuntu)and need some help. I want to load a VPN client for remote access to work. In a terminal console I extracted the tgz file fine, but when I ran
the install command the response was that I needed Super User access to install file.
When I loaded Ubuntu I don't recall having to setup the Super User account. My initial
account that I set up is a member of the admin group and this is the account I'm using 
to try to install the file. Have I missed something???? Any help is greatly appreciated.
Thank you.

AAD10000

---

### Post by taurus on 2008-02-09
You would use sudo in front of a command if you want to install or write to anywhere outside your $HOME directory.

```
sudo make install
```
Then, use the same password that you log in with.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by stevescripts on 2008-02-09
sudo "install command" (no quotes)

Too late again :)

---

### Post by aad10000 on 2008-02-09
Thank you Taurus. Worked great.

AAD10000

---

