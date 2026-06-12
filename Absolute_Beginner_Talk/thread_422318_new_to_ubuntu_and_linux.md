---
title: "new to ubuntu and linux"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by jhrach on 2007-04-25
I just installed Ubuntu server on a new Intel  box for hosting my website and business and it installed great.  Can I now install the desktop version so I have a graphical interface?

Also, what is a  recommended mail server that will give me approximately the same features as MS exchange server?

---

### Post by Sef on 2007-04-25
> Can I now install the desktop version so I have a graphical interface?


Do you want to install it on another computer or just have a graphical interface on your server?

If you want a gui for your server from the terminal type these commands:

```
sudo aptitude update
```

then

```
sudo aptitude install ubuntu-desktop
```

---

### Post by jdonat on 2007-04-25
> **jhrach said:**
> I just installed Ubuntu server on a new Intel  box for hosting my website and business and it installed great.  Can I now install the desktop version so I have a graphical interface?

Also, what is a  recommended mail server that will give me approximately the same features as MS exchange server?

do you mean a graphical interface  on the same box as the server ?  if so, all you have to do is run sudo apt-get install ubuntu-desktop  at the terminal.

can't really help help you with the mail server part though, sorry

---

