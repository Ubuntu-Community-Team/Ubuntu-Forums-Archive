---
title: "Cant MAKE"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by Allrab on 2006-09-27
I try to make something

gcc --version *gives me this text*
gcc (GCC) 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

./configure *gives me this text*
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking whether make sets $(MAKE)... no
checking for gcc... gcc
checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See `config.log' for more details.

*checked config.log and could no understand it*

make depend *gives me this*
bash: make: command not founde

make *gives me this*
bash: make: command not found


The question is as follows. How can I make or get around this problem?

Could use some input on this if you have the time and you might also help someone else that has this problem.

// Allrab

---

### Post by Predius on 2006-09-27
Install the package build-essential.

---

### Post by Allrab on 2006-09-27
That helped a bit but...

make depend *gives this now*
make: *** No rule to make target `depend'.  Stop.

make *gives this*
make: *** No targets specified and no makefile found.  Stop.


Halfway there? or what is the next step?
:rolleyes:

---

### Post by bodhi.zazen on 2006-09-27
I would advise you also install check install```
sudo aptitude install checkinstall
```

At any rate:```
./configure
make
sudo checkinstall
```

If you do not want to use checkinstall the last line would be:```
sudo make install
```

---

### Post by tatimmer on 2006-09-27
make: *** No rule to make target `depend'. Stop.

You have to first "cd" to the directory in which the *.c files and "makefile" are located.  It did not find any file called "makefile" or "Makefile" in the current directory.

---

### Post by Allrab on 2006-09-27
Thank you that did it...

// Allrab

---

