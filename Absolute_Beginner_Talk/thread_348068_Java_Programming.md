---
title: "Java Programming"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by gidra on 2007-01-28
I'm new to linux and would like to start programming in java. On windows i had the JDK libraries and used Jcreator as an editor. If someone can show me what to download or link me to some tutorials i would greatly appreciate. Thanks.

---

### Post by Tomosaur on 2007-01-28
This is more suited to the [programming forum](http://www.ubuntuforums.org/forumdisplay.php?f=39), but Sun's JDK is also available on Linux. Here is the [main Java page](http://java.sun.com/javase/downloads/index.jsp). Choose which JDK variant you want, and then select the .bin file for Linux. The RPM will not work, since that is for Red Hat Linux. You may be able to use alien to convert the .rpm to the correct format, but it's probably just easier to download .bin file.

You should also read the instructions on how to install it if you are unfamiliar with Linux.

---

### Post by gidra on 2007-01-28
And one i've managed to do that how do i start coding and compiling ? Is there anything close to Jcreator or Netbeans on linux ?

---

### Post by Tomosaur on 2007-01-28
Yup, netbeans is available from Sun's website too. It's one of the packages available on the page I linked to, in fact. You code and compile pretty much the same way you would in Windows. You can use a text editor to write your code in, or use an IDE like Netbeans or Eclipse if you prefer those. The IDE will generally allow you to compile by pressing a button in the menu or something. If, however, you use a text editor like gedit, which doesn't have a compile button (although some do, and many are able to be configured to allow it), then you'll need to compile via the command line, like this:

```

javac ./myJavaFile.java

```

I'm not sure about JCreator, I've never used it myself, but a great IDE which I do use is called JEdit - here's the [website](http://www.jedit.org/). Like Eclipse, it is not limited to Java, you can write in pretty much any language you want and it will provide all the features it has when you're writing in Java, such as an integrated terminal, compilation, syntax highlighting, class browsing etc etc etc.

---

### Post by gidra on 2007-01-28
Great info Tomosaur. Thanks a lot, right now i'm a bit busy doing an assignment but i'll give it a try when i'm finished. Cheers :D

---

### Post by aktiwers on 2007-01-28
Eclipse is also available for Linux

---

### Post by phossal on 2007-01-30
Packages for Java JDK6 (needed for eclipse) and eclipse are available in the repositories now. However, I don't use them. My sig includes a link to a tutorial for installing Java directly from SUN, if you don't want the packages.

---

### Post by IYY on 2007-01-30
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_Development_Kit_.28JDK.29_v5.0](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_Development_Kit_.28JDK.29_v5.0)

---

### Post by randomnumber on 2007-01-30
I like eclipse. I think that you should know how to compile and write code with out it. This knowledge helps. 

in terminal

java - run prgm
javac  - compile
java -jar run jar file

Also I use Big Java by Horstman. I like it. The second edition updates to the changes of 1.5, the first only goes to 1.4. There are significant differences.

I also use DATA STRUCTURES AND ALGOITHMS IN JAVA by Drozdek. It seems to be a good book. Data structures are important.

Good Luck

---

