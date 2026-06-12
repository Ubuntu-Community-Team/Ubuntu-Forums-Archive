---
title: "Securing Apace"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by albytrott on 2006-09-24
Morning all. After a little advice.

Finally managed to switch our corporate website from IIS/MS SQL to Ubuntu server, Apache2 and MySQL.

I am after a liitle advice on how to secure Apache, I believe there is a way to prevent the version of apache and OS we are using if the browser is sent to a page that does not exist on our website.

Also the webserver is in the DMZ with no acccess onto the internet, this means that I can't get any updates for the server. What's the best way to get updates to the server without having to grant it access to the internet?

Many thanks

Alby

---

### Post by Miademora on 2006-09-24
[Here]("http://www.ducea.com/2006/06/15/apache-tips-tricks-hide-apache-software-version/") you find a good guide to hide the apache version.

---

### Post by albytrott on 2006-09-25
Excellent, thank you. I just need to sort out updating the server and then it can go live.

Thanks again.

Ste

---

### Post by daschl on 2006-09-25
> **albytrott said:**
>  What's the best way to get updates to the server without having to grant it access to the internet?

Many thanks

Alby

download the (new) debs and burn them on cd/copy them on a usb-stick/... and then install them with dpkg... you may also download official pathes from the httpd website and install them

(this really depends on what you want to do!)

---

### Post by albytrott on 2006-09-25
I would like to make sure that the server is kept up to date. I have a test PC with ubuntu desktop installed and get notification of when new updates are available,  I figured I would have to download the debs to CD but its knowing which debs I need.

Ste

---

### Post by daschl on 2006-09-26
well, the first thing that comes to my mind is that you fire up a server with a similar setup and just download the deb's and dont install them.. and then bring them on the other server..

if your server has no access to the internet you have to bring the data over the internal network or with an other medium to the server..

---

