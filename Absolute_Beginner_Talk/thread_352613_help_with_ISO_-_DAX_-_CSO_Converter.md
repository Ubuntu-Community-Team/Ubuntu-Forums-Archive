---
title: "help with ISO - DAX - CSO Converter"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Fittersman on 2007-02-03
i found this:

[http://kde-apps.org/content/show.php?content=49674](http://kde-apps.org/content/show.php?content=49674)

it seems to have everything i want, but i cannot understand what i am supposed to do to make it work... i tried reading the readme, it has some commands i need to type in but since i dont know what they mean and i dont know wheen to type them in, i dont know what to do... any help is appreciated :)

or if anyone else knows how to convert my ISOs to CSOs on ubuntu

---

### Post by shareMenaPeace on 2007-02-03
Did you tried to search and install this with synaptic?

SYSTEM -> ADMINISTRATIOJN -> SYNAPTIC

---

### Post by Fittersman on 2007-02-03
Not listed there, unless my search skills suck :P

---

### Post by shareMenaPeace on 2007-02-03
You mean you searched with synaptic or you couldnt find synaptic?

Just download the source and follow the readme post if you get stuck.

---

### Post by Fittersman on 2007-02-03
i searched in symnatec, and im having problems understanding the readme, like what folder i have to be in to use the commands i think is my problem but im not sure...

---

### Post by shareMenaPeace on 2007-02-03
Extraxt the source file to a folder eg. in /home/YOURNAME/Desktop
Than open up a terminal window and change to the folder eg.
```
cd /home/YOURNAME/Desktop
```
than run the command from the readme
```
gcc -o ciso ciso.c -lz
```
and 
```
chmod a+x ciso
```

---

### Post by Fittersman on 2007-02-03
sorry if im real noobish but this is what i tried, where am i going wrong?

```
cleippi@cleippi-desktop:~$ cd Desktop/
cleippi@cleippi-desktop:~/Desktop$ gcc -o ciso ciso.c -lz
gcc: ciso.c: No such file or directory
cleippi@cleippi-desktop:~/Desktop$ ls
49674-ISODAXCSO108.tar.gz  IE6.0.desktop  ISODAXCSO
cleippi@cleippi-desktop:~/Desktop$ cd ISODAXCSO/
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO$ gcc -o ciso ciso.c -lz
gcc: ciso.c: No such file or directory

```

---

### Post by shareMenaPeace on 2007-02-03
Ok hmm what is inside the folder?

> ls

---

### Post by Fittersman on 2007-02-03
ls is just the command i used to show what files/folders are inside the one that i am currently in

---

### Post by shareMenaPeace on 2007-02-03
Yes can you post the output?
Im new to linux aswell so maybe someone can help you compiling the code than.

---

### Post by Fittersman on 2007-02-03
thats all it gives me as listed above ^^

---

### Post by shareMenaPeace on 2007-02-03
I dont see the content of ISODAXCSO

Please use this command to list the folder content

```
ls
```

---

### Post by Fittersman on 2007-02-03
ill do even better than that, ill list all the files and folders that i have in there  :)

```
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO$ ls
compiled tools  ISODAXCSO for kommander 1.2.0  readme
How to          ISODAXCSO for kommander 1.3.0  Sources
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO$ cd compiled\ tools/
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/compiled tools$ ls
ciso  daxcr  docmaker  popstation  umdsign
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/compiled tools$ cd ..
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO$ cd How\ to/
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/How to$ ls
How to create valid PS and PDF for DOCmaker.odt  pic0.png
How to create valid PS and PDF for DOCmaker.pdf  readme
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/How to$ cd ..
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO$ cd ISODAXCSO\ for\ kommander\ 1.2.0 
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/ISODAXCSO for kommander 1.2.0$ ls
ISODAXCSO.kmdr
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/ISODAXCSO for kommander 1.2.0$ cd ..
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO$ cd ISODAXCSO\ for\ kommander\ 1.3.0
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/ISODAXCSO for kommander 1.3.0$ ls
ISODAXCSO.kmdr
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/ISODAXCSO for kommander 1.3.0$ cd ..
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO$ cd Sources/
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/Sources$ ls
ciso  copstation-2.21  DAX Creator  docmaker
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/Sources$ cd ciso
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/Sources/ciso$ ls
ciso  readme  umdsign
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/Sources/ciso$ cd ciso
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/Sources/ciso/ciso$ ls
ciso.c  ciso.h  makefile  readme
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/Sources/ciso/ciso$ cd ..
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/Sources/ciso$ cd umdsign
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/Sources/ciso/umdsign$ ls
umdsign.c
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/Sources/ciso/umdsign$ cd ..
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/Sources/ciso$ cd ..
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/Sources$ cd copstation-2.21/
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/Sources/copstation-2.21$ ls
data.h       iniparser.h  main.c    port.h  toc.c
iniparser.c  logo.h       Makefile  readme  toc.h
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/Sources/copstation-2.21$ cd ..
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/Sources$ cd DAX\ Creator/
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/Sources/DAX Creator$ ls
daxfile.h        iso9660search.h  main.c  Makefile  readme.txt
iso9660search.c  iso9660search.o  main.o  ptypes.h
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/Sources/DAX Creator$ cd ..
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/Sources$ cd docmaker/
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/Sources/docmaker$ ls
license.txt  src
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/Sources/docmaker$ cd src
cleippi@cleippi-desktop:~/Desktop/ISODAXCSO/Sources/docmaker/src$ ls
main.c  Makefile

```

well, if you can follow that, it might help...

---

### Post by savethewabbit on 2008-05-06
i have the same problem as the OP - when i try to compile iso-dax-cso using 

gcc -o ciso ciso.c -lz

it says there's no folder called gcc. could it be because the program is thought for a kde environment? (i'm on ubuntu) if so is there anything we can do to set it up?

---

### Post by popupstoppa on 2008-07-16
The easiest way (in my opinion) to convert ISOs to CSOs is by using CISO. It's in the repositories, just go to Synaptic Package Manager and search for CISO. Once you have it installed (note, you do everything from the command line) do the following:

1) Open a terminal
2) Go to the directory of the ISO (cd Documents for instance)
3) Once in the directory, type the following: 

ciso <level> <input> <output>

where level is the level of compression (9 being the highest), input is the input file, and output is the output file. An example would be:

ciso 9 Disgaea.iso Disgaea.cso

Hope this helps.

---

