---
title: "gcc and g++ don't work"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by Ahren on 2006-03-26
Hi,

I am new to Ubuntu, and installed 5.10 on my system today.  I used the Synaptic Package Manager and installed the gcc-3.4 package and the cpp-3.4 package.

However, I am having trouble getting gcc and g++ to work.

When I type g++ at the command prompt, I get
bash:  g++: command not found

same thing for gcc, command not found.

Can anyone help?

Thanks

---

### Post by Sutekh on 2006-03-26
gcc-3.4 doesn't depend on g++ so it won't be installed when gcc-3.4 is

build-essential does depend on both gcc and g++, so install it instead.
```
sudo apt-get install build-essential
```

---

