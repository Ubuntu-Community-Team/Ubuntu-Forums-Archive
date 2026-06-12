---
title: "cinelerra-2.1 ,"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by lifemaximum on 2006-09-24
Hi everyone
I was trying to install [COLOR="Blue"]**cinelerra-2.1**[/COLOR] on my laptop. so i downloaded the package from the website . extracted it and try to installing it by running the configure file in the terminal. but i got the msg below
[COLOR="Red"]

faz@faz-laptop:~$ /home/faz/Desktop/cinelerra-2.1/configure
 *** Nasm is required.  Download it from nasm.sourceforge.net
 *** Yasm is required.  Download it from [www.tortall.net/projects/yasm/](www.tortall.net/projects/yasm/)
Giving up and going to a movie.
faz@faz-laptop:~$[/COLOR]


so than i download [COLOR="DarkOrange"]Yasm[/COLOR] tried to get it installed but than i had no clue how to do it.? and [COLOR="DarkOrange"]Nasm[/COLOR] i couldn't find it anywhere... a little help will be much appericated](*,)

---

### Post by Marsolin on 2006-09-25
Go to this [link]("http://cvs.cinelerra.org/getting_cinelerra.php"). There is a deb package available for [Cinelerra]("http://linuxappfinder.com/package/cinelerra") that will be easier to install.

---

### Post by pay on 2006-09-25
To compile yasm type```
wget http://www.tortall.net/projects/yasm/releases/yasm-0.5.0.tar.gz
tar zxvf yasm-0.5.0.tar.gz
cd yasm-0.5.0/
sudo aptitude install build-essential checkinstall
./configure
make
sudo checkinstall -D make install
```

---

### Post by pay on 2006-09-25
And heres the NASM source [http://sourceforge.net/projects/nasm/](http://sourceforge.net/projects/nasm/)

---

### Post by lifemaximum on 2006-09-25
thanks pay

that took care of Yasm...

now how do i go about installing nasm ?/ 

thanks

---

### Post by lifemaximum on 2006-09-25
okie thanks i got Nasm working also

so i when i was trying to install it i got another error.

faz@faz-laptop:~/Desktop/cinelerra-2.1$ make
make -f build/Makefile.cinelerra
sh: -c: line 1: syntax error: unexpected end of file
make[1]: Entering directory `/home/faz/Desktop/cinelerra-2.1'
gcc -c -O2 -fomit-frame-pointer -falign-loops=2 -falign-jumps=2 -falign-functions=2 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -I../../freetype-2.1.4/include -I../../ -DHAVE_OSS -DHAVE_FIREWIRE  soundtest.c -o i686/soundtest.o
Assembler messages:
FATAL: can't create i686/soundtest.o: No such file or directory
make[1]: *** [i686/soundtest.o] Error 1
make[1]: Leaving directory `/home/faz/Desktop/cinelerra-2.1'
make: *** [all] Error 2


could anyone tell me what i did wrong/?

---

### Post by pay on 2006-09-25
Install nasm by typing```
wget http://sourceforge.net/projects/nasm/
tar jxvf nasm-0.98.39.tar.bz2
cd nasm-0.98.39/
./configure
make
sudo mkdir /usr/man #probably not necessary but I got an error about it not being able to create /usr/man/man1/nasm.1
sudo mkdir /usr/man/man1 #Also probably not necessary
sudo checkinstall -D make install
```

---

### Post by pay on 2006-09-25
Try```
sudo mkdir /i686
``` and make it again.

---

### Post by lifemaximum on 2006-09-25
Did that and i created the i686 directory...but when i tried to build it again i got the following :

[COLOR="RoyalBlue"]
faz@faz-laptop:~/Desktop/cinelerra-2.1$ make
make -f build/Makefile.cinelerra
sh: -c: line 1: syntax error: unexpected end of file
make[1]: Entering directory `/home/faz/Desktop/cinelerra-2.1'
gcc -c -O2 -fomit-frame-pointer -falign-loops=2 -falign-jumps=2 -falign-functions=2 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -I../../freetype-2.1.4/include -I../../ -DHAVE_OSS -DHAVE_FIREWIRE  soundtest.c -o i686/soundtest.o
Assembler messages:
FATAL: can't create i686/soundtest.o: No such file or directory
make[1]: *** [i686/soundtest.o] Error 1
make[1]: Leaving directory `/home/faz/Desktop/cinelerra-2.1'
make: *** [all] Error 2[/COLOR]


so what to do now?

---

### Post by pay on 2006-09-25
You might be trying to create the folder in the wrong directory, try mkdir i686 && sudo mkdir /i686, depending on where it wants the folder. Alternativly ou can try my compiled nasm in the attachments.

---

### Post by lifemaximum on 2006-09-25
I used your nasm dude...and i am still not getting it ...couldn't the developer make it like all other programs easy to download and install...is there any RPM or Bin for cinelerra which enables me to install it 

after i used your file i configured again and try to build it again and what i got was 

[COLOR="Red"]make[4]: Entering directory `/home/faz/Desktop/cinelerra-2.1/libiec61883-1.0.0/src'
if /bin/sh ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include      -I/root/hvirtual/libraw1394-1.2.0/ -MT cip.lo -MD -MP -MF ".deps/cip.Tpo" -c -o cip.lo cip.c; \
        then mv -f ".deps/cip.Tpo" ".deps/cip.Plo"; else rm -f ".deps/cip.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/local/include -I/root/hvirtual/libraw1394-1.2.0/ -MT cip.lo -MD -MP -MF .deps/cip.Tpo -c cip.c -o cip.o
In file included from cip.c:25:
iec61883.h:23:32: error: libraw1394/raw1394.h: No such file or directory
In file included from cip.c:25:
iec61883.h:115: error: syntax error before 'handle'
iec61883.h:129: error: syntax error before 'handle'
iec61883.h:364: error: syntax error before 'handle'
iec61883.h:379: error: syntax error before 'handle'
iec61883.h:574: error: syntax error before 'handle'
iec61883.h:659: error: syntax error before 'handle'
iec61883.h:673: error: syntax error before 'handle'
iec61883.h:881: error: syntax error before 'handle'
iec61883.h:910: error: syntax error before 'handle'
iec61883.h:944: error: syntax error before 'handle'
iec61883.h:967: error: syntax error before 'handle'
iec61883.h:985: error: syntax error before 'handle'
iec61883.h:993: error: syntax error before 'handle'
iec61883.h:999: error: syntax error before 'handle'
iec61883.h:1004: error: syntax error before 'handle'
iec61883.h:1009: error: syntax error before 'handle'
iec61883.h:1015: error: syntax error before 'handle'
iec61883.h:1020: error: syntax error before 'handle'
iec61883.h:1025: error: syntax error before 'handle'
iec61883.h:1030: error: syntax error before 'handle'
iec61883.h:1034: error: syntax error before 'handle'
iec61883.h:1038: error: syntax error before 'handle'
iec61883.h:1055: error: syntax error before 'h'
iec61883.h:1062: error: syntax error before 'h'
iec61883.h:1072: error: syntax error before 'h'
iec61883.h:1087: error: syntax error before 'h'
iec61883.h:1103: error: syntax error before 'h'
iec61883.h:1111: error: syntax error before 'h'
iec61883.h:1121: error: syntax error before 'h'
iec61883.h:1138: error: syntax error before 'h'
In file included from cip.c:26:
iec61883-private.h:160: error: syntax error before 'handle'
iec61883-private.h:212: error: syntax error before 'u_int32_t'
iec61883-private.h:212: warning: no semicolon at end of struct or union
iec61883-private.h:238: error: syntax error before 'raw1394handle_t'
iec61883-private.h:238: warning: no semicolon at end of struct or union
iec61883-private.h:246: error: syntax error before '}' token
iec61883-private.h:258: error: syntax error before 'raw1394handle_t'
iec61883-private.h:258: warning: no semicolon at end of struct or union
iec61883-private.h:266: error: syntax error before '}' token
iec61883-private.h:289: error: syntax error before 'raw1394handle_t'
iec61883-private.h:289: warning: no semicolon at end of struct or union
iec61883-private.h:298: error: syntax error before '}' token
iec61883-private.h:412: error: syntax error before 'h'
iec61883-private.h:428: error: syntax error before 'h'
cip.c:135: error: syntax error before 'handle'
cip.c: In function 'iec61883_cip_fill_header':
cip.c:141: error: 'ptz' undeclared (first use in this function)
cip.c:141: error: (Each undeclared identifier is reported only once
cip.c:141: error: for each function it appears in.)
cip.c:182: error: 'packet' undeclared (first use in this function)
cip.c:186: error: 'handle' undeclared (first use in this function)
make[4]: *** [cip.lo] Error 1
make[4]: Leaving directory `/home/faz/Desktop/cinelerra-2.1/libiec61883-1.0.0/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/faz/Desktop/cinelerra-2.1/libiec61883-1.0.0'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/faz/Desktop/cinelerra-2.1/libiec61883-1.0.0'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/faz/Desktop/cinelerra-2.1'
make: *** [all] Error 2[/COLOR]

i didn get anything out of it ...and have no clue what is wrong with it...

---

### Post by pay on 2006-09-25
It might be easier to do```
wget http://ww2.fs.ei.tum.de/~dr/cinelerra2.1_2.1-1_i386.deb
sudo dpkg -i cinelerra2.1_2.1-1_i386.deb
```

---

### Post by lifemaximum on 2006-09-25
alrite dude....thanks alot for helping... i am gona try that later...

---

### Post by pay on 2006-09-25
oh sorry, I misread something.
This is how I got it working
```
wget http://www.tortall.net/projects/yasm/releases/yasm-0.5.0.tar.gz
tar zxvf yasm-0.5.0.tar.gz
cd yasm-0.5.0/
sudo aptitude install build-essential checkinstall
./configure
make
sudo checkinstall -D make install
wget http://sourceforge.net/projects/nasm/
tar jxvf nasm-0.98.39.tar.bz2
cd nasm-0.98.39/
./configure
make
sudo mkdir /usr/man #probably not necessary but I got an error about it not being able to create /usr/man/man1/nasm.1
sudo mkdir /usr/man/man1 #Also probably not necessary
sudo checkinstall -D make install
sudo aptitude install gstreamer0.8-faad gstreamer0.8-a52dec liba52-0.7.4-dev fftw-dev sfftw-dev sfftw2 fftw3 fftw3-dev mffm-fftw1c2 mffm-fftw-dev fftw2 fftw3-doc liblame0 liblame-dev lame-extras lame toolame glame openexr libopenexr-dev libopenexr2c2a exrtools libraw1394-5 libraw1394-dev libmjpegtools0c2a libmjpegtools-dev mjpegtools libuuid1 uuid-dev libvorbisfile3 libtheora0 libtheora-dev libtheora-bin gstreamer0.8-theora ffmpeg2theora libvorbisenc2 libvorbis0a libvorbisenc2 libvorbisfile3 libvorbis-dev ffmpeg2theora gstreamer0.10-ffmpeg ffmpeg avifile-mjpeg-plugin gstreamer0.10-ffmpeg libfaad2-dev libfaad2-0 libavc1394-dev libavc1394-0 libavcodec-dev libavformat-dev libavifile-0.7c2 gstreamer0.10-ffmpeg gstreamer0.8-dirac gstreamer0.8-faac gstreamer0.8-plugins-multiverse gstreamer0.8-xvid libdirac0c2a autobook libclutils0-dev libclutils0c2 autoconf autoconf-doc autotools-dev libguile-ltdl-1 libltdl3 libltdl3-dev libtool libtool-doc libtiffxx0c2 libtiff4-dev libtiff4 libtiff-tools libtool libltdl3 avidemux libfame-0.9 libpvm3 transcode xvid4conf quicktime-x11utils libpng3 libpng3-dev libpngwriter0-dev libpngwriter0c2 pngcheck pngquant  libdv-bin libdvb-dev libdvbpsi4-dev libdvdplay0 libdvdplay0-dev libdvdread3-dev libasound2 libasound2-dev automake1.7 nasm libxxf86dga-dev libxxf86misc-dev libxxf86vm-dev libx264-dev libsndfile1 libsndfile0 libfaac-dev make libsndfile1 libsndfile1-dev quicktime-utils libxv-dev dvgrab libasound2 libasound2-dev
wget http://optusnet.dl.sourceforge.net/sourceforge/heroines/cinelerra-2.1-src.tar.bz2
tar jxvf cinelerra-2.1-src.tar.bz2
cd cinelerra-2.1/
./configure
sudo make #I got the same error that you got, i thought that you meant you were getting this error with nasm. sorry. running it as root seems to work
sudo checkinstall -D make install
```Goodluck, Sorry it is so messy.
EDIT:The last step still isn't working.

---

### Post by lifemaximum on 2006-09-25
Thanks dude...

i tried all those steps again...and installed everything all over..but like u said it still doesn't work...](*,) ](*,)  i have spend like almost half of the day ...trying to install this thing.

i even tried the debian package and i also get errors with that too. i wonder what is wrong...is it from comp.. or wat?](*,) ](*,) 

has anybody else installed / and how have u done it ?:confused:

---

### Post by pay on 2006-09-25
You could try to add a repository for another distro and then ```
sudo apt-get build-dep cinelerra
sudo apt-get --build source cinelerra
```
p.s. sorry for wasting half your day with solutions that didn't work.

---

### Post by lifemaximum on 2006-09-25
Thanks dude...for trying to help me... I really appericate you spending half a day helping me to install the software. thanks.

---

### Post by lifemaximum on 2006-09-25
Hi

:-k  I jus found this set of instructions in another thread duno if it works though ...  

i will try it later when i have my laptop with me... but here it is jus in case anyone was wondering how to install it like i am... if u tried it earlier than i and it worked ,let me know. 

Thanks
-----------------------------------------------------------------

[COLOR="DimGray"]"Hi, I managed to install Cinelerra using the following procedure

1)
Added these lines to my apt sources:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [http://www.kiberpipa.org/~minmax/cin...ilds/pentium4/](http://www.kiberpipa.org/~minmax/cin...ilds/pentium4/) ./

2)
Couldn't install cinelerra due to unavalability of libopenexr2
Did a package search at debian.org in testing and downloaded the libopenexr2 package from this page.

[http://packages.debian.org/testing/libs/libopenexr2](http://packages.debian.org/testing/libs/libopenexr2)

Then used dpkg to install it:

sudo dpkg -i libopenexr2_1.2.1-2_i386.deb

3)
Couldn't install cinelerra due to unavailabilty of libpng12-0
Did a package search at debian.org in testing and downloaded the libpng12-0 package from this page.

[http://packages.debian.org/testing/libs/libpng12-0](http://packages.debian.org/testing/libs/libpng12-0)

Then used dpkg to install it:

sudo dpkg -i libpng12-0_1.2.8rel-1_i386.deb

4)
Found all the dependancies were now satisfied so installed using:

apt-get install cinelerra

which downloaded and installed fine, loaded fine, very fast, havn't done any editing yet but thought this may help some people.

This is just my way of getting it installed, I really have no idea how this will effect the dependancies of other packages in ubuntu but luckily the missing packages seem to have no dependancies that werent already available so there is only a couple of packages borrowed from debian testing so hopefully wont cause any major trouble but as always use this information at your own risk ."[/COLOR]
_________________________________________________________________
:D

---

### Post by pay on 2006-09-25
I also found these repositories to add to your /etc/apt/sources.list
```
# Cinelerra repository
deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/ ./
deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools ./
deb-src http://www.kiberpipa.org/~minmax/cinelerra/builds/sid/ ./
```
Then just do```
sudo aptitude update
sudo aptitude install cinelerra
```
It worked for me.

---

### Post by lifemaximum on 2006-09-26
i am not sure if i installed ...

how do i run it ? it didn apear in my menu or anything ?

---

### Post by Perfect Storm on 2006-09-26
type:
```
cinelerra
```

You can always make a launcher for it.

---

### Post by lifemaximum on 2006-09-26
HELP

I KEEP GETTING 

[COLOR="Blue"]make[3]: Leaving directory `/home/faz/Desktop/cinelerra-2.1/libsndfile-1.0.11/tests'
make[3]: Entering directory `/home/faz/Desktop/cinelerra-2.1/libsndfile-1.0.11'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/faz/Desktop/cinelerra-2.1/libsndfile-1.0.11'
make[2]: Leaving directory `/home/faz/Desktop/cinelerra-2.1/libsndfile-1.0.11'
make -C quicktime
/bin/sh: -c: line 1: syntax error: unexpected end of file
/bin/sh: i686/c_flags: No such file or directory
/bin/sh: i686/lame_flags: No such file or directory
/bin/sh: i686/objs: No such file or directory
make[2]: Entering directory `/home/faz/Desktop/cinelerra-2.1/quicktime'
make[2]: *** No rule to make target `i686', needed by `all'.  Stop.
make[2]: Leaving directory `/home/faz/Desktop/cinelerra-2.1/quicktime'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/faz/Desktop/cinelerra-2.1'
make: *** [all] Error 2
[/COLOR]


AND WHEN I CHECK FOR INSTALIATION I GET THIS :](*,) 

[COLOR="Red"]========================= Installation results ===========================
make -f build/Makefile.cinelerra install
sh: -c: line 1: syntax error: unexpected end of file
make[1]: Entering directory `/home/faz/Desktop/cinelerra-2.1'
make -C cinelerra install
sh: -c: line 1: syntax error: unexpected end of file
/bin/sh: i686/c_flags: No such file or directory
/bin/sh: i686/objs: No such file or directory
make[2]: Entering directory `/home/faz/Desktop/cinelerra-2.1/cinelerra'
rm -f /usr/bin/cinelerra
cp i686/cinelerra /usr/bin
cp: cannot stat `i686/cinelerra': No such file or directory
make[2]: *** [install] Error 1
make[2]: Leaving directory `/home/faz/Desktop/cinelerra-2.1/cinelerra'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/faz/Desktop/cinelerra-2.1'
make: *** [install] Error 2

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.
[/COLOR]

I keep getting that](*,) ](*,)

---

### Post by lifemaximum on 2006-09-26
Can the problem be related to my vmwareplayer

[COLOR="Red"]Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...
The subnet .  .  .0/ . . .0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install
already exists.  Overwrite? [yes]

Configuring a host-only network for vmnet1

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libboost-python1.33.1 (1.33.1-2) ...
[/COLOR]

every software that i try to install i get that...:confused:

---

### Post by pay on 2006-09-26
Why are you trying to compile it if you installed it through the repository?

---

### Post by lifemaximum on 2006-09-26
i am just trying different ways... none of them yet has produced satisfactory resualts.

---

### Post by pay on 2006-09-26
So you added```
# Cinelerra repository
deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/ ./
deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools ./
deb-src http://www.kiberpipa.org/~minmax/cinelerra/builds/sid/ ./
```to your /etc/apt/sources.list and```
sudo aptitude update
sudo aptitude install cinelerra
```and it still hasn't worked? Did it come up with errors while trying to install? Maybe missing dependencies?

---

### Post by envisionthestorm on 2006-09-26
ok im having trouble with this also. ive added to the sources etc, when I run the install cinelerra command I get

" 
Keep the following packages at their current version:
cinelerra [Not Installed]
libguicast [Not Installed]
libmpeg3hv [Not Installed]
libquicktimehv [Not Installed]

Score is 26

Accept this solution? [Y/n/q/?]
 "

no matter what steps I take after this I get a load of stuff about vmware...

" Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.251.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes]

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to installalready exists.  Overwrite? [yes] dpkg: error processing vmware-player (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
 " 

etc etc etc

---

### Post by pay on 2006-09-26
Try ```
sudo apt-get install -f
sudo apt-get install cinelerra
```

---

### Post by envisionthestorm on 2006-09-26
> **pay said:**
> Try ```
sudo apt-get install -f
sudo apt-get install cinelerra
```

from the first command I get the vmware stuff... exactly the same.
second command i get

"The following packages have unmet dependencies.
  cinelerra: Depends: libasound2 (> 1.0.11) but 1.0.10-2ubuntu4 is to be installed
             Depends: libavc1394-0 (>= 0.5.3) but 0.5.1-1 is to be installed
             Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is to be installed
             Depends: libfreetype6 (>= 2.2) but 2.1.10-1ubuntu2.2 is to be installed
             Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
             Depends: libguicast (>= 1:2.1.0) but it is not going to be installed
             Depends: libiec61883-0 but it is not installable
             Depends: libmjpegtools0 (>= 1:1.8.0) but it is not installable
             Depends: libmpeg3hv (>= 1:2.1.0) but it is not going to be installed
             Depends: libquicktimehv (>= 1:2.1.0) but it is not going to be installed
             Depends: libraw1394-8 but it is not installable
             Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
             Depends: libguicast (= 1:2.1.0-1svn20060918) but it is not going to be installed
             Depends: libquicktimehv (= 1:2.1.0-1svn20060918) but it is not going to be installed
             Depends: libmpeg3hv (= 1:2.1.0-1svn20060918) but it is not going to be installed
"

bear in mind im maybe a 3day old linuxer...

---

### Post by pay on 2006-09-26
cinelerra: Depends: libasound2 (> 1.0.11) but 1.0.10-2ubuntu4 is to be installed
Depends: libavc1394-0 (>= 0.5.3) but 0.5.1-1 is to be installed
Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is to be installed
Depends: libfreetype6 (>= 2.2) but 2.1.10-1ubuntu2.2 is to be installed
Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
Depends: libguicast (>= 1:2.1.0) but it is not going to be installed
Depends: libiec61883-0 but it is not installable
Depends: libmjpegtools0 (>= 1:1.8.0) but it is not installable
Depends: libmpeg3hv (>= 1:2.1.0) but it is not going to be installed
Depends: libquicktimehv (>= 1:2.1.0) but it is not going to be installed
Depends: libraw1394-8 but it is not installable
Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
Depends: libguicast (= 1:2.1.0-1svn2006091 but it is not going to be installed
Depends: libquicktimehv (= 1:2.1.0-1svn2006091 but it is not going to be installed
Depends: libmpeg3hv (= 1:2.1.0-1svn2006091 but it is not going to be installed

Are all the dependencies that you need to install or upgrade to.
Search for the packages here [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
download them and then isntall them (sudo dpkg -i packagename.deb) and then install cinelerra again (sudo apt-get install cinelerra)

---

### Post by envisionthestorm on 2006-09-26
ok done that, 4 of them didnt show up in the searches, hopefully I can get them somewhere else?

libguicast
libiec61883-0
libmpeg3hv
libquicktimehv

the others were already installed apparantly, I re-installed them anyway just to be sure. ran install cinelerra again just to see if anything different came up. got exact same message - tho I dont know if it came up before or not but I noticed this time on the end it says
"E: Broken packages"

---

### Post by pay on 2006-09-26
This program is annoying:P it has hand to find dependencies and its hard to compile. Anyway I need some sleep. It's 4:37am where I am... I'll look into it tomorrow.

---

### Post by envisionthestorm on 2006-09-26
> **pay said:**
> This program is annoying:P it has hand to find dependencies and its hard to compile. Anyway I need some sleep. It's 4:37am where I am... I'll look into it tomorrow.

lol ok, cheers for helping :)

---

### Post by lifemaximum on 2006-09-26
HAHAH  it is good. i am not the only one who cannot get it installed , i feel better.:D :mrgreen:

---

### Post by pay on 2006-09-26
Ok heres my full sources.list ```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/plf dapper free non-free
deb-src http://packages.freecontrib.org/plf dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

# Repository for wine
deb http://wine.budgetdedicated.com/apt dapper main
deb-src http://wine.budgetdedicated.com/apt dapper main

# XGl and compiz
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main

# XMMS2 Repository
deb http://exodus.xmms.se/debian dapper main

# Cinelerra repository
deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/ ./
deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools ./
deb-src http://www.kiberpipa.org/~minmax/cinelerra/builds/sid/ ./

# kubuntu.org packages for the latest KDE version (packages and sources, GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde-latest dapper main
deb-src http://kubuntu.org/packages/kde-latest dapper main

# kubuntu.org packages for the latest amaroK version (packages and sources, GPG key: DD4D5088)
deb http://kubuntu.org/packages/amarok-latest dapper main
deb-src http://kubuntu.org/packages/amarok-latest dapper main

# The Opera browser (packages)
deb http://deb.opera.com/opera etch non-free

# Edgy sources
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://packages.freecontrib.org/plf edgy-plf free 
```Then do a ```
sudo apt-get update
sudo apt-get install cinelerra
```

---

### Post by envisionthestorm on 2006-09-27
" sean@sean-laptop:~$ sudo apt-get install cinelerra
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  cinelerra: Depends: libasound2 (> 1.0.11) but 1.0.10-2ubuntu4 is to be installed
             Depends: libavc1394-0 (>= 0.5.3) but 0.5.1-1 is to be installed
             Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is to be installed
             Depends: libfreetype6 (>= 2.2) but 2.1.10-1ubuntu2.2 is to be installed
             Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
             Depends: libguicast (>= 1:2.1.0) but it is not going to be installed
             Depends: libmjpegtools0 (>= 1:1.8.0) but it is not installable
             Depends: libmpeg3hv (>= 1:2.1.0) but it is not going to be installed
             Depends: libquicktimehv (>= 1:2.1.0) but it is not going to be installed
             Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
             Depends: libguicast (= 1:2.1.0-1svn20060918) but it is not going to be installed
             Depends: libquicktimehv (= 1:2.1.0-1svn20060918) but it is not going to be installed
             Depends: libmpeg3hv (= 1:2.1.0-1svn20060918) but it is not going to be installed
E: Broken packages
" 

no luck ](*,) ](*,) ](*,) ](*,) ](*,) 
think ill b giving up and sticking to windows for video editing soon

---

### Post by Perfect Storm on 2006-09-27
Try this one. It's one I've converted from a .rpm package.

[http://www.filelodge.com/files/room38/1059449/Ubuntu/cinelerra_2.0-2_i386.deb](http://www.filelodge.com/files/room38/1059449/Ubuntu/cinelerra_2.0-2_i386.deb)
Though it's not the newest version.

---

### Post by envisionthestorm on 2006-09-27
> **Artificial Intelligence said:**
> Try this one. It's one I've converted from a .rpm package.

[http://www.filelodge.com/files/room38/1059449/Ubuntu/cinelerra_2.0-2_i386.deb](http://www.filelodge.com/files/room38/1059449/Ubuntu/cinelerra_2.0-2_i386.deb)
Though it's not the newest version.

downloads, installs, loads up.... now I just gotta figure out how to use the thing :D

thanks :D

---

### Post by lifemaximum on 2006-09-27
thanks pay finally i got installed so happy... when i saw the icon there in the menu i felt a sense of accomplishement hahah.... anyways...now it doesn't load up... i mean i keep clicking on the icon ...and nothing happens... ??so how do i get it running](*,) ??

---

### Post by envisionthestorm on 2006-09-27
try typing cinelerra in a terminal. I dont have it in my menus but that wors for me.

---

### Post by lifemaximum on 2006-09-27
faz@faz-laptop:~$ which cinelerra
/usr/bin/cinelerra
faz@faz-laptop:~$ cinelerra
Illegal instruction


that is what i am getting...what is illegal instruction ?

---

### Post by pay on 2006-09-27
That is strange. Maybe its a bug that you should inform the devolopers of.

---

### Post by lifemaximum on 2006-09-28
man i gave up on cinelerra...:-#

---

### Post by Perfect Storm on 2006-09-28
Did you tried the .deb I provided?

---

### Post by Monkus on 2006-09-28
Hey,
I found this. I don't know if it will help, but you never know.

Cinelerra Ubuntu Instructions
(last updated 22th August 2006)

Installing Cinelerra on Ubuntu, the new way.

Ubuntu doesn't play very well with Marillat's Debian repository. So I am
currently also providing packages that are not in Ubuntu.

Current instructions are for Ubuntu 5.10 (Breezy) and 6.06 (Dapper). 5.04 (Hoary) is not supported.

Setting up repositories:

1. Enable universe, multiverse and restricted

Make sure you have following line uncommented in your /etc/apt/sources.list

for breezy:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse restricted

for dapper:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse restricted

2. Add mjpegtools ubuntu backport

for breezy:

deb [http://www.kiberpipa.org/~gandalf/ubuntu/breezy/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/breezy/mjpegtools) ./

for dapper:

deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools) ./

3. Add cinelerra build for your arch:

for breezy:

- i686:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/i686/) ./
- athlonxp:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/athlonxp/) ./
- pentium4:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/breezy/cinelerra/pentium4/) ./

for dapper:

- i686:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/) ./
- athlonxp:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/) ./
- pentium4:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/) ./

Installation:

apt-get update
apt-get install cinelerra


Good luck.

---

### Post by lifemaximum on 2006-09-29
faz@faz-laptop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory


that is what i got ?

---

### Post by pay on 2006-09-29
You need to run apt as root. ```
sudo apt-get update
```

---

### Post by lifemaximum on 2006-09-29
> **pay said:**
> You need to run apt as root. ```
sudo apt-get update
```

yea u are rite ... i forgot...

by the way what are the other movie editors that are as good as cinelerra... i checked the forums around and they all said cinelerra is pretty good...they say it is like the hardcore movie editing software... is there any other software that is as good as cinelerra?:-k

---

### Post by doobit on 2006-09-29
> **lifemaximum said:**
> yea u are rite ... i forgot...

by the way what are the other movie editors that are as good as cinelerra... i checked the forums around and they all said cinelerra is pretty good...they say it is like the hardcore movie editing software... is there any other software that is as good as cinelerra?:-k

Yes, MainActor - but you gotta pay...

[http://www.mainconcept.com/site/index.php?id=395](http://www.mainconcept.com/site/index.php?id=395)

---

### Post by CameronCalver on 2006-10-04
Ok this is a very confusing thread lol can someone give me a how to and a one that works lol

---

