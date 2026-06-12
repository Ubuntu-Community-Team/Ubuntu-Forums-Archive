---
title: "kubuntu equvalent of gedit"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by GQed76 on 2006-07-27
a friend has kubuntu instead of gnome, which im used too.
he needs to do a sudo gedit command. but i dont know what to replace gedit with in kubuntu

---

### Post by Lord Illidan on 2006-07-27
Try ```
kdesu kate *name of file*
```

kate is similar to gedit but has more features.

---

### Post by moma on 2006-07-27
It's "kate"

$ kate 


Another good alternative is: 
$ nano


// moma  
   [http://www.futuredesktop.com/ubuntu6.06.html]("http://www.futuredesktop.com/ubuntu6.06.html")

---

### Post by GQed76 on 2006-07-27
*grin* thanks  amazing how fast this fourm is

---

### Post by Lord Illidan on 2006-07-27
> **moma said:**
> It's "kate"

$ kate 


Another good alternative is: 
$ nano


// moma  
   [http://www.futuredesktop.com/ubuntu6.06.html]("http://www.futuredesktop.com/ubuntu6.06.html")

aye, but he needs sudo privileges and nano is a console app.

---

### Post by aysiu on 2006-07-27
> **Lord Illidan said:**
> aye, but he needs sudo privileges and nano is a console app.
*nano* works just fine, though. ```
sudo nano
``` or ```
kdesu kate
``` or ```
kdesu kwrite
``` or ```
gksudo gedit
``` or ```
gksudo mousepad
``` They all do the same thing.

---

### Post by Lord Illidan on 2006-07-27
> **GQed76 said:**
> *grin* thanks  amazing how fast this fourm is

Aye, aye, sir...we are the best...now where are our tips? :D

---

### Post by easyease on 2006-07-27
too many helpfull people round here eh.lol

---

### Post by Lord Illidan on 2006-07-27
> **easyease said:**
> too many helpfull people round here eh.lol
Just be a little faster!

---

### Post by OU812 on 2006-07-28
What is the difference between 

```
kdesu kate /path
```

and

```
sudo kate /path
```

Thanks.

john

---

### Post by aysiu on 2006-07-28
This is the difference:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

