---
title: "skype &amp; Xara"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by stenella on 2007-12-15
Hi,
I've got the latest Ubuntu installed, and it runs beautifully. I'm now trying to cut my dependecy on windows. There are two programmes I really need, Xara and Skype - the latter as most of our friends and family are on it. When I try to load  Xara I get:

# Preparing package: Xara Xtreme Vector Graphics Tool                           
# Checking for required C library versions ... failed
# FAIL: 
# Your copy of glibc, a core system library, is too old for this package.
# You need at least the following symbols in glibc: GLIBC_2.0.
# 
# This error normally means that whoever built the package did not build it correctly.
# Please report the contents of this message to the provider of this package, and
# ask them to rebuild it using apbuild.
# 
# Upgrading glibc is highly dangerous, so we recommend in this situation that you
# compile the app you want to install from the sources if possible. Sorry :(
FAIL: Unable to prepare package Xara Xtreme Vector Graphics Tool.
Press ENTER to exit.

Um, as a non tech bod - I'm a painter and illustrator working with paint, paper and canvas - I lose my way about the third line... Same thing with Skype. How do I learn how to do these things What's a library, etc? Skype wants me to load a bunch of stuff: 

1.Install 32-bit libraries: sudo aptitude install lib32asound2 ia32-libs-gtk ia32-libs-kde 
2.Download the Ubuntu package ( [http://skype.com/download/skype/linux/](http://skype.com/download/skype/linux/)) 
3.Install skype: sudo dpkg -i --force-architecture <the_package> 
4.Determine if missing any additional 32bit libs: ldd /usr/bin/skype | grep not 
5.Search and download the missing 32bit (i386) libs. (Hint libdbus-1.3, libqt4-core, libqt4-gui, libsigc++-2.0, libXss) 
6.Extract the downloaded *.deb files: dpkg-deb --extract <package> <targetdir> 
7.Copy the necessary library files from the extracted packages to /lib32: sudo cp -i <targetdir>/usr/lib/* /lib32/ 

At the moment it's Greek to me...I have no idea where to begin.
Thanks in advance for any help!
F

---

### Post by jken146 on 2007-12-15
First, go to System > Administration > Software Sources and make sure the Universe repository is enabled.  Then to install Xara Xtreme:
```
sudo apt-get install xaralx
```

For Skype, go to [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and follow the instructions to add the Medibuntu repository.  Then to install Skype:
```
sudo apt-get install skype
```

There is no need to download anything from Skype's own website -- the repositories contain what you need, they'll give you updates automatically in the future.  Installing with apt-get (or aptitude or synaptic or add/remove...) should fix any dependency problems like the glibc thing you were having.

---

### Post by stenella on 2007-12-16
Thanks for the help. I'll have a go today - after I thaw out the pipes and cut some firewood!
About loading Xara You say to  code: sudo apt-get install xaralx. Newbie question: where? I assume I pull up the command console?
Best,
F

---

### Post by stenella on 2007-12-16
Help!
Where do I type the code that jken suggested? Sorry to be such a total noob, but...I'm a bit lost here..
Cheers
F

---

### Post by Tinnu on 2007-12-18
Hi,

I'm surprised nobody answered you yet and you've probably figured it out already, but yes, type that code in the command line.  If you're using the default Ubuntu installation, you should have a little icon that looks like a monitor at the top of your screen.  You can click on that to open a terminal window, or do Applications->Accessories->Terminal.  Let us know if you need any more help!

---

### Post by PhoenixP3K on 2007-12-18
Wow, you're right, two days is a long time to wait for an answer, the thing is that the topics fly-by so fast in this forum, I mostly try to track the unanswered post, but it doesn't mean I get to see the unsolved posts.

---

### Post by stenella on 2007-12-18
Cheers guys,
Yes, it's a busy forum!
I managed to get Xara onto the computer, but haven't had time to give it a work out.

Skype, however is another story! My computer is AMD64 equipped...and I've gotten into a knot trying to get the right repositories, libraries etc. Not to mention trying to figure out the numerous error messages I'm getting about non-findable archives etc. Way out of my depth...

---

### Post by sloggerkhan on 2007-12-18
If you can't get xara to work, inkscape might double as a replacement till then.

Since nobody's really explained what's happening and what the commands you've been given mean, I thought I'd do so.

In ubuntu, there is an online repository that holds many  thousands of pieces of software which you can use with Ubuntu. These pieces of software are divided into different groups depending on whether they have a free software license and whether Ubuntu 'officially' supports them.

Typically, when you want software, you get it from the online repository through one of 3 ways: the Add/Remove choice in the Applications menu, synaptic pachage manager in the System > Administration menu, or vie the command line using the aptitude set of commands.

Sometimes these packages may not be the most up to date, or may have specific problems with your computer. In this case, you may have to go outside of the repository to install it.

When you do this, you have several options. If you can find it, a *.deb filetype is the easiest to install. It will find the program's dependancies (libraries and such) in the main repo and install them so that the program works. However, some programs use binary installers which will not find dependancies and install them for you. For this, you will have to install the missing libraries/dependancies yourself if the program fails to work.

Typically, the things people install that are binaries instead of *.debs or repository packages are mostly the latest versions of games and graphics card drivers, but other programs for which people want the latest features also commonly installed or run from binaries.

In your case, the I think the advice you got explains how to install a Skype binary in such a way that it is included in package management.

---

### Post by Sef on 2007-12-18
> Sometimes these packages may not be the most up to date, or may have specific problems with your computer. In this case, you may have to go outside of the repository to install it.

When you do this, you have several options. If you can find it, a *.deb filetype is the easiest to install. It will find the program's dependancies (libraries and such) in the main repo and install them so that the program works.

Tutorials on installing:

[How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

[Psychocat's installing software]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by peitschie on 2007-12-18
Some-one has posted a how-to for installing Skype on Ubuntu Gutsy that seems reasonable: [http://ubuntuforums.org/showthread.php?t=432295]("http://ubuntuforums.org/showthread.php?t=432295")

---

### Post by stenella on 2007-12-23
Hi, 
Thanks for the help, Skype and Xara are now onboard and seem to be working, though I haven't had the time to fool around yet.  I've been too busy screwing up my copy of Vista. Now, try not to laugh too hard...

I thought I might try to add my copy of XP to the mix, as I have plenty of space on the hard drive and if it worked I'd junk Vista. It's an older copy, without SP2. Needless to say it got about halfway through 'installing devices' and gave up. Ah.... OK, I thought, it's not going to work.  However, it had worked enough to make booting into anything else a non-starter. The recovery disks weren't worth spit either. So, on the basis of having little to lose, having backed up my artwork and such onto a removable drive, I trashed the XP partition. Still couldn't boot into anything. 
So I thought long and hard and then came up with plan B. I erased the Ubuntu partition, and reinstalled it, which reinstalled GRUB as well. Whew. However, it seems that Vista is now in a terminal sulk and won't play no matter what. As HP didn't supply a copy of Vista, I think my Windows days are over... The only problems I have now before I can trash the Windows partition and have more gigs of storage are converting my favourites and contacts from Vista readable to Ubuntu readable ..... Anybody got any ideas?
Cheers, and happy holidays.

---

