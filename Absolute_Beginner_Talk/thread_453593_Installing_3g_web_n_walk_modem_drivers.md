---
title: "Installing 3g web n walk modem drivers"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by synapse321 on 2007-05-24
Hi

I have got as far as downloading and unpacking the modem drivers but don't know how to install the drivers or compile them

I now it involves using sudo

Any help appreeciated.

The files that are unpacked are changelog,copying, ffifo.c,kfifo.h, makefile, nozomi.c, readme, todo.

---

### Post by Bachstelze on 2007-05-24
What do you think a readme file is for ? We cannot guess how your drivers work...

---

### Post by synapse321 on 2007-05-24
I have read the readme file and it states:

check the makefile and run "make" "make install" will copy the files ...

When I run "make" or "make install" all I get is command not found in the terminal window

I would like to add that I am totally new to Linux and feel like giving up already. Driver installation seems so much easier under windows...

---

### Post by Bachstelze on 2007-05-24
To install all the tools required to compile stuff, install the build-essential package.

```
sudo apt-get install build-essential
```

---

### Post by synapse321 on 2007-05-25
when i try the command sudo apt-get install build-essential

I get the following message:

pacckage build essential is not available but refered to by another package this may mean the package is missing has been obsoleted or is only available from another source.

Can anyone shed more light on this message?:(

---

### Post by Bachstelze on 2007-05-25
You just don't have the correct sources enabled. Do this :

```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
sudo touch /etc/apt/sources.list
sudo apt-cdrom add
*** insert your CD here and press enter ***
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by synapse321 on 2007-05-25
hi

Thanks for your help so far.

When i go to the make command I get as far as:

warning compiling for 2.6

make -c/lib/modules/2.16.15-26-386/build SUBDIRS=/home/synapse modules

error 2 lib/modules/2.16.15-26-386/build: no such file or directory. stop

Have I left something out?

---

### Post by synapse321 on 2007-05-25
OK so I cheated by installing ubutu 7.04 which had the drivers pre-installed.

Can anyone from the uk tell me what to do from here with the Option 3g card and how to create a dial up connection and what tel number etc to put in.
Thanks

---

### Post by synapse321 on 2007-05-26
WHen I process the command "make" to compile the drivers i get this error:

warning compiling for 2.6

make -c/lib/modules/2.6.20-15/build subdirs=home/3g/ modules
make *** /lib/modules/2.6.20-15-386/build: NO such file or directory.stop
make *** [defaul] error 2

Does this mean I am missing some kernel source or additional files which I need to download and from where?

---

