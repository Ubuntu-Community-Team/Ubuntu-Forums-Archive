---
title: "Cannot extract tarballs !!"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by D_frag on 2006-09-24
I am a complete linux noob so i dunno if anything is missing that i need to do , I have downloaded two tarballs so far none of them are extarcting i always get this error

tar: mac-3.99-u4-b5/strip_fPIC.sh: Cannot utime: Operation not permitted
tar: mac-3.99-u4-b5/Makefile.am: Cannot utime: Operation not permitted
tar: mac-3.99-u4-b5/Makefile.in: Cannot utime: Operation not permitted
tar: mac-3.99-u4-b5/AUTHORS: Cannot utime: Operation not permitted
tar: mac-3.99-u4-b5/INSTALL: Cannot utime: Operation not permitted
tar: mac-3.99-u4-b5/ChangeLog: Cannot utime: Operation not permitted
tar: mac-3.99-u4-b5/COPYING: Cannot utime: Operation not permitted
tar: mac-3.99-u4-b5: Cannot utime: Operation not permitted
tar: Error exit delayed from previous errors

N.B Sorry guys it was fixed it was a permisions problem i was extracting to a wrong directory ...

---

### Post by Anonii on 2006-09-24
Greetings!

Open the terminal. Go to the directory that your tarball is (using the cd and ls commands) and try this:
**tar xvf <tarball_filename>.tar.gz**

If it doesnt work try:
_sudo tar xvf <tarball_filename>.tar.gz_

---

### Post by D_frag on 2006-09-24
Ok i did manage to extractit and when i read how to install the software i couldnt understand 


Requirement
-------------------

YASM - for compiling the asm source (Currently only needed in x86 and AMD64 platforms), 
       if you don't have it, the corresponding C++ code will be used and ASM codes will not build 
       even the assembly option is enabled.


-------------------
Compile
-------------------
$ ./configure
$ make

--enable-assembly to compile with ASM support (The default is yes)

-------------------
Install
-------------------
$ make install 
(need to be root)

could any one explain to me here what should i do , i got the Yasm  but i don't seem to see it anywhere in my programs ??

---

### Post by Anonii on 2006-09-24
Installing using tarballs (source) is the wrong way in Ubuntu, first of all.

You can use the APT system that will do that for you _MUCH_ faster and easier. Be sure to read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
Its really helpful, and you will understand everything!


If you think that this wont help you. (Read it first). Try this on the extracted folder:

**./configure**
When it finishes without errors (if it does) do:
**make**
and then:
**make install**

But you will surely have tons of problems, from dependencies etc.
So I'd suggest you to install that with APT.

:3

---

### Post by bodhi.zazen on 2006-09-24
Not sure.

You will need ```
sudo aptitude build-essential
```FOR SURE.

I advise checkinstall ```
sudo aptitude build-essential checkinstall
```

Then cd into your extracted directory.

```
./configure
make
sudo checkinstall
```
You may need to enable your respoitories for checkinstall.

If you do not want to check install change the last line to```
sudo make install
```

Otherwise follow your how-to and post errors.

---

### Post by bodhi.zazen on 2006-09-24
> **Anonii said:**
> Installing using tarballs (source) is the wrong way in Ubuntu, first of all.

Unless, of course your application is not in the repositories.

Be sure to enable your repositories and search for your application.

---

### Post by D_frag on 2006-09-24
ok i got this 


dragonfire@dragonfire-desktop:~/Desktop/mac-3.99-u4-b5$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables

---

### Post by bodhi.zazen on 2006-09-24
Did you install build-essential?

---

### Post by D_frag on 2006-09-24
i got this 


```
Unknown command "build-essential
```

and @ the end 
```
 This aptitude does not have Super Cow Powers.
```

---

### Post by bodhi.zazen on 2006-09-24
Ooops :redface:
```
aptitude install build-essential
```

---

### Post by D_frag on 2006-09-24
why do i get 

```
sudo: checkinstall: command not found

```

---

### Post by bodhi.zazen on 2006-09-24
You need to install checkinstall.

Use synaptic or ```
sudo aptitude install checkinstall
```

---

### Post by D_frag on 2006-09-24
Just did that .now when i did sudo checkinstall i got this 


this is the log file 

```
dpkg: status database area is locked by another process

```

and thats whats befoe and after i saw the log file 
```
Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package... FAILED!

*** Failed to install the package

Do you want to see the log file?  [y]: y

Erasing temporary files...OK

Deleting temp dir...OK

```

---

### Post by bodhi.zazen on 2006-09-24
Do you have synaptic running still? If so, close it.

---

### Post by D_frag on 2006-09-24
sucesSSSSSSSSSS !!!!!!!!!!!
Thank you m8 ...been of great help :)

---

