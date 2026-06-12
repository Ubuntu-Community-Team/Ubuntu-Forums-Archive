---
title: "help installing application"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by killzoneman0 on 2006-06-17
i know that you put the terminal to the directory where the source is.  i am not sure of what to do next to compile and install the program.

---

### Post by tonyr on 2006-06-17
If you haven't already, you will need to install the package **build-essential**.  
Sometimes there is a file in the source directory named **INSTALL** or **README** with
some instructions.  If there is also a file named **configure**, then the usual steps
are
```

./configure
make
sudo make install

```

but expect things to not go smoothly. Builds from source usually require
development versions of libraries (packages with **-dev** at the end).
Unfortunately, these are mostly discovered one at a time as you go along.

EDIT: There is an expanded explanation [here]("http://www.psychocats.net/ubuntu/installingsoftware.php").

---

