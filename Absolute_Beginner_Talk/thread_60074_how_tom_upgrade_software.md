---
title: "how tom upgrade software?"
date: 2005-08-26
forum: Absolute Beginner Talk
---

### Post by Radi0ShacK on 2005-08-26
Hi all,
i ve installed a software compiled it from source "usually ./configure; make; sudo make install", but what if i want to update this software what shall i do should i remove this software "remove binary, man pages ...etc ](*,) " then install the updated one or ??? can plz any one answer me? thanks :)

---

### Post by KingBahamut on 2005-08-26
I assume your asking how to upgrade a source package?

---

### Post by Radi0ShacK on 2005-08-26
yes

---

### Post by Radi0ShacK on 2005-08-27
hi,
plz can any one answer me?

---

### Post by amohanty on 2005-08-27
have you looked at checkinstall. You can install it via synaptic.

Then instead of 
configure; make; make install;
you can do 
configure; make; checkinstall;

this will create a .deb. package for you. 
To uninstall the package you can then do a 
dpkg -r <appname>
where appname is usually the filename in <filename>.tar.gz/bz2 etc.

To upgrade in this scenario you would usually have to uninstall the old package and reinstall the new package using the abovementioned checkinstall method.

If you only want to patch, just apply the patch to the source, uninstall the old package and reinstall.

HTH
AM

---

### Post by Radi0ShacK on 2005-08-27
amohanty, thanks alot this is a really cool tip, is this the way to create a debian/ubuntu package "i can distribute it"?

---

### Post by SSTwinrova on 2005-08-27
There's a whole lot more work put into creating the packages that go into the official repositories (dependency resolving, etc.), but any packages you make this way should be fine to give to your friends as long as they have a similar system to yours (since deps will not get resolved automatically).

---

