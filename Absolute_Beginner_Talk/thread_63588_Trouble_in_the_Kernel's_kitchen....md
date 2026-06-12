---
title: "Trouble in the Kernel's kitchen..."
date: 2005-09-08
forum: Absolute Beginner Talk
---

### Post by djnitro on 2005-09-08
Howdy!

I'm trying out Ubuntu for the first time and running into a few problems... I have a feeling this is all very simple to fix, but I guess I just don't have my head around it yet.

--- the Intro ---

I'm installing Ubuntu in order to play UT2004. The install went fairly well, except I hung at "Testing Network Repository". I got around this by re-installing Ubuntu with the network cable unplugged. Ubuntu is now installed but has no internet access. I have grub installed and when I boot to Windows (xp) there's no problem getting online.

my system is an Abit NF8-V mobo 1 gig of ram and an Ati 9800 pro vid card.

--- the problem (I think) ---
I'm thinking the drivers aren't installed for my motherboard. it uses an Nvidia chipset.

--- what I've done so far ---
I went to Nvidia's website and downloaded the linux driver for the on-board ethernet. (filename: NFORCE-Linux-x86-1.0-0306-pkg1.run) I did "sudo sh <filename>" to run it, and it said, "No precompiled kernel interface was found to match your kernel, I'll have to make a new one" (paraphrased) I said, "go for it."

Then it said, "On second thought, I can't do that because I can't find the kernel source tree". 

At this point, I swore at it.  :-x  <-- artist's rendering. That didn't help.

--- in brief ---
What I *think* I need is to install the kernel source, so that the driver file can make it's own driver, (right?) but so far I haven't found what I needed to do it... Or known if what I've found is what I need. I used to use DOS, so I'm comfortable with the cli, but I just don't speak linux yet. 

any help you guys could offer would be GREATLY appreciated.

-/\/itro-

---

### Post by tonysathre on 2005-09-08
u shouldnt have had to install any drivers, did u enable your ethernet card

---

### Post by djnitro on 2005-09-08
[QUOTE=tonysathre]u shouldnt have had to install any drivers, did u enable your ethernet card[/QUOTE]

roger that, but on this mobo, NFORCE controls the onboard Ethernet. I did enable it, but no dice. Tried it both through the router like I have it now as well as direct into the modem

-/\/-

---

### Post by tonysathre on 2005-09-08
if your looking to recompile your kernel with these drivers the sources for your kernel are in /usr/src/linux

---

### Post by djnitro on 2005-09-08
[QUOTE=tonysathre]if your looking to recompile your kernel with these drivers the sources for your kernel are in /usr/src/linux[/QUOTE]

hmm I don't have that dir... In the src dir, I only have an rpm directory... I looked though there, but didn't see a linux dir.

UPDATE:
I went through the Synaptic package installer and now have the headers folders installed.. is that what I need?

-/\/-

---

### Post by skoal on 2005-09-08
djnitro, you're in a catch .22 here.  What you need in order to run the Nforce installer is the kernel header .deb package.  I believe that would be '[linux-headers-2.6.10-5.deb](http://packages.ubuntu.com/hoary/devel/linux-headers-2.6.10-5)' (off a stock Hoary kernel install).

Either copy it to CD, or drop that somewhere in some Windows directory and mount it (either NTFS/FAT32) in Ubuntu.  See the Wiki (or searc forums) on how to mount Window shares.  Then, install it with:

sudo dpkg -i linux-headers-2.6.10-5.deb

...then, you should be able to run the Nforce installer (I think).  I really don't have a clue about this Nforce package, but that's what you'll need to do as you described it here.

\\//_

---

### Post by djnitro on 2005-09-08
[QUOTE=skoal]djnitro, you're in a catch .22 here.  What you need in order to run the Nforce installer is the kernel header .deb package.  I believe that would be '[linux-headers-2.6.10-5.deb](http://packages.ubuntu.com/hoary/devel/linux-headers-2.6.10-5)' (off a stock Hoary kernel install).
[/QUOTE]

well.. rats.. I copied it, mounted it, installed it and it went without a hitch... then I went to run the nvidia installer and it bombed out again... This will probably help out a bunch.. here's the log file it spit out...

```

nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Thu Sep  8 16:47:17 2005

option status:
  license pre-accepted      : false
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : false
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : (not specified)
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA network driver for Linux-x86
-> Found package NVIDIA audio driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA network driver for Linux-x86 (1.0-12)
-> Starting install of NVIDIA network driver for Linux-x86
-> Checking for loaded module nvnet
-> Checking for loaded module forcedeth
-> Trying to remove loaded module forcedeth
-> License accepted.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.10-5-386 (buildd@terranova) (gcc version
   3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Kernel source path: '/lib/modules/2.6.10-5-386/build'
-> Kernel output path: '/lib/modules/2.6.10-5-386/build'
-> Performing cc_version_check with CC="cc".
-> gcc-version-check failed:
   
   ./nvnet/conftest.sh: line 9: cc: command not found
   Could not compile gcc-version-check.c
   
   If you know what you are doing and want to ignore the gcc version check, sel
   ect "No" to continue installation.  Otherwise, select "Yes" to abort install
   ation, set the CC environment variable to the name of the compiler used to c
   ompile your kernel, and restart installation.  Abort now? (Answer: No)
ERROR: ./nvnet/conftest.sh: line 9: cc: command not found
       
       If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.
       
       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the appropriate nvidia-installer command line option.


```

any ideas? it looks like a command is missing... no clue on how to get it though...

-/\/-

---

### Post by skoal on 2005-09-08
oops.  Sorry about that dj.  You apparently are missing gcc.  The easiest route instead of using the packages.ubuntu.com/hoary site, would be inserting (and mounting) your 5.04 install CD.  *I didn't think all those "dev" packages were actually on the install CD itself, but I checked, and they are*.  I should have suggested that (and looked) first...

Just make sure in your /etc/apt/sources.list that the top line:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

does not have a "#" before it (in case you did that after the install).  Then,

sudo apt-get update
sudo apt-get build-essential

Just install that package, since "build-essential" _should_ pull in everything you need, including the deps.  Then, you should be able to continue with Nforce install...

/edit: you may have to comment out all of the remote server entries (in /etc/apt/sources.list), since obviously, you don't have a network connection.  Otherwise, apt-get might error out on ya...

\\//_

---

### Post by djnitro on 2005-09-08
[QUOTE=skoal]

Just make sure in your /etc/apt/sources.list that the top line:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


does not have a "#" before it (in case you did that after the install).  Then,

[/QUOTE]

check.

> 
sudo apt-get update
sudo apt-get build-essential


invalid operation on build essential...

Now, you said to mount the cd... if it shows up on my desktop, it's mounted then, right? (apologizing for my noobieness...)

-/\/-

---

### Post by Nequeo on 2005-09-08
Skoal had a little typo.

You need to type 'sudo apt-get *install* build-essential'.

He's right, though. Build-essential installs straight off the CD.

[EDIT] Yeah, if the CD appears on your desktop it's mounted. Some people think mounting stuff is a pain... But Ubuntu is extremely good at automatically mounting what you need, and I vastly prefer it to those annoying "Drive not ready" messages Windows like to throw around. [/EDIT]

Good luck!

---

### Post by skoal on 2005-09-08
If you can double click on the icon in the desktop and files show up, then yes, it's mounted.  Or, alternatively, you can open up a terminal window and type 'ls /media/cdrom' to see if anything is returned.  I have that auto mounting stuff turned off and just 'mount /media/cdrom' from a terminal instead.

* When you post back what you did from a terminal, include the entire "error" text (if you can) as well.  I can't tell what's going on unless you do.  Anyways, I think I that error is coming from a typo I made earlier.  oops.  The command should be:

sudo apt-get install build-essential

note the "install"...

\\//_

---

### Post by djnitro on 2005-09-08
[QUOTE=skoal]The command should be:

sudo apt-get install build-essential

note the "install"...
\\//_[/QUOTE]

Ah hah! I think we may have something here... I typed that in and the install worked like a champ... I'm rebooting right now... we'll see if that fixed it..

-/\/-

---

### Post by djnitro on 2005-09-08
[SIZE=5]WHOOOOO-HOOOO!
[/SIZE]

<ahem> I mean... thanks a lot! I'm online now and hopefully the rest should be cake now that I have internet access on here...

thanks again!
-/\/-

---

### Post by skoal on 2005-09-08
Yes, sir.  Drop me a 'pm' when you get your rig the way you want it.  I'm very interested in hearing about your NForce performance and experiences on Linux.  I plan on grabbing one for my next linux box....

\\//_

---

