---
title: "How do I run a Java app?"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by FredJones on 2008-03-31
I downloaded TimeTracker (TimeSlot Tracker) from SourceForge but I am at a loss as to how to compile and/or execute it. I have Java installed and java from the command line works, but I don't see how to run the TimeTracker. Can anyone enlighten me?

thanks!

---

### Post by Michael.Godawski on 2008-03-31
To execute it, use the "java -jar" command. To unpack it, use the "jar" command.

So it would be

```
sudo java -jar file.jar
```

---

### Post by &#12467;&#12531;&#12497;&#12452;&#12523; on 2008-03-31
There are a couple of ways you could do it. (mind you Java is installed)

1. May only be for windows
```

@java yourclass.class

```

2.
```

java yourclass.class

```

3. Use the post above me to run .jar files (sort of like a zip but with a bunch of classes)

To compile you would use:
```

javac yourclass.java

```

Hope some of that helped.

---

### Post by bovus on 2008-03-31
> **&#12467 said:**
> 
2.
```

java yourclass.class

```


to run a class file in bash terminal, dont put the ".class" extension, it will give you a class not defined error or something like that.

so it would look like this
```

$ java yourclass

```

---

### Post by &#12467;&#12531;&#12497;&#12452;&#12523; on 2008-03-31
> **bovus said:**
> to run a class file in bash terminal, dont put the ".class" extension, it will give you a class not defined error or something like that.

so it would look like this
```

$ java yourclass

```

Oh yes I forgot, I havn't done Java in awhile. :)

---

### Post by spydon on 2008-03-31
Have you downloaded the TimeTracker .zip or .bin?

---

### Post by stchman on 2008-03-31
> **FredJones said:**
> I downloaded TimeTracker (TimeSlot Tracker) from SourceForge but I am at a loss as to how to compile and/or execute it. I have Java installed and java from the command line works, but I don't see how to run the TimeTracker. Can anyone enlighten me?

thanks!

You need the JRE and the JDK.

```

sudo apt-get -y install sun-java5-bin sun-java5-fonts sun-java5-jdk sun-java5-jre sun-java5-plugin
```

After that you will compile the .java code.  Make sure to include extension.  We will use foo.java as an example in your home directory.

```
javac ~/foo.java
```

After that a .class file will be created, you will run the .class file.

```
java -classpath ~/ foo
```

That is it.

---

### Post by FredJones on 2008-03-31
Thank you all. Got it now. :)

---

### Post by bovus on 2008-03-31
> **stchman said:**
> 

```

sudo apt-get -y install sun-java5-bin sun-java5-fonts sun-java5-jdk sun-java5-jre sun-java5-plugin

```



Correct me if i'm wrong, but shouldnt you be using the latest version of Java, 6, if your going to get the jre and jdk for the first time?

---

### Post by stchman on 2008-03-31
> **bovus said:**
> Correct me if i'm wrong, but shouldnt you be using the latest version of Java, 6, if your going to get the jre and jdk for the first time?

I know that Java 6 is in the repos.  I however have had zero problems with the Java 5.  I tried Java 6 a while back and it gave me problems.

If the user wishes to use 1.6 then substitute 6 for 5 in the apt-get line.

---

### Post by kane77 on 2008-03-31
most of programs are written for java-5, however running 6 is preferred I guess as it will run 1.5 programs alright and will also run 1.6, I have been using both jre and jdk of version 6 and had no problems so far (not counting bug on hardy)

and one more point.. classes usually start with capital letter.

---

