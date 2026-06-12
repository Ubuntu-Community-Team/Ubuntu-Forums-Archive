---
title: "problems with .zip"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by NeoEIRE on 2008-03-12
hi
i keep getting this error code when i try to unzip a file with tag .zip...

 skipping: WPC/D10.pdf             unsupported compression method 98

does any1 know what it means and how i can sort it...?

i have ubuntu 7.04 64bit
i have used:
ARK
Xarchiver
Karchiver
Archiver Manager

and 7up i cant seam to find to select it but i have installed it and uninstalled it to try and find it?

---

### Post by RedLXXXIV on 2008-03-13
Have you tried gzip? That *might* work.

If not, you might be able to unzip it with either WinRAR or WinZip (both are free downloads/evaluation copies) if you install them into WINE.

Give it a try, and post your results!

:) RedLXXXIV

---

### Post by NeoEIRE on 2008-03-13
hi,
winzip and win rar wont install, and i cant find gzip in the install/remover program

gzip i dont know who to install?

---

### Post by oldos2er on 2008-03-13
> **NeoEIRE said:**
> hi,
winzip and win rar wont install, and i cant find gzip in the install/remover program

gzip i dont know who to install?

 gzip should be installed by default. Type "gzip" in a terminal to find out. You can install rar and unrar by typing "sudo aptitude install rar unrar" .

---

### Post by NeoEIRE on 2008-03-14
ok  have it, what is the command to unzip a file in my decktop area called WPC.zip...

i have no idea how to used terminal, only how to cut and past commands into it.

---

### Post by oldos2er on 2008-03-14
First type "cd Desktop" so you're in the right directory. Then type "gzip -d WPC.zip"

---

### Post by hyper_ch on 2008-03-14
```

sudo apt-get install unzip

```

then try again...

---

### Post by NeoEIRE on 2008-03-16
is the cd desktop the correct command for getting in the desktop directory?

it doesnt seam to work

---

### Post by NeoEIRE on 2008-03-16
and what is the command i put into terminal to use unzip, including getting to the right directory?

---

### Post by Oldsoldier2003 on 2008-03-16
> **NeoEIRE said:**
> is the cd desktop the correct command for getting in the desktop directory?

it doesnt seam to work

```
cd ~/Desktop
```

the ~ takes you to /home/<yourusername>

/Desktop is the correct dir for the desktop, linux is caSe SenSiTive....

---

### Post by NeoEIRE on 2008-03-16
when i try to use gzip this is what i get:

neoeire@neoeire-desktop:~/Desktop$ gzip -d WPC.zip
gzip: WPC.zip: unknown suffix -- ignored

---

### Post by NeoEIRE on 2008-03-16
when i try to use gzip this is what i get:

neoeire@neoeire-desktop:~/Desktop$ gzip -d WPC.zip
gzip: WPC.zip: unknown suffix -- ignored

this is where the file is, if anyone can give it a try, if you unzip it, please email it to me in 2 me, its Pdf , image files and its 17mb
[http://files.filefront.com/WPCzip/;9248993;/fileinfo.html](http://files.filefront.com/WPCzip/;9248993;/fileinfo.html)

---

