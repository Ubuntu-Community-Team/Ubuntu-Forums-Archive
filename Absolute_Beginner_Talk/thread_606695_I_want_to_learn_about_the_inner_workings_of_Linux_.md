---
title: "I want to learn about the inner workings of Linux as a OS"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by Melhisedek on 2007-11-08
Hello there folks, 
in short I would like to know some basic things about Linux, like where the installed software goes (I have seen some install into my home directory but can't find others for the life of me), what are different folders for, how does it recognizes different file types (I was browsing around in folders and almost no files have any .exe .txt "extensions") I understand files have flags but how do they get set... How come you don't have to reboot after installing drivers and on and on :)

I have 100s of questions and I could perhaps ask them here but I don't want to bother you guys that much ;) So if anyone could point me to some link that explains such things it would :guitar: 

What can I say, thirst for knowledge... overpowers :D

---

### Post by podunk on 2007-11-08
A good place to start on the nuts and bolts is here:
[http://tldp.org/](http://tldp.org/)

For the extensions look here, sort of dry. Generally speaking as you go along on the nuts and bolts you pick up what does what and where it lives. Generally. :-)

[http://www.openoffice.org/dev_docs/source/file_extensions.html](http://www.openoffice.org/dev_docs/source/file_extensions.html)

---

### Post by PmDematagoda on 2007-11-08
I do not know much about the Emblems, but I do know why you don't need to restart Linux after making important changes such as installing software or updating them.

The greatest reason for this is due to the fact that Linux is mainly modular and very little is integrated with each other as is the case with Windows. 

Now modular means that everything is separate, there are little or no interdependencies. This results in the fact that if one part of the OS is damaged or fails, the other parts are affected very little or none at all, so this means that you can keep using Linux and when one part of the system is changed, it itself only needs to be restarted instead of the entire OS, this is also a great reason why Linux is difficult to bring down. 

But this is very usually the case with only the core parts of the system such as the kernel, the Desktop Environment on the other hand such as Gnome or KDE is integrated or monolithic and there are inter-dependencies with the components of it, this usually means that the whole Desktop Environment can be brought down due to a failure in one program or component, but this does not mean that there is a good chance of the Desktop Environment being brought down easily as well since it is modular enough to withstand good "strikes" and that Gnome and KDE are modular enough so that KDE applications can work on Gnome and vice-versa, this also applies to many other Desktop Environments, this is difficult to achieve on Windows since it is so integrated that it is rather difficult to use applications other than those which are native to the OS. 

But keep in mind that this only applies to the Desktop Environment which in actuality lies or works on the kernel and the core parts of the OS, so a failure in the Desktop Environment doesn't mean the core parts of the system are affected and you can still use Linux except that you will only be using the CLI or terminal to use the system instead of the Desktop Environment. 

So basically Linux is like an intricate jig-saw puzzle, you need all the pieces to complete it, but the entire OS will not be affected even if one piece is removed(Except if you remove the kernel of course;)).

---

### Post by bithkits on 2007-11-08
You might want to work through this :D

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

---

### Post by P4man on 2007-11-08
I hear you!

I have migrated to Ubuntu some 6 months ago, but I still feel lost so  often. There is an enormous amount of linux documentation, but precious little general information that is really **usable** for experienced windows users that are new linux and want to understand what it is they are doing when they copy paste commands from how-to's.

For instance, you need to learn to work with a terminal, use  simple commands  like "ls", "cd", etc. You will find plenty of wiki's and man pages going into insane detail of the "ls" command, but very few that give simple, clear answer the basic questions windows converts struggle with.

Howto's on this forum and other places are excellent, but I feel there is a huge gaping hole for those that want to learn and understand more. How do drivers work in Linux ? Its cool to type "modprobe -whatever -silly -switches", and often copy/pasting stuff like that solves my problems, but what does it DO? How do symbolic links work (they seem quire different from windows shorcuts), what does it mean when I type in "./configure", "make" and "make install" (and why sometimes only 2 of those 3, sometimes you have to repeat the "make" command) etc, etc, etc. Hundreds of such questions  have been answered meanwhile, but  I also got thousands of questions like that left.

I'll probably end up buying a book (!) to teach me stuff like that.

---

### Post by Gremlinzzz on 2007-11-08
good site to learn some things
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by sailor2001 on 2007-11-08
places/home folder is like "my documents" For all your folders in there, click ctrl/h

---

### Post by adam.tropics on 2007-11-08
> **bithkits said:**
> You might want to work through this :D

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)


Frightening!

---

### Post by NathanB on 2007-11-08
> **Melhisedek said:**
> Hello there folks, 
in short I would like to know some basic things about Linux, like where the installed software goes (I have seen some install into my home directory but can't find others for the life of me), what are different folders for, how does it recognizes different file types (I was browsing around in folders and almost no files have any .exe .txt "extensions") 

1)  In Synaptic, if you right-click on the package and select "Properties" you can get a list of the files installed and the paths of where each file is stored.

2)  The basic Linux folder layout is like so:

/bin - executables
/boot - bootstrap loader
/dev - system devices
/etc - configuration files
/home - home directories for regular users
/lib - kernel modules, security info, shared libraries
/mnt - mounts of system devices
/proc - virtual file system allocated in memory only
/root - home directory for the root user
/sbin - programs for starting the system; networking
/temp - temporary data storage
/var - for files that often change in size (logfiles)

3)  This will give you more information than you'll want to know about file extensions:

[http://www.wotsit.org/](http://www.wotsit.org/)

---

### Post by NathanB on 2007-11-08
> **P4man said:**
> I hear you!

<<snipped>>

what does it mean when I type in "./configure", "make" and "make install" (and why sometimes only 2 of those 3, sometimes you have to repeat the "make" command) etc, 


When you download and untar a tarball (those "*.tar.gz" type files) of source code, you are choosing to build the application to fit your particular OS and Hardware.  Developers use Autotools to create these packages, and one task is that they create these "configure" script files which interogate your system to determine how to build the application to fit the environment of your computer.  "make" actually does the building of the application.  "make install" moves the app (or, most likely, creates a symlink) to a directory to allow execution of the app from anywhere without you having to provide the entire pathname.

> 
I'll probably end up buying a book (!) to teach me stuff like that.

Not a bad idea!  :)

---

### Post by jaybombalous on 2007-11-08
> **bithkits said:**
> You might want to work through this :D

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)


Just what I was looking for... Guess  I will just make my own LFS starting with a ubuntu base distro. :) Did I ever mention I love linux(freedom of choice)!!!! :)

---

### Post by richiewrt on 2007-11-08
I will go ahead and post this since It took me a long time to figure out and I didn't ever see it mentioned. I was new to linux recently and never knew about the "man" command. Great place to start looking what individual commands do. Brings up the manual for the command.
example:
man bash      brings up the bash manual
man install     brings up info about the install command

works on most any command and a good place to start and a good way to figure out what arguments can be given to a command.

---

### Post by bithkits on 2007-11-09
> **richiewrt said:**
> I will go ahead and post this since It took me a long time to figure out and I didn't ever see it mentioned. I was new to linux recently and never knew about the "man" command. Great place to start looking what individual commands do. Brings up the manual for the command.
example:
man bash      brings up the bash manual
man install     brings up info about the install command

works on most any command and a good place to start and a good way to figure out what arguments can be given to a command.

Best tip of the day! Thank you so much!

---

### Post by hyper_ch on 2007-11-09
and if you want the manual in a file, you can simply do this:

```

man bash > man.txt

```

---

### Post by bigboy_pdb on 2007-11-09
If you don't know a command for something, use "**apropos**" for example if you're looking for a program that plays music then use the command "apropos music".

Someone mentioned this, but if you know that you have to use a program and you don't know how to use it then use "**man** *programname*". So for example if you want to find out the different options for "ls" then you can use "man ls" to see more on the command. Also, "*programname* **--help**" usually prints how the program can be used and a list of options for it. Furthermore, man pages are opened using the "less" command so you might want to learn how to use it in order to be able to search them.
* "q" is to quit a "man" page
* "/" allows you to search forward from the point you're at using regular expressions
* "?" allows you to search backward from the point you're at using regular expressions
* "n" moves to the next set of characters that matches the expression
* "N" moves to the previous set of characters that matches the expression

On **GNU's documentation website** they have documentation as well. It can be found at:
[http://www.gnu.org/doc/](http://www.gnu.org/doc/)
Their manuals that are easier to read than the "man" pages. So if you want to better understand a program then you should check there. The GNU documentation page also has links to other sources such as free e-books.

**Ubuntu documentation**:
[https://help.ubuntu.com/](https://help.ubuntu.com/)

CRISP web site (**Community Resource and Instructor Support Program**):
[http://snap.nlc.dcccd.edu/](http://snap.nlc.dcccd.edu/)
Check the "Learning Resources", "Links", "Web Pages", and "References" sections. The "Syllabi" section is a good place to find an overview of what you might want to learn along with terms that you can use in search engines.

**System administrators** have a good amount of *nix knowledge so it might be a good idea to research what they do. The following CRISP's site about the levels of system administration:
[http://snap.nlc.dcccd.edu/sysadmin.html](http://snap.nlc.dcccd.edu/sysadmin.html)

The **Red Hat Training site** is a good place to get an overview of some of the things you might want to learn about (especially if you might want to work with Linux as a profession). You can find it here:
[https://www.redhat.com/training/](https://www.redhat.com/training/)

It has already been mentioned, but **The Linux Documentation Project's website** has some really good guides. Their site is:
[http://tldp.org/](http://tldp.org/)
I would recommend first reading "Introduction to Linux - A Hands on Guide" and following that ". For information on the command line you might want to look at "GNU/Linux Command-Line Tools Summary", and for bash scripting you might want to look at "Bash Guide for Beginners" and "Advanced Bash-Scripting Guide". Regarding the "Advanced Bash-Scripting Guide", it is a BASH reference with examples, and not an advanced book that you should read from cover to cover.

For **Linux directory information** you can look at:
[http://www.oreilly.com/catalog/debian/chapter/book/appa_01.html](http://www.oreilly.com/catalog/debian/chapter/book/appa_01.html)
[http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/](http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/)
[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/5022-linux-directory-structure-overview.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/5022-linux-directory-structure-overview.html)

For **GNOME and KDE Keyboard shortcuts**:
[http://www.novell.com/coolsolutions/tip/2289.html](http://www.novell.com/coolsolutions/tip/2289.html)

For **the Linux command line**:
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)
[http://infohost.nmt.edu/tcc/help/unix/unix_cmd.html](http://infohost.nmt.edu/tcc/help/unix/unix_cmd.html)
[http://www.computerworld.com/action/article.do?command=printArticleBasic&articleId=9030259](http://www.computerworld.com/action/article.do?command=printArticleBasic&articleId=9030259)

---

