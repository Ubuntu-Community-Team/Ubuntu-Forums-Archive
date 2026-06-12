---
title: "Help unzipping cpgz file from command line"
date: 2013-05-30
forum: Any Other OS
---

### Post by jps2012 on 2013-05-30
I'm trying to figure out how to unzip files. I've got an old version of Bash (3.2.17) and it doesn't contain 'unzip.' I can't upgrade Bash using 'apt-get' because it also doesn't have 'apt-get.' 

The file I'm trying to unzip is "SYSTEM.BIN.CPGZ" (I'd hoped to repair some file structure problems on an old Mac). 

If someone could tell me how to unzip files with another (older) Bash command, I'd be grateful. And if you know the older version of 'apt-get' (that might help me GET apt-get and install it) ... I thank you.

---

### Post by Cheesemill on 2013-05-30
What OS are you using?

***All*** versions of Ubuntu have apt-get installed and unzip in the repositories.

---

### Post by ShadowVegan on 2013-05-30
Can't you just right click the file and click 'extract here'? Do you not have that option?

---

### Post by jps2012 on 2013-05-30
I'm sure that's true for Ubuntu. But I'm using bash on a Mac (and learning the command line so I can use it on my Mac AND my Ubuntu machine). 

I'm on OS 10.5.8. And no, no option for "extract here" by right clicking (Finder is broken--which is why I'm trying to repair the machine by unzipping a set of files I HOPE will repair it).

---

### Post by sudodus on 2013-05-30
Can you unzip that file somewhere else, and port its content to the Mac as expanded?

---

### Post by jps2012 on 2013-05-30
Sudodus: That's an excellent idea. I'm going to try that. BUT I'd still like to know how to get apt-get or some similar command into my bin/bash folder. Does anyone know what command USED to perform the function of apt-get? And the command the preceded (historically) unzip?

---

### Post by jps2012 on 2013-05-30
My DIRECTORY, I mean. (Still learning the lingo.)

---

### Post by sudodus on 2013-05-30
> **jps2012 said:**
> Sudodus: That's an excellent idea. I'm going to try that. BUT I'd still like to know how to get apt-get or some similar command into my bin/bash folder. Does anyone know what command USED to perform the function of apt-get? And the command the preceded (historically) unzip?

apt-get and aptitude are front-end tools for ***dpkg***

> **jps2012 said:**
> My DIRECTORY, I mean. (Still learning the lingo.)

It's OK, both directory and folder are used for the same thing.

---

### Post by ShadowVegan on 2013-05-30
> **jps2012 said:**
> Sudodus: That's an excellent idea. I'm going to try that. BUT I'd still like to know how to get apt-get or some similar command into my bin/bash folder. Does anyone know what command USED to perform the function of apt-get? And the command the preceded (historically) unzip?

If you already have the software package (software in the Ubuntu repositories can be downloaded from packages.ubuntu.com) you can use
```
sudo dpkg -i <file path>
```
to install the software. That achieves the same thing as apt-get install (although apt-get install will sometimes install related packages as well as the one you are trying to install; dpkg -i will not do this).

---

### Post by oldos2er on 2013-05-30
Moved to Other OS/Distro Support.

---

### Post by jps2012 on 2013-05-30
Thanks, ShadowVegan. I'll try that. I'm sure it will help me on my Ubuntu machine, even if it doesn't work on the OS X files.

---

### Post by jps2012 on 2013-05-30
I was able to unarchive the files using an open source program called TheUnarchiver: [http://wakaba.c3.cx/s/apps/unarchiver.html](http://wakaba.c3.cx/s/apps/unarchiver.html) 

Whew! Now I just have to figure out where to place the Bin files.

---

