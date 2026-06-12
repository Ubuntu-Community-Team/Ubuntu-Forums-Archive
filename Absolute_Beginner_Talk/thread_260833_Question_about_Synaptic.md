---
title: "Question about Synaptic"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by squeemu on 2006-09-19
Hello, I am completely new to Ubuntu, so I am fairly lost. I am looking for a good c and c++ compiler, and I have installed build-essential. When I look at the Synaptic history, it says I have installed gcc, build-essential, and everything else. However, if I cannot find what I have to do to actually run the compiler. When I follow the links to the different folders, all I can find are readmes and FAQ files. What do I do?

---

### Post by Jussi Kukkonen on 2006-09-19
gcc is the executable you're looking for (for both C and C++). There should be a lot of tutorials around the web. Sorry, I have no links.

---

### Post by JNowka on 2006-09-19
what you want to do to compile the source code is go to the directory your c++ source code is and type the following.

g++ filename.ext

This should compile the program into an executable with the name 'a.out' You can rename the executable in anyway that you want.  Not sure how to change the name automatically.

If you want to compile c code and not c++ then you will want to use the following.

gcc filename.ext

Thats about it.

---

