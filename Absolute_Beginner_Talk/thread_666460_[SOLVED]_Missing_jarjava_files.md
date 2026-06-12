---
title: "[SOLVED] Missing jar/java files"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by crazyfuturamanoob on 2008-01-13
I got java compilers. I have typed "javac HelloWorld.java". 
I don't know where to it compiles the files. I tried to search but found nothing.
I'm even not sure does "javac compile to .jar. My problems are:
1) does javac compile .java to .jar?
2) when I type "javac file.java", where the compiled file will go?
3) do I need to add directory after "javac file.java"
Thanks

---

### Post by LaRoza on 2008-01-13
> **crazyfuturamanoob said:**
> I got java compilers. I have typed "javac HelloWorld.java". 
I don't know where to it compiles the files. I tried to search but found nothing.
I'm even not sure does "javac compile to .jar. My problems are:
1) does javac compile .java to .jar?
2) when I type "javac file.java", where the compiled file will go?
3) do I need to add directory after "javac file.java"
Thanks

1. No, it compiled .java to one or more .class

2. Usually in the same directory

3. If you are in the cwd, no.

Run:

```

java HelloWorld

```

After compiling.

---

### Post by SyL on 2008-01-13
[http://ubuntuforums.org/showthread.php?t=659817]("http://ubuntuforums.org/showthread.php?t=659817")

---

### Post by crazyfuturamanoob on 2008-01-14
> **LaRoza said:**
> 1. No, it compiled .java to one or more .class

2. Usually in the same directory

3. If you are in the cwd, no.

Run:

```

java HelloWorld

```

After compiling.
 What cwd means? I have tried that compiling thing multiple times, 
and checked the same directory over and over again, but I can't see
there any files, even if I check the hidden files too. Thanks anyway.

> [http://ubuntuforums.org/showthread.php?t=659817](http://ubuntuforums.org/showthread.php?t=659817)
Uh, thats my first topic but nobody answered my latest question,
so I made this. I don't have patience at all.

---

### Post by SyL on 2008-01-15
java will run your program. So that's the second step, once you have already compile your source and get your .class (with javac)
```

java [-options] class [args...] *         (to execute a class)*
 or  
java [-options] -jar jarfile [args...]     *    (to execute a jar file)*

```




javac will compile .java files and create the .class files 
(to know where the file will be created ; I already answered in your previous topic, [http://ubuntuforums.org/showthread.php?t=659817]("http://ubuntuforums.org/showthread.php?t=659817") )




is it clear?

---

### Post by crazyfuturamanoob on 2008-01-17
When I type "javac ..." I can't find the files anywhere.
Could you give me step-by-step instructions and an example?
Sorry about my stupidity (It's a serious problem).

---

### Post by SyL on 2008-01-18
[**[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=659817[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=659817")

again i explained everything in your previous topic. And you have example given step by step.

the .class files will be in the same directory than your .java class (if you do not use any option).

If you don't find you way with that, i suggest you to ask google: 
[http://www.google.com/search?hl=en&q=java+class+javac+howto&btnG=Recherche+Google&meta=]("http://www.google.com/search?hl=en&q=java+class+javac+howto&btnG=Recherche+Google&meta=")
[http://java.sun.com/j2se/1.3/docs/tooldocs/win32/javac.html]("http://java.sun.com/j2se/1.3/docs/tooldocs/win32/javac.html")

---

### Post by crazyfuturamanoob on 2008-01-19
WOHOOOO!!!!!!!
I MADE IT!!!!
I Finally managed to create a .class file!!
The command was:
"javac /home/user/folder/HelloWorld.java"
This is now solved.

---

