---
title: "Instaling programs without Synaptic"
date: 2005-08-08
forum: Absolute Beginner Talk
---

### Post by ad noiseam on 2005-08-08
Hello,

New to Linux, sorry.

From reading this board, I have understood that the vast majority of the software one could need / use in Ubuntu must be installed through Synaptic. However, I have found a case where I can not use it, and need a bit of help.

I need to use the new version of "File Roller" (version 2.10.3), because it can uncompress .rar archives. The one that comes in Ubuntu does not do this.

If I look for "File Roller" in Synaptic, I get version 2.10.1.

So... I went to File Roller's homepage, downloaded the new version, extracted it, read the "install file", and here comes trouble.

Basically, the installer say to do three things.

**1. type "./configure" in the terminal in the "file roller" directory.**

I get:
```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

```

**2. type "make" in the terminal in the "file roller" directory.**

I get:
```

make: *** No targets specified and no makefile found.  Stop.

```


**3. type "make install" in the terminal in the "file roller" directory.**

I get:
```

make: *** No rule to make target `install'.  Stop

```

I guess my problem is that I have absolutely no clue about Linux and how to install a program. Still, this kind of shows a limit to Synaptic. Can anybody help?

---

### Post by heimo on 2005-08-08
Are you sure you need the latest File Roller and not some other package (unrar or something like that)? If you need to compile new software, you need to have compiler and possibly other stuff (sometimes software libraries) installed. Install package [build-essential]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=build-essential&searchon=names&subword=1&version=hoary&release=all") using Synaptic and try again. :)

---

### Post by SGC on 2005-08-08
You need a compiler:
sudo apt-get install build-essential

* You can't do make or make install if ./configure ended with an error
* install checkinstall (apt-get install checkinstall) then replace (make install) with (checkinstall -D make install) to create a debian package that you can install it or remove it essialy later without recompiling.

---

### Post by ad noiseam on 2005-08-08
[QUOTE=heimo]Are you sure you need the latest File Roller and not some other package (unrar or something like that)?[/QUOTE]

I guess not. Synaptic does not return any result when searching for "rar".

[QUOTE=heimo] If you need to compile new software, you need to have compiler and possibly other stuff (sometimes software libraries) installed. Install package [build-essential]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=build-essential&searchon=names&subword=1&version=hoary&release=all") using Synaptic and try again. :)[/QUOTE]

Done, that. I've typed "./configure" again, got a lot longer list of lines, but neither "make" nor "make install" do anything at all. :(

It's really a bummer. Depending on Synaptic to install anything make it really hard for people to switch to Linux or Ubuntu, IMHO. :( I'll keep trying.

---

### Post by Kimm on 2005-08-08
go to [www.ubuntuguide.org](www.ubuntuguide.org) and do this step:

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

now type, "apt-get install rar" in console, that should get you running :)

[i]Edit:

and you dont have to rely in Synaptic to install software, that would be just foolish. you can also install software from source (I see you tried that) and directly from *.deb packages (or the Red Hat equailent *.rpm). By typing 

"dpkg -i <packagename>.deb" in your console.

If you realy realy cant do without a package of a later version then the one in synaptic you can make a search at debians webbsite, there you can usualy find the latest versions of most software for linux. Firefox that comes bundled with ubuntu should have "deb search" available (click the google icon).

After a quick search I found this:

[http://packages.debian.org/unstable/gnome/file-roller](http://packages.debian.org/unstable/gnome/file-roller)

But please take this warning: if you use this package, or any other package downloaded from debian you must realize that there might be unforfilled dependencies and that the package might not work. ofcourse... if its minor you can make another search but that usualy leads to yet another search.
I recommend you try to build file-roller from source... I'll try it myselfe and get back to you if I have any luck :) [/i]

---

### Post by heimo on 2005-08-08
[QUOTE=ad noiseam]Depending on Synaptic to install anything make it really hard for people to switch to Linux or Ubuntu, IMHO. :( I'll keep trying.[/QUOTE]

IMHO, Synaptic / apt-get makes life easy, and I'm quite sure Linux newbies will agree after they've familiarized themselves with its potential. :) It's a great system and most of the software is there - hard thing is to know which program to use, which package to install.

Great place to search Ubuntu packages:
[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

Hopefully you get FileRoller to work with rars following Kimms advice. (Thanks Kimm!)

---

### Post by ad noiseam on 2005-08-08
[QUOTE=Kimm]"dpkg -i <packagename>.deb" in your console.[/QUOTE]

I feel like an idiot, but where do I get the ".deb" file? The .gz archive I got from File Roller does not include any. :( Do I have to pack this myself somehow?

---

### Post by ad noiseam on 2005-08-08
[QUOTE=heimo]IMHO, Synaptic / apt-get makes life easy, and I'm quite sure Linux newbies will agree after they've familiarized themselves with its potential. :) It's a great system and most of the software is there[/QUOTE]

Yes, it is true. Still, it gives the weird impression that you have to wait for somebody to check in the software before being able to install it. I know that this helps new users (like me) a lot (well, it most cases, see this thread), but it gives a weird after taste.

---

### Post by Kimm on 2005-08-08
you get .deb files from the people that write the program... or perhaps from a dist like Ubuntu. If you download a *.tar.gz yuor not likely to find the .deb there, thats usualy a file that contains the sources of the program. 

When you ran ./configure on the sources of file-roller you most likely forgot to read the output and missed some dependency errors, when compiling from source dependencies arnt corrected automaticly (pretty obvious)...

I'm running make right now... if it succedes I'll give you a .deb of my build, your probably better of with that one then with one from debian!

---

### Post by Kimm on 2005-08-08
build was successfully, but I'm afraid the creation of the package will be prosponed, as my old CRT screen just died when I was writing the control file...

I'm writing this on my dads windoze box.

---

### Post by Kimm on 2005-08-08
Ok, I got my hands on an **old** screen and managed to complete the package.
Here you go:

[http://i.domaindlx.com/MrKimm/file-roller_2.10.3-1_i386.deb](http://i.domaindlx.com/MrKimm/file-roller_2.10.3-1_i386.deb)

I suggest you enable extra repositories before you install it though.

... Tomorrow = trip to computer store ;-)

---

### Post by tonysathre on 2005-08-08
you need gcc and i think cpp, c++, g++. use synaptic to get them. then try ./configure again

---

### Post by poofyhairguy on 2005-08-08
[QUOTE=ad noiseam]
I guess my problem is that I have absolutely no clue about Linux and how to install a program. Still, this kind of shows a limit to Synaptic. Can anybody help?[/QUOTE]

You need a program called unrar nonfree. Search for unrar in synaptic and it will work.  Reboot (or not) and file roller will just work.

No need to do the (painful) thing called installing programs from source code.

---

