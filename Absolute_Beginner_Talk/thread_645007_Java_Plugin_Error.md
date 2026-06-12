---
title: "Java Plugin Error"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-12-19
When using Azureus, I receive this error :

LoadPlugin: failed to initialize shared library libXt.so [libXt.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library libXext.so [libXext.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /usr/lib/Java6u3/jre/plugin/i386/ns7/libjavaplugin_oji.so [/usr/lib/Java6u3/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: _ZTVN10__cxxabiv121__vmi_class_type_infoE]

Am I not using the correct plugin ?...This is the one from Sun's website java.sun.com which I installed my self.

---

### Post by artesian_spring on 2007-12-19
I had some issues with Java that I got around by installing the "Gnu compiler for Java (tm)" (GCJ). Get "gcjwebplugin" and its dependencies using Synaptic or apt-get (or however you prefer to get packages). 

I don't know if this will solve your problems, but it's probably worth a try.

---

