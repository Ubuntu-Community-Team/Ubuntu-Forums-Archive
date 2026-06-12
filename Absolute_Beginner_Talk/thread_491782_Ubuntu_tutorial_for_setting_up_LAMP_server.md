---
title: "Ubuntu tutorial for setting up LAMP server"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by rbradshaw on 2007-07-04
I have installed 7.04 as a desktop application on my laptop PC. I would like to create a LAMP environment for development and testing a future website.

If you can provide me some very clear and well-written instructions on how to do this, I would be greatful.

Thanks, Randy

---

### Post by Axed on 2007-07-04
I would recommend installing your web server in a virtual machine - keeps it seperate from your desktop config, and makes it transportable it you want to move it to another machine (or reformat your current one).

VMware server is very easy to install (Applications > Add/Remove).

Then install Ubuntu server into a new VM and follow this guide:
[http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)

---

### Post by rbradshaw on 2007-07-04
what do you mean install web server in a virtual machine?

---

### Post by hyper_ch on 2007-07-04
VmWare is a virtualization product that allows you to run a second OS within your current one...

So you will normally start your desktop and then once that is booted, you can run another ubuntu instance in vmware... in that ubuntu instance you then install the server stuff.

---

### Post by mlentink on 2007-07-04
You might want to look [here]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by mlentink on 2007-07-04
> **rbradshaw said:**
> I have installed 7.04 ***as a desktop application***

Just noticed this. Do you mean you installed the desktop version? For website development and testing that's fine. But should you want to run that site in a production environment I would recommend installing the server version (use the "INstall a LAMP server" option). If you really want a GUI on it (I personally see no need for it), you could always install it with
```
sudo apt-get install ubuntu-desktop
```

---

### Post by expatCM on 2007-07-04
But if you have installed a Desktop version and you just want to test websites, will this not be an easy approach for you ....
[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

---

### Post by az on 2007-07-04
> **mlentink said:**
> You might want to look [here]("https://help.ubuntu.com/community/ApacheMySQLPHP")

> **expatCM said:**
> But if you have installed a Desktop version and you just want to test websites, will this not be an easy approach for you ....
[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

Actually, using the ubuntu packages is much easier than xampp.  You know what you are getting and converting your website to a production environment is easy, since you are secure and you know what version of the applications you are using and is easy to keep the pieces up to date.

---

