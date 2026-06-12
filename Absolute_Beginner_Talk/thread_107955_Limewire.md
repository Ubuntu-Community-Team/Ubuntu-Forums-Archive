---
title: "Limewire"
date: 2005-12-24
forum: Absolute Beginner Talk
---

### Post by Dr Von Bon Bon on 2005-12-24
I've installed Limewire and have also installed Java (the J2SE runtime thingy) and still when I click on it nothing happens. 

It doesn't come up with an error or anything.
Any ideas?

---

### Post by peanut butter on 2005-12-24
i would try uninstalling it and then using Automatix to install it. this will be the easiest way you should also try frostwire

---

### Post by Perfect Storm on 2005-12-24
Try run limewire in the terminal and see what output comes out.

By the way which package version did you use of limewire?

---

### Post by GTvulse on 2005-12-24
[QUOTE=Dr Von Bon Bon]I've installed Limewire and have also installed Java (the J2SE runtime thingy) and still when I click on it nothing happens. 

It doesn't come up with an error or anything.
Any ideas?[/QUOTE]

```

dradul@the-void:~$ sudo update-alternatives --config java
Password:

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
 +    2        /usr/lib/jvm/java-gcj/bin/java
*     3        /usr/lib/j2re1.5-sun/bin/java

Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/j2re1.5-sun/bin/java' to provide `java'.

```

---

### Post by Badojo on 2005-12-24
ive also had the same problems when trying to install aanything for that matter and well try terminal and if that does not work make sure that you downloadedd the right file format did you download the 32 bit version or the 64 bit version. I am almost positive that you probley suppose to download the 32 bit version my problem was that I downloaded the FreeBSD version DONT DOWNLOAD THAT ONE.

---

