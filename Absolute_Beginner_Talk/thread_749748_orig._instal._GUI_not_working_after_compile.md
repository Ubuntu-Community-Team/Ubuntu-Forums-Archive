---
title: "orig. instal. GUI not working after compile"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Dodelijk on 2008-04-08
Hello, 

I'm trying to install a program (fitky) via the command line. I did have a working copy of fitky which I'd installed via Synaptic but attempting to compile it's source code on the same machine has messed up this installation and now the GUI won't load. 

If i try and run the application by going 'Applications -> Other -> fitky" the application appears  on the application bar ( at the bottom ) for a few moments and then gives up and disappears.  If I try and run the program from the command line I get the following : 
```

error while loading shared libraries: libfityk.so.0: 
cannot open shared object file: No such file or directory

```

I've tried to look into the cause of this error/problem but I don't find anything relating to Ubuntu

Does anyone know what I've done ?

---

### Post by pytheas22 on 2008-04-08
If the program is still listed as installed in Synaptic, uninstall it (it might not hurt to choose the "remove completely" option).  Then try running fitky again.  If it still doesn't work, compile it again, and make sure it compiles successfully...if you get any errors during "make" or "make install," you need to get past them before the program will work.  I don't know how much experience you have compiling stuff, but if you aren't sure whether the program is being built correctly, give more details of the process you took to compile it and we can figure it out.

Also, is there a reason you need to compile this instead of using the package?  If it's because you need a more recent version than Synaptic offers, there might be a simpler solution than compiling yourself (i.e. pulling the package from the Hardy repositories).

---

### Post by neurostu on 2008-04-08
did you try looking to see if you have libfityk installed?  If not check for it with:
```

aptitude search libfityk

```
if it isn't present then search google for a way to install it.

---

