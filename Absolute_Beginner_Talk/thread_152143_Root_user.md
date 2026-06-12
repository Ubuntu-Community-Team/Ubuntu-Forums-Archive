---
title: "Root user"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by micrologix on 2006-03-29
I am new (after 5 years away from it) to Linux and have installed Ubuntu 5.10 from a PC magazine disk. I have used Red Hat previously and during installation ther was an option to create a password for the Root user. When I installed Ubuntu there was no such option and therefore when I try to su root I cannot log in as there is no password. This makes it impossible, or so it seems to me to be able to edit config files as the owner ir Root and I can only view these files in Read Only mode. Is there a way to work around this, thanks in advance for your help.

---

### Post by LanceM on 2006-03-29
if you are using the user you set up on install you use "sudo" and you will be asked for your password. 

sudo gedit /etc/apt/sources.list

---

### Post by frodon on 2006-03-29
All you may want to know is here, i think : [https://wiki.ubuntu.com/RootSudo?](https://wiki.ubuntu.com/RootSudo?)

---

### Post by LanceM on 2006-03-29
I was just getting ready to paste that link also. :)

---

### Post by kaffeine on 2006-03-29
a wiki search is all you need...[ solution here]("https://wiki.ubuntu.com/RootSudo").

---

### Post by micrologix on 2006-03-29
[QUOTE=frodon]All you may want to know is here, i think : [https://wiki.ubuntu.com/RootSudo?](https://wiki.ubuntu.com/RootSudo?)[/QUOTE]

Thanks very much, that explains it nicely.

---

### Post by micrologix on 2006-03-29
Thanks very much, that explains it nicely.

---

