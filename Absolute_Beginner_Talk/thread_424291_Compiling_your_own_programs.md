---
title: "Compiling your own programs?"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by Xarok on 2007-04-26
The only program I've ever compiled was a C "hello world", acctually I think I had a problem with the compiler and it never aactually compiled (this was on Mac OS 10.3).

Occationally I will see linux programs that require the user to complie their own programs. I have no idea how to do this, and know nothing about it.  

What's the purpose of compiling programs yourself?
What issues will I run into?
How well will it integrate with the system? 
How easily can I uninstall it?
How is it done?

(currently using Fiesty on PPC and Drapper Server on i386)

Any information is helpful! Thanks!

---

### Post by Cypher on 2007-04-26
> **Xarok said:**
> The only program I've ever compiled was a C "hello world", acctually I think I had a problem with the compiler and it never aactually compiled (this was on Mac OS 10.3).

Occationally I will see linux programs that require the user to complie their own programs. I have no idea how to do this, and know nothing about it.  

What's the purpose of compiling programs yourself?
What issues will I run into?
How well will it integrate with the system? 
How easily can I uninstall it?
How is it done?

(currently using Fiesty on PPC and Drapper Server on i386)

Any information is helpful! Thanks!

Purpose) If you were to compile a program on your computer, then it will be customized to the libraries and other facilities on your computer. Also, you can control what features of a program you want enabled/disabled which might improve overall performance.

Issue) Depending on the software's maturity, either it will just compile fine with "./configure; make; make install" or give you many screens of errors

Integration) The traditional method was always to compile the program and then copy the resulting binaries to "/usr/local". The issue here is that the nice DPKG and other package management tools don't know about it. You can also, however, create a .DEB file after compilation and install it using DPKG and that will integrate better.

Uninstall) If you go the .DEB route and DPKG, then uninstallation is as easy as "dpkg --remove <package>". If you go the manual route, then you have to delete all the files yourself (granted that you remember WHICH files go with which package)

Done) You would need to first do "sudo apt-get install build-essential" and then download the .TAR.GZ for the sources. Uncompress the sources, and run "./configure" to create the Makefile. Then "make" to build the package.

---

### Post by Happy_Man on 2007-04-26
The purpose of compiling programs is to get an application that has not been packaged especially for your system, like a .deb. The only real issues you will run into are getting the right dependencies (programs the program you're compiling needs to run properly). Any program will "integrate," but beware, YMMV. If you use "checkinstall", the source will be compiled into a .deb, making uninstalling as easy as rooting around in Synaptic for it (yes it will be there). If you're still interested, stick this code into a terminal to get full compiling capabilities:
```
sudo apt-get install build-essential checkinstall
```

To actually compile something, download the source .tar.gz to your home directory and extract it there. After, open up a terminal and type this ONE LINE AT A TIME:

```
cd <name_of_directory_that_was_just_created>
./configure
make
sudo checkinstall

```

Basically what that does is put you into the directory where the source code is and run a configure script to make sure everything works, that you have all your dependencies, etc. It will tell you if you need any dependencies to be installed before you can compile. If everything's all right, you run "make." That basically means compiling. "sudo checkinstall" makes the compiled file into a .deb, stores that .deb in the source directory, and then installs it. Hope this (mini) novel helps!

---

### Post by Cypher on 2007-04-26
AHA Checkinstall, that was the last piece I was trying to remember..and I actually played with it and it's VERY cool..

---

### Post by Xarok on 2007-04-26
Thank you so much guys!

> **Happy_Man said:**
> 

To actually compile something, download the source .tar.gz to your home directory and extract it there. After, open up a terminal and type this ONE LINE AT A TIME:

```
cd <name_of_directory_that_was_just_created>
./configure
make
sudo checkinstall

```

Basically what that does is put you into the directory where the source code is and run a configure script to make sure everything works, that you have all your dependencies, etc. It will tell you if you need any dependencies to be installed before you can compile. If everything's all right, you run "make." That basically means compiling. "sudo checkinstall" makes the compiled file into a .deb, stores that .deb in the source directory, and then installs it. Hope this (mini) novel helps!

So it will know what to configure in the source directory? I don't have to type something like
```
./configure <source_file>
```

I assume that if I'm compiling with Linux on PPC I will need to download the correct source for my architecture right? 

I know WINE won't run on PPC Linux.  Are there a lot of linux programs that don't run on PPC?

---

### Post by Happy_Man on 2007-04-26
Right, if there's a configure script, it will run. If not, run ./autogen.sh in place of ./configure. And no, compiling means making the source code in such a way that is customized to your architecture.

---

### Post by KIAaze on 2007-04-26
> **Happy_Man said:**
>  "sudo checkinstall" makes the compiled file into a .deb, stores that .deb in the source directory, and then installs it. Hope this (mini) novel helps!

Now that is very interesting. :)

But just to be sure:
Is the generated .deb usable on any other computers with a Debian based distro? i.e: Is it equivalent to the usual.deb packages found on the web?

If not, is there an easy program to create .deb packages?
(the tar.gz already being automatically created by most IDEs)

---

### Post by Cypher on 2007-04-26
Yes, you could transport the checkinstall generated .DEB file to another similar  Debian/Ubuntu machine and have it install. You'd have to be careful of architecture and other dependencies though..

---

### Post by Xarok on 2007-04-26
> **Happy_Man said:**
> compiling means making the source code in such a way that is customized to your architecture.

So if I downloaded the source to — for example — VLC, I could use that same source to compile it on any OS and any architecture and it would work?

---

### Post by Cypher on 2007-04-26
Right..that's the beauty of source..:)

---

### Post by Happy_Man on 2007-04-26
Yes. A .deb is a .deb wherever you go.

EDIT: I have to read the rest of the thread before posting more often, methinks.

---

