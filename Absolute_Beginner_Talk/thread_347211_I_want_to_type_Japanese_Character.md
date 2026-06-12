---
title: "I want to type Japanese Character"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by pearlygate on 2007-01-26
Hi all, I installed the japanese language support. Now how do I type in japanese? 

Thanks in advance

---

### Post by ajmorris on 2007-01-26
Did you get just the language support package or the keyboard input package? I am pretty sure they're seperate packages.

---

### Post by pearlygate on 2007-01-26
umm where can I get the keyboard input package? I installed the support package

---

### Post by harerama on 2007-01-27
Hello,

Take a look at this page. It should be done easily! Good luck. :D 

[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)

Sincerely

---

### Post by nike984 on 2007-01-27
If you have installed all required material, and set Japanese as the default language,
SCIM will automatically start after reboot.

If your using English as default, SCIM will not start up,but you can force it to use SCIM in English environment.

open a terminal an wrote

```
sudo ln -s /etc/X11/xinit/xinput.d/scim /etc/alternatives/xinput-en_US

sudo ln -s /etc/alternatives/xinput-en_US /etc/X11/xinit/xinput.d/en_US
```

then reboot and SCIM will work.

---

### Post by ryukent on 2007-01-29
If you want to install Japanese input for any Ubuntu language (not just US english) and set up the fonts so that they actually look nice and the characters are rendered in the same style, follow this link:

 HOWTO: Installing Japanese that looks nice on Ubuntu Edgy : &#26085;&#26412;&#35486;
[http://ubuntuforums.org/showthread.php?t=338991](http://ubuntuforums.org/showthread.php?t=338991)

---

### Post by pearlygate on 2007-02-06
hey thanks a lot. I like the im ja thing. I can always use gedit to type japanese character that I want and copy paste it somewhere. 

Thanks

---

