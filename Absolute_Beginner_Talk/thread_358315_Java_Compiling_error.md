---
title: "Java Compiling error"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by meteora184 on 2007-02-10
I have anjuta IDE, but whenever i trry and compile something, it says "javac not found".  so i was wondering how you could fix this error, or if there is a different compiler. 

I also know that u can compile java without a compiler in windows using the command prompt, and was wondering if it could be done the same in the terminal.

---

### Post by Maestro23 on 2007-02-10
I looked in Synaptic and there is a "javacc" compiler package there.  Is that what you are looking for?

---

### Post by meteora184 on 2007-02-10
i have no clue, i just want to be able to compile my java applications in linux.

---

### Post by jordanmthomas on 2007-02-10
...have you installed sun-java5-jdk?
```
sudo aptitude install sun-java5-jdk
```

If that doesn't work all is not lost.

---

### Post by Maestro23 on 2007-02-10
> **jordanmthomas said:**
> ...have you installed sun-java5-jdk?
```
sudo aptitude install sun-java5-jdk
```

If that doesn't work all is not lost.

Actually java6 is in the repositories now.  Installed it yesterday.

---

### Post by jordanmthomas on 2007-02-10
Ah, the online package search didn't reflect that.  
java6 isn't the jdk though is it?
I am not 100% certain...I use Arch and so I just use the online package search to get package names for Ubuntu users since Arch's name != Ubuntu's name

---

### Post by annda on 2007-02-10
> **meteora184 said:**
> I also know that u can compile java without a compiler in windows using the command prompt, and was wondering if it could be done the same in the terminal.

i'm sorry but someone needs to say this: you CANNOT compile anything without a compiler. you have installed a java compiler in windows. most probably, some program did it for you without you even knowing.

please launch synaptics and search for java. that way you can choose what you want to install. good luck!

---

### Post by Maestro23 on 2007-02-10
> **jordanmthomas said:**
> Ah, the online package search didn't reflect that.  
java6 isn't the jdk though is it?
I am not 100% certain...I use Arch and so I just use the online package search to get package names for Ubuntu users since Arch's name != Ubuntu's name

Everything for java6 is in there now. Including sun-java6-jdk.;)

---

### Post by jordanmthomas on 2007-02-10
> **Maestro23 said:**
> Everything for java6 is in there now. Including sun-java6-jdk.;)
I see that it's in there for feisty, but edgy appears to still have java5.
Whatever...no point in arguing about it.

---

### Post by Maestro23 on 2007-02-10
> **jordanmthomas said:**
> I see that it's in there for feisty, but edgy appears to still have java5.
Whatever...no point in arguing about it.

I'm not arguing be any means man. No harm..no foul:) 

5 and 6 are both in there for Edgy.

Just so the OP gets what he needs.

---

### Post by phossal on 2007-02-11
You have to enable the backport repositories to get sun-jdk6-java. It *seems* easy to pull a third party package (and it may be) like that, but I'm not sure why anyone would go that route instead of just bringing it down from SUN directly. The packages trail SUN's updates by (sometimes) months. The amount of work required to properly install Java using either method is about the same, based on my experience. But the hassles involved with diagnosing a failed *package*  installation suck.

As someone noted below, the only way you're compiling anything is by making sure that a) you have a valid JDK installation and B) that *javac*, the JDK compiler executable, is listed in your *path*.

For the record, I much prefer eclipse over Anjuta for both Java *and C/C++*.

---

