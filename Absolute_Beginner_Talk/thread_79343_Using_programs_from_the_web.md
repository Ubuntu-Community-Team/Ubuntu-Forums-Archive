---
title: "Using programs from the web"
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by discofro on 2005-10-20
I've been looking at a lot of these free program databases online. A lot of the software looks great. So, I download it and I find myself with hundreds of odd files and no 'Double click on this one' executable file. 

So I double click on the one labled install and it says to type in all of these commands... so I try to type them into the terminal and I get a no compatible c compiler error...

What is going on, and how do I use these programs?

---

### Post by gerbman on 2005-10-20
[QUOTE=discofro]I've been looking at a lot of these free program databases online. A lot of the software looks great. So, I download it and I find myself with hundreds of odd files and no 'Double click on this one' executable file. 

So I double click on the one labled install and it says to type in all of these commands... so I try to type them into the terminal and I get a no compatible c compiler error...

What is going on, and how do I use these programs?[/QUOTE]

Can you be a little more specific?  What program are you trying to install?  What commands are you entering?  What are the exact error messages?  In my experience it's not very common to download an executable (program or installer).  You usually have to compile it yourself or get it through the package manager.  Anyway, post as much info as you can.

---

### Post by LHZ on 2005-10-20
You've probably downloadd programs in their 'source code' form. At this stage the program is written down in a programming language, probably C, and needs to be translated by a so called 'compiler' to machine language. There's two things you can do:

1) Open a terminal, and type 

> sudo apt-get build-essential

and then give your password.
This installs a C compiler (among others), so you can compile the source according to the instructions given.

2) Use Synaptic (System->Administration->Synaptic) to install pre-compiled executables directly. Chances are that if the software you want is somewhat popular it's in Synaptic. This saves you all the downloading, untarring and compiling work.

To get access to all possible software (such as media codecs), you can enable extra repositories for Synaptic. You can read all about this on [www.ubuntuguide.org](www.ubuntuguide.org). Substitue 'breezy' for 'hoary' where applicable.

---

### Post by Jenda on 2005-10-20
> 2) Use Synaptic (System->Administration->Synaptic) to install pre-compiled executables directly. Chances are that if the software you want is somewhat popular it's in Synaptic. This saves you all the downloading, untarring and compiling work.
And you should also enable the Universe and Multiverse repositories so that you can see all the software Synaptic (System > Administration > Synaptic package Manager) can get. You do that in Synaptic by clicking Settings > Repositories > Settings, there you check the first checkbox (show disabled software sources) and close the Settings window. Now you can see checkboxes next to each repository, so you have to find the Univ. and Multiv. repos and check them. Do not check the backports if you use Breezy Badger, because they aren't really up yet.

---

### Post by A-star on 2005-10-20
The program you download is the program in it most primitive form = source code.
This means that you have to compile it yourself.
I can only recommend that you search for the program in synaptic (tool to install programs in ubuntu).

if it isn't there you will habe to compile it yourself.
first do
```

sudo apt-get install build-essential
sudo apt-get install checkinstall

```
this you only have to do once.

after this you compile the program as follows, use these command in a terminal at the place where you unpacked the program:
```

./config
make 
sudo checkinstall

```
this will make a deb package for you which can be installed in the following way
```

sudo dpkg -i name_ofpackage.deb

```
this will also enable you to remove it from your system more easily later on.
Hope this helps and don't hesitate to ask questions.

---

