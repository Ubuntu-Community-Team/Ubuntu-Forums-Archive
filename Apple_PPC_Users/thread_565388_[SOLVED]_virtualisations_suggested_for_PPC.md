---
title: "[SOLVED] virtualisations suggested for PPC"
date: 2007-10-02
forum: Apple PPC Users
---

### Post by frog_pilot on 2007-10-02
Hi, I'm looking for virtual environments for ppc-ubuntu where I could try out for instance windows or other linux-distros.

If I am right:

mol - is only for using your Mac OS in Linux

virtual box/server - won't run on ppc-architecture

qemu - I don't know anything about...

xen - my first choice???

What are you using?
Any suggestions are welcome.. ;)

---

### Post by engla on 2007-10-02
Well QEMU is the only emulator out of those (I think). So you can only run windows in qemu, which probably doesn't work too well. 

I know you could use mol to run linux in linux before. So that should be possible for other powerpc distros. If Xen works with powerpc then it's the same thing there.

---

### Post by stmiller on 2007-10-02
The current MOL only boots OS9 or OS X. No Linux PowerPC right now, though that is in the works and should work soon.

Qemu can run Windows, though a bit slow. The kqemu module only works on x86, so under powerpc it is entirely emulation. Check out this qemu manager: [http://qemulator.createweb.de/](http://qemulator.createweb.de/)

BUT! Right now you cannot run a recent PowerPC Linux distro in Qemu. There is a horrible bug where a 2.6 PowerPC Linux kernel will not boot in qemu. 2.4 kernels work, though. So you could perhaps get a PowerPC Linux distro to work, but it would be somewhat of a hack. It seems that the qemu project is more focused on x86 and x86_64.

OR you could just run an x86 Linux distro with qemu, though it's all emulation.

There is a Xen port in the works for powerpc, but it is for ppc64 (G5) only:
[http://wiki.xensource.com/xenwiki/XenPPC/](http://wiki.xensource.com/xenwiki/XenPPC/)

-------------

For me, I have OS X Tiger as a VM with MOL, and Win98SE in qemu on my 867Mhz Powerbook G4. I never need Windows, but have a 1GB image of Win98 there in case I need to execute any windows code. :)

---

### Post by frog_pilot on 2007-10-03
Thanks, stmiller, for sharing your experiences :) Then I will try out a OSX on MOL and a win2k on qemu and look forward to the linuxable mol-version coming soon 8-)

---

### Post by frog_pilot on 2007-10-04
@stmiller: do you use the mol-ubuntu-package 0.9.70-20ubuntu2 or did you download the *tar.bz2 (0.9.72.1) from sourceforge? I think there are many dependencies. the installation described [here]("http://mac-on-linux.sourceforge.net/wiki/index.php/Installation_Instructions#Installing_the_Required_Packages") is too cryptic for my knowledge of linux. I think, I'll first try the ubuntu-default-packages.
In synaptic, in the comment-window is written > In order to actually use
it, you need kernel modules from an mol-modules package built against
your kernel versionWhat does this mean. Can I harm my ubuntu or my nativeOSX-Install which I will run on mol?

---

### Post by stmiller on 2007-10-04
Well the provided ubuntu package of MOL is old, and probably will not work with 10.4 Tiger. I think that you are missing the package* linux-headers* . You can just install the latest mol like this, if you want:

First install these things:
```
sudo apt-get install build-essential subversion linux-headers
```

Then simply issuing
```
svn co http://mac-on-linux.svn.sourceforge.net/svnroot/mac-on-linux/trunk mac-on-linux
```
will download the latest mac on linux (to work good with 10.4, as well as other fixes) 
and then running 
```

./autogen.sh
make		
sudo make install

```
will configure and install MOL, including the modules. When the blue screen comes up in the terminal to configure the modules, just hit spacebar to enable all of them, if they are not all checked.

The you have to edit /etc/mol/molrc.osx as needed. 
And finally issuing 
```
startmol -X
```
will start OS X!

---

### Post by Auria on 2007-10-04
Hi,

in the link you posted, these are simply cmands to be pasted on the terminal. Don't copy the # from the beginning, and backslash means "continuing on the same line". You will also need to add "sudo " witout the quotes in front of the apt-get command because it's a task hat requres admin riviledges. After that, you can simply enter it into the terminal and all needed dependecies will be installed

---

### Post by frog_pilot on 2007-10-05
Many Thanks to stmiller & auria. I will try it tonight and keep you in the loop :popcorn:

---

### Post by frog_pilot on 2007-10-06
Ok, I'm on the run now. I made kinda mixture of stmillers suggestions and the mol wiki. first I installed```
sudo apt-get install autoconf libc6-dev ncurses-dev zlib1g-dev libasound2-dev xlibs-dev libpng12-dev libxxf86dga-dev automake autoconf build-essential subversion linux-headers-powerpc (I only had linux-headers-powerpc-smp and linux-headers-powerpc-smp64) linux-source
```then I issued```
svn co http://mac-on-linux.svn.sourceforge.net/svnroot/mac-on-linux/trunk mac-on-linux
```changed to directory ~/mac-on-linux, executed```
./autogen.sh
```and```
make
```Now i'm on the blue terminal-Window which stmiller outlined in his post. There I'm enabeling every feature of these subcategories as stmiller said:
[QUOTE="mol-config"] Machine Specific Build Targets  --->
Video Drivers  --->
Sound Drivers  ---> 
Network drivers  --->
Device Support  --->
Debugging  ---> 
--- 
Load an Alternate Configuration File
Save Configuration to an Alternate File[/QUOTE]
There I enabled oldworld and amiga support and these things. Is this really necessary? But there is one big issue under "Debugging":
[QUOTE="mol-config"][*] Debugger support

[*] Experimental TTY driver

[*] Log SCSI commands 

[*] Dump network packets 

[*] Dump DHCP negotiation information 

[*] Build a hosted MOL version (WARNING: don't enable this!) [/QUOTE]
I think I should leave the last point unmarked....? But I don't understand what a hosted MOL version is. I will wait a while for reply. If there will be no one when I'm back, I will proceed from my point of view (disable oldworld etc and this mentioned last option...) [-o<

---

### Post by frog_pilot on 2007-10-06
Ok, disabled Amiga, oldworld, hosted mol-version, and the logging features from the debug-section.

Everything went fine on "make" exept:```
+ Entering Linux
/home/mpunk/mac-on-linux/obj-ppc/build/src/kmod/_dev.c: In function &#8216;find_physical_rom&#8217;:
/home/mpunk/mac-on-linux/obj-ppc/build/src/kmod/_dev.c:75: warning: unused variable &#8216;by_type&#8217;
  AS [x]   /home/mpunk/mac-on-linux/obj-ppc/build/src/kmod/_traps.o
  Building modules, stage 2.
WARNING: could not find /home/mpunk/mac-on-linux/obj-ppc/build/src/kmod/.traps.o.cmd for /home/mpunk/mac-on-linux/obj-ppc/build/src/kmod/traps.o
    Kernel source                 : /lib/modules/2.6.20-16-powerpc-smp/build
    Module compiled for           : 2.6.20-16-powerpc-smp
    Running kernel                : 2.6.20-16-powerpc-smp
+ Entering netdriver
make[5]: *** No rule to make target `/home/mpunk/mac-on-linux/obj-ppc/build/src/netdriver/ethertap.c', needed by `/home/mpunk/mac-on-linux/obj-ppc/build/src/netdriver/ethertap.o'.  Stop.
make[4]: *** [_module_/home/mpunk/mac-on-linux/obj-ppc/build/src/netdriver] Error 2
+ Entering util/img
```

I will proceed now and have a look, which funcionality I lost.

Is there a way to undo these changes to my System after all? I meintioned the following:```
# End of "Mac-on-Linux" configuration.
# The next step is probably 'make'.

config.status: creating unconfig
config.status: creating Makefile.defs
config.status: creating config.h
config.status: config.h is unchanged
= Building mol-0.9.73-SVN [Okt 6 2007 23:32]
```

//Edit:
When Im now starting mol, the following appears:```
mpunk@PUNIX-G4:~/mac-on-linux$ startmol -X
Mac-on-Linux 0.9.73-SVN [Okt 6 2007 23:32]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 1
Loading Mac-on-Linux kernel module:
   /usr/local/lib/mol/0.9.73/modules/2.6.20-16-powerpc-smp/mol.ko
The kernel module '/usr/local/lib/mol/0.9.73/modules/2.6.20-16-powerpc-smp/tun.o' appears to be missing.
Running in PowerPC 7400 mode, 128 MB RAM
Timebase: 41.65 MHz, Bus: 166.63 MHz, Clock: 1249 MHz
Using USB mouse on /dev/input/mice
OHCI USB controller registered 
Could not open '/var/local/mol/x11.kbd'
Fullscreen video on VT 9.
Could not open '/var/local/mol/console.kbd'
Video driver(s): [xvideo] [console_video] 
```
Followd by Listing of the available video-modes and th scan for the OSX-Systemvolume. Then I get a window with the mol-splash and nothing will happen. Can you give me any further support for this?

---

### Post by frog_pilot on 2007-10-07
Ok, finally it's runnig I forgot to unpack the kernel-sources and to create a link to the sources /drivers/-Directory.

I gave mol 50% of my Ram its 1024 MB. Now its running and I'm testing functionality...

I wouldn't say its running with nearly native speed. And functionality isn't so good. When I start SIGMA Photo Pro to access my pics, it shows the thumbnails, but the check window, where I can adjust the fotos and so on isn't opening at all. May be it depends on the limited drivers and the limited amount of Ram. For small apps may be its working, but unfortunately it can't substitute booting into OSX for me :(

---

### Post by frog_pilot on 2007-10-09
When I'm working with MOL, there is only the systemvolume (hda3) mounted.

How can I manage to mount my data-volumes hdb4 and hdb5?

///edit:
I will create a new thread for these mol-related Questions.

---

### Post by superFerra on 2007-10-24
Well,
just installer mol from svn ... I had to mix all your instructions but worked!
First macos boot it asked me to install driver. I did ...
Rebooted then:
- Video is a bit blue (before installing drivers was perfect)
-Network isn't recognized ... No Airport extreme and no wired lan except for an en0 lan adapter that i'm not able (not allowed) to configure ...
Any suggestion??

TIA

PS: Installed on an iBook G4 800Mhz ~650Mb ram Airport Extreme ...(bcm4306 rev03)

---

### Post by frog_pilot on 2007-10-24
I also installed the drivers under osx after first start of MOL->OSX and mentioned no difference. Execute molvconfig ```
sudo molvconfig
``` and find out your matching video mode. Edit your /etc/mol/molrc.video.

You can't configure your network from inside OS X running on MOL. Read [this]("https://help.ubuntu.com/community/MacOnLinuxHowto#head-11a36cac4a033ef4bef636c1979016be90ac89b8") and find out the best solution for you.

I didn't configured my network yet because I'm playing with compiz-fusion in the mean time. I gave the sheep-driver a choice but it didn't work on my system. When I will start a new approach I will report here.

I'm on PowerMac G4 MDD Dual 1,25 with 2 GB RAM and GiB-LAN-Adapter.

---

### Post by mfox on 2008-05-25
Almost a year later, I attempted to get MOL running on my PowerBook G4 Al with Tiger/Hardy dual boot. I followed frog_pilot's instructions, up to the svn command, but at the one prior, the result ended with "Checked out revision 145."  When I then tried the autogen, I got:

 Invoking autoheader and autoconf.
./autogen.sh: 20: autoheader: not found
autoheader failed

That's as far as I got.  Any suggestions?

---

### Post by Nixblicker on 2008-05-30
Hi mfox and others,

i have some suggestions for you probably.
I had to install really a big bunch of development packages to make it even compile this. Anyway, after solving this missing dependencies it compile well , including some warnings but when trying startmol -x or any other startmol option it says:

lmoeller@Gsysm94:~/mac-on-linux$ startmol -X 
Mac-on-Linux 0.9.73-SVN [Mai 30 2008 18:28]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 1
Segmentation fault

But back to my suggestions - i had to install the following packages to make it even compile on a more or less virgin hardy installation:

libc6-dev ncurses-dev zlib1g-dev libasound2-dev xlibs-dev libpng12-dev libxxf86dga-devlibc6-dev ncurses-dev zlib1g-dev libasound2-dev xlibs-dev libpng12-dev libxxf86dga-dev automake1.9 xlibs-data 
xlibs-static-dev  x11proto-xext-dev  libxext-dev

I think automake1.9 is the missing package for your specific problem, mfox.

Hope it helps anyhow, good luck

Nix

---

### Post by mfox on 2008-06-06
Thanks for the suggestion, Nixblocker.  I downloaded automake1.9, but when I then issued  
"svn co [http://mac-on-linux.svn.sourceforge.net/svnroot/mac-on-linux/trunk](http://mac-on-linux.svn.sourceforge.net/svnroot/mac-on-linux/trunk) mac-on-linux"

I got:
"Checked out revision 145" again.

When I followed with 
"./autogen.sh"

I got:
"No such file or directory"

Not sure where to go from here.  Perhaps I should remove all of the files, including MOL files and start over?

---

### Post by Nixblicker on 2008-06-06
Hi mfox,

excuse my late response - but i wasn't around for a while.

For my understanding of this whole procedure, the message "Checked out revision 145" is a quite normal feedback of the svn tool, that downloads a copy of the online development trunk to your computer.

But in order to compile it, you have to enter that directory which is copied. So normally you have to type:
```
cd ~/mac-on-linux
```

You can actually extract the directory location from the svn command you used to download the stuff.
The you use:
```
./autogen.sh
```
```
make
``` and
```
sudo make install
```

all in that downloaded directory.

Then it should be compiled and installed already, but most likely you won't reach that point because of other missing dependencies and related compilation errors. 
Wish you success with it  (not meant ironically) even though i made it compile with just a couple of remarks, but no errors - and still have my damn segmentation error when i want to start it. NARF!!!!!

Cu, Nix

---

