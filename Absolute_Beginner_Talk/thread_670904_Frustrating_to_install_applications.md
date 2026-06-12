---
title: "Frustrating to install applications"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by sundar22in on 2008-01-18
I am a newbie to Linux and I installed Ubuntu 7.04 in my machine. I got a debian packages DVD which contains many applications like apache, Php and thousands of others applications. I tried installing apache, php5 etc. using *.deb package and I was unable to install any of the packages.

 I tried atlest 30 *.deb packages and I could not even install one application from DVD!!!  All of the installation failed due to missing dependencies!!


Is it frustrating to install applications in Ubuntu? I dont have internet connection in my Ubuntu machine. Any form of help is appreciated.

Thanks you.

~ Sundar ~

---

### Post by zipperback on 2008-01-18
What version of Ubuntu are you working with?

Is the packages DVD you are using for the same exact version of Ubuntu?

How are you trying to install them?

My advice is to get Ubuntu installed on the target machine, and then install the packages through synaptic via the Internet.

This is the standard way that packages are generally installed.

System -> Administration -> Synaptic Package Manager

Select the packages you want, and click apply.

- zipperback
:popcorn:

---

### Post by bodhi.zazen on 2008-01-18
Packages are not installed that way.

Just because the packages you have are from debian or that they are *.deb does not mean they are compatible with Ubuntu. It would be like trying to ren a Vista *.exe in Windows XP ...

The easiest way is via ADD/Remove programs.

Next easiest would be synaptic.

Last would be the command line (sudo apt-get install apache2 )

If you use those tools dependencies will be managed for you.

See these links :

[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

These assume you have an internet connection.

If you do not have an internet connection, use APTOnCD : [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by wolfen69 on 2008-01-18
unfortunately it will be very difficult if not impossible to install some things without internet. 

aptoncd [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)  is your best bet. but you will need to access the internet and burn a cd which you can use on your machine.

---

### Post by sundar22in on 2008-01-18
Ubuntu version: 7.04
DVD Packages are for Debian 4(May be working for Ubuntu)
I double clicked *.deb package for installation, since I was not successful I used Synaptic package manager to add the DVD for installation and then selected the packages for installation. Even then It failed for the same missing dependency.

~ Sundar ~

---

### Post by bodhi.zazen on 2008-01-18
In general you can not do that, ie you can not mix Debian packages with Ubuntu.

It is possible with Pinning, but this is an advanced topic and can lead to breakage.

See my first post.

---

### Post by sundar22in on 2008-01-18
Thank you all for helping me out. I will try out APTonCD.

~ Sundar ~

---

### Post by aysiu on 2008-01-18
If you don't have an internet connection, you'd probably be better off using straight-up Debian *instead* of Ubuntu.

**Good**: Debian packages with Debian but no internet connection
**Okay**: Ubuntu packages with Ubuntu but no internet connection
**Bad**: Debian packages with Ubuntu regardless of connection

---

