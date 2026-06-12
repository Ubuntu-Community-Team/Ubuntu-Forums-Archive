---
title: "Gcc/G++ compiler"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by marialena5 on 2007-12-26
Hello there!
A few days ago, I installed Ubuntu 7.10. and I then tried to use the gcc compiler to compile a program. I thought it would be included and installed with the whole ubuntu package, but when i gave the command 'gcc -o exe new.c'  the following was printed on my terminal:
new.c:1:19: error: stdio.h: No such file or directory 
new.c:2:19: error: stdlib.h: No such file or directory
[...........-and some other errors-.................]

Does this mean i don't have everything I need to have installed?
I'm kind of new at this, so If you could tell me what else should I download or do, to install properly the gcc compiler, I would appreciate it.

Thnx a lot,
and Merry Christmas!

---

### Post by taurus on 2007-12-26
You need the build-essential package.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by PeterJS on 2007-12-26
Ubuntu's an odd lot in a lot of things it does, one of these is by default it installs no development tools. The good news is there's a meta-package called Build-Essential that has everything you'll need for basic compilation. You might still need to install some -dev packages if you plan on compiling anything more complex than command line program.

---

### Post by LaRoza on 2007-12-26
@OP This confuses many new Ubuntu users (programmers).  I started a wiki on it, [http://laroza.wikidot.com/one](http://laroza.wikidot.com/one), but it is too late for that now.

Also, you might be interested in the Programming Talk forum, it is under "Development and Programming".

---

### Post by marialena5 on 2007-12-26
> **taurus said:**
> You need the build-essential package.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install build-essential
```

I did as you said, and it compiles perfectly:KS! I'll know what to do next time ;)

//Thnx a lot people :)
You' ve been a great help, really fast :)!

---

