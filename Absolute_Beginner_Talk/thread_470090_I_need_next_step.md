---
title: "I need next step"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by edasich on 2007-06-10
I installed ubuntu 7.04 server.

Using advice from helpful forum person, I installed the gnome desktop.

1) Now how do I start the desktop?  

2) Can I make the desktop start automatically?

3) Do I use the desktop to configure the LAMP server programs or must I do that via the command line?


(I already logged out and back in).
thanks

---

### Post by taurus on 2007-06-10
Try

```
sudo /etc/init.d/gdm start
```
or
```
startx
```

---

### Post by edasich on 2007-06-10
Thanks but something is wrong.  First command gave error message of not found:
sudo /etc/init.d/gdm start

With second command  I am told it needs to be installed.  I did, then I get
"creating new authority not writeable"

What next?

---

### Post by taurus on 2007-06-10
Maybe you didn't have gdm installed on your machine when you installed Gnome.

```
sudo aptitude update
sudo aptitude install gdm
sudo /etc/init.d/gdm start
```

---

### Post by edasich on 2007-06-10
Thanks for your patience.  I am trying that.  Right now waiting for hardware abstraction layer to come back. It's been over 5 minutes sitting there.

---

