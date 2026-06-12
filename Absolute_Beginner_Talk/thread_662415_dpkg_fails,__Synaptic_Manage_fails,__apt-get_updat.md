---
title: "dpkg fails,  Synaptic Manage fails,  apt-get update fails"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by cortical on 2008-01-08
Install failures
needed to install alien in order to install tar.gz packaged drivers fro  aCanon i250 Printer.



dpkg -i          falls over 
Synaptic Manager falls over
apt-get update   falls over	

========================
simple dpkg

cb@ublx:~$ sudo dpkg -i canon-i250_2.3_i386.deb
[sudo] password for cb:
Bus error (core dumped)
cb@ublx:~$ 


so try:

cb@ublx:~$ sudo dpkg -configure -a
dpkg: unknown option -o

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
cb@ublx:~$ 


-o from kelp MAY be : 
-O|--selected-only         Skip packages not selected for install/upgrad
but is this actually relevant?


====================

Synaptic Manager, open it >>  falls over
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

=====================


update falls over

cb@ublx:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_AU
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_AU
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_AU
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages [4065kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages [47.2kB]       
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages [112kB]            
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages [4263B]      
Fetched 4228kB in 43m10s (1632B/s)                                             
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
cb@ublx:~$

---

### Post by Rocket2DMn on 2008-01-08
The command is
```
sudo dpkg --configure -a
```
If that fails, it sounds like your .deb file may be corrupt, in which you case you should redownload it.

---

### Post by cortical on 2008-01-09
re: dpkg may be corrupt
ok, downloaded dpkg and reinstalled


sudo dpkg --configure -a
>>
cb@ublx:~$ 

so presumably no problems?


located librpm4  which is Package: librpm4 (4.4.1-14.1ubuntu2)
[http://packages.ubuntu.com/gutsy/libs/librpm4](http://packages.ubuntu.com/gutsy/libs/librpm4)
downloaded
 and now installed >>



cb@ublx:~$ cd ~/Desktop
cb@ublx:~/Desktop$ sudo dpkg -i rpm_4.4.1-14.1ubuntu2_i386.deb
Selecting previously deselected package rpm.
(Reading database ... 91692 files and directories currently installed.)
Unpacking rpm (from rpm_4.4.1-14.1ubuntu2_i386.deb) ...
dpkg: dependency problems prevent configuration of rpm:
 rpm depends on librpm4 (<< 4.4.2); however:
  Package librpm4 is not installed.
 rpm depends on librpm4 (>= 4.4.0); however:
  Package librpm4 is not installed.
dpkg: error processing rpm (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rpm
cb@ublx:~/Desktop$ 


located librpm4  which is Package: librpm4 (4.4.1-14.1ubuntu2)
[http://packages.ubuntu.com/gutsy/libs/librpm4](http://packages.ubuntu.com/gutsy/libs/librpm4)
downloaded
had downloaded rpm , and now installed >>

same result:
cb@ublx:~$ cd ~/Desktop
cb@ublx:~/Desktop$ sudo dpkg -i rpm_4.4.1-14.1ubuntu2_i386.deb
Selecting previously deselected package rpm.
(Reading database ... 91692 files and directories currently installed.)
Unpacking rpm (from rpm_4.4.1-14.1ubuntu2_i386.deb) ...
dpkg: dependency problems prevent configuration of rpm:
 rpm depends on librpm4 (<< 4.4.2); however:
  Package librpm4 is not installed.
 rpm depends on librpm4 (>= 4.4.0); however:
  Package librpm4 is not installed.
dpkg: error processing rpm (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rpm
cb@ublx:~/Desktop$ 



somewhere post all this :
cb@ublx:~$ sudo synaptic

(synaptic:10545): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

---

### Post by shareMenaPeace on 2008-01-09
Hi, 
if such happens to me (missing libs or struf fi searhc it with synaptic and install -- ok thsi it obvious what you done). But and im not realyl sur , but i think RPM packets are for other linux distros, and as ubuntu is debian based you mainly need DEB packages or source files and compile them to DEB?

Cheers

---

### Post by Rocket2DMn on 2008-01-09
You should put the deb file for librpm4 in the same directory as rpm's deb.
rpm is available from the repositories, if your computer is connected to the internet, you should run
```
sudo apt-get install rpm
``` and it will build the dependencies for you.  Also, synaptic should be run with "gksudo" (it's a safety thing...).  Can you not run Synaptic from System->Administration->Synaptic Package Manager ?

shareMenaPeace is right about rpm's and deb's - rpm is a format generally used with Red Hat distributions.  Deb files are used with Debian distributions (like Ubuntu).  RPMs are not guaranteed to work with Ubuntu.

If you must, there is a program called "alien" which can convert rpms to debs.

---

### Post by cortical on 2008-01-09
aware of the function of apt-get but this box is not on the network.

had read up extensively, and understand deb cf.  rpm

rpm to deb is another issue entirely


<< If you must, there is a program called "alien" which can convert rpms to debs.>>

That's exactly what  I am actually trying to get working; is installing alien -  so that I can install tar.gz  format printer driver files (only ones available)

Have worked through the multitude of the dependency cascade, and all that remains is to install the rpm package which is a mandatory dependency. I can't install rpm because dpkg can't sort out its own librpm4 versions range window

Cant run Syanaptic PM it falls over.

Will try gksudo


thanks Rocket and SMP for your input.

---

### Post by Rocket2DMn on 2008-01-09
I'm not sure I see how the tar.gz package has anything to do with rpm's - nowhere are you trying to install an rpm file.  With most tar.gz packages, you extract them to a directory, then configure and make them, like:
```
tar -xzvf printer_drivers.tar.gz ~/canon_drivers
cd ~/canon_drivers/(subdirectory may be created)
./configure
make
make install
```

---

### Post by cortical on 2008-01-09
tried that sequence but make did not seem to result in a makefile... I got as far as the unpacked directory recreated.

Although, I just realized that make may not have been installed; as I think gcc and make may not be installed by default in Ubuntu, I think I had to install those yesterday (another long day)


I may have been creating the unpacked result in the wrong location (i.e.desktop). I note your example is ~/

will read up on this further

<<
I'm not sure I see how the tar.gz package has anything to do with rpm's - nowhere are you trying to install an rpm file
>>

the rpm package was a mandatory dependency requirement, in  the dpkg of the alien install; even though in this instance there are no rpm's. I assume alien is capable of translating rpm's and hence require the rpm packages installed when it itself is installed.  

cb@ublx:~$ cd ~/Desktop
cb@ublx:~/Desktop$ sudo dpkg -i alien_8.64_all.deb
Selecting previously deselected package alien.
(Reading database ... 88932 files and directories currently installed.)
Unpacking alien (from alien_8.64_all.deb) ...
dpkg: dependency problems prevent configuration of alien:
 alien depends on debhelper (>= 3); however:
  Package debhelper is not installed.
 alien depends on rpm (>= 2.4.4-2); however:
  Package rpm is not installed.
 alien depends on dpkg-dev; however:
  Package dpkg-dev is not installed.
dpkg: error processing alien (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 alien
cb@ublx:~/Desktop$

I have worked through installing dehelper and dpkg-dev and their dependencies (no fun at all doing this sort of thing manually, i.e. without a live internet connection), but the rpm package is still a problem. 


I had noted a -r (i think) option to force ignore of dependencies at package installation, but had been reluctant to try this due to  associated warnings.

---

### Post by Rocket2DMn on 2008-01-09
I think it would really help if you could plug this computer into the internet temporarily.  To install from source (with a tar.gz file), you need to install "build-essential" which is really just a package that depends on all the necessary packages like gcc that are required to compile and install.  I think it includes, gcc, g++, make, libc6-dev, and dpkg-dev.
If you can connect to the internet temporarily, you can install alien using apt-get.  What happens after you install those packages in the dependency problems?  Can you then install alien?
After you extract the tar.gz file, show me the contents of the directory you extract to by navigating to that directory with "cd" and printing the contents with "ls".

---

### Post by cortical on 2008-01-10
getting this box on the net is a problem.  I'll see what I can do, in the next week, and get back to you.


thanks

---

