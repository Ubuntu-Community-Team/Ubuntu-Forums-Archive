---
title: "C  compile"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by jon zendatta on 2008-04-21
hello people
having problems here! have installed build-essential! can you please post the codes for C to save & compile..:)

---

### Post by bumanie on 2008-04-21
If you mean compiling from source. First you need to extract the directory - right click on the directory and choose 'extract to here' . You then need to change directory to where the file has been downloaded. Eg if the file has been downloaded to your desktop, open terminal and type > cd ~/Desktop Next>  cd <name of extracted file> followed by ./configure (hit enter), then make (hit enter), then make install - [sometimes sudo make install]. If all dependencies are met, the file/directory should be installed. Look at [this]("http://monkeyblog.org/ubuntu/installing/") first.

---

### Post by northern lights on 2008-04-21
```
gcc -o <name of output file> <source file(s)>
``` does the trick.

The general *nix c-compiler is "cc", but most linux systems ship with "gcc".

Let's call your source file "source.c"

```
gcc source.c
``` compiles it, but gives you a default output file name. If you want to call that something specific, run ```
gcc -o specificoutput source.c
``` If you have several sources, it's simply ```
gcc -o specificoutput source1.c source2.c
```

[EDIT]Just saw the previous post -
do you want to compile a package or your own code? In the earlier case, follow the above post - my rambling is not an option. In the latter, there obviously won't be no configuration script and all...[/EDIT]

---

### Post by jon zendatta on 2008-04-21
cheers bumanie  i am talking about about writing my own code, 0k. as in write the code, save then compile..

---

### Post by Hairy_Palms on 2008-04-21
just to clarify its not in the build-essentials packge its in the gcc package :D

---

