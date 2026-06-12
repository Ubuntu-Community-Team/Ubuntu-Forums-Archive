---
title: "Un-installation of an alien Converted Deb"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-02-15
i did this:
```

shoaibi@saber-rider:~$ sudo alien VMwareTools-5.5.2-29772.i386.rpm
Warning: Skipping conversion of scripts in package VMwareTools: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
vmwaretools_5.5.2-29773_i386.deb generated
shoaibi@saber-rider:~$ sudo dpkg -i vmwaretools_5.5.2-29773_i386.deb 
(Reading database ... 93986 files and directories currently installed.)
Preparing to replace vmwaretools 5.5.2-29773 (using vmwaretools_5.5.2-29773_i386.deb) ...
Unpacking replacement vmwaretools ...
Setting up vmwaretools (5.5.2-29773) ...



```
and now when i try to remove it, i get this:
```

shoaibi@saber-rider:~$ sudo dpkg -r vmwaretools_5.5.2-29773_i386.deb 
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

```
what's this?

---

### Post by ashmew2 on 2007-02-15
It means that when u use to install a .deb package with dpkg it installs , but u cannot delete the package like that.If u want to delete the .deb package , simply do :

```
sudo rm /path/to/the/.deb
```

if u want to remove the thing u installed (that is VMWARE tools) , use the SYnaptic manager!!

---

### Post by shoaibi on 2007-02-15
Butt on Ubuntuguide.org it is suggested to use dpkg -r :(

---

### Post by ashmew2 on 2007-02-15
I havent used dpkg -r frequently but when i tried to use it it wudnt work so i use the synaptic and the command i told u :P and i Enjoy lol

---

### Post by lamego on 2007-02-15
Dpkg -r requires the package name, not the filename, you should read the man page:
```
dpkg -r vmwaretools
```

---

### Post by zAo on 2007-02-15
Yeah, try Synaptic or try:
>  sudo dpkg -r vmwaretools

EDIT: Lol. I'll try to be faster next time :)

---

