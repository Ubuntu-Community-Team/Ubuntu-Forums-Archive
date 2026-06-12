---
title: "command name"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by tiendn on 2007-04-02
Hi!
  Can you show me how to know command name after I've installed a program in synaptic?
                                                                                                                thanks!

---

### Post by NikoC on 2007-04-02
What's the program you have installed?

---

### Post by Kobalt on 2007-04-02
What are you searching for exactly ? I guess you mean the command to launch a program... You can find the launcher using this in a Terminal : 
```
which *program-name-you-want-to-launch*
```
Usually the name of the app is enough to launch it with Alt+F2 though.

---

### Post by tiendn on 2007-04-02
I have installed gcc-h8300-hms for compile c program for hitachi toolkit, but I can't use this command.

---

### Post by david_kt on 2007-04-02
Could your try to open t&#7867;minal, and type:

```
gcc
```

and then press tab twice, it will inform you what kind of command you have in your system. for example, mine are:

```
gcc         gcc-3.4     gcc-4.0     gccbug      gccbug-3.4  gccbug-4.0

```

And then, if you want to know how to use gcc for example, just type:
```
man gcc
```

DK

---

### Post by tiendn on 2007-04-02
Hi
 I think I have installed all packages, but now I am having problem with screen resolution, so when I finish this problem I will try it. ahh, I compile my program on different computer which is install window and I haved install cygwin(simulate linux) and my program is good and I use command "h8300-hms-gcc" on that computer.

---

