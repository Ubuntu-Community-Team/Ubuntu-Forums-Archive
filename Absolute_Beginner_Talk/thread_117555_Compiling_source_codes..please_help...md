---
title: "Compiling source codes..please help.."
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by madu on 2006-01-15
Hi guys...

I'm a newbie so please be patient.. :???: 
I'm running the amd64 version so seems lot of programs are not being able to run properly. I was told that I can use an 32-bit emulater or compile the source code. Now    from my understand I can use the emulater if there is no source code. But if the source code is available, then I can make it to run on the am64 platform.. right?

Anyway, I have no idea how this should be done.. I know what compiling is, from a programming perspective, but not in a program installation perspective.
From my knowledge in these two days i've been experimmenting with Ubuntu, I need to do something like*** ./configure... make... make install..***.

But guys I need to know what exactly i am doing and I need to do.. I searched some basic guodes but none of em had this issue described.

So if somebody can spare a couple of minutes from their time for me, I would like to know the following things.. Thanks in advance...

1) After I downladed the source file, what is the next step?
2) What does ./configure, make and make install do exactly? From programming I know compiling is converting the code to machine language.. that is to a binary file.. So I'm guessing that *make* convers the source code to binary code, and *make install* install the binary file.. am i right guys?
3) What are the things I should specify during these processes? Suppose I download a movie application to desktop and make install in the same directory. But that program should be in Applications->Sound and Video... Do I need to specify anything for it to apper in Sound and Video?
If I make install in the same folder, is it going to be installed in the same folder..? I've been using Windows all these time so I'm still thinking from Windows way.. please correct me..

I really would like to know whats happening when I'm doing something rather than just typing make and make install.. If you guys know a good link, please let me know..
Thanks a bunch guys..!!!

---

### Post by Sef on 2006-01-15
Before compiling from source, you need to download the following, so you can install from source:

build-essential --from the terminal ----> sudo apt-get install build-essential

---

### Post by madu on 2006-01-15
Hi..
yes.. i already downloaded it...
I downloaded and installed couple of applications but I did them looking at postings..
Now I'm interesting in knowin what I actually did..lol..
Thanks for the replies guys...!!!

---

### Post by public_void on 2006-01-15
tar -xvzf [location e.g. /home/username]/FileName.tar.gz (Unpacks the file into a new directory called FileName. (If you put tar --help, you can find what each letter does x, v, z and f.))
cd /FileName (change directory to the new directory)
./configure (configure the install, Note: this is where you could get warnings and messages about missing files and dependencies)
make (compiles the program)
sudo make install (installs it)

If you wnat to be really clever (well not really, but) you can go 
make; sudo make install; cd ..
This complies the program, installs it and cd directory to the previous one in one line, its by putting a ; between commands allows mutliple commands to be carried out with one line.

---

### Post by madu on 2006-01-15
AAh...
Ok... now i see...
Thanks for the reply guys..!!!  :KS

---

### Post by mo_x on 2006-01-15
For most programs it is not necessary to compile them yourself. You can install them with apt-get or synaptic. Did you enable repositories in /etc/apt/sources.list?

---

### Post by madu on 2006-01-15
YEs..
I have enabled the repositories..
Does synaptic does the compiling of source codes?
Can I download a source code and get Synaptic to compile and install for me?

Thanks guys..!!

---

### Post by mo_x on 2006-01-15
Synaptic installs precompiled binaries. What program(s) do you want to install?

---

### Post by Lazy_8ght on 2008-01-07
YES! :D
 Now this is helpful. I've been googling for something like this, now i've found it. 
Thanks on behalf of everyone out there like me.) :P

---

### Post by ByteJuggler on 2008-01-07
> **madu said:**
> 
1) After I downladed the source file, what is the next step?

Source normally comes in an archive (typically a so-called "tarball" or tar.gz archive.)  You normally extract it to a suitable folder.

> **madu said:**
> 
2) What does ./configure, make and make install do exactly? From programming I know compiling is converting the code to machine language.. that is to a binary file.. So I'm guessing that *make* convers the source code to binary code, and *make install* install the binary file.. am i right guys?


./configure creakes a "makefile" file with appropriate configuration options based on your exact system configuration.  

make runs the "make" program with the default make "target" (paramter) "all."  It uses a "makefile" which is a script that defines what to compile and where to.  "Make" is used to automate complicated builds, and to prevent needlessly recompiling stuff that's already been compiled but not changed if repeatedly recompiling a project (such as during development.)

make install again runs the "make" program with the target "install".  By convention, the "install" target usually has commands attached that copies the compiled program binary file to the /usr/bin folder or something similar to that so that the program can be used on the system and is thus "installed".

> **madu said:**
> 
3) What are the things I should specify during these processes? Suppose I download a movie application to desktop and make install in the same directory. But that program should be in Applications->Sound and Video... Do I need to specify anything for it to apper in Sound and Video?
If I make install in the same folder, is it going to be installed in the same folder..? I've been using Windows all these time so I'm still thinking from Windows way.. please correct me..

Usually "make install" will not cause a program to appear in your system menu's.  This is because you can make far fewer assumptions about what might be where when compiling/installing from source, since your source may be compiled on anything from SGI workstations and IBM mainframes to any of the myriad of different Linux distro's to BSD Unixes.  And almost all of them will have differing menu conventions (if they even have a GUI at all.)  So, the moral of the story is, if you install from source you're likely going to have to make your own shortcut (launcher) in the menu yourself.  Fortunately that's relatively easy.

Of course, if it's a popular package that's not yet in the Ubuntu repositories, then you can become the one to compile the program from source, create a shortcut for it, and then to create a .deb package that can then be put into a repository for others to install with Synaptic, complete with a menu entry, specifically for Ubuntu. :-)

---

### Post by hyper_ch on 2008-01-07
> **ByteJuggler said:**
> Usually "make install" will not cause a program to appear in your system menu's.
I tend to think that's wrong. If it's not a gui program it will not appear in the system menu. However Linux has a unified file system hierarchie and there is one folder where all the "menu program files" go to. If the make install has that file, it will appear in the according category... (or something like that)

---

### Post by ByteJuggler on 2008-01-07
> **hyper_ch said:**
> I tend to think that's wrong. If it's not a gui program it will not appear in the system menu. However Linux has a unified file system hierarchie and there is one folder where all the "menu program files" go to. If the make install has that file, it will appear in the according category... (or something like that)

Yes thats true if and only if the source code is specifically targetted at Linux (and possibly/probably with a particular desktop. ) Not all Linux's use the exact same hierarchy and or deskop windowing system, and as I mentioned, there's many many other Unix's as well (AIX, HPUX, IRIX, BSD's etc. etc)  Source code that you download from out of the wild is generally targetted to a generic Unix'ish environment, where you cannot make assumptions about menu's and a GUI is usually not even a given.   There may be exceptions, but don't go thinking you can download any tarball from the internet and expect it to install an icon on your menu's for you in general.  It may, but in the large majority of cases I'd bet it will not.

---

### Post by hyper_ch on 2008-01-07
> **ByteJuggler said:**
> Yes thats true if and only if the source code is specifically targetted at Linux (and possibly/probably with a particular desktop. ) Not all Linux's use the exact same hierarchy and or deskop windowing system, and as I mentioned, there's many many other Unix's as well (AIX, HPUX, IRIX, BSD's etc. etc)  Source code that you download from out of the wild is generally targetted to a generic Unix'ish environment, where you cannot make assumptions about menu's and a GUI is usually not even a given.   There may be exceptions, but don't go thinking you can download any tarball from the internet and expect it to install an icon on your menu's for you in general.  It may, but in the large majority of cases I'd bet it will not.

Ok, I did not consider other *nix

P.S.: Nice signature ;)

---

### Post by ByteJuggler on 2008-01-07
> **hyper_ch said:**
> 
P.S.: Nice signature ;)

;)  I suddenly feel an urge to put a comment about Linx being like a wigwam in my sig... :P

---

### Post by erginemr on 2008-01-07
> **Lazy_8ght said:**
> YES! :D
 Now this is helpful. I've been googling for something like this, now i've found it. 
Thanks on behalf of everyone out there like me.) :P

You may also read the following tutorial for more insight to compiling from source:

[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

---

### Post by battlesound on 2008-01-10
> **erginemr said:**
> You may also read the following tutorial for more insight to compiling from source:

[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

Nice... I just looked at the same page a few seconds before seeing your post and following your link... very good!!  I found it through stumble upon, and I have to reglance at it every now and then.  :lolflag:

I'm just trying to figure out the install from source where you make a deb and it's added in the synaptic package list (not adding a repo, though).  I saw it somewhere, anyway.

---

### Post by erginemr on 2008-01-10
> **battlesound said:**
> Nice... I just looked at the same page a few seconds before seeing your post and following your link... very good!!  I found it through stumble upon, and I have to reglance at it every now and then.  :lolflag:

I'm just trying to figure out the install from source where you make a deb and it's added in the synaptic package list (not adding a repo, though).  I saw it somewhere, anyway.

Then, you need to look at "checkinstall". It allows you to create a Debian package during the source code installation, which you can re-use later on, and also inserts your installation into the apt-get database for an easy uninstallation. In this respect, "checkinstall" does wonders IMHO. The "checkinstall" package should be in the synaptic repositories.

To learn how to use it, please read to the end of the following page:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by battlesound on 2008-01-16
Thanks, erginemr.

I found it after about 5 more minutes of searching, and I learned some more details about it.  Thanks for your info, for sure.  It all helps.  Cool.

---

