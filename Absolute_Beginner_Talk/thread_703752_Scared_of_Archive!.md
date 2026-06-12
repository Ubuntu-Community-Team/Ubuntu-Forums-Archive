---
title: "Scared of Archive!"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by hungryOrb on 2008-02-21
I'm scared! I don't know what this archive is!
I downloaded the 64 version for linux from:

[http://www.acc.umu.se/~emilk/downloads.html](http://www.acc.umu.se/~emilk/downloads.html)

and unzipping the folder, its a folder with files in, ye. And well, I don't know if it needs installing or not, package manager doesnt detect it as one.. but Im new and dont really know the characteristics of a linux install package! Having said that, I realised it might not need installing as such, so I tried opening the file directly. File: 'Phun' which is 3.8mg.

Does anyone know what to do?
TIA

"DESE FYZISC MUST BE MIEN!"

---

### Post by kane77 on 2008-02-21
this is just plain tar.bz2 archive.. so what you need to do is:
unpack it: ```
tar xjvf archivename.tar.bz2
```
then enter the extracted directory:
```
cd Phun
```
and then only run it:
```
./phun
```
however I tried just today the same program (for 32 bit) and for some reason it didn't run (segfault). Give it a try.

---

### Post by lpanebr on 2008-02-21
Hello,

I have gutsy 64bit on AMD and downloaded and tried running both 32 and 64 bit versions but got this erros: Any ideas?:(

32bit
$ ./phun 
./phun: error while loading shared libraries: libaa.so.1: cannot open shared object file: No such file or directory

64bit
$ ./phun 
./phun: error while loading shared libraries: libGLEW.so.1.5: cannot open shared object file: No such file or directory

---

### Post by lpanebr on 2008-02-21
HELLO!

Problem solved thanks to this post: 
[http://www.gamedev.net/community/forums/topic.asp?topic_id=482775&PageSize=25&WhichPage=5](http://www.gamedev.net/community/forums/topic.asp?topic_id=482775&PageSize=25&WhichPage=5)

"...You need to add your Phun directory to your LD_LIBRARY_PATH with

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/tcarroll/Phun

...then install  libSDL_image-1.2 with Synaptic package manager."


where /home/tcarroll/Phun should be the full path to your Phun folder.

Great!

---

