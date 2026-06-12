---
title: "[SOLVED] What is dependencies?"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Sceiron on 2008-02-13
Wondering...

I have been installing some apps that have/need dependencies.
At the same time im reading through the forums and wiki's that installing a programm requires that you have installed some dependencies.

I understand that the installation is dependent of some extra code or programs, but what is really the meaning of dependecies.
Is it parts of/from other distros of linux ?

I have quite some problems seeing the coherence here, can someone pls help me out of the dark ?

Best regards !

---

### Post by billgoldberg on 2008-02-13
Unlike windows .exe that contains all the dependancies in 1 file, so you could have the same dependencies a hundred times on you hard drive, ubuntu/linux uses the 1 dependency for the all the  programs that need it.

So if it the dependency isn't already installed you'll need to install it, but other programs can also use that depedency, so it's more efficient.

Add/remove and synaptic download the dependicies needed for programs by default, also .deb packages do that to. The same for apt-get.

Or atleast that's what I think.

---

### Post by BluePlum on 2008-02-13
I no pro but i think its like a link so to were program can be download/updates from

---

### Post by Trail on 2008-02-13
Image a library that programs can use to burn CDs. This library is just like a piece of code plus instructions for how to use it that only does this - burns CDs.

Now I have two programs, X and Y, and they both burn CDs. Instead of writing the code to burn CDs from scratch, I can have program X use that library for the burning. So program X uses code from the library, and it "depends" on it, because if the library does not exist then X cannot be used. So if you want to install the program X, a package manager knows that X needs the library to be used, and installs it as well.

If program Y also uses the same library to burn CDs, and the library is already installed, then it can use it without installing it a second time.

This has several great benefits. Imagine that each time you click the OK button of your (lets say) KDE environment programs, the *SAME* code gets called. Which means that this code is only loaded once in your memory. Moreover, if lets say clicking the OK button has a bug, just updating the KDE library will fix the bug in ALL applications that use the library. Plus, it's easier for the developers to separate their work this way.

Might be inconvenient at times, but it's a great thing, imo.

---

### Post by hyper_ch on 2008-02-13
if you use synaptic, adept, apt-get or aptitude it will auto-download and install the dependencies.

---

### Post by k2t0f12d on 2008-02-13
> **Sceiron said:**
> Wondering...

I have been installing some apps that have/need dependencies.
At the same time im reading through the forums and wiki's that installing a programm requires that you have installed some dependencies.

I understand that the installation is dependent of some extra code or programs, but what is really the meaning of dependecies.
Is it parts of/from other distros of linux ?

I have quite some problems seeing the coherence here, can someone pls help me out of the dark ?

Best regards !

Hello.

Your question is both simple and complex to try to answer.  There are many ways that a program that runs on GNU/Linux may depend on other programs.  Making many programs that help each other is the way in GNU/Linux and UNIX based operating systems.

Dependencies are not necessarily parts of other distributions.  All the distributions are made out of many programs that are written by many different people.  When a person writes a new program, they will see that others have already made great programs that they can use to help their new program.  The new program then needs these other program as dependencies.

The package manager of a GNU/Linux like Ubuntu tracks these dependencies for you, allowing you to install the program you want to use and automatically get all the dependencies you need to run it.  In Ubuntu GNU/Linux *apt-get* is the command line package management tool.  *Synaptec* and *Adept* are graphical "windowed" programs that do the same job.

---

### Post by Sceiron on 2008-02-13
Thanks a lot.
It's a more clear to me now.

Just one more thing:
If i'm trying to install a program, and i says it needs dependecies, is it then possible to use the command:
"Sudo apt-get update", then "sudo apt-get install program"
Will the dependencies needed be 'auto-installed' ?

Or do i need to install the dependecies for itself ?

---

### Post by k2t0f12d on 2008-02-13
> **Sceiron said:**
> Thanks a lot.
It's a more clear to me now.

Just one more thing:
If i'm trying to install a program, and i says it needs dependecies, is it then possible to use the command:
"Sudo apt-get update", then "sudo apt-get install program"
Will the dependencies needed be 'auto-installed' ?

Or do i need to install the dependecies for itself ?

That depends on how you are installing.  If you are installing the program you want to use with *apt-get*, then that is correct.  *apt-get* will automatically resolve dependenices for you.  The same is true for *Synaptec* and *Adept*; however, if you are installing from source code *or* any other installation method other then *apt-get*, *Synaptec*, or *Adept*, you must resolve any dependencies manually in order to get your program to work correctly.

---

### Post by SunnyRabbiera on 2008-02-13
> **Sceiron said:**
> Thanks a lot.
It's a more clear to me now.

Just one more thing:
If i'm trying to install a program, and i says it needs dependecies, is it then possible to use the command:
"Sudo apt-get update", then "sudo apt-get install program"
Will the dependencies needed be 'auto-installed' ?

Or do i need to install the dependecies for itself ?

sort of yes and sort of no, normally if an app needs dependencies in apt it will normally mark other packages associated with those dependencies.
But this depends on the application, and its sometimes better to use an app like aptitude or synaptic.
The installation process in linux can be a double edged sword sometimes mind you, in some ways its better then the windows system in terms of security as most packages are available in the repositories and those said repositories are monitored so you dont have to worry about malicious stuff.
But this can be annoying when you have an app that is not in the repositories, but normally on systems using apt things go smoothly thanks to apts capabilities.
Trust me apt is wonderful compared to others out there

---

### Post by Martje_001 on 2008-02-13
```
sudo apt-get install program
```
will install the dependencies automatic. 

you use
```
sudo apt-get update
```
to update the 'source' lists. Ubuntu stores all the information of a program which you can install via apt-get on your hard-drive (description, version-number, etc.).
This command will update these lists by downloading the new ones from the ubuntu-servers.

---

### Post by Sceiron on 2008-02-13
> **SunnyRabbiera said:**
> sort of yes and sort of no, normally if an app needs dependencies in apt it will normally mark other packages associated with those dependencies.
But this depends on the application, and its sometimes better to use an app like aptitude or synaptic.
The installation process in linux can be a double edged sword sometimes mind you, in some ways its better then the windows system in terms of security as most packages are available in the repositories and those said repositories are monitored so you dont have to worry about malicious stuff.
But this can be annoying when you have an app that is not in the repositories, but normally on systems using apt things go smoothly thanks to apts capabilities.
Trust me apt is wonderful compared to others out there

Thanks.
But this raises another question for my part.
What is exactly apt? is it a short for application portal something like that, just a wild guess.
So much new things to find out, but im trying :D

---

### Post by popch on 2008-02-13
To look at it from another side:

There are programs (software packages) which can only run if certain other programs are present and properly installed in your computer. There are many reasons why this might be so. Perhaps the new program needs 'services' which the other ones provides, or perhaps the new program is to add a function to the other one.

Another way of saying that is: The (new) program needs another one. 

Still another one is: the (new) program depends on another one.

Hence, if you are about to install a (new) program and one or more programs which the new program needs are not yet installed, the computer complains that there are unresolved dependencies. By that it means to say that needed other programs are missing.

You solve the problem, of course, by finding and installing the needed programs.

As more learned members of this forum already have pointed out, Linux in some cases will do that for you quite automatically, but not in other ones.

---

### Post by Sceiron on 2008-02-13
Thanks for the view from another perspective.
I think i have the dependencies pretty clear now,
Cheers all .

---

### Post by k2t0f12d on 2008-02-13
> **Sceiron said:**
> Thanks.
But this raises another question for my part.
What is exactly apt? is it a short for application portal something like that, just a wild guess.
So much new things to find out, but im trying :D

To understand *apt* you need to understand the idea of *front-end* and *back-end*.  In a computer program the "back-end" is like the engine of a car.  It does the work that makes the car go.  The "front-end" is like the steering wheel which you the user uses to control the car.

*Apt* is the "front-end", i.e. steering wheel, to the program *dpkg*, which is the "back-end", i.e. engine.  You can install and remove software only using *dpkg*, but it is much easier and more convenient to use *apt-get*.

Also, with regard to your question about dependencies, the *dkpg* program is an example of a dependency.  *dpkg* is a dependency of *apt-get*.

Aside from the relationships between programs, I am not aware of any specific *meaning* in the letters *A-P-T*.  Their meaning may be arbitrary to the function that the program provides.  It could mean *automatic package tracking*, because its use includes that ability.

[COLOR="Red"]Edit: SunnyRabbiera is right about the name for APT -----vvv[/COLOR]

---

### Post by SunnyRabbiera on 2008-02-13
> **Sceiron said:**
> Thanks.
But this raises another question for my part.
What is exactly apt? is it a short for application portal something like that, just a wild guess.
So much new things to find out, but im trying :D

Apt stands for Advanced packaging tool, itmanages the packages on your system.
Its not a program per say, just a really cool and versatile way to get more applications and maintain your system.
Apt is perhaps the most versatile and easiest packaging tool on linux today, it usually solves dependencies quite well and its among the most stable packaging systems I have ever seen.
Of course there are others like YUM, YAST and URPMI but for me apt is the best out of all of them.

read here for more information:
[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool]("http://en.wikipedia.org/wiki/Advanced_Packaging_Tool")

---

### Post by Sceiron on 2008-02-13
> **k2t0f12d said:**
> To understand *apt* you need to understand the idea of *front-end* and *back-end*.  In a computer program the "back-end" is like the engine of a car.  It does the work that makes the car go.  The "front-end" is like the steering wheel which you the user uses to control the car.

*Apt* is the "front-end", i.e. steering wheel, to the program *dpkg*, which is the "back-end", i.e. engine.  You can install and remove software only using *dpkg*, but it is much easier and more convenient to use *apt-get*.

Also, with regard to your question about dependencies, the *dkpg* program is an example of a dependency.  *dpkg* is a dependency of *apt-get*.

Aside from the relationships between programs, I am not aware of any specific *meaning* in the letters *A-P-T*.  Their meaning may be arbitrary to the function that the program provides.  It could mean *automatic package tracking*, because its use includes that ability.

[COLOR="Red"]Edit: SunnyRabbiera is right about the name for APT -----vvv[/COLOR]

Smashing !
So yesterday, when i f... up my xorg.conf for the x-th time :P
(was trying to implement a conky file...)
i tried to fix it by using "sudo dpkg-reconfigure -phigh xserver-xorg"
i more or less "reset" the engine ?

But now that i think about it, using that command im resetting what ?
Not the xorg.conf file, but more like the xserver, or is it the same thing?

---

### Post by PmDematagoda on 2008-02-13
This thread has been moved to the Absolute Beginner Thread as this is a support thread and would receive greater help here.

---

### Post by k2t0f12d on 2008-02-13
> **Sceiron said:**
> Smashing !
So yesterday, when i f... up my xorg.conf for the x-th time :P
(was trying to implement a conky file...)
i tried to fix it by using "sudo dpkg-reconfigure -phigh xserver-xorg"
i more or less "reset" the engine ?

But now that i think about it, using that command im resetting what ?
Not the xorg.conf file, but more like the xserver, or is it the same thing?

*xorg conf* is the configuration file that is read when you activate Xorg Xserver.  Xserver itself is a collection of library programs that other programs use to draw the windows on your screen.

*dpkg* reads *deb* package files, the same files that *apt-get* will download from Ubuntu to install on your computer.  This should be obvious since *apt-get* **is** an interface to *dpkg*.

Within each *deb* package there are the files that are needed to install your program.  There is also a list of the names of other programs that you must have to use the program, these are the dependencies, which *apt-get* will automatically read and install for you with your program.

Finally, there are also configuration scripts.  These scripts *specifically* make your program adapt to your computer properly.  When you called:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
What you actually did was send a special request **directly** through *dpkg* to rerun the configuration script from the Xserver deb package that sets up the xorg.conf file for Xserver.

---

### Post by Sceiron on 2008-02-13
Meditate on this I will :-k

---

### Post by k2t0f12d on 2008-02-13
Useful *dpkg* trick:
```
sudo dpkg --get-selections | grep -i install | grep -v deinstall | less
```

This will display a list of package names currently installed on your computer.  The two *grep* commands filter out packages names that aren't listed under *install*.

You can save the list with the following command:
```
sudo dpkg --get-selections >*filename*
```
Where *filename* is the name of the file you wish to create the list in.  The file need not exist before issuing the command, and will be created if it doesn't.  This command would completely overwrite any data stored in a file of the same name anyway, so better to choose a *filename* that doesn't belong to an existing file.

You can then install or reinstall Ubuntu on your computer and reinstall all your favorite packages with the command:
```
cat *filename* | sudo dpkg --set-selections
```
Where *filename* is the name of the file to which you have saved your list.  Of course, you must have a backup of the file saved as *filename* separate from where you install Ubuntu in order to avoid its destruction with the rest of the system during reformatting.  Save *filename* to a location where it will not be deleted.

[COLOR="Red"]**WARNING: DPKG IS A VERY POWERFUL SYSTEM TOOL AND CAN EASILY RENDER YOUR SYSTEM UNUSABLE IF MISUSED.**[/COLOR]

---

### Post by Sceiron on 2008-02-14
"xorg conf is the configuration file that is read when you activate Xorg Xserver. Xserver itself is a collection of library programs that other programs use to draw the windows on your screen."

So i was resetting the xserver, whic was followed by that my xorg.conf is no longer working....
I tried to fix it by replace xorg.conf with xorg.conf.backup.
But i have in some way messed up the backupfiles too.

Should i adress this problem in a new tread on Absolute Beginner Talk, or shall i continue this tread?

And how do i quote certain parts of a message, instead of tthe hole post ?

Sceiron    :-\"

---

### Post by oedha on 2008-02-14
about xorg....you can open terminal and type
sudo dpkg-reconfigure -phigh xserver-xorg

for quote : i think by pressing quote button....i rarely use it.....maybe mine problem is the same with yours......but it not bother me much :)

---

### Post by Sceiron on 2008-02-14
> **oedha said:**
> about xorg....you can open terminal and type
sudo dpkg-reconfigure -phigh xserver-xorg



If you have read the previous posts, you wil see that is excatly what i have done...

About the quote part, from the previous posts, its not that i can't qoute.
But i realised how i can do it now by replaying to this post !

So im back to the same question.
Since this tread have a Header which says "What is dependencies?" would it be better to start a new tread with headline saying something like "xorg.conf broken..."  when i have questions about that specific problem?
Trying to find out about the code of the forums ....

edit:
Does it *bump* when i edit ?
edit2:
no it doesnt

---

### Post by Martje_001 on 2008-02-14
> **Sceiron said:**
> Since this tread have a Header which says "What is dependencies?" would it be better to start a new tread with headline saying something like "xorg.conf broken..."  when i have questions about that specific problem?t
Yes, you should do this ;). 

> 
edit:
Does it *bump* when i edit ?
edit2:
no it doesnt
See [this](http://en.wikipedia.org/wiki/Bump_%28Internet%29).

---

