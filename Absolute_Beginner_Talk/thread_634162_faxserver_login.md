---
title: "faxserver login:"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by mobi3815 on 2007-12-07
Just installed Ubunty 7.10, but getting following message

Ubunty 7.10 faxserver tty 1
Faxserver login: 
:confused:

---

### Post by taurus on 2007-12-07
Did you install the server version or the desktop version?  

Log in with your username and password and see what happens when you run this command at the prompt.

```
startx
```

---

### Post by mobi3815 on 2007-12-07
password:

---

### Post by taurus on 2007-12-07
Didn't you create an account (username and password) when you installed it?

---

### Post by mobi3815 on 2007-12-07
administrator@faxserver: "$

---

### Post by taurus on 2007-12-07
> **mobi3815 said:**
> administrator@faxserver: "$

```
startx
```
And if you get an error message like command not found, then you have installed the server version which doesn't come with any window manager.  Therefore, you need to install one.

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by mobi3815 on 2007-12-10
sudo /etc/init.d/gdm: command not found

---

