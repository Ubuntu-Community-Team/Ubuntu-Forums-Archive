---
title: "uninstalling LaCie"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by caltabellotta on 2007-02-16
Hello,

I have installed [Lacie lightscribe labeller]("http://www.lacie.com/products/product.htm?pid=10803") for unix, being that my dvd drive has the ability to burn images onto discs.  After finding out that lacie does not work, and that it takes a very long time to access the applications menu when it is installed, i would like to remove it.  Synaptic, Add/Remove shows no signs of it being installed, and therfore i realized I need to do it manually.  Anyone know how to get this done?  Thanks,

Calta

---

### Post by jpeddicord on 2007-02-17
The file appears to be an RPM (yuck!). To remove it, you will need to run:
```
sudo rpm -e lightscribe
```You might have to hit <tab> after you type lightscribe to complete the rest of the package.

---

### Post by watson540 on 2007-03-07
I hope you did not use rpm to install it. you should have used alien to make a deb package. lightscribe works under dapper out of the box and if you're running edgy it will work too but it is a rather drawn out but very well outlined process. you can see the thread in these forums about it, do a search for edgy lightscribe

---

