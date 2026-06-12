---
title: "Registering java and javac commands"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by gamechampionx on 2007-04-17
I've installed the JDK using the auto-extracting file into some directory on my machine.

I've been able to determine that bin/javac is working, but the javac command is not registered.  Also, the java command is similarly not registered.

I'm wondering if there's a simple way to register the java and javac commands to link to the files in that directory without too much hassle.

Note that I followed the instructions on the Java Sun web site, but they did not register the commands.

---

### Post by taurus on 2007-04-17
You can configure it like

```
sudo update-alternatives --configure java
```
and pick the one that you installed from the list as your default version.

---

### Post by gamechampionx on 2007-04-17
There is only 1 program which provides java
(/usr/bin/gij-wrapper-4.1). Nothing to configure.

I sort of have the new java stuff just in my own directory and haven't moved it anywhere "important" yet.  Not sure what to do exactly.

---

### Post by taurus on 2007-04-17
Try

```
sudo update-alternatives --config java
```
Otherwise, look at all the arguments/options with

```
sudo update-alternatives --help
```

---

### Post by thelinuxguy on 2007-04-17
> **gamechampionx said:**
> 
Note that I followed the instructions on the Java Sun web site, but they did not register the commands.

Append these two lines to /etc/bash.bashrc (replace /opt/jdk1.6.0 with your Java folder)
```

export JAVA_HOME=/opt/jdk1.6.0
export PATH=${JAVA_HOME}/bin:${PATH}

```

Works for you?

---

### Post by gamechampionx on 2007-04-17
Thanks for the tip, but it won't let me modify that file as it's read-only.  I tried chmod +w but that didn't seem to help me out at all.

---

### Post by SOULRiDER on 2007-04-17
You could have also installed the sun-java6-jdk package:

```
sudo aptitude install sun-java6-jdk
```

---

### Post by gamechampionx on 2007-04-17
Thanks, I knew there would be an easier way to do it lol.

The javac command was registered as desired.

Java also works.

Somehow though, "man java" doesn't work while "man javac" does.  I think I might have broke this while tinkering with things previous.  I'm trying to figure out how to fix this, but I'm not really sure of what I'm doing.

---

### Post by thelinuxguy on 2007-04-17
> **gamechampionx said:**
> Thanks for the tip, but it won't let me modify that file as it's read-only.  I tried chmod +w but that didn't seem to help me out at all.

You need to be root to edit that file since its outside your home folder and regular users don't have write permission on the file.

```

gksudo gedit /etc/bash.bashrc

```

---

