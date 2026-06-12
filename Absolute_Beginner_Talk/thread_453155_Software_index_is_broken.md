---
title: "Software index is broken"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by Agent47 on 2007-05-24
Hi ! Its looks like I **** up it. and now update manager is giving me this error : it is impossible to install or remove any software. Please use the package manager Synaptic or run sudo apt-get install-f in a terminal to fix this issue at first.
But problem is that I cant run package manager Synaptic, it will give me similar error and in terminal I m not very good also. I try to do in terminal but I got some error that I do not have this privilegs etc.
How I can fix this problem?

---

### Post by Bachstelze on 2007-05-24
Run this in your terminal :

```
sudo apt-get -f install
```

---

### Post by Agent47 on 2007-05-24
> **HymnToLife said:**
> Run this in your terminal :

```
sudo apt-get -f install
```

I did it and error is: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by Bachstelze on 2007-05-24
Run it, then, and don't forget sudo !

---

### Post by Agent47 on 2007-05-24
What do you mean? Of cause i run it but then i get : dpkg: requested operation requires superuser privilege
what does it mean ? How I can get superuser privilege?

---

### Post by Bachstelze on 2007-05-24
That's what sudo is for...

---

### Post by Dayylin on 2007-05-24
Enter the command           sudo dpkg --configure -a

---

### Post by Agent47 on 2007-05-24
I told you I m not master in terminal and my knowledge about ubuntu is quite tiny. So I really do not know any commands. If you are so smart and nice would you help me a little ? What do I have to write in terminal window?

---

### Post by Agent47 on 2007-05-24
I figured out this but : priit@Priit-VAIO:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-00-2ubuntu2); however:
  Package sun-java6-bin is not installed.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-restricted-extras:
 ubuntu-restricted-extras depends on sun-java6-plugin; however:
  Package sun-java6-plugin is not configured yet.
dpkg: error processing ubuntu-restricted-extras (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-plugin
 ubuntu-restricted-extras
priit@Priit-VAIO:~$

---

### Post by Bachstelze on 2007-05-24
You need to install sun-java6-bin. Since you r APT doesn't seem to work, you'll have to install it manually.

```

cd
wget http://mirrors.kernel.org/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-00-2ubuntu2_i386.deb
sudo dpkg -i sun-java6-bin_6-00-2ubuntu2_i386.deb
```

---

### Post by Agent47 on 2007-05-24
I think I can kiss you ;) You solve my problems many thanx

---

