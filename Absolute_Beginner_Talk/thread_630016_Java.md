---
title: "Java"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by OlyPerson on 2007-12-02
So I want to learn to program in Java, but I don't understand:
1) what I need to install to do stuff
2) how I get to it once I've installed it
3) what I do once it's installed (what and where I save the file as
4) this isn't really with the other ones, but how I view the source of already made Java programs.

Thanks!

PS: Firefox keeps randomly closing without warning, what's up with that?

---

### Post by bwald on 2007-12-02
To answer all of your questions:

1. I'm pretty sure Ubuntu comes with all the programs you need.

2. Same for this one, they should already be in your $PATH, but if not just reply to this post and I'll explain how to add them.

3. As for this part, this is a bit more complicated.  [_Wikipedia's article on java_]("http://en.wikipedia.org/wiki/Java_%28programming_language%29") is very comprehensive and explains the basics of the Java language.  When you create java files, you save them with the file extension ".java".  It doesn't matter where you save them, but for cleanliness you might want to create a folder ~/java_files or something so you don't clutter up your home directory.  To compile the code, run 

```
javac foo.java
```

where "foo.java" is the name of your source code.  This will produce another file called "foo.class" which is the "byte code" from your source code.  To run the byte code, run

```
java foo
```

4. To view your (or any) source code, just look at the "foo.java" file.  You can either do this from the command line with any editor, such as gedit.  (If you're interested in doing a lot of programming I'd suggest learning to use the vim editor, but thats a task all to itself)

```
gedit foo.java
```

---

### Post by PeterJS on 2007-12-02
> **OlyPerson said:**
> So I want to learn to program in Java, but I don't understand:
1) what I need to install to do stuff

You need the sun-java6-jdk (or 5 if you so choose).
> 
2) how I get to it once I've installed it
As mentioned above, and this goes for all software, everything under linux, especially Ubuntu, is on the path, so finding it really isn't that important.
> 
3) what I do once it's installed (what and where I save the file as)
Java's non too picky about file names and locations, as long as the complete directory structure for a given program matches it's package structure, and the file names match the class names. For basic programs all the classes will most likely be in one un-named package, so just having everything in one directory will work.

If you're going to be learning java, I would suggest using the Eclipse IDE, it takes care of bunch of things automatically for you, like setting up the right directories, compiling and running debug programs, and includes a bunch of builtin java documentation, such as which library packages have which classes so you're not constantly looking up builtin classes, basic code completion, and will highlight errors and warnings in real time as you program and explain the error.

> 
4) this isn't really with the other ones, but how I view the source of already made Java programs.
Well that depends. JAR archives are just zip files with a defined organization and some extra meta data, so you can open the jar with the zip manager of your choice, and the code will either be there or not. If it's not included in the archive there's not much you can do.

Thanks!

PS: Firefox keeps randomly closing without warning, what's up with that?[/quote]

---

### Post by OlyPerson on 2007-12-02
Thanks, that mostly worked.  However, when I moved the file or even saved the file anywhere but my home directory it said:
 javac: file not found: Foo.java
Usage: javac <options> <source files>
use -help for a list of possible options
What happened?

And also, is running it in the CL the best and/or only place to work with compiling and the likes?

---

### Post by PeterJS on 2007-12-02
As I mentioned the Eclipse IDE will handle comping and all that fun stuff.

The reason that it only works when the files are in you home directory is because you are running javac from your home directory and by default javac only looks in the system libraries and the current directory. If you run javac from a different directory with your source files in it, it will work again.

---

### Post by OlyPerson on 2007-12-03
And I switch dir. by
 ```
cd /paul/java_files
```
right?
Sorry, I'm still getting used to this whole system.

And I got Eclipse, is it easy to use?

---

### Post by bwald on 2007-12-03
Yes, thats the general idea, but your location is wrong.  Home directories (i.e. the directory where you will/should save all you personal files) are located at:

/home/[user name]

So if you wanted to move from, say, your home directory to a subfolder in your home directory called "java_files" you would type the following:

```
cd /home/[user name]/java_files
```

There are all kinds of shortcuts and things to make this easier.  In my example, I specified the "full path" of the folder "java_files."  In other words, I described it from the root folder, from /, you can also use a file's "relative path" which locates it relative to where you are currently.  For example:

Lets say I'm in the location /home/bwald/java_files/program1/source and I want to go to /home/bwald/java_files/program2, I can use either of the following commands:

"absolute path"
```
cd /home/bwald/java_files/program2
```

"relative path"
```
cd ../../program2
```

the "../" just means "go up one directory," so the relative path one is saying "go up two directories and then down into the directory "program2."  

Hope that helps.

---

### Post by oni5115 on 2007-12-16
I'm also new to Java programming in Linux, so I thought I'd ask a question that would be quite helpful to anyone starting out.   

I installed sun-java6-demo and sun-java6-doc, but I have no clue where it decided to store the demos/source code and API documentation.  Where did it go?  :confused:

In windows I just used Textpad (could do text highlighting and supported compiling).  I think I will take a look at eclipse too to see if I liked that.

---

### Post by The Cog on 2007-12-16
Open synaptic, find the package sun-java6-demo, right-click it, select Properties, and you should see a tab for installed files. 

I would like to recommend these two resources to anyone learning java:
The Java Tutorial: [http://java.sun.com/docs/books/tutorial/](http://java.sun.com/docs/books/tutorial/)
BlueJ IDE: [http://www.bluej.org](http://www.bluej.org)

BlueJ is an interesting IDE that I think really helps with understand object-oriented ideas. I just wish they'd sort out the truly awful editor fonts.

---

### Post by staticvoid on 2007-12-16
[geany]("http://geany.uvena.de/") is good. simple and straight forward

make sure you install ubuntu-restricted-extras and sun-java6-jdk

sv

---

### Post by oni5115 on 2007-12-22
Thanks for the help, found the demos and docs.  So far I like Geanie too, seems to be a bit more than I had with Textpad, without being too confusing like Eclipse was (of course... the documentation of Eclipse not working didn't help any :lolflag:)

Thanks for the recommendations and the help.

---

