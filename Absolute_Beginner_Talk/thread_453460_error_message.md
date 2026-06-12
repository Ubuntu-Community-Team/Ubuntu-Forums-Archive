---
title: "error message"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by Timmy66 on 2007-05-24
.E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

can somebody help please.I'm really trying to make this work.because I can not stand bill gates or microjunk.

---

### Post by Nythain on 2007-05-24
in terminal try typing sudo dpkg --configure -a
sounds like something you were installing in synaptic or  with apt-get got interrupted during set up.

---

### Post by Timmy66 on 2007-05-24
dpkg: unknown option -o

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
bloodcrystal@bloodcrystal-1:~$ 

this what came up after I typed it in the terminal

---

### Post by Nythain on 2007-05-24
thats an a not an o... its sudo dpkg --configure -a

---

### Post by Timmy66 on 2007-05-24
Thank you,sorry for sounding like a true noob.It worked flawlessly after I typed in the right line thank you once again.

---

