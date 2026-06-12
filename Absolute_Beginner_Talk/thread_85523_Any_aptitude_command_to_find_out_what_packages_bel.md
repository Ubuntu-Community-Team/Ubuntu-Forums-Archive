---
title: "Any aptitude command to find out what packages belong to a virual package?"
date: 2005-11-02
forum: Absolute Beginner Talk
---

### Post by Akhran on 2005-11-02
Eg. aptitude search somepackage
Results : v somepackage <--- virtual package.

Is there a way to find out what are packages that belong to the virtual package?

Thanks !

---

### Post by Kyral on 2005-11-02
apt-cache show <package>

They will be listed under Depends

---

### Post by Akhran on 2005-11-02
Doesn't seem to work. 

Eg. I did a 'aptitude search openldap'
one of the results show 
v   sourceforge-ldap-openldap, which is a virtual package.

when I do apa-cache show sourceforge-ldap-openldap, nothing turns up. How do I find out what are the packages providing the source-ldap-openldap virual package, preferably via aptitude?

Thanks again !

[QUOTE=Kyral]apt-cache show <package>

They will be listed under Depends[/QUOTE]

---

