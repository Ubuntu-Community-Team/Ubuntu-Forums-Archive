---
title: "trouble with java compiler"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by Nagasaki911 on 2006-02-07
I am of course new to ubuntu and i already googled my problem to no success.  I saw an earlier thread here but was not able to post on it, the person had a similiar problem but the solutions that other members suggested didn't work for me.

Basicaly, i already downloaded/extracted the file and so i have hte jdk file sitting there.  whenever i try to compile it using the javac command i get 

sean@Sean:~$ javac javaTest.java
bash: javac: command not found


Can anybody offer up any help?

---

### Post by Packard Dell on 2006-02-07
did you set its classpath? if not, open a terminal and do the following:
1. type** sudo gedit ~/.bashrc** then press [ENTER]
2. add this line **export PATH=/path/to/your java/jdk<version>/bin/:$PATH** (of course, replace the */path/to/your java* to the directory where you installed it) at the very end of your .bashrc file, press enter to leave a carriage return.
3. save it and close gedit.

try compiling....

---

### Post by Packard Dell on 2006-02-07
> Basicaly, i already downloaded/extracted the file and so i have hte jdk file sitting there. whenever i try to compile it using the javac command i get 

have you actually installed it?

---

### Post by geekphreak on 2006-02-07
If you're unsure how to get java install properly, get the self-extracting .bin file you can simply run. After that all you need to do is tweak the PATH and you're set.

---

### Post by Nagasaki911 on 2006-02-07
i think i already installed it and i did download the self extracting file i am just having oroblemts with the path

---

### Post by kaamos on 2006-02-07
what is the output of
```
which javac
```
and
```
locate javac
```
The tools should install to your user PATH so I think your Java installation isn't in a good shape. You did install the jdk, right?

---

### Post by JakeSpeare on 2006-02-07
You need to set your path to the java install directory (as set out above)

Once done if you still have probs, you can temporarily set the classpath to your current directory as follows:

to compile:

javac -classpath . yourfile.java

to run:

java -classpath . yourfile

---

### Post by Nagasaki911 on 2006-02-07
thanks for all your help i finally got it to work using the ~/.bashrc

thanks

---

