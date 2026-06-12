---
title: "What is C Shell and how i can install it?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-01-13
Hi
thank you for reading my post
Can some one explain what is C Shell and how i can install it into my ubuntu 7.10?
I have an script which i need to execute and it does not execute because of some errors like

```

bash: setenv: command not found

```

It should be executed with a command like:

```

 source db2cshrc

```


Thanks.

---

### Post by mali2297 on 2008-01-13
From [Wikipedia]("http://en.wikipedia.org/wiki/C_shell"):
> 
The C shell (csh) is a Unix shell developed by Bill Joy for the BSD Unix system. It was originally derived from the 6th Edition Unix /bin/sh (which was the Thompson shell), the predecessor of the Bourne shell. Its syntax is modeled after the C programming language. The C shell added many feature improvements over the Bourne shell, such as aliases and command history. Today, the original C shell is not in wide use on Unix; it has been superseded by other shells such as the Tenex C shell (tcsh) based on the original C shell code, but adding filename completion and command line editing, comparable with the Korn shell (ksh), and the GNU Bourne-Again shell (bash).


You can install tcsh through apt-get or synaptic. Start it then from the terminal with
```

tcsh

```
and try to run your script.

---

