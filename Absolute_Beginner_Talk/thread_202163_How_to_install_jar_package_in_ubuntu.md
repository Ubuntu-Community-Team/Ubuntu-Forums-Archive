---
title: "How to install jar package in ubuntu?"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by pigmario on 2006-06-22
I download files from [http://panda-igs.joyjoy.net/java/gGo/](http://panda-igs.joyjoy.net/java/gGo/) in jar format which is platform independent and i also install jre 1.5 and jdk 1.5 from sun website but
i can't figure out how to install this package any help would be appreciate.:)

---

### Post by scxtt on 2006-06-22
i don't think you install them, i think you run them from the command line, something like:
[indent]$:> <java_binary> java_file.jar[/indent]but i don't know what the <java_binary> would be by name ... try typing "j" into the terminal and hitting tab, then see what your options are, could be as simple as "$:> java java_file.jar" ...

or i could be wrong entirely ... :p

---

### Post by pigmario on 2006-06-23
I try this and it get this error
> 
pigmario@Sephiroth:~/Download$ java gGo-1.0.jar
Exception in thread "main" java.lang.NoClassDefFoundError: gGo-1/0/jar
pigmario@Sephiroth:~/Download$

and i also try this
> 
pigmario@Sephiroth:~/Download$ java_vm gGo-1.0.jar
java_vm process: You need to set both JAVA_HOME and PLUGIN_HOME

 what should I do next ??

---

### Post by scxtt on 2006-06-23
hmm, if you're using bash, give this a try:
[indent]$:> JAVA_HOME=<directory where java_vm is>; export JAVA_HOME[/indent]
[indent]$:> PLUGIN_HOME=<directory where java plugins are>; export PLUGINS_HOME[/indent]that'll create the variables, but i don't know if it'll help ...

---

### Post by woot on 2006-06-23
[http://panda-igs.joyjoy.net/java/gGo/](http://panda-igs.joyjoy.net/java/gGo/)
java -jar yourfile.jar is de correct syntax if im not mistaken

and its right there on their site.....why dont you look there?

Linux
Unpack the .tar.gz installer somewhere and run gGo.install. Start the JAR installer with java -jar ggo-1.0.jar or install the RPM with rpm -i ggo-1.0.rpm.
If you use the .jar installer, you should copy [ggo-path]/bin/ggo to some directory in your PATH, like $HOME/bin or /usr/local/bin, then you can start gGo with ggo.
The RPM and tar.gz installers are started with ggo as well. No need to copy scripts with both, everything in place already.
Basically it makes no difference which of the installers you use for Linux, except the JAR installer does not require root privileges, if this is of concern for you. The installed Java files are exactly the same.

---

### Post by Mega Man X on 2006-06-23
Hi!

What do you get when you type "java -version" on the terminal? The correct way to run a jar file is:

java -jar <jar_file_name.jar>

---

