---
title: "Need help installing programs"
date: 2005-09-07
forum: Absolute Beginner Talk
---

### Post by cb2k on 2005-09-07
I am new to Ububtu and Linux and im trying to figure out how to install programs.

Im trying to install synaptic so i can get other packages but every time I run it get this error:

checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH

I can’t figure out why. Any help would be appreciated. Thanks

---

### Post by amohanty on 2005-09-07
whoa... why do you need to install synaptic, it should have been installed by default. If you did a _server_ (ie you dont login into the machien via a graphical/GUI login screen) install just do the following at the command prompt:

sudo apt-get install ubuntu-desktop

To be able to install stuff from source you need to install the build-essentials package.

HTH
AM

---

### Post by aysiu on 2005-09-07
Why do you have to install Synaptic? If you're using Ubuntu, Synaptic should already be there: System > Administration > Synaptic.

---

### Post by cb2k on 2005-09-07
I didnt do the server install like you are talking about. I guess I should have since this computer is going to become a ftp/file server. Ill reinstall and give that a try on a server install.

---

### Post by cb2k on 2005-09-07
[QUOTE=aysiu]Why do you have to install Synaptic? If you're using Ubuntu, Synaptic should already be there: System > Administration > Synaptic.[/QUOTE]


I must have missed it.... I take a look before I rebuild. Thanks

---

### Post by cb2k on 2005-09-08
Ok I got the build-essentials package. Is there anything else im going to need to get started in the linux world?

---

### Post by amohanty on 2005-09-08
Ok. before you make your foray into the world of configure make and make install, I would like to suggest a few things:

1. Pick any O'Reilly book on linux based on your experience level.
2. Install the default Ubuntu install on your machine, dont select server or anything else, just do the default install
3. Read the book and try out the things suggested therein on the ubuntu box as you go through them
4. Use google
5. Use google
6. Use google 
7. If you need some specific answers search the forums, or post the question.

Then you might want to attempt a server setup. Setting up servers in Linux is not hard, however if you are better prepared you will find the experience far more smooth and you will also learn a lot more on the way, instead of going - why doesnt this work like windows. 

HTH
AM

---

### Post by wvslkr on 2005-09-08
I think these may help you.
[http://ubuntuguide.org/](http://ubuntuguide.org/)
[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)

---

