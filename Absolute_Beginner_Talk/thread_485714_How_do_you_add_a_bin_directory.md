---
title: "How do you add a bin directory?"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by netyire on 2007-06-27
How do you add a custom bin directory, to allow program execution from a custom directory from any path in the terminal?

So that instead of having to navigate to the location where you compiled a custom program, and typing ./customprogram, you can just type customprogram in the terminal?

---

### Post by hvc123 on 2007-06-27
just add the directory to your %path%.

i think its in etc/profiles

so if you type in "export"
you should get your profiles enviroment.

also i could be talking total **** but thats what i think

---

### Post by whizbaby on 2007-06-27
Dont do this like that. Try (one of both, if u ask me take 1):
1-add the install directory to your path (in /home/your_user_name/.bashrc) or
2-create a link from where you want to start it to where it is installed.


1) lets assume nano is your favorite editor, then
nano .bashrc

lets call the path your prog is installed to /fancyplace/prog/prog.bin
add a line saying

export PATH=$PATH:/fancyplace/prog/

save and exit, close ALL terminals, open a new one and prog.bin should be callable directly.

2) lets assume you want a link prog.bin in your home, then type (in your home)
ln -s /fancyplace/prog/prog.bin prog.bin

Also look at 'man bash' and 'man ln'.
I guess you can set execution permissions by yourself...

---

### Post by netyire on 2007-06-27
Thanks! It works now :D

---

### Post by Nekiruhs on 2007-06-27
Or, by default if you make a folder called bin in your home, Bash adds that to your path on the next login. If way you dont need root to edit it.

---

