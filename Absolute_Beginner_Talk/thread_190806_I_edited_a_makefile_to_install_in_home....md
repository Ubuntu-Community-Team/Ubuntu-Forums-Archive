---
title: "I edited a makefile to install in /home/..."
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by J-Rod on 2006-06-06
and I am getting a message I don't quite understand. I have compiled ToME, and now would like it to rest in my home directory, so I will have full access to it and i can install mods. Here's the message I get in terminal after I have compiled:

```
jrod@jrod-laptop:~/Desktop/tome-233-src/src$ make -f makefile.std
*** Note: In order to use the install rule, which now actually
*** handles the installation of the library dir, you need to edit
*** this makefile, going to the top and making sure LIBDIR suits
*** your desired install dir properly. The LIBRARY_DIR you used
*** to set in config.h is now ignored and obsolete with respect
*** to this makefile. Note that if you edit this makefile, you may
*** need to recompile so all the files that reference those defines
*** notice the changes.

```

I get that rright after the initial make, and I edited the makefile, and ran the compile string again, and get the same message. What I need to understand is what I have to do to get the 'install" command to instlal the program and know where the modified libs folder is. Thanks for any help!

---

