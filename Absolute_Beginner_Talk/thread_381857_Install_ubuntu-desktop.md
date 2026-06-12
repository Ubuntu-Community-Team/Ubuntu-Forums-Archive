---
title: "Install ubuntu-desktop"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by cmaksymchuk on 2007-03-11
Hi All,

I just installed the ubuntu server 6.1 and want to install the desktop envronment.  My internet connectino is giviing me problems lately so I was wondering if I could somehow install the desktop off of the ubuntu-desktop 6.1 cd?  Could I do this and if so how do I do it?   Change my sources.list?

Thanks in advance,

C

---

### Post by Kobalt on 2007-03-11
Yes you will need to add a line in your sources.list, a line corresponding to a Desktop CD of Ubuntu 6.10. You will have to do this all in command line, this way : 
```
sudo apt-cdrom
```
(make sure you have the Desktop CD in your drive)
Reload your source package manager :
```
sudo aptitude update
sudo aptitude upgrade
```
And then install your ubuntu-desktop package : 
```
sudo aptitude install ubuntu-desktop
```

---

### Post by cmaksymchuk on 2007-03-11
Thanks for the reply.  I just tried off the internet again... one last time.  But instead of using aptitude, I used apt-get.  Should I have used aptitude?  What is the difference and when should I use one over the other.

---

### Post by cmaksymchuk on 2007-03-11
Ok, I followed your directions.  but then when I went to install ubntu desktop it just asked me for the server cd again.  Any idea's?

---

### Post by aysiu on 2007-03-11
You can't install packages off the **Desktop CD**. Well, actually, you can install some packages (like *build-essential* or *ndiswrapper-utils*), but you can't install the package set you want (*ubuntu-desktop*)--for that, you need the **Alternate CD.**

Your best bet, since you "just installed" the server edition, is to "just install" the Desktop CD right over it.

---

### Post by Kobalt on 2007-03-11
I don't know if the ubuntu server cd contains the ubuntu-desktop package actually... Which is why I wrote Desktop CD before, and not Server...

---

### Post by Kobalt on 2007-03-11
Aysiu : out of curiosity, how come you can't install ubuntu-desktop from the Desktop CD ?

---

### Post by aysiu on 2007-03-11
> **Kobalt said:**
> Aysiu : out of curiosity, how come you can't install ubuntu-desktop from the Desktop CD ?
The Desktop CD doesn't have all the packages required for the *ubuntu-desktop*, but it has a live session that gets copied over when you install it to your hard drive. That's why the Alternate CD takes three times as long to install as the Desktop CD--the Alternate CD actually takes all the .deb files and unpacks them and installs them the "proper" way.

---

### Post by Kobalt on 2007-03-11
Thanks for the info ;)

---

