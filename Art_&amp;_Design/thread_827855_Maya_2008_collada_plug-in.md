---
title: "Maya 2008 collada plug-in"
date: 2008-06-13
forum: Art &amp; Design
---

### Post by ckonstantinos on 2008-06-13
Hi All,

I’ve installed Feelling Collada plug in on Maya2008 on a Linux Ubuntu gutsy OS.

When I open the plug in Manager on maya2008, the collada plug in appears in the list but if i try to load it, it gives me the following error:

Error: Unable to dynamically load : /autodesk/maya2008/bin/plug-ins/COLLADA.so
/autodesk/maya2008/bin/plug-ins/COLLADA.so: undefined symbol: CreatePlugin (COLLADA) //

I have checked all the collada copied files (Collada.so, *.mel, *.xpm) and they are in the correct maya folders…
Does anyone knows what is this CreatePlugin symbol? I’ve installed the 3.05B collada version that is supposed to be compatible with maya2008.

I’ve also installed nvidia Cg1.5 toolkit since I’ve red that it is required in order to run the collada plug in.

Is it because the COLLADA.so file was precompiled? I’m trying to compile it from source but there are several problem with the different versions of gcc compilers and I don’t have a detailed guide for it.

Please let me know if anyone has managed to install this plug-in successfully or if you have any advice.
Thank you

---

### Post by shea241 on 2008-07-15
I'm experiencing the same problem.  Let me know if you find out anything (and, of course, I will let you know if I find something)

---

### Post by slegrand on 2009-06-06
Same. And will let you know if I find out the problem.
> Is it because the COLLADA.so file was precompiled? I’m trying to compile it from source but there are several problem with the different versions of gcc compilers and I don’t have a detailed guide for it.
Maybe a stupid question but are you sure it was compiled for your architecture?
Where did you find it btw?

---

### Post by dowen on 2009-08-22
The 3.05B plugin on linux only supports Maya8.0 and Maya8.5 and doesn't export CreatePlugin. I don't know why the windows version is different but it seems to be.

The nextgen plugin mostly works for linux with Maya2009 but it hangs when exporting a mesh with materials.

---

