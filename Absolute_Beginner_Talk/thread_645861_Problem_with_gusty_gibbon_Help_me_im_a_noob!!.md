---
title: "Problem with gusty gibbon? Help me im a noob!!"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by cold clock on 2007-12-20
Hi people

im having problems with my ubuntu 7.10! every time i try and add a program using anything, package manager, add and remove program, synaptic package manager in will load th files and give this error message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i try putting in "dpkg --configure -a" into the terminal and it dosent really do anything. it comes up with this

rowan@Xanadu:~$ dpkg --configue -a
dpkg: unknown option --configue

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
rowan@Xanadu:~$ 

i have realy screwed up this computer in the past (hense why im trying linux it seems to be alot better (this coming from a hardcore windows user :))) but i could be something easaly fixable can anyone help me!!!

cheers (please help this noob :))

---

### Post by plvaulter06 on 2007-12-20
i would help you, but i loaded ubuntu last night and i have the exact same problem!!! haha ill be waiting for an answer also

---

### Post by jryprt on 2007-12-20
> **cold clock said:**
> Hi people

im having problems with my ubuntu 7.10! every time i try and add a program using anything, package manager, add and remove program, synaptic package manager in will load th files and give this error message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i try putting in "dpkg --configure -a" into the terminal and it dosent really do anything. it comes up with this

rowan@Xanadu:~$ dpkg --configue -a
dpkg: unknown option --configue

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
rowan@Xanadu:~$ 

i have realy screwed up this computer in the past (hense why im trying linux it seems to be alot better (this coming from a hardcore windows user :))) but i could be something easaly fixable can anyone help me!!!

cheers (please help this noob :))

Check you spelling (dpkg --configure -a)(dpkg --configue -a)

---

### Post by Darkade on 2007-12-20
try typing
sudo dpkg --configue -a
this happened to me a while ago and that's how it worked for me.

---

### Post by thelatinist on 2007-12-20
You've misspelled "configure."

---

### Post by cold clock on 2007-12-20
thank you people, it is all now solved :):):)!!![spelling mistake]:lolflag:

---

### Post by Zoltarp on 2007-12-20
I too am a noob but I am sure someone with experience will help. This is a bump 4 you.

---

### Post by plvaulter06 on 2007-12-20
what is the terminal?? where is it?

---

### Post by ugm6hr on 2007-12-20
> **plvaulter06 said:**
> what is the terminal?? where is it?

Look at my Signature link below (courtesy of aysui).

---

