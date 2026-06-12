---
title: "Beginner With Culture Shock"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by Frederick J. Harris on 2007-04-12
This is my first post!  Just a few days ago I successfully managed to get my laptop set up as a dual boot XP/Edgy Eft machine.  I was impressed.  I can see that a lot of work went into 
this.  Right off the bat my widescreen on my laptop configured well, and the sound card worked too.

My initial exhilaration phase has ended though and unfortunately I seem to now be falling into a state of 'culture shock'.  I hadn't realized the phenomenal extent to which this whole Linux/Ubuntu experience is based on being 'online', i.e., internet connectivity.  My main objective for acquiring Linux/Ubuntu is to explore further opportunities to do application
programming.  However, I have not yet figured out a way to acquire the programming tools I need without being online WITH LINUX.

My Windows World consists of high speed broadband internet access at work, however, I am not allowed to connect personal machines to their network, so that doesn't seem to help me with my new Linux endeavors.  At home I have a dial up account and am also within range of unsecured wireless networks with which I am able to easily connect with Windows.  So you see, it isn't that I have anything against being online or am in anyway unfamiliar with it, it is just that I find myself in what I consider to be the somewhat unusual predicament of having a really cool and neat operating system on my computer which seems to be nearly worthless to me...

if(ONLINE == TRUE && ONLINE_WITH_LINUX == TRUE)
{
   Proceed();
}
else
{
   DealWithWindowsVista();
   exit(1);
}   

My Linux skills are not yet developed enough to undertake the rather difficult process of getting Win-Modems or unsupported wireless cards working.  The only real alternative I can see at this time is signing up for DSL service at home, which will more than double my monthly connection costs.  I suppose I had taken for granted the Windows model of acquiring and installing software would apply here in Linux, but it doesn't seem to.  In that world I'd somehow get the software I needed onto a floppy or CD or in a directory of my choosing and install it from there.  In this Ubuntu world it seems I can either...

Add/Remove Applications   >>  Programming

or

Synaptic Package Manager  >>  Development

or

sudo apt-get install build-essential

...however, all seem to relie on not just being online, but being online with Linux.  Am I making some faulty suppositions here?  This is only day 3 or 4 in my Linux life, so I realize I could and probably am wrong.  But I do have several Ubuntu books which I just bought, and in them are directions for getting such things as ndiswrapper working, so that I can get a wireless card working, so that I can connect to the internet with Linux, but 
ndiswrapper-utils-1.8 needs to be downloaded with Synaptic Package Manager or the Terminal which all require an active connection to the internet.  This is the very definition of a Catch-22 situation!  And the fact that I have internet access all over the place doesn't seem to help me!  With Ubuntu it seems that I have to be online before I can get online!  

Please don't take any of these comments in a negative way as I'm still very enthused about Linux and Ubuntu.  I can clearly see that this is neat stuff.  I'm not giving up yet.  I'm just frustrated about this impasse I've reached where I can see all these programming tools I desperately want such as the GNU C and C++ compilers, but I can't have them because the only way I can have them is if Ubuntu, connected to Ubuntu's software repositories,
downloads and installs them for me.  

There is finally a question here.  If I do sign up for a broadband DSL account at home is it virtually guaranteed that I'll be able to get online without problems with my new and perfectly working 6.1 Ubuntu distribution?  Further, without the Catch-22 situation of
having to download any more software through a Ubuntu connection I don't have?  This is really the only 'out' I can see.  Perhaps my ISP will allow me to bring my laptop in to see if it will connect under Ubuntu before I have to fork out the cash.  I'll have to find that out.

Possibly another question, if I havn't lost your attention!  Is there a way of downloading software using Windows, and either storing it on a CD/DVD or partition Ubuntu can read, and then directing Ubuntu to install the software from there instead of all this Synaptic Package Manager/Repository stuff that is at the heart of my difficulties?

---

### Post by annda on 2007-04-12
you can download any available package via a browser. they are all here:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

just make sure you download the dependencies too - they are all listed.

once you have those packages on a cd or usb flash disk, you can simply double-click to install them. just start with clicking the dependencies.

that way, you will have an experience similar to my earlier attempts to make friends with .rpm packages on RedHat and Mandrake. Debian-based systems, which use .deb packages, are more user friendly because they track, download and install all needed packages automatically. but there is no reason you couldn't do it manually.

UPDATE: if you are worried about network compatibility, buy a linux-supported wifi card (no ndiswrapper needed). ethernet should work without problems in any case. and before you get a DSL account and order a modem/router, search the forums to find out if it's supported out of the box.

---

### Post by bcmiller on 2007-04-12
I think the answer is to download the packages you need in windows and burn them to CD.  I think you should be able to visit the sites that appear in your sources list and get the files you need in order to get your wireless running.  From that point you will be under your own power.

If you did get DSL you would be online instantly.

el oh el... once again I am a worthless echo

---

### Post by Duckyspetrie on 2007-04-12
I'm a noob too, but my advice is to either download Feisty 7.04 beta or wait 1 week until the final release comes out. I had the same problem as you (kinda) with 6.10 but 7.04's wireless capabilities worked fine straight out the box. Go to linux-laptop.com and find your computer to set up wireless.

---

### Post by Denis on 2007-04-12
Some people have already suggested downloading the software packages on a computer connected to the internet and burning those packages on a CD. 

An easy way to do this is to
[LIST]
[*]open Synaptic
[*]Mark any software you would like to install (Synaptic will automatically check for dependencies)
[*]Instead of clicking "Apply", chose **generate package download script** in the File menu. 
[*]Open the script you have generated and you will find a list of the packages you've selected to install
[*]You can use this list to download the packages on a computer connected to the internet
[*]Save these packages on a CD, a USB stick etc.
[*]In your Ubuntu system you can open those packages and install them
[/LIST]

You can also download the Ubuntu DVD, which contains more software, and configure Synaptic to use the DVD as a "repository". To do this chose "Add CD" in the Edit menu of Synaptic. You can even use your CD, although I don't know if it contains much software. 

I hope this helps you out. So, if you have the packages on a CD, you don't need an internet connection more than you need it in Windows.

---

### Post by zvacet on 2007-04-12
Here is something to enable your dial up.
[https://help.ubuntu.com/community/DialupModemHowto]("https://help.ubuntu.com/community/DialupModemHowto")

---

### Post by oilchangeguy on 2007-04-12
this problem is simple to solve. get a highspeed internet connection. most cable and phone companies have entry level packages available, with pricing at or near dial-up prices. and your connection speed will probably be increased from the maybe 50kps, to 300-500kps. for the same money. this is a no brainer.

---

### Post by Frederick J. Harris on 2007-04-12
Thanks Very Much annda, bcmiller, duckyspetrie, and Denis!  I'm in assimilation mode now on these suggestions, and I'll keep working on it till I get it worked out.  Excellent points on the
wireless card and checking first on router compatibility!  Thanks!

---

### Post by adriantry on 2007-04-12
Hi Frederick

Here are two more suggestions that might help:

1. You could purchase an external dial-up modem. Many of these will work out of the box with Ubuntu. I've done this on several computers in the past with great results.

2. You could use a Linux distro that comes on multi CDs or a DVD. That way you can install additional programs from the CD or DVD instead of having to download them. Some options are Debian, openSUSE, Fedora and Mandriva.

Adrian

---

### Post by wormser on 2007-04-12
You can get DSL for under $15 a month.  Just google [DSL Deals]("http://www.google.com/search?q=dsl+deals&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a").  Not having high speed internet these days is like not having running water!  You are going to have questions or need additional packages, so you might as well drop $15 a month for DSL.

---

### Post by Boztech on 2007-04-12
If you are *truly* interested in developing in Linux you need to do yourself the favor of getting broadband internet.  Much of the Linux development process is online research/collaboration thru mailing lists,etc.  Dial-up is truly obsolete in modern PC technology.  

Since you alluded that you can get DSL we can assume you don't live in a remote rural area where only relatively expensive satellite broadband is available.  Typical DSL costs are less than $30/m.  Nothing personal, but if you can't afford the extra $10-20/m over dial-up costs, you have a big budget problem and you should probably concentrate on addressing that before anything else.

Good luck.

---

### Post by FuriousLettuce on 2007-04-12
If you only need intermittent access, you said that there were unsecured networks you could access through Windows. The way your post reads, it implies that you can't do this in Linux - does your wireless not work properly (not that I'm condoning piggybacking)?

---

### Post by Frederick J. Harris on 2007-04-15
No, my wireless isn't working in Linux because I have one of those miserable BroadCom cards that require nDisWrapper, and I can't get nDisWrapper and follow the instructions in my Ubuntu book to set up nDisWrapper
because my Synaptic Package Manager freaks out when I attempt to install anything due to the fact that my
sources.list file is apparently telling it to go to the internet to get the package.....  See where I've been!  Catch 22.

Not that I'm admitting to anything you know, but somehow or other, I don't remember exactly how, I've managed to come by the nDisWrapper deb files, as well as 25 or 30 deb files comprising the entire build-essential package, and somehow those files found their way to my Windows C drive, which drive is of course accessable from Ubuntu.

That being the case, how do I install all that stuff?  The various paths in my Sources.list file certainly aren't doing me any good.  Could I just remark out the entirety of that file and put one reference in it to the location of the various packages on my Windows partition, so that Synaptic Package Manager uses that instead as my 'Repository'.  If I could do something like that I'd be able to effectively make an end run around my present Catch 22 predicament.

---

### Post by FuriousLettuce on 2007-04-15
This should help you: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-c49fa124c9a644ddc4d126256060b93888fe0be3](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-c49fa124c9a644ddc4d126256060b93888fe0be3)

---

### Post by annda on 2007-04-15
you can burn those packages to cd and in synaptic settings > repositories > third-party software add the cd to to the repositories' list.

---

### Post by Frederick J. Harris on 2007-04-15
Hello Annda!  Yes, I'm still working on this stuff.  I spent a great deal of time attempting to follow your and Denis' instructions, and that led me to studying all about 'Repositories'.  I followed your link, I believe [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and I downloaded to the best of my ability all the build-essential packages, and all their dependencies.  Then, in snooping around my Ubuntu installation I found various files that looked liked compilers to me such as gcc-4.1, gcc-4.1 and so on. Also, when I opened Synaptic Package Manager I found that some of the packages contained in the build-essential package had green rectangles associated with them. This raises to me the broader question of whether or not compilers and linkers are installed by default as part of an installation?  This might be getting off topic and perhaps I ought to start another thread in Programming about it, but I'll raise it here anyway.  So perhaps I can command line compile right now???????  I have the GNU C/C++ compilers for Windows on that installation.  I could perhaps check the compiler output to see what the compiler switches are.  I usually do any command line compiling I do in Microsoft's Visual Studio with VC 6.0 and I'm not familiar with the compiler/linker options in GNU C.

I'm moving as fast as I can on several fronts to solve this connectivity problem of mine, but I'm anxious to start
coding right away.  To me, in terms of means and ends, the 'End' isn't to 'be online', it is to code.  If I need broadband to work with Linux I'll get it.  But I'm trying to be careful and follow your advice about double checking with my ISP as to whether their modems/routers will work with Linux , 'out of the box'.

Downloaded the link above and studying it.  Thanks!

---

### Post by FuriousLettuce on 2007-04-15
If you want to test if you have the compilers installed (if Synaptic gives green rectangles for build-essentials, you should do), simply type a hello world program. Open a terminal (Applications -> Accessories -> Terminal), then type
```
nano hello.c
```
this opens a lightweight terminal text editor called nano. Type the following in (I'm sure you know how to hello world, I'm not attempting to be patronising, just thorough)
```
#include <stdio.h>
int main(void)
{
          puts("Hello World");
          return 0;
}
```
Type ctrl and x together, then type y and press enter. This saves the file as hello.c. Next, compile it:
```
gcc -ohello hello.c
```
then attempt to run it by doing 
```
./hello
```
if it all works fine, gcc is installed! To see offline info on various switches etc, do 
```
man gcc
```
man is Unix's manual program - simply type man X, where X is the name of the program you want info on, and you'll get a manual in standard formatting explaining all the options for that particular program.

Sorry if the example was patronising, I'm just trying to take you through each step :)

---

### Post by Frederick J. Harris on 2007-04-15
Thanks for the help FuriousLettuce.  Unfortunately, it didn't seem to work.  Close, but no cigar!  The compiler appears to be there, as I thought, but apparently all the usual headers are missing.  All I added to your program was a getchar();  in case it would just flash by if it compiled, but the compiler gave me an error that no such file as stdio.h existed.  Imagine that!

Well, it was worth a try.  I've got all those deb files from build-essential download.  Below is a listing from Windows.  The ones with a 'match' to the right are ones that were highlighted in green in Synaptic.  From your previous link I've come to understand that if I copy a deb file I want to install to my /home directory I can issue a command something like this to cause dpkg to install it...

sudo dpkg -1 libc6-dev_2.4-1ubuntu12_i386.deb

???  I'm not sure which ones to try to install first though.... 

belocs-locales-bin_2.4-1ubuntu6_i386.deb
binutils_2.17-1ubuntu1_i386.deb
build-essential_11.3_i386.deb                          match
coreutils_5.96-5ubuntu4_i386.deb
cpio_2.6-17_i386.deb
cpp-4.1_4.1.1-13ubuntu5_i386.deb
cpp-doc_4.1.1-6ubuntu3_i386.deb
cpp_4.1.1-6ubuntu3_i386.deb
dpkg-dev_1.13.22ubuntu7_all.deb                        match
dpkg_1.13.22ubuntu7_i386.deb
g++-4.1_4.1.1-13ubuntu5_i386.deb                       match
g++_4.1.1-6ubuntu3_i386.deb                            match
gcc-4.1-base_4.1.1-13ubuntu5_i386.deb
gcc-4.1-locales_4.1.1-13ubuntu5_all.deb
gcc-4.1_4.1.1-13ubuntu5_i386.deb
gcc_4.1.1-6ubuntu3_i386.deb
glibc-doc_2.4-1ubuntu12_all.deb
libacl1_2.2.39-1ubuntu2_i386.deb
libc6-dev_2.4-1ubuntu12_i386.deb                       match
libc6_2.4-1ubuntu12_i386.deb
libdb4.4_4.4.20-6ubuntu1_i386.deb
libgcc1_4.1.1-13ubuntu5_i386.deb
libgdbm3_1.8.3-3_i386.deb
libselinux1_1.30-1ubuntu1_i386.deb
libstdc++6-4.1-dev_4.1.1-13ubuntu5_i386.deb            match
linux-libc-dev_2.6.17.1-11.37_i386.deb                 match
locales_2.3.22_all.deb
make_3.81-2_i386.deb
patch_2.5.9-4_i386.deb
perl-base_5.8.8-6_i386.deb
perl-modules_5.8.8-6_all.deb
perl_5.8.8-6_i386.deb
tzdata_2006m-1ubuntu1_all.deb

33 File(s)     32,153,720 bytes

---

### Post by bobplano on 2007-04-15
well if you try to install one when the dependencies aren't installed it will tell you how many and which ones, so just try whichever one you want first and go from there.

---

### Post by FuriousLettuce on 2007-04-15
I admire your determination - I think I'd get bored and just quickly do it all through synaptic at an internet cafe / mates house / uni / work!

The pages in packages.ubuntu.com will tell you the dependencies e.g., [http://packages.ubuntu.com/edgy/devel/gcc](http://packages.ubuntu.com/edgy/devel/gcc), to search for other packages, press 'home' at the top of the page and search for the package. As you attempt to install each package, you will be notified of its dependencies (which may be quicker than looking them up). The ones you should aim to install first are libc6, gcc and g++ (and their dependencies - I think you have them all), which are the GNU c and c++ compilers.

NB: Because you would run ./hello from the command line, you don't need teh getchar(); - it's not like windows where a terminal flashes up and disappears, the text is simply printed inline. This is what you would see:
```
username@home: ~$ ./hello
Hello World
username@home: ~$
```

EDIT: Also, although the .deb files may exist in your home directory, they won't be installed there, they'll be installed system-wide. The idea is that programs depend on certain libraries etc, and rather than each program installing a copy of the libraries local to itself, which leads to code redundancy, one system-wide copy of each library is installed and available to all applications. That way you end up with a slim system containing only the things you need (many people never need to compile anything etc) and without code redundancy.

---

### Post by annda on 2007-04-15
i'm nothing of an expert, but maybe adding a burned cd to the repositories could help the system resolve all the dependencies.

it would be nicer to include a directory usind an apt line, but i have no idea what it would look like. i hope someone can tell you that.

---

### Post by FuriousLettuce on 2007-04-15
That is a point, if you have the install CD, it may have the right packages on it. To add it as a repository, go to Synaptic, then go to settings -> repositories, then tick the option that says 'CDrom with Ubuntu 6.10 Edgy Eft', click OK and then click 'Reload' - most of the sources will fail (they are internet). Next, attempt to install things like gcc and g++, see if it asks you to put the CD in. If it does, they should install fine!

---

### Post by Frederick J. Harris on 2007-04-15
At this moment I am exactly seven days into my new Ubuntu Linux life.  Except for a course in Fortran in the mid seventies where I keypunched cards to write programs for a mainframe, I've used Microsoft OSs all my life.  So I need to be determined to learn this stuff.

I've got two books to help, plus you guys/gals, for which I'm thankful.  The books are Kier Thomas' "Ubuntu Linux" and "The Official Ubuntu Book" by various authors.  The first came with a DVD on it containing 6.1 Edgy Eft.  The Official ... came wit 6.06 LTS.  I installed the 6.1 Edgy Eft.  

The thing that has been hardest for me to grasp is the software installation situation which I feel to be absolutely and radically different from Windows.  I'm slowly recovering from the shock of it as I read, study, and think about dpkg, apt, sources.list an so on.  Perhaps in the fullness of time I'll have a better understanding of the philosophical underpinnings of an 'Online Operating System'....

But my not being 'connected' sure freaks out Synaptic!  And I hate to have any part of my computer system in dispair!  It seems the solution would be to just modify sources.list to only point to a CD or preferably a directory of my choosing where I put acquired deb files.  But as Annda said, what is the syntax of that line?  Just making a guess, if a typical online access looks like this...

deb [http://archive/ubuntu/](http://archive/ubuntu/)......

perhaps a CD line would be...

deb cdrom://     ???

or the files of unknown origin on my Windows drive...

deb /media/dev1/Documents And Settings/Fred/My Documents/Ubuntu/BuildEssential

then, in the fullness of time, after reading, studying, and attempting 15129 posts relating to getting ndiswrapper to work, I finally get my connection working, I can revert to the original sources.list file, my computer can call home to mama, and life will be again good, as I become assimilated into the borg....

So, from the comments I'm hearing about dpkg its internal logic functions to seek out files in some sort of list contained within it, it attempts to reconcile files it tries to copy to the disk with dependencies that should already be on the disk, and fails gracefully and does nothing (other than output missing dependencies) if any dependencies are not met?  That was a very confusing job downloading those files listed several posts back.  Tomorrow then I'll try running dpkg and see what happens.  I really appreciate the help!

---

### Post by bwhite82 on 2007-04-16
You can burn all those .deb files to a CD, then boot into Linux and from the command line type:
> 
sudo apt-cdrom add

This will scan the disk for packages and also add the disk to your sources.list file. Then when you goto install a file, it will scan the disk for the file and install it from there.

Once you get used to it, the package system that comes with Ubuntu, you will find, is very easy to use. The main difference is that in windows, packages (Installers) come default with all of those dependencies, which in time bog down your system with unnecessary junk even after you've removed said program. Linux is leaner because it only installs dependencies that it needs and many cases, searches your HD for already-installed dependencies, and also completely removes said dependencies once you removed the package.

Aptitude/Synaptic, you simply will not find a better combination in any other distro for installing programs. I haven't seen anyone mention it thus far, but you can simply double-click on the .deb file on your desktop to install the package (instead of using dpkg -i). Synaptic will automagically check for correct dependencies once you do so, and will display a nice big, green checkmark if you're good to install it, otherwise it tells you exactly which dependencies need installed first.

I hope this helps. Good luck!

BTW, installing from online is much nicer, because Aptitude automatically checks for dependencies AND automatically downloads and installs them for you, quite nice really.

---

### Post by Nesmontu on 2007-04-17
1) To setup Synaptic/apt to use only cd-rom, you don't have to manually add the cdrom line to your sources list -- you can also open Synaptic, go to Settings --> Repositories, uncheck everything, and check the cd-rom. 
2) The installation cd normally includes the build-essentials package + dependencies. On the other hand, since you've already downloaded them, you can also navigate (in a terminal) to the directory where you saved them and type "sudo dpkg *.deb" -- this should install all packages, unless there's still a missing dependency somewhere...
3) No experience with dialup, but setting up ndiswrapper is fairly simple. Here's the Ubuntu wiki page:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
Or search the "howtos" forum for ndiswrapper, there's plenty of guides :)

---

### Post by Frederick J. Harris on 2007-04-18
Making progress here!  For the past several days I've been sweating blood, going without food,
and losing sleep in a epic death struggle with dpkg and installing 'build-essential' so that I
could do programming on my dual boot WinXP / Ubuntu laptop (HP DV-8000 with wide screen, 2 gigs 
ram, AMD turion 64 bit, BroadCom wireless).  My wireless doesn't work 'out of the box', and I
didn't want to struggle to fix it, even though that's what most thought I should do.  I hate 
hardware.  So, with the help of everyone here I finally figured out how I could download the
huge 'build-essential' package (there are about 40 dependency sub-packages), transfer them to
my Ubuntu computer, and install them there.  Backing up though, I might point out that 
FuriousLettuce gave me directions for command line compiling a Hello, World! program, which I 
did try before installing the build-essential package.  For you see, it appeared to me that I 
had some compilation tools on my laptop already from my installation, e.g., gcc, the GNU C/C++
compiler.  However, it didn't work.  The compiler was there, but there were no libraries (I got
a message that stdio.h wasn't found).

The way I did the installation of the fourty or so packages was to copy them to a ...

     /home/DebPkgs/

directory, and execute dpkg from there...

sudo dpkg -i  package_name_uglier_than_dirt.deb

Some went in right away.  Others errored out stating there were missing dependencies.  In
these cases it tells you what the dependencies are, so you have to hang in and fight it.  
However, there were two packages that looked pretty darn important that absolutely, under
no circumstances, would go in.  When I tried to put ...

g++-4.1_4.1.1-13ubuntu5_i386.deb

in, it complained that this package couldn't go in because it was dependent on...

libstdc++6-4.1-dev_4.1.1-13ubuntu5_i386.deb

Nice names, huh?  Been staring at names like that for two days!  And if I then tried to put
that one in it complained it couldn't go in cuz it was dependent on...

g++-4.1_4.1.1-13ubuntu5_i386.deb

Circular dependencies!  So I figured, great!  I've got a broken build system before I even
start!  And doing programming with a perfect build system is hard enough as it is!  But after
I got everything in I could I opened up Synaptic and took a look at what it could tell me about
installed packages, and lo-and-behold, it seemed to be telling me that almost all the development
software and libraries were installed.  So I returned to FuriousLettuce's Hello, World! program
and to my amazement it compiled and ran!!!!!  Getting brave, I decided to elaborate on it a
little by adding a string and a memory allocation to it and that worked too.  Here is the code...

```

//  command line >> gcc -o ForLoop.exe ForLoop.c
//  ./ForLoop.exe

#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main(void)
{
 unsigned int i;
 char szStr[]="Hello, World!";
 char szStr1[]="...And Hello, Universe!\n";
 char* pStr=0;
 
 pStr=(char*)malloc(64);
 strcpy(pStr,szStr);
 strcat(pStr,szStr1);
 for(i=0;i<20;i++)
     printf("%u\t%s",i,pStr);
 free(pStr); 

 return 0;
}

```

I was worried though about the C++ stuff though cuz of those unresolveable dependencies
so I next tried this...

```

// Bare bones beginning of string class
// g++ -o strClass.exe strClass.cpp          //.cpp for C++ linkage (see man g++) 
// ./strClass.exe

#include <string.h>
#include <stdio.h>

class String
{
 public:

   String(char* pStr) //Constructor with initialization asciiz character array
   {
    pStrBuffer=new char[strlen(pStr)+1];
    strcpy(pStrBuffer,pStr);
   }


   String(const String &strAnother) //Copy Constructor
   {
    pStrBuffer=new char[strlen(strAnother.pStrBuffer)+1];
    strcpy(pStrBuffer,strAnother.pStrBuffer);
   }


   String() //Uninitialized Constructor - Does nothing
   {
    pStrBuffer=NULL;
   }


   ~String() //Destructor
   {
    if(pStrBuffer) //Don't try to [] delete a NULL pointer!
       delete [] pStrBuffer;
   }

   void Print(void)
   {
    printf("%s\n",pStrBuffer);
   }


 private:
   char* pStrBuffer;
};


int main(void)
{
 String s1("Hope This Works");
 s1.Print();

 return 0;
}

```

Worked perfect.  Can't believe it!  So, if you don't have internet access on your Ubuntu
installation, you can look up the packages you want at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and
download them to some media and get them onto your Ubuntu box and install them from there
with dpkg.  I guess.

By the way, on Linux they compile down to about 7.5 K.  That's decent.

Below is what the 'Development' and 'Libraries - Development' left pane selections looked
like after I did all the dpkg stuff.  The 'Nooooooooo..' lines are packages not 'green', i.e.,
not installed (and, seemingly, un-installable)....

```

[FONT="Courier New"]Synaptics Package Summary   >>  Development
==============================================================================
binutils                        The GNU assembler, linker and binary utilities
binutils-static                 statically linked binutils tools
bsh                             Java scripting environment (BeanShell) Version 2
build-essential                 informational list of build-essential packages
dbus                            simple interprocess messaging system
desktop-file-utils              Utilities for .desktop files
g++                             The GNU C++ compiler
g++-4.0                         Nooooooooooooooooooooooooooooooooooooooooooooo!
g++-4.1                         The GNU C++ compiler
gcc                             The GNU C compiler
gcc-3.3-base                    The GNU Compiler Collection (base package)
gcc-4.0                         Nooooooooooooooooooooooooooooooooooooooooooooo!
gcc-4.1                         The GNU C compiler
gcc-4.1-locales                 The GNU C compiler (native language support files)
gdb                             The GNU Debugger
gettext                         GNU Internationalization utilities
gij                             The GNU Java bytecode interpreter
gij-4.1                         The GNU Java bytecode interpreter
intltool-debian                 Help i18n of RFC822 compliant config files
linux-headers-2.6.15-26         Nooooooooooooooooooooooooooooooooooooooooooooo!
linux-headers-2.6.15-26-386     Nooooooooooooooooooooooooooooooooooooooooooooo!
linux-headers-2.6.17-10         Header files related to Linux kernel version 2.6.17
linux-headers-2.6.17-10-generic Linux kernel headers for version 2.6.17 on x86/x86_64
linux-headers-386               Nooooooooooooooooooooooooooooooooooooooooooooo!
linux-headers-generic           Generic Linux kernel headers
linux-kernel-headers            Nooooooooooooooooooooooooooooooooooooooooooooo!
linux-libc-dev                  Linux Kernel Headers for development
make                            The GNU version of the "make" utility.
mcpp                            Matsui's CPP implementation precisely conformed to standards
mono-gac                        Mono GAC tool
pkg-config                      manage compile and link flags for libraries
po-debconf                      manage translated Debconf templates files with gettext


Synaptics Package Summary   >>  Libraries - Development
===================================================================================
libc6-dev                       The GNU Standard C++ Library v3 (development files)
libcapi20-dev                   Nooooooooooooooooooooooooooooooooooooooooooooooooo!
libstdc++6-4.0-dev              Nooooooooooooooooooooooooooooooooooooooooooooooooo!
libstdc++6-4.1-dev              The GNU Standard C++ Library v3 (development files)
[/FONT]
```

So, where I seem to be at is this!  My C and C++ build system seems to be working.  That
might keep me occupied and out of trouble for awhile, but eventually I'm going to tire of
console programs and wajnt to do GUI stuff.  I'm still wondering if my build system will
handle that?  I know nothing about GUI programming in Linux.  All I know is that there is
something called X, gnome, and what??? KDE or something???  And I've got gnome, and X too?
In Windows I do the somewhat unusual route of accessing the Windows Api directly in my
programming with either C, C++ or PowerBASIC ([www.PowerBASIC.com](www.PowerBASIC.com) << awesome language!, and
they are working on a Linux port!)  What do you do in Ubuntu?  Here is a Windows Api program
that makes a simple Window in C...

```

/*Simple Window/Form with No Child Windows*/
#include <windows.h>

LRESULT CALLBACK WindowProcedure(HWND hwnd,UINT message,WPARAM wParam,LPARAM lParam)
{
 if(message==WM_CLOSE) 
 { 
    PostQuitMessage(0);
    return 0;
 }   

 return DefWindowProc(hwnd, message, wParam, lParam);
}

int WINAPI WinMain(HINSTANCE hIns,HINSTANCE hPrev,LPSTR lpszArg,int iCmdShow)
{
 char szCaption[6]="Form1"; 
 WNDCLASSEX winclass;
 MSG messages;
 HWND hMain;
   
 winclass.hInstance=hIns;
 winclass.lpszClassName="Form1";
 winclass.lpfnWndProc=WindowProcedure;
 winclass.style=CS_HREDRAW | CS_VREDRAW;
 winclass.cbSize=sizeof(WNDCLASSEX);
 winclass.hIcon=LoadIcon(NULL,IDI_APPLICATION);
 winclass.hIconSm=LoadIcon(NULL, IDI_APPLICATION);
 winclass.hCursor=LoadCursor(NULL,IDC_ARROW);
 winclass.lpszMenuName=NULL;
 winclass.cbClsExtra=0;
 winclass.cbWndExtra=0;
 winclass.hbrBackground=(HBRUSH)COLOR_BACKGROUND;
 RegisterClassEx(&winclass);
 hMain=CreateWindow("Form1",szCaption,WS_OVERLAPPEDWINDOW,100,100,400,350,0,0,hIns,0);
 ShowWindow(hMain,iCmdShow);
 while(GetMessage(&messages,NULL,0,0))
 {
  TranslateMessage(&messages);
  DispatchMessage(&messages);
 }

 return messages.wParam;
}

```

How do you do that in Linux?  And what are your opinions of the likelihood of my build
system being OK?

PS -  I'm really thankful for everyones help.  I've printed out everyones replies and will save
      them

---

### Post by FuriousLettuce on 2007-04-18
Well done for getting this far! The packages you list as 'uninstallable' are deprecated - e.g., if you look at the version numbers, they're all lower than the currently installed packages (linux-headers-2.6.15-26 < linux-headers-2.6.17-10-generic, in this case the headers for the kernel, and are mutually incompatible, same for gcc-4.0 < gcc-4.1 - there's no point in having them installed).

You mentioned that the file compiled down to 7.5K, there are various optimisations available for speed etc. The one for binary file size is -Os, so the command would become
```
g++ -Os -ostrClass.exe strClass.cpp
```

NB: For the filenames, BASH (the command line) has tab completion - all you need to do is type in enough of the filename so that it can be uniquely identified, then press tab, and BASH will fill in the rest. For example, if a directory contains 4 files:
1) aaab
2) abbb
3) abcb
4) abbc

You could reference each one by doing:
1) aa <TAB>
2) abbb (since abb does not uniquely identify the file, we need to put the entire name in)
3) abc<TAB>
4) abbc (same reason as 2))
This 'tab completion' works for any file / directory - and is certainly useful when installing packages etc!

I'm afraid I'm not familiar with GUI programming under Linux, only command line, so I couldn't say how much you'd have to change that. If you're familiar with C#, C++, or any other .NET language, there is an independent project to bring the .NET platform to Linux - it's under the repositories as Mono. It also has its own IDE, MonoDevelop, which should aid you in writing for .NET. 

I'm fairly sure I'm right in saying that if you're planning on programming purely for Linux without .NET, you'll need to drop windows.h and all the Windows calls I'm afraid.

EDIT: X is basically the protocol which allows things to be drawn to the screen. GNOME and KDE are different 'environments' which run on top of X. You can see the difference if you google KDE and GNOME screenshots, or see [http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System) for a description of X and screenshots as well. NB: You can see the basic X windowing system if you go to command line (CTRL + ALT + F1), login (same username and password as normal), then type 
```
sudo /etc/init.d/gdm stop
``` to stop the graphical interface, then just simply type
```
X
```
NB: Unix/Linux is case-sensitive - the capitalisation does matter. X is the common basis that Linux windowing is built on. To get back to your normal screen, go back to the command line (CTRL + ALT + F1), press CTRL + C to kill X, then type 
```
sudo /etc/init.d/gdm start
```
This also highlights the highly modular way that Linux is built. If you navigate to /etc/init.d, you will see a list of services, all of which can be started or stopped at will. 'gdm' is GNOME display manager (e.g., Linux doesn't depend on the GUI at all to run), you will also notice things like networking etc which can be used to administer whole parts of the Linux system.

GNOME and KDE are built on different graphics libraries - rather than there being one provided by 'Linux', there are several open source libraries, useful for different things and used by different projects -  KDE uses a library called qt, and GNOME uses a library called GTK (now GTK2). Each have their own bindings and calls etc, and it's up to you which one you want to develop for. GTK programs can be run inside KDE, and qt programs can be run in GNOME - you simply have to install the dependencies (not really feasible without the net, but if you do get online, install 'Amarok' from the repositories - it's built on qt and can show you the differences between general qt development and GTK development, as well as being an awesome audio player). There are other, smaller libraries around as well, which can be developed for, and may not have such meaty dependencies. If you can program in Java, you can use the tools built into it to create programs which are completely desktop environment- (KDE, GNOME, xfce) and platform-independent.

DOUBLE EDIT: Just read your post before last, you mention /media/dev1/Documents and Settings/.... One thing to note (I know that part of the directory is part of the Windows filesystem) is that file/directory names with spaces are more hassle than they're worth, since Linux interprets spaces in a string as the end of the command (it would attempt to read /media/dev1/Documents, with 'and' and 'Settings/...' being different arguments / commands), which would generate errors. If you do need to access files/directories with spaces in the names, it is done thus:
```
/media/dev1/Documents\ and\ Settings/...
```
The '\' is an escape character (just like in C), and can be used to escape otherwise special characters - you may even have to insert them into the middle of a filename if it has for example a $ in it (abc$dk would become abc\$dk).

Finally, Unix/Linux doesn't care about file extensions. You mentioned in the last post that you made a file with a .exe extension, like you would in Windows. Linux analyses the file by its contents, not its extension, thus a .jpg file could just as easily be a text file as an image file (although generally convention is followed). The convention for binary files under Unix is simply just the filename without an extension, since almost all other filetypes are by convention given an extension. You can see that the extension is independent by doing
```
file filename.exe
```
where filename is the name of the file that you are interested - it will tell you that it is a binary file. If we assume that the file has a .exe extension, we can rename it by doing
```
mv filename.exe filename
```
Here, mv means move (essentially rename when called for a single file), filename.exe is the original filename, and filename is the output filename. If you now do
```
file filename
```
you will see the same output as before, and you would if you moved it from filename -> filename.jpg -> filename.gz etc.

Sorry about the long, rambling post, but I do believe that they ought to be useful one way or another!

---

### Post by Frederick J. Harris on 2007-04-20
FuriousLettuce,

     Don't know if you are still following this, but thanks again for the additional info.  Now that I've essentially achieved my goal of getting a build system for Ubuntu put together and working, I am very relieved as I was burning the midnight oil, so to speak, and putting myself under stress to get it working.  Now I can relax and take the rest of my learning of Linux in a more relaxed and systematic manner.  

     The issue of what libraries and program archecture I'll want to use for GUI programming in Linux will take me some time to resolve.  I'm following up on the leads you provided, and I can see there are quite a variety of choices!

     Oh, yea!  That Windows "Documents and Settings" thing!  I wasn't sure how Linux would react to it so rather than take a chance I copied all those deb files to /home/DebPkgs to run dpkg on them.  Just now though I tried putting that long string in quotes and that seems to work, at least with ls...

ls "/media/hda1/Documents and Settings/Fred/My Documents/Ubuntu/BuildEssential"

     Not sure if that works with other commands, but if it does that appears to be a somewhat cleaner solution than escape sequences.  Actually, I truely hate file paths with spaces in them, and I essentially never use them in any programming I do.  In fact, it was issues relating to this that caused me to give Linux a try.  The very first time I ever saw that 'Documents and Settings' directory was with Windows 2000, and I nearly puked when I saw it!

---

### Post by achron on 2007-04-20
Since you are dual-booting (as I do, since there are just simply some apps I have that have no replacement on the *nix side), what I've found quite useful is a FAT32 partition.  

XP and Ubuntu can both read and write FAT32 out of the box, so I have NTFS on one drive for the XP filespace, the Linux format (drawing a blank on the name at the moment) and swap on another drive to keep Ubuntu safe, and my ancient 20Gig is FAT32, my shared drive where, if I seriously hose up Ubuntu by tinkering where I oughtn't, I can boot into XP, retrieve what I need, and stick it on the FAT32.  I know Ubuntu can read NTFS, but I try not to go to the Windows drive from Linux.

---

### Post by Frederick J. Harris on 2007-04-20
I must confess, I've been casting covetous eyes upon about 8 gigs of FAT32 space into which my laptop's manufacturer put a full backup of my XP installation.  And $10 bought me the backup CD, right?  One of these days....

---

