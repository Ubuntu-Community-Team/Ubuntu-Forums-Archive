---
title: "noob question"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Benifited on 2007-04-10
im slowly learning how to use the terminal. i got the "'cd "command down right but im confused on the "./configure" and "make" commands do i just put them in or what im really lost here. any tips would really be a great help thx.

---

### Post by Razorback on 2007-04-10
You would use those commands if you were manually installing and compiling programs.  I would stick with Synaptic Package Manager to install programs for now.  Then when you get comfortable you could try those out.

---

### Post by FrostyFlames on 2007-04-10
Well it depends. You normally use "./configure" and "make" in the directory root of a program you are trying to compile. Trying to run either one of those commands from just opening a terminal will get you nothing. If you're trying to compile and install, cd into that directory and try the configure and make commands. Hope that makes some sense. :/

---

### Post by Benifited on 2007-04-10
> **FrostyFlames said:**
> Well it depends. You normally use "./configure" and "make" in the directory root of a program you are trying to compile. Trying to run either one of those commands from just opening a terminal will get you nothing. If you're trying to compile and install, cd into that directory and try the configure and make commands. Hope that makes some sense. :/

yea it does make sense because i am trying to install stuff. but when i go into the directory and try to configure or make so that i can install i get no where

---

### Post by Benifited on 2007-04-10
> **Razorback said:**
> You would use those commands if you were manually installing and compiling programs.  I would stick with Synaptic Package Manager to install programs for now.  Then when you get comfortable you could try those out.

could i use synaptic package manager if i downloaded the package?

---

### Post by Razorback on 2007-04-10
> **Benifited said:**
> could i use synaptic package manager if i downloaded the package?

Actually, synaptic will download, compile and install the program.  It will also download and install any dependencies for that program.  I have been told that manually compiling can be challenging, not impossible, but challenging.

What programs are you wanting to install?

---

### Post by Benifited on 2007-04-10
> **Razorback said:**
> Actually, synaptic will download, compile and install the program.  It will also download and install any dependencies for that program.  I have been told that manually compiling can be challenging, not impossible, but challenging.

What programs are you wanting to install?

quicktime and kooldock

---

### Post by Razorback on 2007-04-10
I am not on my ubuntu system.  Have you checked synaptic to see if they are in the repositories?

---

### Post by machoo02 on 2007-04-10
> **Razorback said:**
> Actually, synaptic will download, compile and install the program.  

Actually, Synaptic does not compile programs for you.  Synaptic will download pre-compiled binaries of the programs/libraries that you need from the repositories and install them.

To install single .deb (binary package for Ubuntu/Debian) you can do this through the command line via dkpg, and a GUI installer is GDebi.

About the packaes you want to install:```
 aptitude search quicktime
p   libquicktime-dev                              - header files for developing applications with quicktime
p   libquicktime0                                 - library for reading and writing Quicktime files        
p   quicktime-utils                               - quicktime utilities                                    
p   quicktime-x11utils                            - quicktime graphical utilities
```

If you are trying to watch quicktime movies, then I believe quicktime-x11utils is the package that you want.  Kooldock is also in the repositories, so you should be just an aptitude install away!

---

### Post by j002 on 2007-04-10
They might be binaries (executable files).

go into the directory, if there is a file with :

program name

and no extension, then try :

./program name

to invoke the program.

If you can, try and find a .deb file of the same program, by Googling "program ubuntu" or "program debian".
Then you just double-click on the icon and the Debi-installer will run.  (Then you need to get all the dependencies...)

---

### Post by Benifited on 2007-04-10
> **Razorback said:**
> I am not on my ubuntu system.  Have you checked synaptic to see if they are in the repositories?

no there not there

---

### Post by Benifited on 2007-04-10
> **j002 said:**
> They might be binaries (executable files).

go into the directory, if there is a file with :

program name

and no extension, then try :

./program name

to invoke the program.

If you can, try and find a .deb file of the same program, by Googling "program ubuntu" or "program debian".
Then you just double-click on the icon and the Debi-installer will run.  (Then you need to get all the dependencies...)

ok im going to try and look for them in that format .deb right cool thx

---

### Post by Maestro23 on 2007-04-10
Some links to help you out:

Useful Links:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

Restricted Formats(mp3, playing DVD, etc..): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Managing Repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

Community Docs: [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

CommandLine Beginners: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Basic Commands: [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Using the Terminal: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Top 10 Commands for noobs: [http://blog.lxpages.com/2007/02/25/top-10-linux-commands-for-newbies/](http://blog.lxpages.com/2007/02/25/top-10-linux-commands-for-newbies/)

Graphic Card Drivers
ATI supported cards: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)
Installing ATI Drivers: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
Installing Nvidia Drivers:[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Super Grub Disk: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Getting rid of junk: [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)


Welcome and Good luck.

---

### Post by nsilva on 2007-04-10
A concise answer is:
you use the ./program-name, to execute a script that is in the directory you are in... that is why u use 
./configure (you are executing the script in the directory you are in)

make command, follow the instruction written in the MAKEFILE, which should be in the same directory. This MAKEFILE tells the compiler how to compile the program.

One last steo sometimes needed is to do, "make install" This requires you to be root (or to do sudo make install) this just places the right files in the directories the user does not have writing permision, such as /etc, or /usr/

This is a quick answer, please google around, there must be 100000000000 links about this topic.

---

### Post by Benifited on 2007-04-11
when i try to make it says:

make: *** No targets specified and no makefile found.  Stop.

help!!!!!

---

### Post by Benifited on 2007-04-11
ok i got quicktime installed that was hard.:)  how do i run it ?

---

### Post by Benifited on 2007-04-11
bump

---

### Post by machoo02 on 2007-04-11
> **Benifited said:**
> no there not there
Both Quicktime and Kooldock **are** the repositories...just make sure you have universe enabled.

---

