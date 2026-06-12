---
title: "How do I launch the desktop from the command line?"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by marv12marv on 2007-09-01
I've installed the server version and successfully login. However, I'd like to know utilize the desktop. What is the command?

---

### Post by taurus on 2007-09-01
If you install a server version, there is no desktop UNLESS you install it first.

```
sudo aptitude update
sudo aptitude install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by marv12marv on 2007-09-01
Thanks. But my ubuntu installation doesn't have network access. Where can I down load the ubuntu-desktop component (from within windows and then I'll copy it over to my ubuntu hard drive)?

---

### Post by overdrank on 2007-09-01
> **marv12marv said:**
> Thanks. But my ubuntu installation doesn't have network access. Where can I down load the ubuntu-desktop component (from within windows and then I'll copy it over to my ubuntu hard drive)?

Hi you can try this
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)
Or if you downloaded the live cd it maybe easier!
[http://releases.ubuntu.com/feisty/](http://releases.ubuntu.com/feisty/)

---

### Post by taurus on 2007-09-01
Did you use the desktop CD (LiveCD) or the server CD to install the server version on your machine?

---

### Post by marv12marv on 2007-09-01
Which CD should I download? Can I get it off the server cd?

---

### Post by ruibernardo on 2007-09-01
You have to download the **Alternate CD**. Only the Alternate (or the DVD) will have the ubuntu-desktop package for you to install.

---

### Post by taurus on 2007-09-01
The server CD only has only the server version on it.  Why don't you download and use the desktop CD to install it on your machine.  It comes with Gnome window manager so no need to do anything extra after you install it.  Simple and easy.

---

### Post by marv12marv on 2007-09-01
I've installed it as a server because I want to run it as both a web server (Tomcat) and as a client on the same box.

---

### Post by scxtt on 2007-09-01
you can install any server-based package on a Desktop install ... there is NO real advantage to using the server version and chucking X on it vs. installing the Desktop version and adding server packages ...

---

### Post by Chris S. on 2007-09-01
If you don't know how to install a server on the Ubuntu Desktop version, you could search around the forums for some stickies.  Look for instructions for installing a LAMP server, which I've read is more or less what you get with Ubuntu Server.

---

### Post by marv12marv on 2007-09-02
Thanks! Then I'll go ahead and install the desktop  CD and then add the server stuff to it (unless anyone here sees an advantage to installing the server first and then adding the desktop).

---

### Post by marv12marv on 2007-09-02
When I insert the Alternative CD into the system, how do I a.) access it and b.) install components off of it?
Thanks in advance - yous are so incredibly helpful.

---

### Post by scxtt on 2007-09-02
are you trying to do this w/ the server version?  you need to add the Alt. disk as a repository - read up on **apt-cdrom**

---

### Post by taurus on 2007-09-02
Try

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
-or-
startx
```

---

### Post by marv12marv on 2007-09-02
Yes, I'm gong to add the desk top from the server version (I want LAMP!). I"ll try:

sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
-or-
startx

Thanks Taurus!!!

---

### Post by Hennanoi on 2008-06-02
> **taurus said:**
> If you install a server version, there is no desktop UNLESS you install it first.

```
sudo aptitude update
sudo aptitude install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

I just stuck with a similar problem, tried the above command and voila. I have desktop now! :)

Thank you for the help..

H.

---

