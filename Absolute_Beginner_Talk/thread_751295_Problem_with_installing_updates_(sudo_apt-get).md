---
title: "Problem with installing updates (sudo apt-get)"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by Cato Censorius on 2008-04-10
Hi.
I'm having trouble installing new updates to Ubuntu. When I try I first get this message:

"Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

When I run it in the terminal I get a message telling me that dpkg (whatever that is) was interrupted, and that I must run "dpkg --configure -a". I try running that and also try switching "-a" with "sudo apt-get install" -although I don't know why I think that should work. When I try the first of these two I'm told that I need super-user-access (My computer works in Norwegian, and "super-user-access" is my translation. I don't no if it is correct, but I hope it's close). When I try the second I get a list of commands connected to "dpkg"
Here is my terminal after all this:

nils@littlefinger:~$ sudo apt-get install -f
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
nils@littlefinger:~$ dpkg --configure -sudo apt-get install -f
dpkg: conflicting actions -s (--status) and -

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
nils@littlefinger:~$ dpkg --configure -a
dpkg: den ønskede handlingen krever superbrukertilgang
nils@littlefinger:~$ 
nils@littlefinger:~$ 

Oh, yes. I'm using Ubuntu 7.10 Feisty Fawn.

---

### Post by pedro_orange on 2008-04-10
Try actually running "dpkg --configure -a"

---

### Post by ukripper on 2008-04-10
try it with sudo :

```
sudo dpkg --configure -a
```

---

### Post by davidgutu on 2008-04-10
sorry yo

Hard luck

I had kinda the same prob

---

### Post by Cato Censorius on 2008-04-10
Thank's a lot. "sudo dpkg --configure -a" solved the problem. Again: thanks.

---

