---
title: "I want to setup a workstation for java, c/++ , matlab"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by gth835x on 2007-04-30
Can anyone point me in the direction I need to go if I want to be able to write and compile java, c/++, matlab (is there a program for matlab on ubuntu?).   Just had it one day with windows and got ubuntu so i am new to the linux world.

---

### Post by taurus on 2007-04-30
For C/C++, you need to install the build-essential package.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

For java, you need to install Sun's Java.

```
sudo aptitude install sun-java6-jre
java -version
```

For matlab, you need to purchase a copy of matlab and install it on your machine first before you can use it.

---

### Post by whee on 2007-04-30
Eclipse is the most widely used Java IDE if i'm not mistaking, it's free, open source and also available for Linux/Ubuntu.

---

### Post by UltraMathMan on 2007-04-30
You could probably start with installing the build-essential package. Not sure about a development enviroment, but matlab does make a linux version.

Hope this helps :)

EDIT: wow, once again I'm just a little too late, it never ceases to amaze me how fast responses are around here!
Taurus, if looking to code in java would one need "sun-java6-jdk" in addition to "sun-java6-jre"?

---

### Post by KIAaze on 2007-04-30
As alreday said, for java, there's Eclipse.

For C/C++, there's gcc and g++ in the build-essential of course, but there a lot of other IDEs available like KDevelop, Anjuta and code::blocks (and Eclipse again).

---

