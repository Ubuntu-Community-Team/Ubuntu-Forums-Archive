---
title: "gnome-mag + compsoite + full screen"
date: 2006-10-10
forum: Assistive Technology &amp; Accessibility
---

### Post by jasongrieves on 2006-10-10
Please read below on how to get gnome-mag + composite working on your Edgy Eft ONLY.

Thanks!

---

### Post by jasongrieves on 2006-10-10
COMPOSITE + Edgy Eft ONLY!!!!!

Make sure Composite is enabled/running AND YOU ARE RUNNING EDGY EFT

Section "Extensions"
        Option "Composite" "Enable"
EndSection


Should be in your xorg.conf file.  Assuming your graphics driver can run Composite.  Most can.  If you are having trouble look elsewhere :).  Careful about moding the xorg.conf as you can screw things up on your display.


1) unzip the folder
2) run "sudo make install" (if this doesn't work, use sudo apt-get install build-essential"
3) run "/usr/local/bin/magnifier --ignore-composite=0 -f -m --smooth-scrolling"

I am keeping the deb away until this becomes more stable and edgy becomes more stable....happy testing![/QUOTE]

---

### Post by jasongrieves on 2006-10-10
one kinda neat thing you can do is have some animated graphics runnign with this.  You should see the compositing engine keeping up great wit the se!!!

Everything seems to be running pretty well over here.  I still need to sdo some testing with the events + at-spi layer

---

### Post by pinballkid on 2006-10-11
Could you post a screenshot?

---

### Post by RKCole on 2006-10-28
Hello, Jason.

I'm not sure what I did wrong, but upon running
```

make install

```
I receive the following:
```

bob@bandgc:~/Programs and Utilities/Accessibility/gnome-mag/gnome-mag-0.14$ make install
Making install in idl
make[1]: Entering directory `/home/bob/Programs and Utilities/Accessibility/gnome-mag/gnome-mag-0.14/idl'
make[2]: Entering directory `/home/bob/Programs and Utilities/Accessibility/gnome-mag/gnome-mag-0.14/idl'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/idl/gnome-mag-1.0" || mkdir -p -- "/usr/local/share/idl/gnome-mag-1.0"
 /usr/bin/install -c -m 644 'GNOME_Magnifier.idl' '/usr/local/share/idl/gnome-mag-1.0/GNOME_Magnifier.idl'
/usr/bin/install: cannot remove `/usr/local/share/idl/gnome-mag-1.0/GNOME_Magnifier.idl': Permission denied
make[2]: *** [install-idlDATA] Error 1
make[2]: Leaving directory `/home/bob/Programs and Utilities/Accessibility/gnome-mag/gnome-mag-0.14/idl'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/bob/Programs and Utilities/Accessibility/gnome-mag/gnome-mag-0.14/idl'
make: *** [install-recursive] Error 1

```

Am I doing something incorrectly?

This was done in the final release fo Edgy.

Thanks and take care.

---

### Post by cerdiogenes on 2006-10-29
Hi,

make install alter system files, so we must run it with sudo:

#: sudo make install

and then type the super user password.

Best regards,
Carlos.

---

### Post by cerdiogenes on 2006-11-01
> **pinballkid said:**
> Could you post a screenshot?

You can view a screenshot of a full-screen 4x magnification with bilinear-interpolation here:

[http://www.gnome.org/~carlosd/gnome-mag-full-screen.png](http://www.gnome.org/~carlosd/gnome-mag-full-screen.png)

Best regards,
Carlos.

---

### Post by jasongrieves on 2006-11-01
> **jasongrieves said:**
> Hi,


COMPOSITE + Edgy Eft ONLY!!!!!

Make sure Composite is enabled/running AND YOU ARE RUNNING EDGY EFT

Section "Extensions"
        Option "Composite" "Enable"
EndSection


Should be in your xorg.conf file.  Assuming your graphics driver can run Composite.  Most can.  If you are having trouble look elsewhere :).  Careful about moding the xorg.conf as you can screw things up on your display.


1) unzip the folder
2) run "sudo make install" (if this doesn't work, use sudo apt-get install build-essential"
3) run "/usr/local/bin/magnifier --ignore-composite=0 -f -m --smooth-scrolling"

I am keeping the deb away until this becomes more stable and edgy becomes more stable....happy testing!

edit, thanks for the change for sudo

---

### Post by StevenKannel on 2006-11-04
Hi Jason,

I followed all of your steps as described and I am still getting a "no make rule" error.  Is there anything I'm missing?

---

### Post by RKCole on 2006-11-04
Hello, guys!

Sorry...but I'm having the same problem as StevenKannel.  Even with sudo I still have the same problem.  What am I doing wrong?

Thanks for all the help.

Take care.

---

### Post by cerdiogenes on 2006-11-04
> **RKCole said:**
> Hello, guys!

Sorry...but I'm having the same problem as StevenKannel.  Even with sudo I still have the same problem.  What am I doing wrong?

Thanks for all the help.

Take care.

Can you post the new error messages?

Best regards,
Carlos.

---

### Post by RKCole on 2006-11-04
Here is what I get when I run
```

sudo make install

```
while in the unzipped directory
```

Making install in idl
make[1]: Entering directory `/home/bob/Programs and Utilities/Accessibility/gnome-mag/gnome-mag-0.14/idl'
make[2]: Entering directory `/home/bob/Programs and Utilities/Accessibility/gnome-mag/gnome-mag-0.14/idl'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/idl/gnome-mag-1.0" || mkdir -p -- "/usr/local/share/idl/gnome-mag-1.0"
 /usr/bin/install -c -m 644 'GNOME_Magnifier.idl' '/usr/local/share/idl/gnome-mag-1.0/GNOME_Magnifier.idl'
/usr/bin/install: cannot remove `/usr/local/share/idl/gnome-mag-1.0/GNOME_Magnifier.idl': Permission denied
make[2]: *** [install-idlDATA] Error 1
make[2]: Leaving directory `/home/bob/Programs and Utilities/Accessibility/gnome-mag/gnome-mag-0.14/idl'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/bob/Programs and Utilities/Accessibility/gnome-mag/gnome-mag-0.14/idl'
make: *** [install-recursive] Error 1

```

---

### Post by Cabb on 2006-11-05
Hi,
I got Edgy installed today (I'm multibooting). I had trouble getting Orca to speak but somehow I managed that (I have no idea how), so now I'm looking into full-screen magnification again.
I installed the ATI-drivers and then I enabled composite, but I too get that one make error.
I've got another question: The title says "full-screen" so I was wondering if I have to go into xorg.conf and add the dummy driver and so on, for this one to work.

---

### Post by cerdiogenes on 2006-11-05
> **Cabb said:**
> Hi,
I got Edgy installed today (I'm multibooting). I had trouble getting Orca to speak but somehow I managed that (I have no idea how), so now I'm looking into full-screen magnification again.
I installed the ATI-drivers and then I enabled composite, but I too get that one make error.
I've got another question: The title says "full-screen" so I was wondering if I have to go into xorg.conf and add the dummy driver and so on, for this one to work.

No, you don't have to add a dummy driver. Full-screen magnification is achieved throw COMPOSITE.

I downloaded the tarball provided by jason and I will test it here. The errors being reported are very strange IMO and have no idea why they are happening, so I will test the tarball by myself.

Best regards,
Carlos.

---

### Post by cerdiogenes on 2006-11-05
I get a sligthly different error when running "#: sudo make install":

```

make[1]: Entering directory `/home/kadu/downloads/gnome-mag-0.14/po'
/home/jgrieves/packages/gnome-mag/gnome-mag-0.14/install-sh -d /usr/local/share/locale
make[1]: /home/jgrieves/packages/gnome-mag/gnome-mag-0.14/install-sh: Command not found
make[1]: *** [install-data-yes] Error 127
make[1]: Leaving directory `/home/kadu/downloads/gnome-mag-0.14/po'
make: *** [install-recursive] Error 1

```

The way to resolve this was to type:
```

./configure
sudo make install

```

Then I started gnome-mag from the local directory:
```

#: /usr/local/bin/magnifier -fmz 2 --ignore-composite=0

```

Best regards,
Carlos.

---

### Post by RKCole on 2006-11-05
I am sorry for this...but I get an error even on running 
```

sudo ./configure

```

Here is the output:
```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/bash: /home/bob/Programs: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for intltool >= 0.35.0... 0.35.0 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for library containing strerror... none required
checking whether gcc understands -Wno-sign-compare... yes
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wno-sign-compare
checking what language compliance flags to pass to the C compiler... 
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for Win32... no
checking for aclocal flags... 
checking for X... no
configure: error: X development libraries not found

```

I'm not sure what it means by "X development libraries not found" as I have build-essential installed if it has anything to do with that.

---

### Post by jasongrieves on 2006-11-05
sorry guys, you won't be able to build it because you don't have the development libs.  The purpose of make install should just be a quick and dirty install of my compiled stuff to your /usr/local.  

the fact that you can't remove the idl for the magnifier baffles me.  Especially since you are typing "sudo make install"

/usr/bin/install: cannot remove `/usr/local/share/idl/gnome-mag-1.0/GNOME_Magnifier.idl': Permission denied

is this correct?

I thought that gnome-mag used the idl from /usr/share/idl/gnome-mag-1.0

If all else fails, you can just run the binary from within the tarball.  you have to navigate to the folder and such, but this should work...

---

### Post by jasongrieves on 2006-11-05
> **cerdiogenes said:**
> I get a sligthly different error when running "#: sudo make install":

```

make[1]: Entering directory `/home/kadu/downloads/gnome-mag-0.14/po'
/home/jgrieves/packages/gnome-mag/gnome-mag-0.14/install-sh -d /usr/local/share/locale
make[1]: /home/jgrieves/packages/gnome-mag/gnome-mag-0.14/install-sh: Command not found
make[1]: *** [install-data-yes] Error 127
make[1]: Leaving directory `/home/kadu/downloads/gnome-mag-0.14/po'
make: *** [install-recursive] Error 1

```

The way to resolve this was to type:
```

./configure
sudo make install

```

Then I started gnome-mag from the local directory:
```

#: /usr/local/bin/magnifier -fmz 2 --ignore-composite=0

```

Best regards,
Carlos.

I guess make was there depending on install-sh in my directory.  I'll try to find a better solution while not overwriting gnome-mag in edgy.  I can probably just build a gnome-mag-beta.deb and let it install to /usr/local.  I'm sure this goes against some of the polocies of debian, but so does make/make install :)

---

### Post by Cabb on 2006-11-16
I can't do make either, so I tried running it directly from the archive-folder, with the command-line parameters mentioned. However, I get a black screen, with a cross-hair and the mouse pointer in the middle, and when I do ctrl+c to close it, I get back but the terminal window has resized itself so that no text is visible. Any idea what is happening here?

---

### Post by fredskronk on 2006-11-29
I have tried all of the solutions mentioned here and none of them seems to be working. Will there ewer be a beta.deb and in that case when will it be released? To get full screen magnification (even if it's just a beta) is the only thing i need to be able to make the change to Linux.

---

### Post by jasongrieves on 2006-12-03
Sorry its been a crazy semester.  I can work on this in 1.5 weeks......

---

### Post by RKCole on 2006-12-05
No worries, jason.  I'm in college myself and I know exactly how things can be.  This is finals week for me...and it's going to be tough.  Have a lot of programming assignments, and for my Linux class ( :) ) I have to set up and demonstrate various servers and features.  Without Orca/magnifier, none of this would be possible.  I'm just so grateful to have what I have.

Take your time, though.  I know exactly how things can be with college.

Take care

---

### Post by fredskronk on 2007-01-03
How is things going? Is there coming any beta.deb? Would be nice to have it you know.

---

### Post by www.unreadedpost.com on 2007-01-10
> **pinballkid said:**
> Could you post a screenshot?
+1
sorry question?

---

### Post by jasongrieves on 2007-01-10
the developers have finally included the patches into the main source tree of gnome-mag.  I just built the latest gnome-mag and tested on latest ubuntu (fiesty) and it works pretty well with full screen support.  

The problem is currently the gnome-mag package in ubuntu is being built WITHOUT composite support.  In other words the latest ubuntu will have the version of gnome-mag with full screen support but will not have the composite support corrrectly turned on in the program.  I'll try to talk to the  package maintaner and try to get this taken care of.  Otherwise I'll just build the debs and put them here.

---

### Post by jasongrieves on 2007-01-10
i took a movie via vmware but its way to big for these forums

---

### Post by Henrik on 2007-01-10
Hi Jason!

I've filed a request for it here in LP: [https://bugs.launchpad.net/ubuntu/+source/gnome-mag/+bug/78714](https://bugs.launchpad.net/ubuntu/+source/gnome-mag/+bug/78714)

Please add your comments there. Let's try out best to get it into the default tree before resorting to custom debs :)

---

### Post by cerdiogenes on 2007-01-12
What´s the problem to build gnome-mag with COMPOSITE support?

---

### Post by Henrik on 2007-01-12
Apparently it won't build at all today on Feisty, but neither will any of our python apps :-k


Basically Feisty is still all up in the air (as it should be at this stage). Daniel is looking at gnome-mag. I'm sure he'll have it sorted out soon.

---

### Post by RKCole on 2007-01-12
Hi, guys!

Will this new release work on Edgy as well, or will it just be Feisty only?

Take care.

---

### Post by jasongrieves on 2007-01-13
Apparantly Firefox cached this forum so I didn't see any of you all's post until today!

I have gotten this to work no edgy and fiesty.  Henrik, what problems did you encounter?

---

### Post by jasongrieves on 2007-01-13
> **RKCole said:**
> Hi, guys!

Will this new release work on Edgy as well, or will it just be Feisty only?

Take care.

The new package would be for fiesty (assuming the new build gets put into fiesty)  

however building on edgy works just as well for me.  gnome-mag is a simple packages with few dependents.

---

### Post by RKCole on 2007-01-13
So, when everything is completed, would I just need to go to the GNOME Accessibility page and download the latest gnome-mag (source) to build on Edgy, or is there a different method for this?

I'm really looking forward to this.

Thanks for the input, Jason.

---

### Post by jasongrieves on 2007-01-13
hi,

this should work
```

sudo apt-get install build-essential gnome-devel libxdamage-dev libxcomposite-dev

wget ftp://ftp.gnome.org/pub/gnome/sources/gnome-mag/0.14/gnome-mag-0.14.1.tar.gz

gzip -d gnome-mag-0.14.1.tar.gz

tar -xvf gnome-mag-0.14.1.tar 

cd gnome-mag-0.14.1/


```

if you want to replace your current gnome-mag (not recommended but I do it anyway haha)

```

./configure --prefix=/usr
make all
sudo make install

```

If you want to have two versions of gnome-mag (not a problem at all, just make sure you know which one your running)
```

./configure
make all
sudo make install

```


*note this will only work if you overwrite the magnifier in /usr.  If you try to run orca with the default build magnifier it will not use it.

run orca --gui-setup
in magnifier tab change the contents of top and left to 0 and max out right and bottom
click apply

*note do not try to remove the cursor.  They are still working out the cursor bugs

alternatively you can run magnifier alone 
magnifier -f -m

or if its in the default build dir
/usr/local/bin/magnifier -f -m

---

### Post by RKCole on 2007-01-13
Thanks, Jason!

When you mentioned the cursor, did that apply to the crosshairs as well (can't stand those myself)?

Thanks.

---

### Post by jasongrieves on 2007-01-13
> **RKCole said:**
> Thanks, Jason!

When you mentioned the cursor, did that apply to the crosshairs as well (can't stand those myself)?

Thanks.

no I get rid of the cross hairs ASAP

did the setup work?  I tried on both edgy/fiesty, seems to work on with mine

---

### Post by jasongrieves on 2007-01-14
[https://launchpad.net/ubuntu/+source/gnome-mag/+bug/78714](https://launchpad.net/ubuntu/+source/gnome-mag/+bug/78714)

looks like we'll see this working in fiesty by default!

just tested the new version and it works well.  You might be able to downlaod the deb and use it in edgy, I'll try this later...

---

### Post by RKCole on 2007-02-27
Sorry for bringing back an older post, but I finally got a chance to compile gnome-mag-0.14.1 and I am using full-screen magnification as I type this.  I never knew what I was missing with this as now I do not have to strain my neck (haha) to read again as I had to with my previous configuration.  This is amazing!

Thanks for the information on how to set this up, Jason!  I just can't wait to see what the future holds for assistive technology in the realm of Linux.

Take care!

---

### Post by linbetwin on 2007-03-02
I have tested the zoom function in beryl 0.2 under PCLinuxOS. The zooming is so nice and smooth and now you can even use your keyboard and mouse for input when the desktop is zoomed. 

There are only two problems with this implementation:
1) the zoom doesn't follow cursor focus, so you have to move your mouse to see what you're typing.
2) the mouse pointer is not zoomed and I haven't found a way to change the mouse pointer to a bigger size in KDE.

---

### Post by jasongrieves on 2007-03-05
> **linbetwin said:**
> I have tested the zoom function in beryl 0.2 under PCLinuxOS. The zooming is so nice and smooth and now you can even use your keyboard and mouse for input when the desktop is zoomed. 

There are only two problems with this implementation:
1) the zoom doesn't follow cursor focus, so you have to move your mouse to see what you're typing.
2) the mouse pointer is not zoomed and I haven't found a way to change the mouse pointer to a bigger size in KDE.

Yeah I have done some testing with this also and found the same limitations.  I am not sure what to think of this development versus the gnome-mag.  I believe we need the magnifier built into the window manager at some point, but I am not sure this is the right time.  Its difficult since gnome/kde/xfce all have different window managers, but I really believe getting the window manager to handle the work is the key to a robust magnifier.  Its great to see this technology though!

---

### Post by linbetwin on 2007-03-05
Jason, I don't know if you have time to answer this, but how is gnome-mag + orca in feisty ? (I can't install a Herd CD right now). Does it work out-of-the-box? Any major bugs or incompatibilities with OOo, FF, etc. ? Is it a major improvement from Edgy?

Thank you.

---

