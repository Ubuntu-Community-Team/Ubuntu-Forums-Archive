---
title: "Azureus plugin load error"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-11-20
I downloaded vuze azureus from their website, extracted it and tried to run it. One of the errors that I received were this:

LoadPlugin: failed to initialize shared library libXt.so [libXt.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library libXext.so [libXext.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /usr/lib/Java6u3/jre/plugin/i386/ns7/libjavaplugin_oji.so [/usr/lib/Java6u3/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: _ZTVN10__cxxabiv121__vmi_class_type_infoE]


For the first two, I found a that was named libXt.so.6 and libXext.so.6 in /usr/lib. As for the last one, I'm quite sure that the plugin exists as I installed java myself. Could the undefinied symbol problem be one from the Sun website, or is it azureus trying to get at a resource that does not exist in the library?

---

