---
title: "missing lib thats not missing.."
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2007-06-12
The error:

./ac3d: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

The strange thing is i have both libstd++6 and libc6 installed :/

Any ideas?

---

### Post by mostwanted on 2007-06-12
```


./ac3d: error while loading shared libraries: libstdc++-libc6.2-2.**so.3**: cannot open shared object file: No such file or directory
```

You probably have a wrong version of libstdc++ installed. Notive the so.3 at the end. Either edit the ac3d script so that it loads the proper version (shouldn't be too difficult with search/replace, but could create unexpected problems) or see if the proper version is in the repositories.

---

### Post by dgrafix on 2007-06-12
hmm, i cant find it in synaptic or apt-get and ac3d is a binary.

---

### Post by dgrafix on 2007-06-12
ok fixed it i needed this one:
apt-get install libstdc++2.10-glibc2.2

So anyone wanting to install AC3D modelling program ([http://www.inivis.com/](http://www.inivis.com/)) need to do the above on ubuntu fiesty!! 

now we know :)

---

### Post by vgillestad on 2007-06-17
Thanks man. I had the same problem as I was using the "Java Decompiler" found at this page: [http://www.kpdus.com/jad.html](http://www.kpdus.com/jad.html)

After having installed the package you've referred to, I was able to convert my .class files to .java.

---

