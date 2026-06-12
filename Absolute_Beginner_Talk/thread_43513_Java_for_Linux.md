---
title: "Java for Linux"
date: 2005-06-22
forum: Absolute Beginner Talk
---

### Post by Trojan1313 on 2005-06-22
Now, I think I got the Java SDK through Synaptic. But how do I use it to compile (or interpret, not sure what it's called with Java) my pieces of codes? Can I just use gedit for any Coding needs?

---

### Post by Wombley on 2005-06-22
[QUOTE=Trojan1313]Now, I think I got the Java SDK through Synaptic. But how do I use it to compile (or interpret, not sure what it's called with Java) my pieces of codes? Can I just use gedit for any Coding needs?[/QUOTE]

Any text editor, including gedit, will work to edit Java files. Once saved, gedit will give syntax highlighting to the files too. The command to compile a java file from a terminal  (Applications->System Tools->Terminal) is:

javac foo.java

To run the created file:

java foo

---

### Post by Trojan1313 on 2005-06-22
[QUOTE=Wombley]Any text editor, including gedit, will work to edit Java files. Once saved, gedit will give syntax highlighting to the files too. The command to compile a java file from a terminal  (Applications->System Tools->Terminal) is:

javac foo.java

To run the created file:

java foo[/QUOTE]
 Where foo is the filename?
So "file.java" in /home/mydir/ would be compiled with:
javac /home/mydir/file.java
and then run with
java /home/mydir/file

Right?

---

### Post by Wombley on 2005-06-22
[QUOTE=Trojan1313]Where foo is the filename?
So "file.java" in /home/mydir/ would be compiled with:
javac /home/mydir/file.java
and then run with
java /home/mydir/file

Right?[/QUOTE]

Yes, all that is right - javac creates a .class file which contains the code compiled for the virtual machine. Java then runs this file when you type java filename (minus the .class ending for some reason...).

---

### Post by Kvark on 2005-06-23
Can gedit run the code you type in it?

For example with another editor called textpad if you hit Ctrl+2 while having a .java file in focus it complies and launches it as application. And if you hit Ctrl+3 it launches it in an applet viewer. Any way to do shortcuts like that with gedit?

---

### Post by N'Jal on 2005-06-23
I don't think so, i think gedit IS just a text editor. Have you tryed Sun's netbean's or borlands JBuilder? They seem good, and have the functionallity your looking for, if a little confusing if like me you don't know what your doing.

---

### Post by Wombley on 2005-06-23
[QUOTE=N'Jal]I don't think so, i think gedit IS just a text editor. Have you tryed Sun's netbean's or borlands JBuilder? They seem good, and have the functionallity your looking for, if a little confusing if like me you don't know what your doing.[/QUOTE]

Closest thing in gedit I think is Run Command - it's a plugin, and allows you to run a command from the tools menu. To enable:

Edit->Preferences->Plugins, check "Shell Command"

To use:

Tools->Run Command, fill in options,  (eg "javac foo.java && java foo" to compile and run). Special codes you can use are %f for the current document filename with path and %n for the filename without the path (see the help)

I agree that you're probably better off with a different text editor for serious programming, one IDE that wasnt mentioned above is [Eclipse](http://www.eclipse.org/). Some plain text editors probably have the functions you mention as well - I believe [JEdit](http://www.jedit.org/) is used extensively for java development, and seems to be a very advanced text editor.

---

