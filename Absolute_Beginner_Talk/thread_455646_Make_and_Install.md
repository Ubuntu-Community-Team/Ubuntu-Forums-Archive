---
title: "Make and Install"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by JordanII on 2007-05-26
I am trying to compile something from source and I got it configured, but how do I make and install it? Thanks!

~Jordan

---

### Post by meng on 2007-05-26
After:
./configure

you then do:
make
sudo make install

---

### Post by deadgobby on 2007-05-26
First make sure that the program you are trying to install is in Synaptic first. 2cd here is a link
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

 
./configure
make
make install

---

### Post by meng on 2007-05-26
> **deadgobby said:**
> First make sure that the program you are trying to install is in Synaptic first.
I think you mean make sure it's NOT in Synaptic, because if it is then you wouldn't want to install from source.

---

### Post by JordanII on 2007-05-26
I am trying to install a patched GTK2 and "make" does not work.

~Jordan

---

### Post by meng on 2007-05-26
You mean "make" is not recognized as a command, or returns some other error?
What version of Ubuntu?
Try this:
sudo apt-get install build-essential
then run make

---

### Post by JordanII on 2007-05-26
> **meng said:**
> You mean "make" is not recognized as a command, or returns some other error?
What version of Ubuntu?
Try this:
sudo apt-get install build-essential
then run make

I am running Feisty. I already tried the build essential package and it says that I already have it. It says that no make file was found. Thanks!

~Jordan

---

### Post by ramjet_1953 on 2007-05-27
Could you be a bit more specific?

"Make does not work" tells us nothing!

What errors are you getting, when you run make?

Also, are there any dependancy issues?

Regards,
Roger :cool:

---

### Post by Celegorm on 2007-05-27
If there is a readme file that came with the source, you should probably take a look at it. Also, are you sure you are in the right directory to run the make command?

---

### Post by JordanII on 2007-07-14
There where missing dependencies. I got it all taken care of. Thanks!


~Jordan

---

### Post by kukibird1 on 2007-07-14
> **JordanII said:**
> I am trying to compile something from source and I got it configured, but how do I make and install it? Thanks!

~Jordan


Try a program called Checkinstall when compiling programs from source .


./configure
make
sudo checkinstall

It passes  install info to your package manager for  easy uninstallation .

I used make install and had to manually seach for  files  when uninstalling  not fun .

---

### Post by JordanII on 2007-07-16
> **kukibird1 said:**
> Try a program called Checkinstall when compiling programs from source .


./configure
make
sudo checkinstall

It passes  install info to your package manager for  easy uninstallation .

I used make install and had to manually seach for  files  when uninstalling  not fun .

Thanks a lot!!! That should be really helpful. Thanks again!!!  :mrgreen:



~Jordan

---

