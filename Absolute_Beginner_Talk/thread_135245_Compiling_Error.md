---
title: "Compiling Error"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by tadashi on 2006-02-23
I tried to run sudo ./configure and for the last line I get:
checking for C compiler default output file name... configure: error: C compiler cannot create executables

The system also cannot find make.  Am I missing files for compiling source code and making make files?

---

### Post by ubuntuuser on 2006-02-23
Have you already installed the package build-essentials? That's where make is, and I think it has gcc as a dependency. Install build-essentials and try it again.

---

### Post by tadashi on 2006-02-23
Well, that partially did the trick.  It now gets stuck on
checking for X... configure: error: Can't find x includes.  Please check your installation and add the correct paths.

I did not see x includes in the package manager.  Are they called something different?

---

### Post by claydoh on 2006-02-23
try installing libgnome2-dev, which *should* install (as dependent packages) most of the missing *-dev packages you will need to begin compiling things.

If configure still errors on a particular library, you may have to track down the corresponding -dev package

---

### Post by tadashi on 2006-02-23
thanks.

---

