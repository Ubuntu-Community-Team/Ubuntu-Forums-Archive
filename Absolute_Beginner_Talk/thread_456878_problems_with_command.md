---
title: "problems with command"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by ooblez on 2007-05-28
so i was installing microsoft truetype fonts via the command prompt and my net cut out.
now i get this:

> henry@henrys-laptop:~$ sudo apt-get -y install unrar 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


so i do this:
> henry@henrys-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege


please help!

---

### Post by moma on 2007-05-28
Run it as administrator, superuser (sudo).

$ [COLOR="SeaGreen"]sudo dpkg --configure -a[/COLOR]

It will ask your (normal user) password.

Read: [http://ubuntuforums.org/showthread.php?p=1283789#post1283789](http://ubuntuforums.org/showthread.php?p=1283789#post1283789)

---

### Post by ooblez on 2007-05-28
ok thanks, thats brought up
> henry@henrys-laptop:~$ sudo dpkg --configure 
dpkg: --configure needs at least one package name argument

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
henry@henrys-laptop:~$ 


what now?:)

---

### Post by moma on 2007-05-28
Did you forget something. The little -a at the end.

---

### Post by ooblez on 2007-05-28
ehe. thanks.

sorry about that, your helps really apprecated:)

---

