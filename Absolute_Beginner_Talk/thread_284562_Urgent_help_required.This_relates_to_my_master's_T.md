---
title: "Urgent help required.This relates to my master's Thesis"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by eternalhate on 2006-10-25
So I was forced to use Linux for a part of my master's thesis as the software I am trying to use is not supported by windows.
I don't know why, but I chose Ubuntu, primarily because it's just one CD.

So I installed th OS, did some fooling around, got mp3s to work etc.

Now..I am stuck when it comes to actual work.
I am trying to install this program called passcal which converts seismic data from one format to another.

[http://www.orfeus-eu.org/links/conversion.htm]("http://www.orfeus-eu.org/links/conversion.htm")

Now this is what I get after make install:

```
devb@devb-desktop:~/Desktop/passcal1.9/src$ sudo make install
Installing executables in /home/devb/Desktop/passcal1.9/convert
make[1]: Entering directory `/home/devb/Desktop/passcal1.9/src'
cp: cannot stat `modem/sun4/tmodem': No such file or directory
make[1]: *** [install_bin] Error 1
make[1]: Leaving directory `/home/devb/Desktop/passcal1.9/src'
make: *** [install] Error 2

```

I found out that such a directory does not exist. I made that directory..and got this error:

```
devb@devb-desktop:~/Desktop/passcal1.9/src$ sudo make install
Installing executables in /home/devb/Desktop/passcal1.9/convert
make[1]: Entering directory `/home/devb/Desktop/passcal1.9/src'
cp: omitting directory `modem/sun4/tmodem'
make[1]: *** [install_bin] Error 1
make[1]: Leaving directory `/home/devb/Desktop/passcal1.9/src'
make: *** [install] Error 2
devb@devb-desktop:~/Desktop/passcal1.9/src$

```

Any help would be highly appreciated.It's really urgent.

---

### Post by dbd on 2006-10-25
before running make install did you first do:
./configure
and:
make
?

---

### Post by UnknownVariable on 2006-10-25
Try backing up one directory and running the command again. So instead of being in passcal1.9/src, you'd just be in passcal1.9. You can use
```
cd ..
```
to move up one folder level.


Edit: Yeah, what the above user posted before me is needed as well. :)

---

### Post by eternalhate on 2006-10-25
On "./configure"
I get this:
```

devb@devb-desktop:~/Desktop/passcal1.9/src$ ./configure
bash: ./configure: No such file or directory

```

---

### Post by UnknownVariable on 2006-10-25
Not all packages have a config file, so the next step is the make command. Run **make** and see what happens. :)

---

### Post by NetworkGuy on 2006-10-25
eternalhate - 

From synaptic, load the build-essential package.   You may be missing some packages needed for compiling programs.  These do not install by default. 

Also check the passcal1.9 directory structure for a configure script.  This is where you need to start the compile process from.

---

### Post by Brunellus on 2006-10-25
silly question:  have you installed the build-essential package yet?

```

sudo aptitude install build-essential

```

---

### Post by eternalhate on 2006-10-25
I have build-essential.
I cant see any config script in the folder. Can I upload the "readme" and the 
"makefile" for you guys to have a look?

---

### Post by TitusDalwards on 2006-10-25
could you please send us the names of files in ~/Desktop/passcal1.9 
directory.

---

### Post by funkyade on 2006-10-25
from the docs -

> The  PASSCAL software suite
was  written  and  developed  on  Sun  SPARCStations   under
SunOS4.1.4  and has been compiled under Solaris 2.4.  All of
the programs now run under the  LINUX  operating  system  on
Intel  platforms (386 or greater).  PASSCAL is still running
SunOS on it's field computers, so this remains our operating
system  of  choice. No other platforms are supported at this
time (the PASSCAL program has no other hardware  platforms).
At  the  end of this document are sections on: compiling the
software, the PASSCAL Database, the role of  Tcl/Tk  in  our
programming,  documentation  of the PASSCAL software, and  a
discussion of patch releases and bug reports.

you are going to need tcl/tk installed.
```
#> sudo aptitude install tcl8.4 tcl8.4-dev
```

hth

---

### Post by NetworkGuy on 2006-10-25
Are there any text files that might have the directions you need to compile the program?  

BTW - I'm trying to d/l the source right now.

---

### Post by eternalhate on 2006-10-25
Hey thanks a lot. I'd try that package. There's some more comments to be removed from the makefile.
You guys are really helpful.

---

### Post by eternalhate on 2006-10-25
Here's a link to the Readme

[http://www.sendspace.com/file/xrt3p2]("http://www.sendspace.com/file/xrt3p2")

---

### Post by NetworkGuy on 2006-10-25
Wow, this is old stuff :)

Looks like we need to edit some files before you can even compile this thing.
However the first file we need to edit per the direction is .cshrc.  I don't think Ubuntu uses the csh shell, but I'm not sure if the same lines will work in the .bashrc file

You can try to add ```
setenv ARCH linux
``` to your .bashrc file by typing ```
gedit .bashrc
``` from a command prompt.  

After that according to the directions:

```
 There is a Makefile in this directory which you should use to compile
the code at your site. Before you run the Makefile, edit it to
reflect the system on which it is being compiled. The current release
supports both SunOS and Solaris as well as the Linux OS.  Once you
have un/commented out the appropriate lines, TYPE: 

	 make

```

Then if I'm reading right you need to edit the makefile that is created from the make command and edit the bin_dir and man_dir to point to where you want the install to happen and then type 
```
 sudo make install 
```

From there it starts to get too deep for me, but I hope this at least get everything up and somewhat running for you.

---

### Post by eternalhate on 2006-10-25
I installed that package.
I edited the makefile as directed.
here's a link to the edited verson:
[http://www.sendspace.com/file/o4f19j]("http://www.sendspace.com/file/o4f19j")
I did make and got a lot of text with a lot of warnings, errors etc
On Make install I get the same error.

---

### Post by eternalhate on 2006-10-25
@Network guy:
Could you please elaborate on the .bashrc file?
Where is this file?

---

### Post by NetworkGuy on 2006-10-25
At the very beginning of the makefile 

```
# set PASSCAL to point to where the PASSCAL directory was untar'ed
# eg. PASSCAL = /passcal/prog/passcal1.9
#

PASSCAL =  /home/devb/Desktop/passcal1.9

```
Is your useraccount on your machine devb?  If not you may want to change it to the correct location.

I'm not sure about where to put the binaries.  Compiling isn't my strong point. :(

---

### Post by NetworkGuy on 2006-10-25
.bashrc is a hiddden file in your home directory.

From the terminal (and your home dir) type ls -a for a list of all files in your home dir including the hidden ones.

Putting a period in front of a file will make it hidden if I remember correctly.

---

### Post by eternalhate on 2006-10-25
yup.My useraccount is devb.
Well, this just doesnt seem to work
I got the .bashrc thing but it isn't helping either.

Can somebody tell me whether this is happening due to Ubuntu? Should I try some other distro for linux where it can be smoother?

---

### Post by starscalling on 2006-10-25
dude youll end up running into similar problems
pm me if u must but get me an exact link to exactly what your trying to install
i'll help u get it working
i e i'll get it working here and document it all ;)

[edit: adding info]
hint: checkinstall automake alien are needed things in my mind. 
one must always be able to uninstall what your installing or it can get a little messy ;p

---

### Post by eternalhate on 2006-10-25
[ftp://www.orfeus-eu.org/pub/software/mirror/iris_soft]("ftp://www.orfeus-eu.org/pub/software/mirror/iris_soft")

I was trying to install PASSCAL1.9.14.tar.gz
It's on that page.

---

### Post by NetworkGuy on 2006-10-25
I defer to starscalling at this point.  This is getting deeper than I tread right now.   Sorry :(

---

### Post by eternalhate on 2006-10-25
Thanks a lot starscalling. Your help would be much appreciated.

---

### Post by starscalling on 2006-10-25
1. set synaptic to consider all recommends as neededs
alien checkinstall automake1.9 build-essential
installs:
alien
autoconf
automake1.9
autotools-dev
binutils
build-essential
checkinstall
cpp
cpp-4.0
debconf-utils
debhelper
dpkg-dev
g++
g++-4.0
gcc
gcc-4.0
html2text
installwatch
libbeecrypt6
libc6-dev
libmudflap0
libmudflap0-dev
linux-kernel-headers
m4
make
rpm
adding the tcl stuff:
tcl8.4/-dev/-doc 
tclreadline




i e all those just installed... lol fresh install of ubuntu via last night ~_^


[edit adding info]
btw i noticed a livecd on another linky,....
[ftp://ftp.passcal.nmt.edu/passcal/software/linux/](ftp://ftp.passcal.nmt.edu/passcal/software/linux/)

---

### Post by doobit on 2006-10-25
It looks like they already have an RPM compiled for Fedora Core. You maybe could use alien to convert it to .deb
Someone else here could confirm that.
[http://www.passcal.nmt.edu/software/software.html](http://www.passcal.nmt.edu/software/software.html)

---

### Post by starscalling on 2006-10-25
thus my alien recommendation
but im gonna try compiling first


COMPILE AND INSTALL:

To compile and install this release see the README
file in the src directory.  
            ^^^
One NOTIBLE new requirement, GNU's compiler, gcc is now required for
several of the PASSCAL programs that link with the Postgres library.
These programs (and needed Passcal library functions) are made using
the 'make pdb' command.  At Lamont, we are using the latest gcc, version
2.7.2.2 availible since February 20, 1997 as:
	[ftp://prep.ai.mit.edu/pub/gnu/gcc-2.7.2.2.tar.gz](ftp://prep.ai.mit.edu/pub/gnu/gcc-2.7.2.2.tar.gz)
Making and installing it is fairly straight forward, see the included 
README in the gcc tar file.


doing that bit

---

### Post by doobit on 2006-10-25
Shhesh, this thread was just one page when I started researching ...

---

### Post by starscalling on 2006-10-25
right...
it hated compiling
missing stuff ~____~ gonna try the alien thing



[edit]
adding photo of rpms im grabbing

---

### Post by eternalhate on 2006-10-25
How does Alien work? I downloaded the rpm.

---

### Post by eternalhate on 2006-10-25
How does Alien work? I installed alien.
I have the rpm.

---

### Post by starscalling on 2006-10-25
well i dled rpms listed above in pic and then via terminal changed to desktop



sudo alien *.rpm
that creates .deb files which i will then 
sudo dpkg  -i install *.deb

---

### Post by DigitalAxis on 2006-10-25
*Mostly repeats, but oh well*

[The current PASSCAL download page]("http://www.passcal.nmt.edu/software/software.html")


Ok, the important part of what I've found.
1.) A PASSCAL liveCD based on Knoppix can be found here: [ftp://ftp.passcal.nmt.edu/passcal/software/linux/]("ftp://ftp.passcal.nmt.edu/passcal/software/linux/").  Note that if this version is recent enough or still contains the features you'll need, any data you process will have to be loaded from, and saved to a hard disk (which requires some extra steps)

2.) RPMs (for Fedora Core 5, apparently?) can be found at the same location.

3.) There appears to be a source bz2ball at the same location as the liveCD and the RPMs.  There is also a very recent-looking source .zip file here:[ftp://ftp.passcal.nmt.edu/passcal/software/src/]("ftp://ftp.passcal.nmt.edu/passcal/software/src/")

4.) With enough digging there are also places you can find versions of TCL/TK that (I presume) PASSCAL is supposed to work with.

---------------------

Anyway, these newer versions might be easier to compile on Ubuntu.  Libraries change from time to time; GCC 4 is stricter than GCC 3 (and GCC 2)... you may have more luck with these new ones.

---

### Post by starscalling on 2006-10-25
```
nekostar@nekostar-desktop:~$ cd Desktop/
nekostar@nekostar-desktop:~/Desktop$ ls
passcal1.9            PASSCAL-2006-110.i386.rpm      passcal stuff          PyPASSCAL-2006-110.i386.rpm  Screenshot-81% of 1 file - Downloads.png
PASSCAL1.9.14.tar.gz  passcal-NMT-2004.057.i386.rpm  PQL-2006-242.i386.rpm  readme2.0passcal             xview-devel-3.2p1.4-6.i386.rpm
nekostar@nekostar-desktop:~/Desktop$ alien *.rpm
Must run as root to convert to deb format (or you may use fakeroot).
nekostar@nekostar-desktop:~/Desktop$ sudo alien *.rpm
passcal-fc5_2006-111_i386.deb generated
passcal_2004-58_i386.deb generated
pql_2006-243_i386.deb generated
pypasscal-fc5_2006-111_i386.deb generated
Warning: Skipping conversion of scripts in package xview-devel: postinst
Warning: Use the --scripts parameter to include the scripts.
xview-devel_3.2p1.4-7_i386.deb generated
nekostar@nekostar-desktop:~/Desktop$ ls
passcal1.9                PASSCAL-2006-110.i386.rpm      passcal stuff          PyPASSCAL-2006-110.i386.rpm      Screenshot-81% of 1 file - Downloads.png
PASSCAL1.9.14.tar.gz      passcal-fc5_2006-111_i386.deb  PQL-2006-242.i386.rpm  pypasscal-fc5_2006-111_i386.deb  xview-devel-3.2p1.4-6.i386.rpm
passcal_2004-58_i386.deb  passcal-NMT-2004.057.i386.rpm  pql_2006-243_i386.deb  readme2.0passcal                 xview-devel_3.2p1.4-7_i386.deb
nekostar@nekostar-desktop:~/Desktop$ sudo dpkg -i *.deb
Selecting previously deselected package passcal.
(Reading database ... 84128 files and directories currently installed.)
Unpacking passcal (from passcal_2004-58_i386.deb) ...
Selecting previously deselected package passcal-fc5.
Unpacking passcal-fc5 (from passcal-fc5_2006-111_i386.deb) ...
Selecting previously deselected package pql.
Unpacking pql (from pql_2006-243_i386.deb) ...
Selecting previously deselected package pypasscal-fc5.
Unpacking pypasscal-fc5 (from pypasscal-fc5_2006-111_i386.deb) ...
Selecting previously deselected package xview-devel.
Unpacking xview-devel (from xview-devel_3.2p1.4-7_i386.deb) ...
Setting up passcal (2004-58) ...
Setting up passcal-fc5 (2006-111) ...
Setting up pql (2006-243) ...

Setting up pypasscal-fc5 (2006-111) ...

Setting up xview-devel (3.2p1.4-7) ...
nekostar@nekostar-desktop:~/Desktop$

```


mm i dont get it
i dont see any executable commands ~____~


i'm gonna try dling the live cd burning it and booting from it.... maybe it will make abit more sense as i dont see any " passcal " commands via shell executable unless the rpm's are supposed to have different commands....

---

### Post by eternalhate on 2006-10-25
I am downloading the live CD...it'll take a long time
Will keep trying alien meanwhile.

---

### Post by starscalling on 2006-10-25
alien == dead end.. i finished making the debs and installed em and there is no obvious way to execute anything nor are there any obvious new programs....
i'm trying the bin method.. 
```
nekostar@nekostar-desktop:~/Desktop/passcal/src$ make
ERROR: Makefile vars ARCH or PASSCAL are not set!
env PASSCAL =
env ARCH =
Please set these important Makefile variables!
make: [all] Error 1 (ignored)

```


here's the makefile....

```
# 1.  Set the PASSCAL variable to point to the software's home
#     directory.
#
# 2.  Edit the BIN_DIR and MAN_DIR to reflect where you would
#     like the executables and manual pages to be placed.
#     Manual pages and executables are COPIED and not moved.
#     We recommend NOT installing man pages and simply setting
#     your MANPATH to point to $PASSCAL/man (see README in this
#     directory for more details).
#
# 3.  Follow the directions below for the type of architecture
#     you are using (SunOS, Linux, Solaris).  Compiling the 
#     PASSCAL software requires the gcc compiler available from
#     www.gnu.org (source code) or www.sunsite.unc.edu and 
#     www.sunfreeware.com (Solaris packages).

setenv PASSCAL /home/nekostar/Desktop/passcal

setenv POSTGRES   /passcal/local/pgsql

setenv BIN_DIR  ${PASSCAL}/bin
setenv LIB_DIR  ${PASSCAL}/lib
setenv MAN_DIR  ${PASSCAL}/man
setenv MODEL_DIR  ${PASSCAL}/database/data/model

setenv X11INC /usr/openwin/include
setenv X11LIB /usr/openwin/lib

setenv CC gcc
setenv INSTALL install

setenv MAKE make
setenv PASSCHEXE 'chmod a+x'
setenv PASSCP cp
setenv PASSINSTALL install
setenv PASSRM rm
setenv PASSTAR tar

if ($OSTYPE == "solaris") then
echo "setting up for solaris"
setenv ARCH sun4
setenv ADD_LIBS "-lgen -lnsl -lsocket"
setenv ADD_CFLAGS="-DSOLARIS2 -I$X11INC -DOWTOOLKIT_WARNING_DISABLED"
setenv ADD_LDLIBS -L$X11LIB
setenv DBLIB   ../db/PORT/solaris.2.2
setenv DBINCLUDE ../db/PORT/solaris.2.2/include
setenv LEX_LIB -ll
setenv MFLAGS "ARCH=sun4"
setenv ARCH ${ARCH}
setenv MMACROS $ARCH
setenv DBLIB ../db/PORT/solaris.2.2
setenv DBINCLUDE ../db/PORT/solaris.2.2/include

else
if ($OSTYPE == "Linux" || $OSTYPE == "linux") then
echo "setting up for Linux"
setenv ARCH linux
setenv DBLIB   ../db/PORT/linux/
setenv DBINCLUDE  ../db/PORT/linux/include
setenv ADD_LIBS -L/usr/X11/lib
setenv LEX_LIB -lfl
setenv ADD_LDLIBS -L$X11LIB
setenv RANLIB ranlib
setenv ADD_CFLAGS "-DLINUX -I$X11INC"
setenv MMACROS $ARCH 
setenv RANLIB $RANLIB 
setenv MFLAGS "PASSCAL=`pwd`"

#######if not solaris or linux
else
echo "Oooops OS type is not supported"
exit 0
endif
endif

```



well.................
lots of phail
finishing grabbing and burning livecd...
if that doesnt work i would recommend hoping someone can really get down and dirty for j00 or just get fedora

---

### Post by DigitalAxis on 2006-10-25
There are no new programs?  Have you tried opening up the .deb files (which are more or less .tar.gz files with specific contents) and looking for executables?  They might simply have gone to some obscure place not in your executable path, like /opt/bin/passcal

---

### Post by starscalling on 2006-10-25
naw 
i am too busy atm this is one of like 5 things im doing... like trying to actually earn a living ~_~
anyway like i said getting livecd and if thats kosher great if not fukkit



trying the livecd now!

---

### Post by starscalling on 2006-10-25
screw it i'll double post im tired of editing...
use the livecd man it works ok.. should also have an installing option..... its basically an optimized knoppix
there is some explination stuff in /opt/local/passcal/man/db*********/index.html which you can open with a web browser... sorry bud...

---

### Post by hod139 on 2006-10-25
I know i'm jumping late in this thread, but from the readme on passcal's website:
> 

The python and passcal software suite gets installed in /opt/passcal.  About
250MB are required to be available in /opt/passcal.

IMPORTANT before running PASSCAL software:
Set your shell to /bin/tcsh using the chsh program.

Set your path, PASSCAL, and MANPATH environment variables in your .cshrc file:

	setenv PASSCAL /opt/passcal
	set path=(${PASSCAL}/other/bin ${PASSCAL}/bin $path)
	setenv MANPATH ${PASSCAL}/man


---

### Post by starscalling on 2006-10-26
oooo that makes sense
the live cd still seemed to want to dl the thing
but it was knoppix so im sure it oculd have been installed... and did have some instructions........

---

