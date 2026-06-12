---
title: "Manually Install Dependencies"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by Cochese on 2007-01-11
How do you install dependencies if you don't have an internet connection?

I can't use apt-get and they don't show up in synaptics.

libcompress-zlib-perl
libextutils-depends-perl
libextutils-pkgconfig-perl
libgtk2-trayicons-perl

This is what I need to install, I have downloaded them as tar.gz

---

### Post by bodhi.zazen on 2007-01-11
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

This first site is good, but goes down from time to time ...

	[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Cochese on 2007-01-11
When I type ./configure in the folder I created I get command not found.

---

### Post by bodhi.zazen on 2007-01-11
Did you install build-essential

---

### Post by Cochese on 2007-01-11
No, I didn't have it installed, but I do now.

Now it tells me, No such file or directory.  Is there something else I need to install?

Thank you both, for your responses and help.

---

### Post by bruenig on 2007-01-11
You need to make sure you are in the same directory as the ./configure file if there even is one.
```
cd /wherever/the/extracted/directory/is
```
Then
```
ls
```
Make sure in the output, you see a file that says configure (it should be green if you have colored enabled) then run ./configure.

---

### Post by Cochese on 2007-01-12
Thank you all for your help. I just wanted to follow up on what I did.

I found this site

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

and downloaded all the packages I need as .deb files. That made it really easy to install them.  Once I downloaded them on another computer I just used a usb drive and moved them.

---

