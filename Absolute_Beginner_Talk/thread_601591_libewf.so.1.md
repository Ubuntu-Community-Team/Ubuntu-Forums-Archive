---
title: "libewf.so.1"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by robulus on 2007-11-03
Hi Folks,
In my quest to recover some deleted photos from an SD card, I've downloaded/compiled/made the most recent version of testdisk (6.9).

I think it all went ok, BUT when I try to run the program as root, I get 
testdisk: error while loading shared libraries: libewf.so.1: cannot open shared object file: No such file or directory

when I try to locate this file, I find these:
/usr/local/lib/libewf.so.1
/usr/local/lib/libewf.so.1.0.1

When I try to run it as non-root, it prompts me to run the program again as root.

Have you seen an error like this when running recently compiled programs?  And if so, how to deal with it?

cheers!
Robin.

---

### Post by Perfect Storm on 2007-11-03
You properly had to point where the application need/had to read the specific file while you're doing the compiling.
Is libewf also compiled?

To solved the root problem delete the the applications hidden folder in your home directory.

---

