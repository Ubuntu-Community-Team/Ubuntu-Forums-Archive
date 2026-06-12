---
title: "Python"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by Terry S on 2008-03-17
Hi

I tried to run the installed chess program included with Ubuntu 7.10 and I got this message:

[COLOR="Red"]Your system does not have the required software to enable 3D mode. Please contact your system administrator and ask them to install the OpenGL Python bindings and the GtkGLExt Python bindings.
[/COLOR]
Which is odd because the chess program has worked in 3D before. 

Can anyone tell me how to get and install the required bindings?

Terry S

---

### Post by weezy8802 on 2008-03-17
> **Terry S said:**
> Hi

I tried to run the installed chess program included with Ubuntu 7.10 and I got this message:

[COLOR="Red"]Your system does not have the required software to enable 3D mode. Please contact your system administrator and ask them to install the OpenGL Python bindings and the GtkGLExt Python bindings.
[/COLOR]
Which is odd because the chess program has worked in 3D before. 

Can anyone tell me how to get and install the required bindings?

Terry S
 
do you have restricted drivers enabled? if so you may want to try
```
sudo apt-get install
```
after install you can put in the bindings

if that dont work you can search for stuff in the cache with
```
apt-cache search
```
after search you may enter any keyword or application.

Hope it helps.

---

### Post by bruce89 on 2008-03-17
```
sudo aptitude install python-gtkglext1 python-opengl
```

A few wee packages are required to get 3D to work.

---

### Post by Terry S on 2008-03-17
Hi weezy8802

I have the Nvidia drivers installed. As I said it is odd because the game worked in 3D a couple of days ago!!!

I will do as you suggest.

Thank you for your help.

Terry S

---

