---
title: "Screen doing funky things with Ubuntu and Xubuntu for PPC."
date: 2010-11-01
forum: Apple Hardware Users
---

### Post by trauma-d on 2010-11-01
Hi,
 this is my first thread so bear with me. I have an Apple ibook 3G with a 500mhz ppc processor and 384MB of Ram that _used_ to run OSX 2.8 but I am trying to install linux on it. I want to install Ubuntu or Xubuntu on it because I have been a Ubuntu user for a couple of years and I love it. But when I tried to install them my screen does funky things. The screen only fills up part of the screen and then there is like a partial mirror image of the screen on bottom of that screen and i think its something to do with the graphics config because I installed Yellow Dog Linux on it and it worked for a while and then does the same thing so I know its not the screen its self. I hope to get a few pics of it soon. But I was wondering if anyone has had the same problem or knew how to fix it.:confused:

:)Thanks,

---

### Post by linuxopjemac on 2010-11-02
Can you give me the link in everymac.com of your iBook please ?

---

### Post by trauma-d on 2010-11-02
> **linuxopjemac said:**
> Can you give me the link in everymac.com of your iBook please ?
 
 
[http://www.everymac.com/systems/apple/ibook/stats/ibook_500.html](http://www.everymac.com/systems/apple/ibook/stats/ibook_500.html)
 
I think this is the one. mine has a dvd-rom and 128mb of factory ram.

---

### Post by linuxopjemac on 2010-11-02
ok, in a terminal do the following:
```
wget http://mac.linux.be/files/xorg/ibook1.txt
sudo mv ibook1.txt /etc/X11/xorg.conf
```

Reboot and enjoy.

---

### Post by trauma-d on 2010-11-04
> **linuxopjemac said:**
> ok, in a terminal do the following:
```
wget http://mac.linux.be/files/xorg/ibook1.txt
sudo mv ibook1.txt /etc/X11/xorg.conf
```
 
Reboot and enjoy.
 
 
Thank you, this worked perfectly! And it was pretty simple. I thought I was gonna have to do a lot more work and edit things myself but that was easy.
Thanks again :-D

---

### Post by linuxopjemac on 2010-11-04
You are welcome.

---

### Post by dfeifer on 2011-03-02
Just wanted to say thank you as well. I have the same ibook with the same symptoms and this fixed it as well.

---

