---
title: "how e can set the home path in deb package"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by cnu_sree on 2007-08-21
iam creating a deb package in ubuntu.
i want to place some files in home path
so how can i set  the home path in deb package
i will explain with example:
my user name is sree
so iam placing a file 1.txt  in /home/sree 
but how can  create .deb package to place 1.txt in home/sree
but the user name is not same in all the ubuntu sytem so how can i trace the user name in .deb 
thank u,inadvance
sree

---

### Post by ddrichardson on 2007-08-21
I'd post this in Programming - you're more likely to hit the right audience.

---

### Post by capink on 2007-08-21
One way to achieve this is to place the file 1.txt in some place like /usr/local/packagename and then add postinst script to the package that will do the following:

```
for i in `who | awk '{print $1}' | tr '\n' ' '`
do
cp /usr/local/packagename/1.txt /home/$i
done
```

note that this will copy the file to all logged in users at the time of install. And you will probably have to make another postrm script to reverse the above process when uninstalling the package.

---

### Post by ayu on 2007-08-21
I don't know about debs, but in the shell if you want only the current user you can just use the variable $USER or $USERNAME, or the command whoami.

---

### Post by Kilz on 2007-08-21
[The hard way to make a deb ]("https://wiki.ubuntu.com/HowToBuildDebianPackagesFromScratch?highlight=%28deb%29")

[The easy way to make a deb]("http://linuxdevices.com/articles/AT8047723203.html")

---

### Post by capink on 2007-08-21
> **ayu said:**
> I don't know about debs, but in the shell if you want only the current user you can just use the variable $USER or $USERNAME, or the command whoami.

Since deb packages require root privileges, these variables as well as the command whoami will point to the root account.

---

