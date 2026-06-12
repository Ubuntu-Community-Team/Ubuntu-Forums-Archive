---
title: "How to copy a driver from the CDROM to the src directory on the harddrive"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by marianlibrarian on 2006-11-26
I can't get any more beginner than this:
How do you copy files from the CDROM to the src directory on the harddrive?

I found the drivers for my DSL modem and the instructions say: 

Go to directory src. Type:

make
sudo cp cayman3341.ko /lib/modules/ 'uname - r'/kernel/dirvers/usb/net/
sudo depmod

Then it says:
After that you can plug the modem in and configure your new network device.

I need to know how to "go to directory src", and how do I get the files that are on the CDROM to get on the harddrive?

Thank You.

---

### Post by christhemonkey on 2006-11-26
To change directory use the `cd` command.
```
cd /new/location 
```

So in your case:
```
cd /media/cdrom0/src/ 
```

(or something similar to that!)

---

### Post by marianlibrarian on 2006-11-26
Thank you.

I found the terminal thing under accessories. I don't know any other way to get to the place to type in "commands".

I can't tell if the sequence of commands given are 3 separate lines or one single line...

when I type in the word make it says "command not found" 

what is "make"? There is a file called make in the src directory on the CDROM. There is no src directory on the harddrive. The way the instructions are stated, it looks like I am supposed to go to the src directory on the CD and then type in the 3 commands. But when I go to the src directory on the CD, I can't get past the first command "make".

Are these proper commands to install a driver in Ubuntu?

---

### Post by LLRNR on 2006-11-26
Marianlibrarian, yes, the Terminal from Applications -> Accessories IS the way to type in commands. The "cd" command is similar to the one in DOS. The three lines of code given in the manual are in fact three different lines, so you must type them in each at a time.

The make command failed because in order to use it you need a special package installed on your system. So, from the terminal, you need to enter:
```
sudo aptitude install build-essential
```
It will ask you for your password, and then you will have to confirm (with a 'y') that you accept the install of this package. When it's all done, from the directory (go there with cd /media/cdrom/src) enter the 3 commands given in your manual, one at a time.

LLRNR

---

### Post by christhemonkey on 2006-11-26
To install a driver with make, you will need to install the utility make.

If your online with ubuntu you can just type:
```
sudo apt-get install build-essential 
```

But just noticed that your setting up your internet connection, so you will need to visit [packages.ubuntu.com](packages.ubuntu.com) and search for make (making sure to download all the things it needs which are listed below it)


The src directory is indeed on the cd.

And yes sorry, all commands given here are written into a terminal.

---

### Post by marianlibrarian on 2006-11-26
> **christhemonkey said:**
> To install a driver with make, you will need to install the utility make.

If your online with ubuntu you can just type:
```
sudo apt-get install build-essential 
```But just noticed that your setting up your internet connection, so you will need to visit [packages.ubuntu.com]("http://packages.ubuntu.com") and search for make (making sure to download all the things it needs which are listed below it)


The src directory is indeed on the cd.

And yes sorry, all commands given here are written into a terminal.

Overwhelmed!

There are two ways to search:
Search Package Directories
Search the Contents of Packages

I can also Browse through packages by selecting Dapper or Dapper Back Port(?).

I chose search the contents of packages using the term "make" and the next screen had:
**FILE                                                       PACKAGE**   usr/bin/make						    [devel/make]("http://packages.ubuntu.com/dapper/devel/make")
usr/lib/apt-build/make					    [devel/apt-build]("http://packages.ubuntu.com/dapper/devel/apt-build") [[COLOR=red]universe[/COLOR]]
usr/lib/freebsd/make					    [devel/freebsd5-buildutils]("http://packages.ubuntu.com/dapper/devel/freebsd5-buildutils") [[COLOR=red]universe[/COLOR]]
usr/share/doc/aegis/examples/config.example/make	    [devel/aegis]("http://packages.ubuntu.com/dapper/devel/aegis") [[COLOR=red]universe[/COLOR]]
usr/share/doc/pugs-doc/talks/perl6-apw2005/make		    [interpreters/pugs-doc]("http://packages.ubuntu.com/dapper/interpreters/pugs-doc") [[COLOR=red]universe[/COLOR]]
usr/share/lintian/overrides/make			    [devel/make]("http://packages.ubuntu.com/dapper/devel/make")
usr/share/texmf/source/generic/xypic/src/MAKE		    [tex/tetex-src]("http://packages.ubuntu.com/dapper/tex/tetex-src") [[COLOR=red]universe[/COLOR]]
usr/share/ucblogo/helpfiles/make			    [devel/ucblogo]("http://packages.ubuntu.com/dapper/devel/ucblogo") [[COLOR=red]universe[/COLOR]]
After staring at that for a while, I thought the words build and universe looked pretty good, so I clicked on that link. The next screen has a description and a list of other packages related to this one, and finally it has "download" this package after that. Then there are 3 architectures. So I figured i386 sounded alright. I click on that link and this happens:
You have searched for the contents of *apt-build* in *dapper*, architecture *i386*.
Package contains 16 files, displaying files 1 to 16.
**FILE                                                       PACKAGE**   usr/bin/apt-build					    [devel/apt-build]("http://packages.ubuntu.com/dapper/devel/apt-build") [[COLOR=red]universe[/COLOR]]
usr/lib/apt-build/apt-build-wrapper			    [devel/apt-build]("http://packages.ubuntu.com/dapper/devel/apt-build") [[COLOR=red]universe[/COLOR]]
usr/lib/apt-build/c++					    [devel/apt-build]("http://packages.ubuntu.com/dapper/devel/apt-build") [[COLOR=red]universe[/COLOR]]
usr/lib/apt-build/cc					    [devel/apt-build]("http://packages.ubuntu.com/dapper/devel/apt-build") [[COLOR=red]universe[/COLOR]]
usr/lib/apt-build/g++					    [devel/apt-build]("http://packages.ubuntu.com/dapper/devel/apt-build") [[COLOR=red]universe[/COLOR]]
usr/lib/apt-build/g++-i486-linux-gnu			    [devel/apt-build]("http://packages.ubuntu.com/dapper/devel/apt-build") [[COLOR=red]universe[/COLOR]]
usr/lib/apt-build/gcc					    [devel/apt-build]("http://packages.ubuntu.com/dapper/devel/apt-build") [[COLOR=red]universe[/COLOR]]
usr/lib/apt-build/gcc-i486-linux-gnu			    [devel/apt-build]("http://packages.ubuntu.com/dapper/devel/apt-build") [[COLOR=red]universe[/COLOR]]
usr/lib/apt-build/make					    [devel/apt-build]("http://packages.ubuntu.com/dapper/devel/apt-build") [[COLOR=red]universe[/COLOR]]
usr/share/apt-build/Release				    [devel/apt-build]("http://packages.ubuntu.com/dapper/devel/apt-build") [[COLOR=red]universe[/COLOR]]
usr/share/doc/apt-build/README.Debian			    [devel/apt-build]("http://packages.ubuntu.com/dapper/devel/apt-build") [[COLOR=red]universe[/COLOR]]
usr/share/doc/apt-build/changelog.gz			    [devel/apt-build]("http://packages.ubuntu.com/dapper/devel/apt-build") [[COLOR=red]universe[/COLOR]]
usr/share/doc/apt-build/copyright			    [devel/apt-build]("http://packages.ubuntu.com/dapper/devel/apt-build") [[COLOR=red]universe[/COLOR]]
usr/share/man/es/man1/apt-build.1.gz			    [devel/apt-build]("http://packages.ubuntu.com/dapper/devel/apt-build") [[COLOR=red]universe[/COLOR]]
usr/share/man/fr/man1/apt-build.1.gz			    [devel/apt-build]("http://packages.ubuntu.com/dapper/devel/apt-build") [[COLOR=red]universe[/COLOR]]
usr/share/man/man1/apt-build.1.gz			    [devel/apt-build]("http://packages.ubuntu.com/dapper/devel/apt-build") [[COLOR=red]universe[/COLOR]]
But these are not actual files or links to files to download. If you click on any of those links it takes you to the same page and if you click on the download link it takes you to the above page and round and round and round and....

I am so lost. And I have to get two little kids ready to go to church and I have to walk away from this right now.

---

### Post by christhemonkey on 2006-11-26
Sorry, i will try to be a little clearer!
(im assuming your using edgy eft 6.10? and not dapper drake 6.06 LTS)
[LIST]

[*]First vist this site: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

[*]Then type what you want to search for in the "Search Package Directories Box", which in this case is "make"

[*]This will take you here: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=make&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=make&searchon=names&subword=1&version=edgy&release=all)

[*]Then look for what you want, Which for you is `make`.

[*]Click the link saying edgy just underneath make, which will take you here: [http://packages.ubuntu.com/edgy/devel/make](http://packages.ubuntu.com/edgy/devel/make)

[*]Then you can see the dependencies, in this case its just libc6 (>= 2.4-1) ((which is installed by default in this case)

[*]Then click on the link for your architecture in the download make section, your architecture is probably i386 unless you have a mac or are running the 64bit edition.

[*]This will take you here: [http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fm%2Fmake-dfsg%2Fmake_3.81-2_i386.deb&md5sum=818d9b86d322629e5f218e8a101157c9&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fm%2Fmake-dfsg%2Fmake_3.81-2_i386.deb&md5sum=818d9b86d322629e5f218e8a101157c9&arch=i386&type=main) Where you need to select a mirror that is close to you.

[*]Click to open with Gdebi Package Installer

[*]Select to install package

[*]Now this package has been installed!

[/LIST]

The modem driver install may need more than just make, but post back the output if the commands they gave you fail.

---

### Post by marianlibrarian on 2006-11-26
> **christhemonkey said:**
> Sorry, i will try to be a little clearer!
(im assuming your using edgy eft 6.10? and not dapper drake 6.06 LTS)[LIST]
[*]First vist this site: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
[*]Then type what you want to search for in the "Search Package Directories Box", which in this case is "make"
[*]This will take you here: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=make&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=make&searchon=names&subword=1&version=edgy&release=all)
[*]Then look for what you want, Which for you is `make`.
[*]Click the link saying edgy just underneath make, which will take you here: [http://packages.ubuntu.com/edgy/devel/make](http://packages.ubuntu.com/edgy/devel/make)
[*]Then you can see the dependencies, in this case its just libc6 (>= 2.4-1) ((which is installed by default in this case)
[*]Then click on the link for your architecture in the download make section, your architecture is probably i386 unless you have a mac or are running the 64bit edition.
[*]This will take you here: [http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fm%2Fmake-dfsg%2Fmake_3.81-2_i386.deb&md5sum=818d9b86d322629e5f218e8a101157c9&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fm%2Fmake-dfsg%2Fmake_3.81-2_i386.deb&md5sum=818d9b86d322629e5f218e8a101157c9&arch=i386&type=main) Where you need to select a mirror that is close to you.
[*]Click to open with Gdebi Package Installer
[*]Select to install package
[*]Now this package has been installed![/LIST]
The modem driver install may need more than just make, but post back the output if the commands they gave you fail.

I am using dapper 6.06 and I had the steps all the way to "then click on your achitecture" that is where everything is different. make for dapper does not take you to a download page with a mirror close to anybody it just does that listing thing like I put in the previous post. Try it and see only use dapper not edgy. I followed exactly what you said but the 8th step is different for dapper.

---

### Post by christhemonkey on 2006-11-26
Ok, for dapper, your search will lead you to here:
[http://packages.ubuntu.com/dapper/devel/make](http://packages.ubuntu.com/dapper/devel/make)

An then to here:
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fm%2Fmake%2Fmake_3.80%2B3.81.b4-1_i386.deb&md5sum=984a347383e53e343b4566aa4641ca24&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fm%2Fmake%2Fmake_3.80%2B3.81.b4-1_i386.deb&md5sum=984a347383e53e343b4566aa4641ca24&arch=i386&type=main)

And it does not matter if there is not a mirror close to you anyway, it just might increase the speed marginally of the download.

---

### Post by CatKiller on 2006-11-26
Actually, build-essential is on the Ubuntu installation cd.

---

### Post by marianlibrarian on 2006-11-26
If Stupidity got us into this mess, 
then why can&#8217;t it get us out?

Well, I really like your signature, even when the reality of it is like a slap in the face. :)

Thanks for the help. I may revise my signature - Open mind?? Somewhere along the way my brain DID fall out. :0

---

### Post by szf on 2006-11-26
> **marianlibrarian said:**
> 
... I may revise my signature - Open mind?? Somewhere along the way my brain DID fall out. :0

I caught this thread this morning - I was penning a response when I did a refresh and saw that my input was already redundant... :) 

Compiling your own driver is *difficult*, so I tip my hat to you. If there's any chance you can enlist lazyweb and ubuntuforums, maybe you won't have to go through this process. It was an ADSL modem, yes? What are your findings so far?

---

### Post by marianlibrarian on 2006-11-26
> **szf said:**
> I caught this thread this morning - I was penning a response when I did a refresh and saw that my input was already redundant... :) 

Compiling your own driver is *difficult*, so I tip my hat to you. If there's any chance you can enlist lazyweb and ubuntuforums, maybe you won't have to go through this process. It was an ADSL modem, yes? What are your findings so far?

Well, after doing everything in this thread, I found that I did not have administrative privilages. I was sure that I had given my user name adminitrative privalages but it didn't stick? So I figured that one out [http://www.ubuntuforums.org/showthread.php?t=241964&page=2&highlight=the+underlying+authorization+mechanism+%28sudo%29+does+-allow+you+to+run+this+program](http://www.ubuntuforums.org/showthread.php?t=241964&page=2&highlight=the+underlying+authorization+mechanism+%28sudo%29+does+-allow+you+to+run+this+program). 

I typed in the commands from the beginning post and got some errors when I used the terminal. So I went to the file manager and double clicked each of the two files that were in the src directory on the cd. THen I checked the device manager and sure enough - there was the device for netopia. Too bad the driver doesn't work. But now I know how to install one - sort of?

My other alternative is not to use the USB interface on the modem but to use ethernet. So I will have to get an ethernet card and install --- hardware! 8-[

Anyway, that is where things are now. I am trying to get a grip on using this operating system because I will be installing this on some of my computers at my library. This system is an old system that I almost threw away and thought this would be a good way to try and salvage it and not pollute. But for it to be useful I have to have internet access on it. My poor husband will get this machine if I ever get internet access on it.

Thanks for ALL the help I got here. :KS

---

### Post by CatKiller on 2006-11-26
> **marianlibrarian said:**
> My other alternative is not to use the USB interface on the modem but to use ethernet. So I will have to get an ethernet card and install --- hardware! 8-[

That's not too bad. Ethernet is a fairly straightforward option, and there's a **lot** of information out there on how to do it.

Good luck!

---

### Post by szf on 2006-11-26
> **marianlibrarian said:**
> 
My other alternative is not to use the USB interface on the modem but to use ethernet. So I will have to get an ethernet card and install --- hardware! 8-[


If you're willing to try the hardware ethernet option - send me an e-mail through the forum. I can send you an Intel Pro100 PCI card - this is a card that has worked with Linux for a good long time (e100/e1000 driver support).

---

