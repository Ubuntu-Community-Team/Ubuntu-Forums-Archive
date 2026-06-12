---
title: "Where do I put files I want to compile"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by Dance Commander on 2006-04-01
This is my first post and my first month of using Ubuntu.  I would first like to say that Ubuntu (5.10) has been great to me as well as these forums.

My question:  When I download source code where should I put these files? After I "make" and "make install" a file, where does the program go?

Many of the readme's and instructions usually do not tell me these types of trivial instructions and I'm a little lost.  I just finished downloading, compiling, and installing an application called ImageMagik.  Everything went well, but I'm not sure if everything is in the right place.

What is the usual procedure that most people use for downloading, compiling, etc. applications.  I prefer using the Package Manager but it isn't always possible.

Thanks! :) sorry if this is such a silly question

---

### Post by ComplexNumber on 2006-04-01
> When I download source code where should I put these files?
i usually put mine in my home directory in a folder such as  'KDE-sources' or 'Gnome-sources'

> 
After I "make" and "make install" a file, where does the program go?
before you 'make', you will usually have to run the 'configure' script by typing in './configure'. by default, they will go into /usr/local after you've installed it...unless specificed otherwise. to speficy otherwise, use './configure --prefix=<other directory>' (for example,  './configure --prefix=/usr'. generally, its best not install programs in /usr because its best to seperate the programs which are installed via deb/rpm via a packagae manager and the programs installed from source (thats my way of seeing things anyway). type in './configure --help' for miore information.

---

### Post by Dance Commander on 2006-04-02
Okay, I've already installed the application and I know it works.  If I want to take your advice and re-install it.... how would I do so?  I guess the new question is:  how do I uninstall an application?

Thanks for responding.  :)

---

### Post by xenmax on 2006-04-02
I think you can just move your executable to where you want it. I don;t think where it is located matters from perspective of its usability, except that it would probable be helpful if place where you move it to is included in your PATH var. I think this is because exec file is created in location where perform "make install" and a copy is just placed in dir pointed by --prefix/--exec-prefix.

Somebody plz correct me if this assesment is wrong?

---

### Post by belikralj on 2006-04-02
I just started to learn to program in Linux and have started to learn how to make "make" files. Though I don't have a clue about installs if you use make to make a program you usually just get "make" to execute a code from a file with the filename "makefile" or what ever you type in after make, which in your first post I would assume would be the "install" so if you are wondering where it all goes go into the directory in which you were when you used the make directive or the one you saved the original file in and open the makefile with a text editor. There will be a bunch of compiler directives and ammong all the code should be your folders to which you save the files to including the uninstall directives.

I think I'm right, but again I just started my self and so I don't really know for certain this is how it is, how ever it may be worth checking out.

Hope this helps!  :-k

---

### Post by Dance Commander on 2006-04-02
Thank you for all of your replies.  :-D 
I'm still a little nervous about all of this stuff, but a little more confident now.  

Does anyone know if there is a Wiki or Howto on compiling/install/uninstalling programs on to Breezy? (total beginner style).  Covering topics on how to add the new app. to the menu bar, etc.  

Does anyone recommend a book that would cover an intro to doing these things, such as Linux for Dummies?

---

### Post by Sutekh on 2006-04-02
- Try this link for installing software

[Psychocats.net -  Installing Software in Ubuntu](http://www.psychocats.net/ubuntu/installingsoftware.php)

 - It covers installing software through various means, ranging from very easy (Synaptic) to quite involved and difficult (compiling from source)

 - Also these Ubuntu Wiki links

[Ubuntu Wiki - Software - Installing and Running Software](https://wiki.ubuntu.com/UserDocumentation#head-57224fc8a4bfcbe0286245ae95b4f4c7ebb4c4ef)

[Ubuntu Wiki - Synaptic HOWTO](https://wiki.ubuntu.com/SynapticHowto)


 - As for adding an entry to the menu its very easy.  Open up the Menu Editor (from the Applications -> System Tools menu).  

 - When you create a new entry most of the fields are descriptive and up to you what goes in them.  The important one is the command field.  If the application is installed properly, all that needs be in there is the name of application.  

 - Use the Menu Editor to view the properties for some other programs so you can get a feel for what's required.

---

### Post by 3rdalbum on 2006-04-03
To uninstall a program, open a terminal and navigate to the directory which contains the Makefile. Type:

```

sudo make uninstall
sudo make clean

```

The first command uninstalls, the second command removes the source files.

---

### Post by Dance Commander on 2006-04-03
Thank you, Sutekh!  Then link to Psychocats.net was quite good.  I really don't need tutorials on the Synaptic stuff, but was looking for the more advanced stuff.  I really like it when people explain what things mean when they are writing the tutorial.  Ex.  I finally found out what "sudo" means.... "switch user do" or "super user do."  Sounds silly but it makes more sense to me this way and is easier to remember.  

Ubuntu has made Linux so easy for everyone and still has all the advanced features of any OS.  I think I have a pretty good grip on the basics (except for the meaning of many commands like the "sudo" example).  I wish installing things were ALL as easy as Synaptic.  I have Multiverse and Universe installed as well but I still need to complie some apps for a server I am trying to build.  Ubuntu has definately made my life easier!

---

