---
title: "Development tools for Ubuntu"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by jonl on 2008-03-30
Hi

I'm pretty new to Ubuntu and Linux, but I find the philosophy very interesting. I'm used to create and deploy computersoftware using Borland Developer Studio(c++ mainly) and wonder if there is a ubuntu-equivalent to that tool? 
Also, I used MS SQL to create databases for my database-applications, and I'm in the need for a tool for that as well

I appreciate any help and comment on the subject.

thanx :)

jonl

---

### Post by Michael.Godawski on 2008-03-30
for mysql check out this documentation site
[https://help.ubuntu.com/community/ApacheMySQLPHP?highlight=%28mysql%29](https://help.ubuntu.com/community/ApacheMySQLPHP?highlight=%28mysql%29)

when you open the add/remove application (applications > add/remove) and type mysql into the search filed you get some results, some applications which can organize mysql databases

for c++ try this

[http://www.anjuta.org/features](http://www.anjuta.org/features)

---

### Post by adelahunty on 2008-03-30
Many of the development packages you can get for Linux are in two parts - the compiler / interpreter, and an IDE in which to use it.  This differs from a more Windows approach, in which everything is much more tightly integrated - Visual Studio springs immediately to mind.

With regards to the language compiler / interpreter, your first stating point should be the GCC package, which contains C, C++, and fun little numbers like Fortran (shudder!).  In it's simplest form, you type something up in a text editor of your choice (emacs is common, since it is soooo powerful, and practically an OS in itself!),  and then compile at the command line.  Simple, quick, and since you don't need an X environment to use it, you can run it on minimal equipment and still get good results - I remember setting up a machine solely for compilation at uni which had a Pentium 75, and worked very nicely indeed.

As for a pretty IDE, then still considered by many to be one of the best examples of open source software on the planet is the KDevelop suite for KDE.  Similarly, the Designer which comes with the QT install is pretty darn fine.  If you are into Gnome rather than KDE, take a look at anjuta, but I am not so keen on that personally.  If you're into Java, then either Netbeans (my favourite) or Eclipse are good bets too.

A lot depends on what you want to do.  If C and C++ are your things, then I don't think you're going to get much better pieces of software than those I have listed above.  If you are into other languages, your best bet is probably to have a look through the forums both here and with regard to the language in question, and see what you find.  There's really no space to list everything here - one thing about open source software is that there tends to be a lot of choice... :)

---

