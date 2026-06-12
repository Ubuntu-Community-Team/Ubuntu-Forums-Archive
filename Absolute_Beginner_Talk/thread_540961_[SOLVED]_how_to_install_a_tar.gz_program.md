---
title: "[SOLVED] how to install a tar.gz program"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by DarinB on 2007-09-02
every time i go to install a tar.gz program like hp latest printer driver i get a makefile not found.
i had the same with other programs like ntfs-3g i finnally gave up on that one and jsut put in a new hard drive and made it ext3. so what am i doing wrong.

cd Desktop
tar -zxvf XXX.tar.gz
then i cd to the xxx directory
./configure

i always get makefile no
then the make command says no makefile found

i tried sudo and it doesn't configure

this has happened with any program i have tried.

help??

---

### Post by overdrank on 2007-09-02
> **DarinB said:**
> every time i go to install a tar.gz program like hp latest printer driver i get a makefile not found.
i had the same with other programs like ntfs-3g i finnally gave up on that one and jsut put in a new hard drive and made it ext3. so what am i doing wrong.

cd Desktop
tar -zxvf XXX.tar.gz
then i cd to the xxx directory
./configure

i always get makefile no
then the make command says no makefile found

i tried sudo and it doesn't configure

this has happened with any program i have tried.

help??

HI and as for  ntfs-3g you can use synaptic manager to install it. Why are you using a tar to install your printer what model is it? And if you try to make a file have you install build essential?

---

### Post by Vorian on 2007-09-02
it could also be ./autogen or something similar.

can you provide a link to the driver?  :)

---

### Post by Arwen on 2007-09-02
There's always must be a makefile in installation tar.gz files,right? Maybe the permissions aren't ok,make sure you can modify makefile and the whole folder:change to 775(sudo chmod 775 file or sudo chmod -r 775 folder) while being root(sudo -i) and then do ./configure,make and make install.I don't know if you need gcc for that..

---

### Post by mysticmatrix on 2007-09-02
> **DarinB said:**
> every time i go to install a tar.gz program like hp latest printer driver i get a makefile not found.
i had the same with other programs like ntfs-3g i finnally gave up on that one and jsut put in a new hard drive and made it ext3. so what am i doing wrong.

cd Desktop
tar -zxvf XXX.tar.gz
then i cd to the xxx directory
./configure

i always get makefile no
then the make command says no makefile found

i tried sudo and it doesn't configure

this has happened with any program i have tried.

help??

I don't think HP would be providing you a source code of their drivre which you can install. If you may provide link from where you downloaded the driver, we might help.

---

### Post by Bachstelze on 2007-09-02
> **Arwen said:**
> There's always must be a makefile in installation tar.gz files,right?

No. A Makefile is most often used to compile source code and not all tar.gz files contain source code. They're archives, just like ZIPs, you can put whatever you want in them.

---

### Post by DarinB on 2007-09-02
i just got back on line and i have a lot of homework to do to understand this.
i needed the latest hplip driver to use my phototsmart printer to publish a booklet. 
i had no problem with the advanced widows software but i  don't have it for my ubuntu box and i am away from windows now.
i will check on the permissions thing as well.
i check back when i get back home.

the ntfs i wanted the latest version because i read on the forums that it actually worked. but i couldn't get the tar ball to make.

so i gave up and reformatted my extra hard drive to ext3 and the heck with windows formats.

i just am trying to figure out why i can't seem to add any program using the tarzxvf and ./configure make make install commands.

it makes me crazy to not be able to so it.
be back in a few days thanks everybody

---

### Post by jordanmthomas on 2007-09-02
See if there's a file in your untarred directory labeled README or INSTALL.  If so, read those:
```
less INSTALL[COLOR="Indigo"] #or README[/COLOR]
```
They should tell you what you need to do to install the program you have downloaded (particularly the INSTALL file).

---

### Post by Paul133 on 2007-09-02
It's possible it's not source. It might be a binary. Not all tar.gz files have source in them, just like .zip's can contain anything.

---

