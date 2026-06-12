---
title: "Adobe 7 install"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by DevNull11 on 2006-10-25
I just installed adobe acobat 7 using the rpm from there web site. Then I ran this command:  
alien -di /home/sam/Downloads/AdobeReader_enu-7.0.8-1.i386.rpm to convert it to a .deb and install adobe. However I cannot run the acroread com and to open adobe or run it from the start applications menu. I took a look at the permissions on the /usr/bin/acroread file and noticed  that it did not have the execute permission and I wonder if all the adobe files are like that.

---

### Post by Perfect Storm on 2006-10-25
If you setup universe and multiverse in your source list it's easy to get Adobe installed.



```
sudo aptitude install acroread mozilla-acroread acroread-plugins
```


No need to mess with .rpm packages.
Before installing from the repo, uninstall the converted .deb.

---

### Post by DevNull11 on 2006-10-25
How would I uninstall the converted .deb

---

### Post by meng on 2006-10-25
sudo dpkg -r AdobeReader
(not sure about that last part, it could be acroread or some variation thereof)

---

### Post by DevNull11 on 2006-10-25
root@sam-laptop:~# dpkg -r | /root/adobereader-enu_7.0.8-2_i386.deb
/root/adobereader-enu_7.0.8-2_i386.deb: line 1: syntax error near unexpected token `newline'
/root/adobereader-enu_7.0.8-2_i386.deb: line 1: `!<arch>'
dpkg: --remove needs at least one package name argument

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

---

### Post by skymt on 2006-10-25
```
sudo dpkg -r adobereader-enu
```

---

### Post by DevNull11 on 2006-10-25
> **skymt said:**
> ```
sudo dpkg -r adobereader-enu
```

wow I tryed everything but that



Thnks for the Help It works great now

---

