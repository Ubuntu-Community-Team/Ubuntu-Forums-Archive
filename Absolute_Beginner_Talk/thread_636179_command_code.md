---
title: "command code"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by ssaamon on 2007-12-09
I was wondering if there was a directory I could go to too see the C implementations for the command line code? like for example:

if I used: sleep 5

in the terminal, where could I see the source code for the sleep command?



does it used the C function sleep(TIME)?


thanks so much

saamon

---

### Post by cmnorton on 2007-12-09
It sounds like you'd need the source code for bash. Off hand, I don't know what it would be under if using synaptic manager. But you apparently can get it from [ftp://ftp.gnu.org/gnu/bash/](ftp://ftp.gnu.org/gnu/bash/) .

---

### Post by ssaamon on 2007-12-09
thanks for that :)

does anyone know where the source code is on the system?

thanks

---

### Post by Dr Small on 2007-12-09
The actual file for sleep is located in /bin/sleep, but I have no idea how you would view the actual source code.

---

### Post by dfreer on 2007-12-09
[Coreutils]("http://packages.ubuntu.com/gutsy/base/coreutils") is the package that provides /bin/sleep.
You should be able to download the source code with this command:
```
sudo apt-get source coreutils
```
The source code should then be located in your current directory, I do believe. Of course, since there is quite a few programs provided by that package, I'm not entirely sure where the source code specifically pertaining to sleep would be located.

---

