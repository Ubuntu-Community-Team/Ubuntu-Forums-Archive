---
title: "Trouble running JAVA app."
date: 2005-09-13
forum: Absolute Beginner Talk
---

### Post by JordanR on 2005-09-13
Brand new to Ubuntu and the Linux world, but I think I'm getting the hang of it pretty quickly.  Trying to run DVArchive which can be downloaded from their website as a zipped up Java application (with no Windows installer).  I've downloaded it, I've unpacked it to a folder on my desktop (for now).  But it will not run.  At first, .jar files were associated with the archive manager.  Fixed that.  
I tried downloading JAVA runtime, but it doesn't seem to want to install.

Any help would be GREATLY appreciated.

---

### Post by evilghost on 2005-09-13
Did you do:
[http://www.ubuntuguide.org/#jre](http://www.ubuntuguide.org/#jre)

---

### Post by JordanR on 2005-09-14
Thanks evilghost.  I'll give it a shot tonight.
Somehow I'm not thinking that's going to help only because the Java RTE for Firefox wasn't what I needed to do on my Windows Machine, but I'll give it a shot.

---

### Post by JordanR on 2005-09-19
Ok, I tried it.  I tried it with 1.4 and 1.5.  No good.  I get the message ```
Failed to load Main-Class manifest attribute from DVArchive.jar
``` 
Any thoughts?

---

### Post by blastus on 2005-09-20
[QUOTE=JordanR]Ok, I tried it.  I tried it with 1.4 and 1.5.  No good.  I get the message ```
Failed to load Main-Class manifest attribute from DVArchive.jar
``` 
Any thoughts?[/QUOTE]

I'm not familar with DVArchive. What command are you entering to run it? The above error tells me that the META-INF/MANIFEST.MF file in the JAR file does not have a "Main-Class" attribute in it--in other words, the JAR file is NOT executable--it could just be a library.

A JAR file is like a ZIP file. Open it with a file archiver and look for the META-INF/MANIFEST.MF file. The manifest file contains attribute/value pairs. One of the attributes that may be used in a manifest is the "Main-Class" attribute. This attribute is used to identify the main class that should execute when the JAR file is "executed." In Java the "main class" is the class that has the method "public static void main(String[] args) {}" in it. On Windows, to execute a JAR file you can double-click on it (I'm not sure what the equivalent is on Linux yet.) You can also execute a JAR file with the syntax...

```
java -cp [thejarfile.jar] [themainclass]
```

So if the jar file is DVArchive.jar and the main class is org.dv.Archive then...

```
java -cp DVArchive.jar org.dv.Archive
```

...would execute the JAR file. I use Apache Ant so it's been a while since I've messed with things like CLASSPATHs and such.

---

