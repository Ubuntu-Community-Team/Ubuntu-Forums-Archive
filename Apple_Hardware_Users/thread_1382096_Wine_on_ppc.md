---
title: "Wine on ppc"
date: 2010-01-15
forum: Apple Hardware Users
---

### Post by guybrush.d on 2010-01-15
Hi guys,
for the joy of every LINUX PPC USERS i'll present the wine installation on PPC linux! :P
Here we are:

1) WHY? 
Well because maybe flash doesn't work, or you wanna play some windows game, or use 
some windows programs...
2)SPEED
I have an ibook clamshell 366Mhz that i will overclock soon, but you don't have to expect 
very high emulation because you will have a double translation of the cpu instruction.
3)HOW?
Here we are...

1) First of all, wine doesn't run on PPC architectures so how is described here "http://en.opensuse.org/PowerPC_x86_Emulator" you will have to use qemu, i won't describe here what is the better cpu emulator
i just used it. So trough synaptic install qemu amd with this you will also have the possibility to install a virtual machine with windows.

2) create a directory on you hd. My is /home/ARC_X86/

3) get the following RPMS:
ash-0.3.8-8.i386.rpm
bash-2.05b-20.i386.rpm
compat-libstdc++-7.3-2.96.118.i386.rpm
coreutils-4.5.3-19.i386.rpm
glib-1.2.10-10.i386.rpm
glibc-2.3.2-11.9.i386.rpm
gtk+-1.2.10-25.i386.rpm
libgcc-3.2.2-5.i386.rpm
libjpeg-6b-26.i386.rpm
libstdc++-3.2.2-5.i386.rpm
libtermcap-2.0.8-35.i386.rpm
libungif-4.1.0-15.i386.rpm
XFree86-4.3.0-2.i386.rpm
XFree86-libs-4.3.0-2.90.55.i386.rpm
zlib-1.1.4-8.i386.rpm

and the last wine .rpm

I've also tried some newer version of the files but some didn't 
work at all.

4) copy the rpm to the dir you've just created (/home/ARC_X86/)

cp *.rpm /home/ARC_X86/

5) extract the rpms in this dir with rpm2cpio and cpio

rpm2cpio ash-0.3.8-8.i386.rpm | cpio -idmv

I know could be more easy to use the *.rpm but i got some problem 
with cpio (malformed file or something) with the newest version 
of the libraries so i used the old version, and i had a more clear 
sight on the extracting operation of the single rpm.

At this point you will have a complete linux x86 subsystem in your
/home/ARC_X86/

now little explanation:

Extracting wine in this way doesn't make a real installation, infact
wine installer usally create a .wine dir in your $HOME, so what i did 
it has been just simple as to copy my .wine from the desktop pc 
(it's an x86) to my IBOOK! ;)

And now you will have the x86 subsystem dir plus .wine dir in your 
home dir.:P

So what now?

Also if there sould be a way to load an x86 app through qemu, i simply
create a shell script that load my app. Here we are:

nano x86_execute

then write

#!/bin/bash

declare -x WINEDLLPATH="/home/ARC_X86/usr/lib/wine"
declare -x LD_LIBRARY_PATH="/home/ARC_X86/usr/lib:/home/ARCHS/rh_x86/usr/X11R6/lib"
qemu-i386 -L /home/ARCHS/rh_x86 /home/ARC_X86/usr/bin/wineserver
qemu-i386 -L /home/ARCHS/rh_x86 /home/ARC_X86/usr/bin/wine-pthread $1

then press CTRL + o and CTRL + X to save and exit, yoiu can also use gedit
or kate to generate the script

Now let's make it executable

chmod +x x86_execute

if you want you can link it to /usr/bin (sudo ln -s x86_execute /usr/bin)
to put it in you path or just copy it to /usr/bin :D

OK I KNOW IT HAS BEEN VERY LONG BUT FORGIVE ME PLEASE ;)

This is the end now every time you will want to execute an x86_app
you will just have to write for example:

x86_execute <app-name>

for every application you have installed into the x86_subsystem, 
i'm just trying to make a shell script that will help in the installation
of the programs, i'will publish it as soon as i can.

I hope helped many people like me that own a powerpc and love linux,
CIAO.:P

---

### Post by linuxopjemac on 2010-01-15
dude, we are in Ubuntu, not Mandrake or Redhat...

---

### Post by guybrush.d on 2010-01-15
Hi linuxopjemac,
i know that and i'm sorry but this was the fastest way to unpack the packages i found! :rolleyes:
if someone knows how to unpack the packages in a dir without using archive manager 
is welcome!

Anyway i think it's not important which ways you'll take through the path if the end will lead
to freedom! CIAO:P

---

### Post by llamabr on 2010-01-16
> **guybrush.d said:**
> 
Anyway i think it's not important which ways you'll take through the path if the end will lead
to freedom! CIAO:P

Yes, the freedom of running broken ms apps with an emulator that barely works.

Wine is almost never the correct solution to whatever you're trying to do.  Whatever it is you want, there's likely a native application that will satisfy your needs.  If not, one can probably be scripted for you.

---

### Post by sliketymo on 2010-01-16
Dual-boot seems to work pretty good for me.

---

### Post by 1984dc on 2011-04-13
Sorry for seeming a little ignorant (i've only been using the penguin for just over a year), but how do you  > get the following RPMS:
ash-0.3.8-8.i386.rpm
bash-2.05b-20.i386.rpm
compat-libstdc++-7.3-2.96.118.i386.rpm
coreutils-4.5.3-19.i386.rpm
glib-1.2.10-10.i386.rpm
glibc-2.3.2-11.9.i386.rpm
gtk+-1.2.10-25.i386.rpm
libgcc-3.2.2-5.i386.rpm
libjpeg-6b-26.i386.rpm
libstdc++-3.2.2-5.i386.rpm
libtermcap-2.0.8-35.i386.rpm
libungif-4.1.0-15.i386.rpm
XFree86-4.3.0-2.i386.rpm
XFree86-libs-4.3.0-2.90.55.i386.rpm
zlib-1.1.4-8.i386.rpmDo i need to install anything? I tried wget and apt-get, but that didn't work.

Many thanks 

Dc

---

### Post by pauljwells on 2011-04-13
Impressive work, but I probably won't bother for the reasons given by llamabr!

@1984dc - RPMs are 'Red Hat Package Manager' packages (equivalent to Ubuntu 'deb' files.) You can usually find them on the web like [http://rpm.pbone.net/]("http://rpm.pbone.net/") although that site seems to be down at the moment...

---

