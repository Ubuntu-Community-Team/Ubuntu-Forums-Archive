---
title: "Frostwire STILL wont work"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-10-17
I have tried installing it from automatix, I have used the HOWTO posted here, and I have tried doing it manually. Every single time it gives me the same thing:

sam@sam-laptop:~$ frostwire
runFrost.sh: 44: Syntax error: "(" unexpected (expecting "}")



Help please? :)

---

### Post by tgunner on 2006-10-17
Have java installed correctly?

---

### Post by gustolove on 2006-10-17
try aMule?

---

### Post by voodoonirvana on 2006-10-17
Yes I have Java installed (correctly). And does aMule have the same amount of files/peers as frostwire or limewire?

---

### Post by DougieFresh4U on 2006-10-17
Just to mention a couple of things I went through:: Do you have Java 1.4  & Sun Java 5? Also if you are running Edgy, the dash  has to be changed to bash. Don't know if this helps, but thought I would try.

---

### Post by taurus on 2006-10-17
Also, how did you install frostwire, by hand, with Automatix, repos?

---

### Post by voodoonirvana on 2006-10-17
I have tried using automatix, and I have tried it using the HOWTO here. Neither worked. Both gave me the same message. Oh, and Im in Dapper.

---

### Post by taurus on 2006-10-17
Have you tried to install this one?

[http://www.frostwire.com/](http://www.frostwire.com/)

```
sudo dpkg -i FrostWire-4.10.9-2.i586.deb
```
p.s.  Don't forget to remove the current version that you have on your machine first before you install the one from above!!!

---

### Post by voodoonirvana on 2006-10-17
> **taurus said:**
> Have you tried to install this one?

[http://www.frostwire.com/](http://www.frostwire.com/)

```
sudo dpkg -i FrostWire-4.10.9-2.i586.deb
```
p.s.  Don't forget to remove the current version that you have on your machine first before you install the one from above!!!

Yep, did that. Same message.

---

### Post by underdog512 on 2006-10-17
If you have frostwire installedbut its just not running try this 

sudo update-alternatives --config java

select sun's

---

### Post by voodoonirvana on 2006-10-17
Is the 3rd the sun one? Im assuming so, seeing that it says "J2SE"

---

### Post by voodoonirvana on 2006-10-17
> **underdog512 said:**
> If you have frostwire installedbut its just not running try this 

sudo update-alternatives --config java

select sun's

Okay I chose option 2 and then tried the dpkg thing again and it still gave me the same thing. But is it really supposed to be trying to open a ".sh",  is that even the right file extension?
And could you or someone give more specific instructions on how to try and install frostwire after running the java config. Thanks.

---

