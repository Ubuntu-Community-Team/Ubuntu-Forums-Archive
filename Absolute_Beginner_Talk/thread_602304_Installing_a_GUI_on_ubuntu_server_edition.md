---
title: "Installing a GUI on ubuntu server edition"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by uberhaxor??? on 2007-11-04
Hi, i want to install the lightest GUI possible for my ubuntu server 7.04. I heard about IceWM and Fluxbox, but am not sure which to choose. Also, if i install Fluxbox, will it give me a GUI with menu so on?

How would I go about installing Fluxbox?

---

### Post by ajmorris on 2007-11-04
> **uberhaxor??? said:**
> Hi, i want to install the lightest GUI possible for my ubuntu server 7.04. I heard about IceWM and Fluxbox, but am not sure which to choose. Also, if i install Fluxbox, will it give me a GUI with menu so on?

How would I go about installing Fluxbox?

Yes fluxbox has a GUI with menus and is a very good lightweight WM.
I havnt run ubuntu server edition myself before, but if you have apt-get, just run sudo apt-get install fluxbox.

---

### Post by Soarer on 2007-11-04
Or you could look at Webmin ([www.webmin.com](www.webmin.com)). It is a web front end for server components like Apache, MySql, DNS, NFS, Samba etc. etc. 

You can control the server from any other PC browser.

---

### Post by davidmaxwaterman on 2007-11-08
> **Soarer said:**
> Or you could look at Webmin ([www.webmin.com](www.webmin.com)). It is a web front end for server components like Apache, MySql, DNS, NFS, Samba etc. etc. 

You can control the server from any other PC browser.

I've used webmin before, so I like it. How can I get it using apt-get? Is there some apt-get setup to do to point to the correct place?

Max.

---

### Post by Soarer on 2007-11-09
It's no longer in the repositories, so you can't use apt-get.

Installation instructions are on the webmin site at [http://www.webmin.com/deb.html](http://www.webmin.com/deb.html). Obviously you need to use the Debian package.

---

