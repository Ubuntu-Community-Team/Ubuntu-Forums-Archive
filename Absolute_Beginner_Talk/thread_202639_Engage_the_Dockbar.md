---
title: "Engage the Dockbar"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by J.J Morrison on 2006-06-23
I downloaded gdesklets but the launcher won't work so I found Engage and followed this [site]("http://www.supriyadisw.net/2006/04/engage-on-my-ubuntu-dapper-drak  e.html") and everything was workin fine until I entered ```
sudo apt-get install engage
``` then I got: 
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package engage
  The CVS? version looking confusing so I didn't try that anybody else another way of installing it. Please and Thank You

---

### Post by Technoviking on 2006-06-23
Did you add 
```
deb http://soulmachine.net/breezy/ unstable/
```
to /etc/apt/sources.list

---

### Post by moore.bryan on 2006-06-23
check the post on [http://www.macewan.org/category/ubuntu-linux/](http://www.macewan.org/category/ubuntu-linux/)... it talks about how the soulmachine repo no longer works.  follow those directions and things should be good.

---

### Post by J.J Morrison on 2006-06-23
Thanks but I dont know what to do at this step:
Next we need to edit or create /etc/apt/preferences with:

Package: enlightenment
Pin: version 0.16.999*
Pin-Priority: 999

Package: enlightenment-data
Pin: version 0.16.999*
Pin-Priority: 999

---

### Post by J.J Morrison on 2006-06-23
I tried downloading from the soulmachine repo first and someone told me that it didn't work anymore and told me to try this [link]("http://www.macewan.org/category/ubuntu-linux/") and it doesnt work either so does anybody have the link?

---

### Post by moore.bryan on 2006-06-24
it wants you to create/edit the file "preferences" in /etc/apt and paste in that info...
in the terminal, try:
username@ubuntu:~$ sudo gedit /etc/apt/preferences

when gedit opens, it will either have found the file and opened it or opened a blank file.  either way, just paste in
Package: enlightenment
Pin: version 0.16.999*
Pin-Priority: 999

Package: enlightenment-data
Pin: version 0.16.999*
Pin-Priority: 999 

save in gedit and exit out... that should send you back to your terminal where you can run through the rest of the stuff.

---

### Post by siguy on 2006-06-27
Unfortunately it appears those instructions no longer work either.

---

### Post by moore.bryan on 2006-06-28
what do you mean?

---

### Post by cak3p on 2006-07-03
This tutorial move to [http://www.supriyadisw.net/2006/04/engage-on-dapper-drake](http://www.supriyadisw.net/2006/04/engage-on-dapper-drake) . I hope it will help you Have a nice day and good luck :KS

---

