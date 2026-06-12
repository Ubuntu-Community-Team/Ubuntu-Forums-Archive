---
title: "Copying File"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by bern1939 on 2007-11-24
Running Ubuntu 7.10
Just cannot remember how this was done previously!!

I have the file [COLOR="Red"]**'own.sty**[/COLOR]' on the desktop.
I want to get it into the /usr/share/texmf/tex/latex folder

the command I use is:
bernard@bernard-desktop:~$ sudo cp own.sty /usr/share/texmf/tex/latex
[sudo] password for bernard:
cp: cannot stat `own.sty': No such file or directory
bernard@bernard-desktop:~$ 

It is telling that the file is not on the desktop??

Any ideas as to why this should be?

Thanks

Bern

---

### Post by geeree on 2007-11-24
> **bern1939 said:**
> 
the command I use is:
bernard@bernard-desktop:~$ sudo cp own.sty /usr/share/texmf/tex/latex
[sudo] password for bernard:
cp: cannot stat `own.sty': No such file or directory
bernard@bernard-desktop:~$ 
It is telling that the file is not on the desktop??


You are executing that command in your home directory ~/. But the file you want to copy is one your dektop, i.e. in the directory ~/Desktop/. So the correct way to do this will be: 

```
sudo cp ~/Desktop/own.sty /usr/share/texmf/tex/latex/
```

Another way to understand this is to change your working directory to ~/Desktop and then execute your command. Like this: 

```

cd Desktop
sudo cp own.sty /usr/share/texmf/tex/latex/

```

Girish.

---

### Post by bern1939 on 2007-11-24
Excellent and thank you.

Bern

---

