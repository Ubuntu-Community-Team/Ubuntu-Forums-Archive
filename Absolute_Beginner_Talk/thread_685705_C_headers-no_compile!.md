---
title: "C headers-no compile!"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by coyotech on 2008-02-02
I need to start programming in C and have been using Geany (but I get the same errors if I use other compile commands from the terminal). I'm writing simple c programs like hello world, which call for include stdio.h and common things like that, and they don't compile because they can't find the header. I've tried other things, including compiling the code from proper ubuntu c source code. Same error on all. I figure this is due to my ignorance of Linux and C...

Where are the headers supposed to be? Do I change the include path (I tried that):(? Do I save my c programs somewhere other than my home directory? Have I missed installing something? I've downloaded and installed about a million dependent files, and the compiler seems to work, but it can't find a library or header file, whatever I'm doing. Unless I'm in the kernel...then it compiles. That seems a little risky and difficult. Can anybody recognize what I'm doing wrong? This is kind of embarrassing!

---

### Post by taurus on 2008-02-02
You need to install the build-essential package.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by coyotech on 2008-02-02
Thanks!

---

