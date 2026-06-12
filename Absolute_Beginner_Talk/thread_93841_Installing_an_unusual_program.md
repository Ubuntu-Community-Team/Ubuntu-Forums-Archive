---
title: "Installing an unusual program"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by andrewL on 2005-11-22
Hi there,
I have a problem with an installation of the science program ARB. The program is set up to align multiple DNA sequences.  

After I've installed the program I get an error and the program won't run.  The error message that pops up says:

error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

I checked under the apt-get area and saw that I have libstdc++6 as my installed version. Evidently, the program doesn't recognize it for some reason. Does anyone know how I can work around this to recognize the version I have?

Any help would be greatly appreciated.

cheers,
andrewL

---

### Post by Xian on 2005-11-22
Install this package:

```
$ sudo apt-get install libstdc++2.10-glibc2.2
```

---

### Post by andrewL on 2005-11-23
Thanks Xian,
  the gui now works.  Your help is greatly appreciated.  
cheers,
Andrew

:-)

---

