---
title: "dpkg"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-03-29
get this error when invoke dpkg

/usr/bin/dpkg: /usr/bin/dpkg: cannot execute binary file

lex1:(

---

### Post by aysiu on 2006-03-29
Have you always had this error, or did this happen recently? In what way are you trying to invoke dpkg?

Have you tried this? ```
sudo chmod 755 /usr/bin/dpkg
```

---

### Post by lex1 on 2006-03-29
here iswhat happened

lex1@xstation:~$ sudo chmod 755 /usr/bin/dpkg
Password:
lex1@xstation:~$ sudo -i dpkg wine_0.9.5-winehq-1_i386.deb
/usr/bin/dpkg: /usr/bin/dpkg: cannot execute binary file
lex1@xstation:~$

---

### Post by cronholio on 2006-03-29
Try:

```
sudo apt-get --reinstall install dpkg
```

---

### Post by lex1 on 2006-03-29
still no joy

lex1@xstation:~$ sudo apt-get --reinstall install dpkg
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 1812kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main dpkg 1.13.10ubuntu4 [1812kB]
Fetched 1812kB in 25s (70.9kB/s)

Preconfiguring packages ...
(Reading database ... 74712 files and directories currently installed.)
Preparing to replace dpkg 1.13.10ubuntu4 (using .../dpkg_1.13.10ubuntu4_i386.deb) ...
Unpacking replacement dpkg ...
Setting up dpkg (1.13.10ubuntu4) ...

lex1@xstation:~$ sudo -i dpkg wine_0.9.5-winehq-1_i386.deb
/usr/bin/dpkg: /usr/bin/dpkg: cannot execute binary file
lex1@xstation:~$ updatedb
fatal error: updatedb: You are not authorized to create a default slocate database!
bliss1@xstation:~$ sudo updatedb
lex1@xstation:~$ sudo -i dpkg wine_0.9.5-winehq-1_i386.deb
/usr/bin/dpkg: /usr/bin/dpkg: cannot execute binary file
lex1@xstation:~$


lex1:rolleyes: :rolleyes:

---

### Post by meborc on 2006-03-29
is there a difference between 

**sudo dpkg -i**
&
**sudo -i dpkg**

or not

? ...

---

### Post by engla on 2006-03-29
[QUOTE=meborc]is there a difference between 

**sudo dpkg -i**
&
**sudo -i dpkg**

or not

? ...[/QUOTE]
yes, absolutely. Only the former works, since the -i is an option for dpkg, not sudo.

---

### Post by cronholio on 2006-03-29
](*,)

^^ That's the problem, exactly. I'm glad I'm not the only one that didn't spot it.:p

---

### Post by meborc on 2006-03-29
i thought so :mrgreen:

---

