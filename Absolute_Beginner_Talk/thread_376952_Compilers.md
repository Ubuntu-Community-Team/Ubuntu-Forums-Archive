---
title: "Compilers"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Sizzlintrumpet on 2007-03-05
Hello, this will be my first post on ubuntuforms.com, and I am ready to get my hands dirty. I would appreciate a little help thougth from those with more experience. My first question, is does anyone know where I can get a list of keywords that are important to know for using the console. Also if anyone knows, where I could find a compiler for C++ and/or Java. I would really appreciate the help and look foward to posting more.

---

### Post by jd65pl on 2007-03-05
gcc is a compiler you will find it in the repositories

here are some simple commands you might find useful [http://jamie.dumbill.googlepages.com/ubuntucommands2](http://jamie.dumbill.googlepages.com/ubuntucommands2)

---

### Post by Sizzlintrumpet on 2007-03-05
Okay complete noob here, I was just wondering what are repositories, and how do you access them, I've breifly heard this term while googling for answers. Recently I decided maybe forms were the best way to get results to help me though. ^_^

---

### Post by tkjacobsen on 2007-03-05
Repositories are the archives from which you can download and install packages. You use them via a package manager. Go to applications -> Add/remove or system->administration->synaptic package manager for a more advanced version

---

### Post by the_nomad on 2007-03-05
[here]("http://ubuntuguide.org/wiki/Ubuntu#How_to_apt-get_the_easy_way_.28Synaptic.29"). this might help you activate your repositories. then open a terminal and 
```

sudo apt-get install build-essential

```
to install c/c++ compiler.

to compile a c file open terminal, go to your directory (cd /your/directory/) and there 
```

gcc -o output_name the_file.c

```

to compile a c++ file open a terminal, but in this case use g++ instead of the gcc command.

a list of usefull commands you can find [here]("http://www.computerhope.com/unix.htm"), and [here]("http://www.ss64.com/bash/").

hope it helps.

---

