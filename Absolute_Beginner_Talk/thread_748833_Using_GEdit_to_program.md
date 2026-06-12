---
title: "Using GEdit to program"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by UFRaymond on 2008-04-07
Hello fellow forum-goers,

I'm looking to use GEdit to program in Java, C, C++, and C#.  Yes, I've visited[HowTo: Program using GEdit]("http://ubuntuforums.org/showthread.php?t=453732") , but that only goes into the design and colors to prevent bugs.

I want to know how to use GEdit to compile all of said programming languages and run them without any errors.

**Note:** I have no experience using the command-line [terminal] in Linux, or for that matter any other type of Unix.

//  Edit  //  Let's just say I'm using *only* c++, could someone please explain how to compile a c++ code from the terminal if it was made on GEdit?  Note, I just typed:
```
sudo apt-get install build-essential
```

I downloaded all packages offered by this prompt.

Thanks,
Ray

---

### Post by Vadi on 2008-04-07
Compiling something is language dependant. Some languages don't even require compilation (interpreted ones).

Since compiling is different for languages, you should check out how to do it for a specific one... but the ones I know, to compile a java app you do **java source.java**, to compile C you do **gcc code.c**, and C++ is **g++ code.cpp**. C# I don't know.

---

### Post by fluffman86 on 2008-04-07
gedit does not compile for you.  You have to do that via the terminal.  

For java, it's just like you would compile in windows.  First download the java packages you need using add/remove programs or synaptic.  Then, using a terminal, cd to the directory that your .java files are in...just like in Windows.  If the folder with your java files is called "program" and it's on the desktop, then type "cd ~/Desktop/program" then compile by typing "javac MainProgram.java"

For other languages, download the build-essential package.  Again, you can do this through synaptic (System > Administration > Synaptic Package Manager) or you can type "sudo apt-get install build-essential" from the terminal.  This should install your C and C++ compilers.  You can use the command "gcc" in the terminal to compile a C program, similar to how you would do it in Windows.

Hope that helps!

---

### Post by SOULRiDER on 2008-04-07
Remember Gedit is just a text editor. What you probably should be using is an IDE and not Gedit.

---

### Post by Inxsible on 2008-04-07
If you don't want to use the command line, you may want to look into IDE's

The one that I like most is Eclipse and its a great tool for incremental builds and with plugins, it also supports other languages. I use plugins for Ruby, Scala and a host of JEE technologies. Eclipse also has a version for C/C++

If Eclipse isn't something you like then there are other IDE's like Anjuta, NetBeans etc

---

### Post by fluffman86 on 2008-04-07
as Vadi said, to compile a C++ code, first save the code that you typed in Gedit to somewhwere on your hard drive, like your home/raymond/code/seepluscode.cpp

to compile, first change to the directory of the code in terminal:
```
cd home/raymond/code/
```

then compile with g++
```
g++ seepluscode.cpp
```

That will create a file called a.out.  To run your c++ program, stay in your current directory and type:
```
./a.out
```

(That's (dot)(slash)a(dot)out, incase you can't see the dots there...it's a little difficult on my laptop...)

---

### Post by SOULRiDER on 2008-04-08
> **Inxsible said:**
> If you don't want to use the command line, you may want to look into IDE's

The one that I like most is Eclipse and its a great tool for incremental builds and with plugins, it also supports other languages. I use plugins for Ruby, Scala and a host of JEE technologies. Eclipse also has a version for C/C++

If Eclipse isn't something you like then there are other IDE's like Anjuta, NetBeans etc

I also agree on using Eclipse. I actually really like EasyEclipse which is an Eclipse distribution. Check it out at [http://easyeclipse.org](http://easyeclipse.org)

---

