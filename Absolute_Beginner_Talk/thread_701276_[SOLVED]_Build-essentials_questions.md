---
title: "[SOLVED] Build-essentials questions"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Sceiron on 2008-02-19
Yo,
need help with explanation on some issues.
1. I think i have found out that Ubuntu i a Debian based distribution, which means it builds on ...... from debian ?

2. What is the build-essential good for, is this only necessary when u build code directly form source ?
I have read that build-essential are a list of pointers, a set of compiling tools etc.

3. What is the meaning of a "meta-package" ?
Build-essential is a meta package isnt it ?

-Trying to know why, not just how-
Sceiron

---

### Post by pedro_orange on 2008-02-19
> **Sceiron said:**
> 
1. I think i have found out that Ubuntu i a Debian based distribution, which means it builds on ...... from debian ?

Yes it's based on Debian. 

> 
2. What is the build-essential good for, is this only necessary when u build code directly form source ?
I have read that build-essential are a list of pointers, a set of compiling tools etc.


build-essential is a set of programming libraries along with alot of other essential tools for building apps from source / building debian packages. If you install it using:

```
sudo apt-get install build-essential
```

You can actually see a list of what it contains in /usr/share/doc/build-essential/list

> 
3. What is the meaning of a "meta-package" ?
Build-essential is a meta package isnt it ?


A meta package is a package that contains an XML Meta data file that describes what is contained within the package I presume. Metadata is conventionally associated with all files including a file's owner, group and other attributes. Like read/write/execute permissions etc.

---

### Post by mimada on 2008-02-19
Yes, Ubuntu is based on the Debian kernel but it's different enough that you need to be really cautious when installing stuff from the Debian repositories. In fact, you shouldn't as a rule.

"Build-essential" is a meta-package. It installs the gcc compiler and support libraries. It's important if you want to start programming or want to install some stuff not in the repositories.

A meta-package is a collection of files that work together. Some programs have "dependencies" which are files that are needed by the application for it to function. For example, if you want to install the program Eclipse (which is a programming environment), you would need to install Sun's Java first, otherwise it will not run. Thus, Eclipse is dependent on Java. A possible meta-package may combine Java and Eclipse together (not likely because of potential licensing problems with Java).

Hope this helps.

---

### Post by Sceiron on 2008-02-19
> 
You can actually see a list of what it contains in /usr/share/doc/build-essential/list


I'll try this when i get home from work :)
Thanks !

---

### Post by jan quark on 2008-02-19
Sceiron
king crimson is the best

---

### Post by Sceiron on 2008-02-19
> **jan quark said:**
> Sceiron
king crimson is the best

Indeed

---

### Post by Sceiron on 2008-02-19
> 
A meta-package is a collection of files that work together. Some programs have "dependencies" which are files that are needed by the application for it to function. For example, if you want to install the program Eclipse (which is a programming environment), you would need to install Sun's Java first, otherwise it will not run. Thus, Eclipse is dependent on Java. A possible meta-package may combine Java and Eclipse together (not likely because of potential licensing problems with Java).

Hope this helps.

I have investegated the dependencies before :) :
[http://ubuntuforums.org/showthread.php?t=695608&highlight=dependencies+sceiron](http://ubuntuforums.org/showthread.php?t=695608&highlight=dependencies+sceiron)

Thanks

---

