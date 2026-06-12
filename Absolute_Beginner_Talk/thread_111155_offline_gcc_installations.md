---
title: "offline gcc installations"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by bigwab on 2006-01-01
Hello all,

I have just installed ubuntu 5.10 using the PC (Intel x86) install CD on a P4 PC.

I'm a beginner with linux operating system and i have several questions related to gcc.

1. Is it possible to install several versions of gcc and have the ability to choose which version to compile my code with?

2. How can I install gcc into my system? Please keep in mind that I do not have internet access on the ubuntu pc.

3. I believe you may ask, why would I need to use more than one version of gcc, well I'm carrying out a research and I need to use a tool that measures functional cohesion. The only tool I found was "FUNCO", and it uses a slightly modified gcc 2.6.3. That is why I need more than one version. The new one for my other work, and the old one for FUNCO.

Thank you for your help.

Take Care.

---

### Post by UbuWu on 2006-01-01
[QUOTE=bigwab]
2. How can I install gcc into my system? Please keep in mind that I do not have internet access on the ubuntu pc.
[/QUOTE]

It is on the install cd. Select build-essential in synaptic or do an 'apt-get install build-essential'. However there is only one version on the cd.

---

### Post by bigwab on 2006-01-02
What is "synaptic"?

I have the old version of gcc 2.6.3 with me. 

I will try 'apt-get install build-essential' when I return home.

Thanks

---

### Post by coredump on 2006-01-02
I just used Synaptic on an Ubuntu 5.04 system for Mac/PPC to install 'build-essential' and it worked fine.  I already had the CD in the drive, and the package manager just found it and installed the files.  Great!  Now I can compile C code and even have a look at the PPC assembler...

Thing is, I'd never have expected the installer to have behaved like that -- to install stuff from CD (in the first place) but not install everything.  I'd assumed that it had installed everything it had on the CD, and that didn't include GCC, and I'd have to install it from the network.

Now, if only I could find out how to right-click with a Mac one-button mouse.

---

### Post by bigwab on 2006-01-02
Thank you so much UbuWu. gcc was installed beautifuly and extremely fast!

Now remaining is my first question, is it possible to install and work with two different versions of gcc?

Thanks again.

---

### Post by Jukey on 2006-01-02
what's gcc?

---

### Post by bigwab on 2006-01-02
[QUOTE=Jukey]what's gcc?[/QUOTE]

gcc is a C & C++ compiler.

---

### Post by az on 2006-01-02
Yes, you can have many version of gxx installed and use any one.

gcc-2.6 is as old as the hills.  I don't think you will find it anymore.  What is the oldest version of gcc that will work with the source you have?

---

### Post by bigwab on 2006-01-02
Yes, you are right, it is very old. But I managed to find it. I just don't know how to install it, and how to use it seperately.

---

