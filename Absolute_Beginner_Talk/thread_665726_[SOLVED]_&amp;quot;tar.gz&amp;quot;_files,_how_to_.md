---
title: "[SOLVED] &amp;quot;tar.gz&amp;quot; files, how to install without sudo-apt or internet"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by ctoaun on 2008-01-12
Does anyone know of some precise steps for installing tar.gz&#8221; files? Please do not point me to the post entitled, &#8220;how to install anything in Ubuntu.&#8221; Having read it and attempted to use it, I&#8217;ve concluded the post is missing something because I&#8217;ve successfully followed some sites instructions without encountering any problems.

I cannot use sudo-apt as I only have dialup and broadband wireless for now.

thanks

---

### Post by Paul820 on 2008-01-12
tar.gz files are just like .zip or .rar files in windows. They are archives, you extract them.

---

### Post by Tenken on 2008-01-12
What exactly is the tar.gz file you are working with? If you are talking about source code, you're going to have to compile the program yourself, which means installing build essentials, which I think are located on the install cd.

```
sudo apt-get install build-essentials
```

The process for installation differers with each program as they all have different compile time options. What program are you trying to install?

---

### Post by p_quarles on 2008-01-12
The "tar.gz" extension indicates an archive, similar to .zip or .rar. To extract it:
```
tar -zxvf *name-of-file*.tar.gz
```
This will usually give you a directory with the source code, and in some cases it will give you an executable binary. 

The basic procedure for compiling source code is like this:
```
./configure
make
sudo make install
```
Most source packages come with README files, though, and you should. 

That said, it is very likely that you will need to get dependencies for just about every package you want to compile. In addition, compiling anything requires you to have the "build-essential" package installed. 

Basically, this isn't going to save you bandwidth. I would look for a different solution if I were you, such as obtaining a CD/DVD that you can use as a repository for apt-get.

---

### Post by twin_57103 on 2008-01-12
To extract these archives, right click on them and open with archive manager.  This will let you extract them.  After that, installation will depend on the type of file that's in the archive.

---

### Post by amo-ej1 on 2008-01-12
Well a .tar.gz is a zipped tar archive. you can extract their contents easily using 

```

tar -zxvf archive-name.tar.gz

```

But it heavily depends on the contents how to install if further than that. Since you seems to be referencing to a package my guess would be that it will contain sourcecode, and each sourcecode has its own way on getting installed on the system. C/C++ sourcecode need a C/C++ compiler, perl code needs a perl interpreter and such ... so you can typically extract the archive on your systems. But if it contains sourcecode you will need additional steps depending on the contents.

And typically it will be C/C++ sourcecode and you will need the contents of the build-essential package, but this will be a problem since you're on dial-up connection. 

It could perhaps be more useful if you try to state exactly what you plan to install

---

### Post by ctoaun on 2008-01-12
> **Tenken said:**
> What exactly is the tar.gz file you are working with? If you are talking about source code, you're going to have to compile the program yourself, which means installing build essentials, which I think are located on the install cd.

```
sudo apt-get install build-essentials
```

The process for installation differers with each program as they all have different compile time options. What program are you trying to install?

Please note: sudo-apt is not currently an option, no internet

Trying to get wifi working, which  according to [this:]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-818e0ccb34dc3e6733f798494fb6ce95ea5548c6") I need to install ndiswrapper-utils-1.9. this in turn leads me [here]("http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=562382")


Here is a command that never works for anything: tar -zxvf name-of-file.tar.gz
no such file or directory even if copy paste is utilized

---

### Post by p_quarles on 2008-01-12
> **ctoaun said:**
> I was trying to install this program, dependencies and cabextract. This way I had some internet.
Source is [Here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-818e0ccb34dc3e6733f798494fb6ce95ea5548c6")

Here is a command that never works for anything: tar -zxvf name-of-file.tar.gz
no such file or directory even if copy paste is utilized
You need to be *in *the directory in which the file is located. You can also double-click on the file from the file browser, and that will do the trick as well.

---

### Post by ctoaun on 2008-01-12
> **amo-ej1 said:**
> Well a .tar.gz is a zipped tar archive. you can extract their contents easily using 

```

tar -zxvf archive-name.tar.gz

```

But it heavily depends on the contents how to install if further than that. Since you seems to be referencing to a package my guess would be that it will contain sourcecode, and each sourcecode has its own way on getting installed on the system. C/C++ sourcecode need a C/C++ compiler, perl code needs a perl interpreter and such ... so you can typically extract the archive on your systems. But if it contains sourcecode you will need additional steps depending on the contents.

And typically it will be C/C++ sourcecode and you will need the contents of the build-essential package, but this will be a problem since you're on dial-up connection. 

It could perhaps be more useful if you try to state exactly what you plan to install

This code, "tar -zxvf archive-name.tar.gz,"  has never worked, even when everything is copied and pasted. One of the errors is: "child is returned status 2."  sudo aptitude works sometimes. 

as for the " source code," I cannot comment. there has been nothing to indicate source code was or was not an issue. Thanks though

---

### Post by p_quarles on 2008-01-12
You do realize that you need to replace "archive-name" with the actual archive name, right?

That command works fine, so the only conclusion is that you are doing something incorrectly. If you can retrace your exact steps, or perhaps even post a screenshot of the terminal in which you are running the command, someone will be able to help.

---

### Post by ctoaun on 2008-01-12
> **Tenken said:**
> What exactly is the tar.gz file you are working with? If you are talking about source code, you're going to have to compile the program yourself, which means installing build essentials, which I think are located on the install cd.

```
sudo apt-get install build-essentials
```

The process for installation differers with each program as they all have different compile time options. What program are you trying to install?

I do not have internet access, but thanks

---

### Post by ctoaun on 2008-01-12
**Too all:**

Thanks,  here it is simple

To have internet, I need to get my wifi to work, currently dual booting Ubuntu & XP. XP was the original OS. 

1) I need to install install ndiswrapper-utils-1.9 & cabextract

1A) This is according to a post where the provided  solution is for a laptop that is virtually identical to one of my own. This is the [first post]("http://ubuntuforums.org/showthread.php?t=663581&highlight=wireless&page=2"):  

1b) This first post then sends me to this post, [click here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-818e0ccb34dc3e6733f798494fb6ce95ea5548c6").

2) The second post, identified in 1b), post then sends me to the following sourceforge [page]("http://sourceforge.net/project/showfiles.php?group_id=93482")

3) This command never works "tar -zxvf ndiswrapper-version.tar.gz"
in fact "tar -zxvf" has never worked.

Here are the variations that I tried and the results:

xxxx111@xxxx111-laptop:~$ tar -zxvf ndiswrapper-version.tar.gz/home/xxxx111/Desktop 
tar: ndiswrapper-version.tar.gz/home/xxxx111/Desktop: Cannot open: No such file or directory 
tar: Error is not recoverable: exiting now 
tar: Child returned status 2 
tar: Error exit delayed from previous errors 
xxxx111@xxxx111-laptop:~$ tar -zxvf ndiswrapper-1.51 
tar: ndiswrapper-1.51: Cannot open: No such file or directory 
tar: Error is not recoverable: exiting now 
tar: Child returned status 2 
tar: Error exit delayed from previous errors 
xxxx111@xxxx111:~$  
xxxx111@xxxx111-laptop:~$ tar -zxvf ndiswrapper-1.51/home/xxxx111/Desktop 
tar: ndiswrapper-1.51/home/xxxx111/Desktop: Cannot open: No such file or directory 
tar: Error is not recoverable: exiting now 
tar: Child returned status 2 
tar: Error exit delayed from previous errors 
xxxx111@xxxx111-laptop:~$ tar -zxvf ndiswrapper-version.tar.gz/home/xxxx111/Desktop 
tar: ndiswrapper-version.tar.gz/home/xxxx111/Desktop: Cannot open: No such file or directory 
tar: Error is not recoverable: exiting now 
tar: Child returned status 2 
tar: Error exit delayed from previous errors 
xxxx111@xxxx111-laptop:~$

---

### Post by p_quarles on 2008-01-12
Yep, just bad syntax. Try this:
```
tar -zxvf /home/*username*/.Desktop/ndiswrapper-version.tar.gz
```

---

### Post by ctoaun on 2008-01-12
> **p_quarles said:**
> Yep, just bad syntax. Try this:
```
tar -zxvf /home/*username*/.Desktop/ndiswrapper-version.tar.gz
```

Thanks for the quick responses but...

Nothing works, same errors. It's not typing because everything is copy and paste.

I just copied and pasted your solution onto a text document. Then below this, I copied from the terminal screen.

Everything matches exactly except username. I copied all the file attributes from properties, so what's next.

also, I've always copied for the purpose of sudo anything without a problem until now.

---

### Post by ugm6hr on 2008-01-12
@ctoaun:
Are you running Ubuntu7.10 / Gutsy?

If so, you may not need to *compile* ndiswrapper at all.  The Gutsy repository has it in a .deb file that can be double-clicked to install.  Have you tried it?  Compiling the latest ndiswrapper (according to this: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-043c7a370f7f416ffe637a052bb89d39fc75e841](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-043c7a370f7f416ffe637a052bb89d39fc75e841)) is only required for a small minority of users.

The .debs are linked under Architecture (chose the correct one!) in the table at the bottom of these pages:
[http://packages.ubuntu.com/gutsy/misc/ndiswrapper-common](http://packages.ubuntu.com/gutsy/misc/ndiswrapper-common)
[http://packages.ubuntu.com/gutsy/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/gutsy/misc/ndiswrapper-utils-1.9)

Just download them, copy them to your Desktop in Ubuntu, and double-click in the order above.

Cabextract is also required by the look of things:
[http://packages.ubuntu.com/gutsy/utils/cabextract](http://packages.ubuntu.com/gutsy/utils/cabextract)

If this is what you are trying to follow: [http://ubuntuforums.org/showpost.php?p=4109652&postcount=18](http://ubuntuforums.org/showpost.php?p=4109652&postcount=18)

Then this should now work (except the wget command - you will have to download the driver manually elsewhere).  Just install the above packages (double-click), then follow the insrtuctions, ignoring the apt-get and wget ones.

Good luck.

---

### Post by ctoaun on 2008-01-12
I'm on it at this moment

By the way do you know why I am having problems with this command?

All the other ones work, and a copy & paste compare indicates that I've done nothing wrong syntax wise

---

### Post by p_quarles on 2008-01-12
Probably because the file you have has a specific version name that you haven't entered. What's the output of this?:
```
ls .Desktop
```

---

### Post by oldos2er on 2008-01-12
> **ctoaun said:**
> **Too all:**

3) This command never works "tar -zxvf ndiswrapper-version.tar.gz"
in fact "tar -zxvf" has never worked.

Here are the variations that I tried and the results:

xxxx111@xxxx111-laptop:~$ tar -zxvf ndiswrapper-version.tar.gz/home/xxxx111/Desktop 

 First, from your command prompt, type "cd Desktop". Then "tar -zxvf ndiswrapper-version.tar.gz" where you replace "version" with the actual version of the file you downloaded. Or, type "ndis" then hit the Tab key for file name completion by the shell.

 If this is a source tarball, you won't be able to compile it until you install a package called build-essential. You can use Synaptic to install this from the Ubuntu live CD.

---

### Post by ctoaun on 2008-01-12
what does architecure mean? you said choose the correct architecture.

---

### Post by p_quarles on 2008-01-12
> **ctoaun said:**
> what does architecure mean? you said choose the correct architecture.
The type of processor you're running. If you don't know, run this command and post the output here:
```
uname -a
```

---

### Post by Tenken on 2008-01-12
He is talking about processor architecture. i386 is what most people have if you have a 64-bit CPU use the i386_64.

---

### Post by ctoaun on 2008-01-12
thanks

I get i686, which is neither x386 nor the amd64 offered as choices.
I am running an AMD 64 athlon inn that computer

---

### Post by nikoPSK on 2008-01-12
tar.gz is jsut a compression method, you have to untar them. :)

nikoPSK

---

### Post by Tenken on 2008-01-12
> thanks

I get i686, which is neither x386 nor the amd64 offered as choices.
I am running an AMD 64 athlon inn that computer

Then use the amd64 architecture.

---

### Post by p_quarles on 2008-01-12
> **Tenken said:**
> Then use the amd64 architecture.
Actually, the architecture of the processor is less important than the kind of kernel running on the machine. Since either i386 or AMD64 versions of Ubuntu will run on that processor, I still recommend checking with:
```
uname -a
```

---

### Post by erfahren on 2008-01-12
actaually it would depend on whether it's Ubuntu 32-bit or Ubuntu 64-bit - if you're using regular 32-bit Ubuntu use the regular i386 package

EDIT: same thing that p_quarles is saying

---

### Post by ctoaun on 2008-01-12
> **Tenken said:**
> He is talking about processor architecture. i386 is what most people have if you have a 64-bit CPU use the i386_64.

I searched the internet. My CPU is a  AMD Athlon 64 3200

Someone said 32 bit vs 64 bit Ubuntu. I don't know the difference. I'm running the x386 version. Since I was told that the correct architecture is important, I am now at a complete stop, unable to proceed without clarification.

Please do not use unexplained terms. When terms, which do not appear at the HP or newegg site, are used, all progress halts. The ultimate question is what do I need from this [site]("http://packages.ubuntu.com/gutsy/misc/ndiswrapper-utils-1.9") Thanks

---

### Post by avik on 2008-01-12
> **ctoaun said:**
> I searched the internet. My CPU is a  AMD Athlon 64 3200

Someone said 32 bit vs 64 bit Ubuntu. I don't know the difference. I'm running the x386 version. Since I was told that the correct architecture is important, I am now at a complete stop, unable to proceed without clarification.

Okay, so you have a 64-bit processor (amd64).  However, you may be running a 32-bit OS (which is okay too).

Please post the output of:

```
uname -r
```

---

### Post by ctoaun on 2008-01-12
2.6.22-14-generic #1 SMP

---

### Post by p_quarles on 2008-01-12
I'm about to give up here, as it seems you're ignoring my advice. 
```
uname -r
```
will only give you the *version* of the kernel. To get the architecture, you need to run:
```
uname -a
```

---

### Post by ctoaun on 2008-01-12
> **p_quarles said:**
> I'm about to give up here, as it seems you're ignoring my advice. 
```
uname -r
```
will only give you the *version* of the kernel. To get the architecture, you need to run:
```
uname -a
```

Already posted "uname -a" info. It looks like "uname -r" except it adds "1686 GNU?Linux" after the date

---

### Post by p_quarles on 2008-01-12
> **ctoaun said:**
> Already posted "uname -a" info. It looks like "uname -r" except it adds "1686 GNU?Linux" after the date
Okay. I did see that, but I had no way of telling if that was what you got from the command, or if you were answering someone else's question.

Definitely go with the i386 package then.

---

### Post by ctoaun on 2008-01-12
> **p_quarles said:**
> Okay. I did see that, but I had no way of telling if that was what you got from the command, or if you were answering someone else's question.

Definitely go with the i386 package then.

Alrighty, I'll give it a try and I'll let everyone know where I'm at here shortly, thanks.

---

### Post by nikoPSK on 2008-01-12
No problem. :popcorn:

---

### Post by ctoaun on 2008-01-12
> **nikoPSK said:**
> No problem. :popcorn:

If you were talking to me, I do not know what you meant.

---

### Post by ctoaun on 2008-01-12
Wont allow me to delete this response

---

### Post by p_quarles on 2008-01-12
> **ctoaun said:**
> Wont allow me to delete this response
Hmm. That's strange that Synaptic won't use it.

Try installing it with the command line:
```
sudo apt-get install build-essential
```
The package is on the CD, so it should automatically try to install it from there. If it doesn't, you'll have to modify your repository list, which I can tell you how to do. 

If you get the same "disk corrupt" message using apt-get, you might have to download a new disk with the computer that's connected to the net. 

Btw: you don't need the build-essential package if you're trying to install the package that's been discussed over the last couple pages. That's only for source code.

---

### Post by ctoaun on 2008-01-12
> **Tenken said:**
> What exactly is the tar.gz file you are working with? If you are talking about source code, you're going to have to compile the program yourself, which means installing build essentials, which I think are located on the install cd.

```
sudo apt-get install build-essentials
```

The process for installation differers with each program as they all have different compile time options. What program are you trying to install? [ndis wrapper]("http://packages.ubuntu.com/gutsy/misc/ndiswrapper-common") and [URL="http://packages.ubuntu.com/gutsy/utils/cabextract"]cabextract
[/URL]
A file search of my disk indicates that there are dozens of  programs that say build something. Therefore is "build essentials" a file name or a name given to a collection of programs?

Synaptic alleges that the CD is corrupt even though every thing shows up fine in the file manager.

---

### Post by oldos2er on 2008-01-12
"build-essential" is the name of the package you need to install.

 Is the corrupt CD you're referring to your install CD? Have you run its internal check for defects?

---

### Post by erfahren on 2008-01-12
this is the actual package
[http://packages.ubuntu.com/gutsy/devel/build-essential](http://packages.ubuntu.com/gutsy/devel/build-essential)

---

### Post by erfahren on 2008-01-12
oh, I should mention that what you actually need there (on that page) is the packages with the red dots (the dependencies) - in this case those packages are what actually make up the "build-essential" package

-- In other words, the build-essental package is actually only a "list" of those dependency packages marke in red.

---

### Post by ctoaun on 2008-01-12
> **erfahren said:**
> this is the actual package
[http://packages.ubuntu.com/gutsy/devel/build-essential](http://packages.ubuntu.com/gutsy/devel/build-essential)

Appreciate the effort,  but this does not work either.

Reason: I can't change or I do not know how to change  the file permissions.
Sudo login does not grant one the authority to do this.

In other words, to install a deb, after I right-click the file, I select properties. Under the permissions tab, I find that the permissions are set root.

I do not know how to change the permissions on a deb file located on my desk top

On a positive note, at least it appears that gdebi-gtk would work if the file had permissions

---

### Post by oldos2er on 2008-01-12
In a terminal, type "gksudo nautilus". This will give you root access to your file system. Then navigate to build-essential, right-click, and you should see a 'open with GDebi' option.

---

### Post by erfahren on 2008-01-12
you should just be able to double-click them and they'll open with Gdebi -- you'll get prompted for your password

---

### Post by ctoaun on 2008-01-12
[B]T[SIZE=2]hanks for the advice, no offense intended, but I feel as though we are getting colder.  
[/SIZE] 
[/B][SIZE=1]Fact 1) tar -zvxf does not work on the computer in question. How do I know this? simple I copy and paste from the terminal into a document. Then I take the command from the instruction and the syntax corrections from this forum and I paste them below, so that three perfectly aligned rows are created. therefore, since there are no discrepancies, the error is not mine.

2) The build essentials files are tar.gz files. I cannot open them with Gdeki-whatever (gtk I think, not looking at it now) so if these file are needed I cannot install them.

3) the only thing that I can install is a deb file. This I know because it was accidentally done this morning.

4) No advice that requires an internet connection (i.e. sudo-apt or wget) is viable. My only options are Broadband WIFI, which I cannot install into I install the drivers, which is what this post is about.

**[SIZE=2]5) My two paramount questions  are: [/SIZE]**


5.1) A paramount question becomes is there away to get these tar.gz files in deb format? 
?
5.2) Is there away to convert these files into deb by downloading a deb pkg designed for this purpose?

again, no offense intended. None of the preceding should be construed to mean that I do appreciate everyone's efforts but unless convinced otherwise, my troubleshooting instincts are telling me that we are going off base

[/SIZE]

---

### Post by PeterJS on 2008-01-12
> **ctoaun said:**
> [B]T[SIZE=2]hanks for the advice, no offense intended, but I feel as though we are getting colder.  
[/SIZE] 
[/B][SIZE=1]Fact 1) tar -zvxf does not work on the computer in question. How do I know this? simple I copy and paste from the terminal into a document. Then I take the command from the instruction and the syntax corrections from this forum and I paste them below, so that three perfectly aligned rows are created. therefore, since there are no discrepancies, the error is not mine.


Have you tried using tab completion to make sure that you're getting the file name right?
ex

tar -zvxf ndis[tab]

Baring that have you gotten the file to extract using file roller?

> 
2) The build essentials files are tar.gz files. I cannot open them with Gdeki-whatever (gtk I think, not looking at it now) so if these file are needed I cannot install them.

To download the debfile from the package listing you need to click on the link with your arch, and then select the mirror you want to use.

> 
**[SIZE=2]5) My two paramount questions  are: [/SIZE]**


5.1) A paramount question becomes is there away to get these tar.gz files in deb format? 

Yes, it's called checkinstall. Run through the build install process as normal and when you get to the make install step, run checkinstall instead.

> 
5.2) Is there away to convert these files into deb by downloading a deb pkg designed for this purpose?

[http://packages.ubuntu.com/gutsy/admin/checkinstall](http://packages.ubuntu.com/gutsy/admin/checkinstall)

Kinda tangental to the discussion at hand, but is there a specific reason you can't use the connection your posting from to down load packages from the repositories?

---

### Post by ctoaun on 2008-01-12
at the site

---

### Post by oldos2er on 2008-01-12
Install build-essential from your ubuntu live cd. Go to System, Administration, Software Sources, and make sure the box under 'Installable from CD-ROM/DVD' is checked.

---

### Post by ctoaun on 2008-01-12
> **oldos2er said:**
> Install build-essential from your ubuntu live cd. Go to System, Administration, Software Sources, and make sure the box under 'Installable from CD-ROM/DVD' is checked.

Of course I did that, not!:) Will do in a bit

It does not give me a checkbox. It gives me an emboldened "Installable from CD...DVD." says, "to install from DVD or Cd, insert the medium into the drive

---

### Post by ugm6hr on 2008-01-13
@ctoaun:

There are 2 separate lines of advice running in this thread.  That is why things are getting confusing.

You state that you **can** install .deb files, but you **can't** untar the.tar.gz files.  If that is true, then why don't you follow my advice that I gave last night?  You state you cannot do anything that requires internet - but you are clearly online at the moment.  I assume you have another computer that you can download files from, right?  If so - *download* the .debs I suggested, copy them to your Ubuntu Desktop and double-click.

If that is true - then my advice should be a lot easier than compiling ndiswrapper from source, which is what you are trying to do with the .tar.gz file, although you are clearly getting stuck at the very first stage.  Since compiling from source is not nearly as easy as installing a .deb (by your own admission), I still cannot follow why you haven't tried my procedure (or reported back on progress).

I have not seen this thread for a few hours - but figure the following have caused you problems:

1. You don't knwo which "Architecture" you have.  I think it is reasonable to say you have the **i386**, since my uname -a also states i686 (and I installed the 32-bit Ubuntu).  If you installed Ubuntu yourself, then you should remember it gave you option as to which type of computer you have (see screenshot attached at bottom).  i386 is the "Standard Personal Computer", while AMD64 is the "64-bit AMD and Intel".  I hope that clarifies this issue. (Also - see EDIT below)

2. You have clearly edited one reply, and I wonder whether that is because you have been unable to install cabextract with the .deb. If so, this will be because cabextract has dependencies that you don't already have installed.  I note you say you dual-boot with Windows.  Therefore, the *easiest* way to resolve this is to extract the driver **in Windows**, and merely copy the correct .inf and .sys files to Ubuntu.  All cabextract does is un-compress an .exe file, which is obviously easier to do in Windows.  In fact, assuming you installed the driver in Windows, those files should already be somewhere in your Windows installation (in a hidden folder).  You could just try searching for them (bcmwl5.inf and any other files in the same folder, specifically bcmwl5.sys).  There is another way to get cabextract *with its dependencies*, using an offline installer, but I'd just use Windows.

3. You do not need to use wget to download the driver - just put the ftp: address into a web browser ([ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)), it should download it for you.

PS: If you are still persevering with the untar procedure - post the results from this:
```
cd ~/Desktop
ls
```

EDIT: Have seen the next post - which also agrees you have i386 Ubuntu (32-bit).  They also agree you should try using the .deb files first rather than the .tar.gz files.
Your question about *converting* a tar.gz into a .deb is unnecessary, since the .deb files **already exist**, and just need to be downloaded (from where I linked them earlier).
You do not need build-essential if you are only using .deb files (as I am sure you have already realised).

Links: **Direct links to i386 .deb files** - install in this order!
[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/universe/c/cabextract/cabextract_1.2-2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/c/cabextract/cabextract_1.2-2_i386.deb)

---

### Post by skullmunky on 2008-01-13
wow, what a long and tangled thread.  kind of like the process of getting wireless to work often is, itself. :)

almost afraid to just add more noise here, but let me see if I can offer some help, and see if i get what the issues are ... 


*  I'm 99.99% sure you're using the i386 version, also known as the 32-bit version.  
* you want to install the wireless drivers, but the instructions involve using apt-get to download packages, which is obviously a catch-22.  the start of all this is the .tar.gz file of ndiswrapper you got from sourceforge, which is a less-convenient way of installing it...  ?

* if there's a way you could plug your laptop into an ethernet connection that might make the whole thing easier.  then you can use the commands that involve apt-get, etc, which is simpler than using the .tar.gz files.   or, if 

* my guess on what the correct uncompressing command is is this:

```

cd ~
cd Desktop
ls
tar -xzf ndiswrapper-1.51.tar.gz

```

i put the ls in there to get a list of the files just in case the file is named something different or it turns out it's not actually on the Desktop at all, or something wacky like that.

once you do get it uncompressed, the next step is to use the "make" command to compile it.  the .tar.gz file from sourceforge has the source code, which you then compile to create the actual program.  the process usually looks something like this:

```

cd ndiswrapper-1.51
make
sudo make install

```

.deb files are nice because you can just double-click them and they install.  apt-get and synaptic are even nicer because they download the .deb file for you AND install it.  so i'd say see if you can get those before working with the .tar.gz file anymore.

---

### Post by ugm6hr on 2008-01-13
> **skullmunky said:**
> ```

cd ndiswrapper-1.51
make
sudo make install

```

.deb files are nice because you can just double-click them and they install.  apt-get and synaptic are even nicer because they download the .deb file for you AND install it.  so i'd say see if you can get those before working with the .tar.gz file anymore.

One of the problems is the absence of build-essential to compile using make / install.  Thus, I would agree with the final statement.

---

### Post by ctoaun on 2008-01-13
> **ugm6hr said:**
> @ctoaun:

There are 2 separate lines of advice running in this thread.  That is why things are getting confusing.

You state that you **can** install .deb files, but you **can't** untar the.tar.gz files.  If that is true, then why don't you follow my advice that I gave last night?  You state you cannot do anything that requires internet - but you are clearly online at the moment.  I assume you have another computer that you can download files from, right?  If so - *download* the .debs I suggested, copy them to your Ubuntu Desktop and double-click.

See below

If that is true - then my advice should be a lot easier than compiling ndiswrapper from source, which is what you are trying to do with the .tar.gz file, although you are clearly getting stuck at the very first stage.  Since compiling from source is not nearly as easy as installing a .deb (by your own admission), I still cannot follow why you haven't tried my procedure (or reported back on progress).

I have not seen this thread for a few hours - but figure the following have caused you problems:



2. You have clearly edited one reply, and I wonder whether that is because you have been unable to install cabextract with the .deb. If so, this will be because cabextract has dependencies that you don't already have installed.  I note you say you dual-boot with Windows.  Therefore, the *easiest* way to resolve this is to extract the driver **in Windows**, and merely copy the correct .inf and .sys files to Ubuntu.  All cabextract does is un-compress an .exe file, which is obviously easier to do in Windows.  In fact, assuming you installed the driver in Windows, those files should already be somewhere in your Windows installation (in a hidden folder).  You could just try searching for them (bcmwl5.inf and any other files in the same folder, specifically bcmwl5.sys).  There is another way to get cabextract *with its dependencies*, using an offline installer, but I'd just use Windows.

3. You do not need to use wget to download the driver - just put the ftp: address into a web browser ([ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)), it should download it for you.

Yeah, I went to Mozila & got an FTP program, didn't need it though

PS: If you are still persevering with the untar procedure - post the results from this:
```
cd ~/Desktop
ls
```

EDIT: Have seen the next post - which also agrees you have i386 Ubuntu (32-bit).  They also agree you should try using the .deb files first rather than the .tar.gz files.
Your question about *converting* a tar.gz into a .deb is unnecessary, since the .deb files **already exist**, and just need to be downloaded (from where I linked them earlier).
You do not need build-essential if you are only using .deb files (as I am sure you have already realised).

Links: **Direct links to i386 .deb files** - install in this order!
[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.43-1ubuntu2_all.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/universe/c/cabextract/cabextract_1.2-2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/c/cabextract/cabextract_1.2-2_i386.deb)

Thanks! I am trying this windows route right now...however
Figured out the architecture last night shortly after. Did the deb thing last night after getting help from the forum,PeterJS?  The forum, wikki page could be indicted for being misleading. It did not say that it was just a link to mirrors as most sites do. I was told the red dots were what I needed, so I right-clicked and downloaded useless (perl php?) files. This I blame on the formatting of the page because a "control F" search of the page failed to produce the word mirror, so how was one to know. This directly led me to think that tar.gz was my only option since it was clearly available at the bottom of the page.It was not until last night that I learned that the page is just a link to the actual Ubuntu Mirrors.  I just learned (from the last post, someone name skull...) how to untar tar.gz. 

I'll let you know where this leads

---

### Post by ugm6hr on 2008-01-13
> **ctoaun said:**
> I'll let you know where this leads

If those .deb files download and install OK, then the rest of the commands should work as they are, assuming you put the files in the correct directories (specifically for cabextract).

Hopefully this should at least let you follow those instructions, which I presume you have checked are appropriate for your wifi card.

---

### Post by ctoaun on 2008-01-13
Thanks all, this is now solved.

In no particular order, special thanks to 
UGM6hr, erfahren PeterJS skullmunky

What I learned, so no one has to read through all six pages&#8221;

1) Tar.gz files are easiest to locate, untar and then install if they&#8217;re on the desktop. See replies 51-53. In some cases, it may be easier to copy commands into a text document before typing into the terminal. Copy the instruction into a text twice document, one above the other. Then add the file location and the file name to the second one. They should match. If they match, copy the second one into the terminal. This helped me to learn not to make type-o's, especially with sudo.

2)	Gdebi is great for a double-click install of deb files. This was answered for me in this [URL="http://ubuntuforums.org/showthread.php?p=4130073&posted=1#post4130073"]post
[/URL]
3)	Build essentials may be necessary to compile from source.

4)	Don&#8217;t get upset with yourself! Commands are only as good as the directions provided, so they are not always usable. In example, linmodems.technion.ac.il does not organize its info. Apparently, they&#8217;ve no concept of the flow chart approach. Organizing download, release notes and install information in a flow chart fashion would allow people with different yet similar needs to more easily find needed information. This concept has been used from agriculture to NASA, so I'm sure it would work. Additionally, they cannot apparently  separate critical information from less frequently needed information. Even the forum page alludes to this. We&#8217;d fired them long ago.

5)	Forum pages can be misleading. In example, this [page]("http://packages.ubuntu.com/gutsy/misc/ndiswrapper-common") says, "download &#8220;ndis wrapper.&#8221;
It does not say left click to go to the download mirror. In fact, unlike many sites, no where does it say &#8220;left-click on the word &#8220;all&#8221; to go to a download mirror,&#8221; which is the very important information! I spent hours trying to make useless files work & searching the net for no reason! How was I to know?

Again thanks all solved everything but [URL="http://ubuntuforums.org/showthread.php?p=4130907#post4130907"]wireless
[/URL]
Thread closed

---

### Post by skullmunky on 2008-01-15
congrats, glad its working. 

addendum about un-tar'ing.  

as someone mentioned a page or two back, "tab complete" is your friend.

what's that, you say?  just hit the TAB key while typing a long and elaborate filename, and the shell will fill in the rest for you.  that way you know you've got it right, cuts down on typos by a huge amount.

---

