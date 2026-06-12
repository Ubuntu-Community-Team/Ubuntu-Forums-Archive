---
title: "gcc can't create executables"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by voiceofxile on 2006-06-07
I'm trying to configure a wine program for gaming, i have it unzipped. when I ./configure it begins but tells me that my compiler can't create executables. I assume this means it won't configure the program.

I learned that ubuntu doesn't automaticly have  gcc or   make    commands, but i used the package manager to get them...maybe there are multiple installs that conflict and hence i cant use gcc?

anyone know what i can do? I'm def new to this, but i'm trying very hard to learn all that i can on my own.  thanks

:confused:

---

### Post by UbuntuJohan on 2006-06-07
Try adding sudo in front of your command. To make sure it isnt a permission problem
If you haven't already done that?
i.e
sudo ./configure.sh

---

### Post by nanotube on 2006-06-07
another thing to try is to install package "build-essential"
that should pull all the compilers and their dependencies automatically. it may be that you are simply missing some package, build-essential will take care of that.

---

### Post by voiceofxile on 2006-06-07
yes, i have used the sudo command :(

---

### Post by voiceofxile on 2006-06-07
i was looking for that build essentials package, thanks alot. I'll give it a try now :mrgreen:

---

### Post by voiceofxile on 2006-06-07
You have my thanks, now I have the build-essentials package and I can read up and  figure it out.  :mrgreen:

---

