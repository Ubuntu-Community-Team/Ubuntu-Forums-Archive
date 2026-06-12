---
title: "Need somebody"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by Dedaw on 2008-03-30
I need somebody who'd be willing to take some of their time to teach me the ins and outs of Ubuntu(to their knowledge at least), because I'm getting really irritated with it as I have no clue what I'm doing :P

Preferably somebody who knows ** a lot** about it ;)

---

### Post by Tatty on 2008-03-30
The best method of learning is to run into a problem and then set about fixing it...

Do you have any problems currently?  If so then feel free to post them on this forum... thats what its all about :popcorn:

---

### Post by Afkpuz on 2008-03-30
I can help.  I would call myself an intermediate level user, so I should be able to help get you going.  So first, a few questions to gauge where you're coming from

1.) Which version of Ubuntu are you using? 

2.) What type of computing background do you have?  (i.e. internet only stuff, programming, gaming, custom building,etc)

3.) Is there anything you'd like your computer to do that you can't figure out?

---

### Post by wolfen69 on 2008-03-30
2 good sites are [www.ubuntuguide.org](www.ubuntuguide.org) and [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) be patient and have fun.

---

### Post by crashcoredump on 2008-03-30
I am also a newbie to Ubuntu and Deb distros but I do have some BsD experience and some RH experience.

I will be glad to answer any questions that I can,

My msn is [email]etchingsj@ally.com[/email]

Good Luck

---

### Post by oedha on 2008-03-30
[http://help.ubuntu.com/community](http://help.ubuntu.com/community)
:)

---

### Post by JoshuaRL on 2008-03-31
First of all, welcome to Ubuntu!  Sorry you've been having problems, but as was pointed out the best way to learn this is to fix what problems you are having.  If you could post them here, we would be happy to walk you through the fixes.  That way you can understand the logic behind the OS and be able to troubleshoot stuff on your own too.

The websites mentioned are great, and the community here at the forums is unparalleled.  So instead of one person that may not have all the solutions you seek, you have hundreds!  Thats open source!

---

### Post by Dedaw on 2008-03-31
1.) 7.10
2.) HTML programming, custom building


I'd just like to know how to install programs pretty much. And hopefully, soon, learn the coding of Ubuntu so I can set programs to run in Ubuntu without any other software ;)

---

### Post by JoshuaRL on 2008-03-31
Programs are pretty easy.  Go to System->Preferences->Software Sources and make sure everything except the CD and source code is enabled.  Then go to Applications->Add/Remove and search for anything you want.

Another option is System->Administration->Synaptic Package Manager.  That will be a little more in depth, and have a lot more librarys and the like.

Also, there's [http://packages.ubuntu.com/](http://packages.ubuntu.com/).  And you can install anything that is a .deb for Ubuntu.

---

### Post by Afkpuz on 2008-03-31
Ok, here's the lowdown on installing programs in ubuntu.  So far, I've discovered 5 main ways to install programs.  There might be more, but these are the ones that came to my mind.  Remember that these methods are different from windows because LINUX IS NOT WINDOWS. 

1.) Add/remove
2.) Synaptic Package Manager
3.) .deb packages and similar formats (like .rpm)
4.) From source
5.) .sh files

**1.)Add/Remove**
This one is easy.  Goto Applications>Add/Remove Programs to access this app.  Here are some nicely categorized programs with descriptions.  This area is a list of programs availible to download from the repositories.  I'm not positive, but I don't believe any command line interface programs are listed here.   Only graphical interface programs appear in this list and an icon will be added to the Applications menu once the install is done.  There are also codec packages here as well.  Installing of a package is easy and you've probably already used this.  Just check the box next to the program and click apply.  

**2.) Synaptic Package Manage**
This program will show you all of the program availible for install from the repositories.  The repos are just a big collection of programs tailored for ubuntu.  It is located in System>Administration>Synaptic
When you install a program though synaptic, it could be anything.  Both gui and cli (comman line interface) programs are contained here as well as codecs and libraries.  Sometimes, after installing a program, you will get an icon in Applications.  Sometimes, you need to go find where the program is installed.  You can find this by right clicking on the package name in synaptic and selecting "installed files".  More on that if you need it.

Synaptic is great because there are so many packages that you can choose from.  Synaptic also has a command line format that you can use in coding.  First, find out the exact name of the package you want to install.  You can check the names on synaptic.  It lists the exact package name when you select a package.  Here is the format you would paste into a terminal (Applications=>Accessories=>Terminal)

```
sudo apt-get install packagename
```

A little about the inner workings of synaptic and add/remove:
These packages are prepared for installation.  They are easy to install and all their dependencies are automatically downloaded.  When using the source code method of installing, you have to make sure to install all the dependencies on your own.  So, thats why synaptic sometimes tells you that you need to install something else in addition to what you wanted.  Alot of dependencies that you will need are libraries.

**3.) .deb files**
This is short for debian files and are also very easy to install.  You will find these on the internet.  When looking for linux programs, you might be able to download a .deb file.  This is probably the closest thing to a .exe file you'll find in ubuntu.  Once you've downloaded the .deb, just double click on the file and the installer will begin.  .deb files usually do not need any input from you and the installer will install any dependencies you might need.  Like synaptic, you might not always get an icon to launch the newly installed program.  I'm sure there is a command for installing a .deb file, but I don't know it.  Maybe someone else can help there

.rpm files are like debian files, but need to be converted.  Use the package called alien to convert .rpm files into .deb dfiles.

```
sudo apt-get install alien
sudo alien packagename.rpm
```


ok, this post is getting long.  I'll tell you about the other 2 methods later.  This should help you get going.  Let me know if you have any questions about this stuff.

---

### Post by Afkpuz on 2008-04-01
Ok, so now a little bit on the last two methods of installing.

**4.) From source/binaries**

Source code is just the raw information for a program and is not really tailored for use on any system.  You'll need to configure it to be used in Ubuntu, then install it.  So, when looking around the net, you'll find lots of binaries out there for programs.  When you download these, you'll need to use the command line to install them.  You can tell that they are binary files because once extracted out of the .tar, there will be no INSTALL.sh.  Rather, you'll see a configure.sh file.

First off, you'll probably need to make a place for this progam to live.  I recommend making a folder within your home folder called "Installs".  Then, extract your tarball into the Installs folder.  Then, open up the terminal.

You'll need to install this package in order to configure binaries for ubuntu.  
```
sudo apt-get install build-essential
```

Then, you'll need to change directories to the newly extracted folder.
```
cd Installs/binaryname
```

Then, you'll need to run the configure file

```
sudo sh configure.sh
```

The configure file checks that you have all the needed dependencies.  If you don't have them all, you will receive an error message.  That message should tell you which package to install, or at least give you some direction as to where to look.  If the configure shell script completes successfully, a make file should have been generated.  If the configure function returns an error, you won't get a make file.  

So now, you need to run the following

```
sudo make
```

I'm pretty sure that the make command is what configures the program for ubuntu and gets it into a usable format for ubuntu.  Then finally, you need to install the program.

```
sudo make install
```


**5.) .sh files**
These are also extremely easy to use.  These install files will be downloaded from the net and will contain some sort of file called "INSTALL.sh" or something similar.  In this instance, you don't need to convert or make or do anything.  You just need to exceute the install file.  So, open a terminal and change directories to wherever you extracted the .tar archive.  

```
sudo sh INSTALL.sh
```

You might need to modify the name from all caps, but just make sure that you point it to the install file with the .sh ending.  


So thats it.  In my opinion, the only difficult method is installing from source.  And the main difficulty there is finding the depndencies on your own.  So, I hope this helps you out.

---

