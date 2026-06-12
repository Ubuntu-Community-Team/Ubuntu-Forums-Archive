---
title: "Java Version"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by ayesha kalra on 2007-05-28
Hi 

I am an absolute beginner to Ubuntu. I downloaded JAVA from here and installed as per instructions

[http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp) 

(the self-extracting file and installed it, everything went fine)

I think the Java I installed is version 6 (update 1), but when I type <java -version> in the terminal it says "java version 1.4.2", "gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)". 

So I think I am not able to "link " the latest version. Any advice on how to do this will be helpful.

I am sure I will be bothering you people a lot more as I wet my feet in linux via Ubuntu.

Thanks
Ayesha

---

### Post by mahiyar on 2007-05-28
This is a very common problem. On the command line type >>sudo update-alternatives --config java   and you will see a list of all your java versions select the one that is the latest.

---

### Post by DJ Wings on 2007-05-28
GIJ and GCJ are the open-source Java compilers. They have nothing to do with the version of the main Java libraries.

---

### Post by ayesha kalra on 2007-05-28
To mahiyar

This is what I get when I typed what you 

There is only 1 program which provides java
(/usr/bin/gij-wrapper-4.1). Nothing to configure.

I cannot choose the version. 

To DJwings

How do I know which version of java libraries are installed in the system?

Thanks for suggestions
Ayesha

---

### Post by taurus on 2007-05-28
If you are running Feisty, you can install the latest version, 1.6 directly from a terminal.

```
sudo aptitude update
sudo aptitude install sun-java6-bin sun-java6-plugin
java -version
```

---

### Post by ayesha kalra on 2007-05-28
To Taurus

I typed what you suggested, the terminal screen shows license agreement and stop there. There is no way to accept the agreement (even after scrolling down to the bottom).

Is there something I am missing here?

Thanks
Ayesha

---

### Post by taurus on 2007-05-28
Do you see the <OK> at the bottom left side?  Hit the Tab key to highlight the <OK> and hit the Return key to accept it.

---

### Post by ayesha kalra on 2007-05-28
To Taurus

It works! Thanks a lot. I guess I can start a new thread now. 

I am excited.
Ayesha

---

