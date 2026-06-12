---
title: "need help setting classpath"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by spearfish on 2007-05-17
Hi,

I recently installed Java on my system, and I am having a problem related to my "CLASSPATH".  The system seems to choke on anything that I run, after it compiles.  For example, if I write a Java class called "welcome", then compile it and run it:

>java welcome
Exception in thread "main" java.lang.ClassFormatError: welcome (unrecognized class file version)
at java.lang.VMClassLoader.defineClass(libgcj.so.7)
at java.lang.Classloader.defineClass(libgcj.so.7)
...
at gnu.java.lang.MainThread.run(libgcj.so.7)

My Java book says something about setting the CLASSPATH when this error occurs, but nothing I have tried seems to work. (sigh)  How do you set the "classpath"?

-A

---

### Post by taurus on 2007-05-17
What have you done so far and you did configure your java, right?

```
java -version
```

---

### Post by Iokua on 2007-05-17
spearfish, your book is correct. You just need to set your CLASSPATH variable so Java knows where to look for imported classes. My guess is that you need to add the current working directory to your CLASSPATH. Unfortunately, I'm not on my Ubuntu machine at the moment and I can't remember exactly how to do this in your bash profile, but  you can add it temporarily using the java compiler's --classpath option. Try this and then try to run your program again:

```
javac -classpath $CLASSPATH:./
```

This just adds ./ (your working directory) to the CLASSPATH.

Then, if this works, you can add this to your bash profile so that you don't have to do it every time you log out. I can't remember how to do this at the moment but I can figure it out when I get home.

---

