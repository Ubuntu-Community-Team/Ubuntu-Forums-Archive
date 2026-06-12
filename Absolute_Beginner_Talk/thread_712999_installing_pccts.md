---
title: "installing pccts"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by neoragexxx on 2008-03-02
i am trying to install pccts . the instructions are :

DEC/VMS support added by Piéronne Jean-François (jfp@altavista.net)

0. Download [http://www.polhode.com/pccts133mr.zip](http://www.polhode.com/pccts133mr.zip)

1. Unzip the distribution kit to your preferred location.

2. set default to the main pccts directory.

3. @makefile.vms

   This will create in directory [.bin]:

        antlr.exe
        dlg.exe
        sorcerer.exe
        genmk.exe

i have no idea how to do step 3 . i tried typing @makefile.vms in the terminal but i got:
bash: @makefile.vms: command not found

i tried to install pccts through package manager but when i try to use it the libraries cannot be found when i use gcc. 

any help will be highly appreciated

---

### Post by neurostu on 2008-03-02
Did you try:
```

sudo apt-get install pccts

```

Searching with aptitude results in:
```

s@localhost:~$ aptitude search pccts
p   pccts                           - The Purdue Compiler Construction Tool Set

```

So pccts is contained in the ubuntu repos

---

### Post by neurostu on 2008-03-02
What libraries cannot be found that it is looking for?

btw. Installing by hand will not include the libraries.  so using synaptic or apt-get will ALWAYS be better then intalling by hand.

---

### Post by neoragexxx on 2008-03-02
ok thanks well i manage to include the libraries by dynamic linking..

 ln -s /usr/include/pccts/* /usr/include/

now i get 

/tmp/ccbSbMmc.o: In function `expr':
ex.c:(.text+0x244): undefined reference to `_zzmatch'
ex.c:(.text+0x2ea): undefined reference to `_zzmatch'
ex.c:(.text+0x326): undefined reference to `_zzmatch'
ex.c:(.text+0x4d2): undefined reference to `zzsyn'
ex.c:(.text+0x4e6): undefined reference to `zzresynch'
/tmp/cci4F1fc.o: In function `zzerrstd':
scan.c:(.text+0x7c0): undefined reference to `zzLexErrCount'
scan.c:(.text+0x7c8): undefined reference to `zzLexErrCount'
collect2: ld returned 1 exit status

I am sure that all the code and commands i use are right so it must be the installation or something missing.. it worked perfectly on the same ubuntu installation i had before but i just don't remember how i made it work .

---

### Post by neoragexxx on 2008-03-02
no one knows ? :(

---

### Post by neurostu on 2008-03-02
When you try to install with apt-get do you get those same errors?

---

### Post by neoragexxx on 2008-03-02
it was the apt-get installation i was talking about. i haven't done the manual.

---

