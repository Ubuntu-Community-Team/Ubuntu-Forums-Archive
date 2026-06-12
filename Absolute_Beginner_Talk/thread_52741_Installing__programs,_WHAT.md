---
title: "Installing  programs, WHAT?"
date: 2005-07-28
forum: Absolute Beginner Talk
---

### Post by noid1037 on 2005-07-28
I have downloaded programs to install on the linux platform and dont know what to do!  For example, I downloaded air-snort, to my desktop.  The tar.gz file is there but I dont know what to do.  Should I download it to a specfic folder?  Then what?  I read the readme's but I dont know what program to run to get into the files they are talking about.  My learning curve is once I do it, I get it but since I have never done this .... you get it.

Wondered if someone can walk me thru it?  Thanks so much so when I have another program I am not lost and I can help others.  By the way, Unbuntu is a easy OS to convieve just ahving problems with the programs and such.

Thanks again
Noid-Tampa

---

### Post by aysiu on 2005-07-28
So air-snort isn't in the repositories? Have you tried looking for it using [Synaptic Package Manager?](http://www.nongnu.org/synaptic/action.html)

You may have to [enable extra repositories](http://ubuntuguide.org/#extrarepositories).

---

### Post by Sam on 2005-07-28
If it's not available in Synaptic, you should download the binary, then copy it to /opt or /home/<username>/opt, or download the source and compile it (see README or INSTALL files provided with the archive).

---

### Post by aysiu on 2005-07-28
[QUOTE=Sam]If it's not available in Synaptic, you should download the binary, then copy it to /opt or /home/<username>/opt, or download the source and compile it (see README or INSTALL files provided with the archive).[/QUOTE] According to [this website](http://www.artfiles.org/ubuntu.com/archive/pool/universe/a/) it's been in the universe repositories since June 29, 2005, so there should be no need to compile it from source.

---

### Post by Sam on 2005-07-28
[QUOTE=aysiu]According to [this website](http://www.artfiles.org/ubuntu.com/archive/pool/universe/a/) it's been in the universe repositories since June 29, 2005, so there should be no need to compile it from source.[/QUOTE]
I didn't check. So noid1037, add the extra repositories and type in a terminal
```
$ sudo apt-get install airsnort
```

---

### Post by [Cyanide] on 2005-07-28
I don't think his question was "Does this software come with Ubuntu", but rather how to install ANY kind of software that he's downloaded.

I too would like to know what the process is for installing ANY kind of software on Ubuntu...

---

### Post by aysiu on 2005-07-28
[QUOTE='[Cyanide]']I don't think his question was "Does this software come with Ubuntu", but rather how to install ANY kind of software that he's downloaded.

I too would like to know what the process is for installing ANY kind of software on Ubuntu...[/QUOTE] I think the answer would be the same--enable extra repositories and search the repositories. If it isn't there, then you can ask how to install it. I've yet to find a program I want (besides Opera) that isn't in the repositories.

---

### Post by dcraven on 2005-07-28
I don't know for sure, but there is a good chance that the tar.gz file he downloaded was a source tarball. This means that inside the tar.gz archive are nothing but plain text files that are meaningless to your computer until compiled. The compile process is not difficult (making some assumptions here of course) but might involve manually installing library dependancies and such.

The fact that you can, and in fact did download the source code to your program may seem like a bit of a pain, or maybe unusual. But, this is part of the reason some of us love Linux as we do! For those who have no use for source code, I'd like to join the others in this thread and suggest the official Ubuntu repositories.

Good luck, and have fun!
~djc

---

### Post by hod139 on 2005-07-28
While it is always easier to install from the ubuntu repositories via synaptic or apt (maybe we should promote aptitude over apt), or a .deb file, it doesn't hurt to know what a tar.gz file is.

A tar.gz file is a [gzip](http://www.gzip.org/) 'ed [tar](http://www.gnu.org/software/tar/tar.html)  file  :) 

What does that mean?  A tar file is simply a container or package containing, in this case, the source files to the program.  There is no compression in this container, so typically you will see the tar archive compressed using the gzip utility, hence the .tar.gz extension.  For more compression you can use [bzip2](http://www.bzip.org/) , which you will see sometimes as a .tar.bz2 file.  Basically, if you are familar with a zip or jar file, then that is what you can consider the tar.gz file to be.  It is a compressed archive containing many files, in this case the source code to the program.

The first step is to uncompress the archive.  You can right click it and use the gui tools available, or on the command line you can type
> tar -xzvf foo.tar.gz 
where x means extract, z means it is gzip'ed (use j for bz2 and leave blank for no compression), v means be verbose (print the names of the files as they are extracted), and f is followed by the file to extract. For all the juicy details on tar see the man pages (man tar).

The next step is to go to the extracted contents of the archive, and look for a README file and/or an INSTALL file.  These files will tell you how to install but typically you only have to type 3 commands:
> 
./configure
make
sudo make install

and cross your fingers.  Many things can go wrong (wrong compiler version, missing libraries, etc...) and that is why prebuilt packages are _so_ much better.

Hopefully this helps explain things

---

### Post by cwaldbieser on 2005-07-29
Additionally, there is program called "checkinstall" that you can get from the repositories that will do the ./configure, make, make install steps for you and integrate the installation with the package manager (so you easily uninstall it later).

---

### Post by poofyhairguy on 2005-07-29
This is awesome wiki page

[https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29](https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29)

then type the name of the program in the "run" thing.

---

