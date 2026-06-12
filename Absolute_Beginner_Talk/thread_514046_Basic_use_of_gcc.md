---
title: "Basic use of gcc"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by voxelnaut on 2007-07-31
I'm not sure if I should be posting this here or in the programming forum, but since the matter is likely trivial, I decided to try here.

I am learning C++ and have recently switched to Ubuntu from Windows (I'm trying out Kubuntu right now). As far as I can tell, the gcc compiler is already included in Kubuntu, but I can't figure out how to use it. Trying the first thing that comes to mind...

*gcc HelloWorld.cpp*

...produces the error...

*gcc: error trying to exec 'cc1plus': execvp: No such file or directory*

...which leaves me confused. Unless there's something I don't understand about the commandline, there's probably something that needs to be configured before use?

Thank you for your time.

---

### Post by KIAaze on 2007-07-31
gcc is for compiling C code, while g++ is for compiling C++ code (usually in .cpp files).

My guess is that you don't have g++ installed.

Try ```
sudo aptitude install build-essential
```

It should install g++ along with all the other necessary programs for compiling source code.

Then run ```
g++ HelloWorld.cpp
```

---

### Post by voxelnaut on 2007-07-31
Aaaand... it works! :)

Just another quick question... how and where can I get a list of g++ commandline switches?

And that will be the end of my triviality for the day. Thanks!

---

### Post by KIAaze on 2007-07-31
```
man g++
man gcc
```

(They both have the same man page actually.)

---

### Post by Tensk8 on 2007-08-06
hi I'm new in ubunto too,  and I'm having the same problem. I do what was posted here but i recived ths:


bash: g++: command not found
 after doing :
sudo aptitude install built-esscential


Need help ????

---

### Post by KIAaze on 2007-08-06
It's:
```
sudo aptitude install build-essential
```

Can you check if you have the g++ binary (executable):
```
ls /usr/bin/g++
```

And also if your PATH variable is set correctly:
```
echo $PATH
```

---

