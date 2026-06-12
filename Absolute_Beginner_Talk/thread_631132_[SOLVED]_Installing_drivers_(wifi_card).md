---
title: "[SOLVED] Installing drivers (wifi card)"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by popeye6984 on 2007-12-04
Hi there!
I got the drivers for my linksys WPC11 v3 PCMCIA card from linksys website. I unzipped them in a folder ....
I followed the instructions, but I have a problem with the /usr/src/linux folder (is incomplete or missing).
What does it mean? What I have to do?
thanks!

---

### Post by erfahren on 2007-12-04
you probably need to create it. can you give a link to the instructions you're going by?
is there a README or install guide of some sort in the archive?

---

### Post by erginemr on 2007-12-04
Hello,

It is the Linux kernel headers (source files) that the installer is looking for. Despite what the installer thinks, in Ubuntu they are kept under a directory "/usr/src/linux-headers-<kernel version here>", where the kernel version can be obtained from the following command:
"uname -r"

You can also see the location of the Linux header files by visiting "/usr/src" from within Nautilus (file manager). See the atached screenshots.

Once you have identified the directory, the question is: Does the installer program allow you to input the location of the source files? 

If so, then you should specify it (the one with the word generic in its name) when prompted. If not, you should create a shortcut (symbolic in linux-speak) "/usr/src/linux", which will point to the real directory.

From the command line:
cd /usr/src  (open up a terminal and change to the source directory)
ls  (find out the correct header directory)
sudo ln -s /usr/src/<linux header directory> linux  (create a symbolic link to the real directory with the root permissions, see the 3rd attachment)
(Here the format is ln –s <target> <new link>)
Re-run the installer.

Good Luck!

---

### Post by popeye6984 on 2007-12-04
Yes, in the file there is a readme with the instructions. 
> To build linux-wlan-ng you will need:
   - Configured kernel source code for the kernel you are running.  
     Ideally, this will be the resulting tree after building your own 
     kernel.  Configured means that you have at least run 'make config',
     'make menuconfig', or 'make xconfig'.  If you are trying to build
     linux-wlan-ng for a previously existing kernel binary (one you did 
     not build yourself), look for help on the mailing lists because it 
     can be tricky.  I always run against kernels I've built myself, so I'm 
     not much help in this area.
   - The good David Leffler identified that if you are having difficulty
     with *_netlink_* symbols, you may have a problem with 'make clean' in
     the kernel tree.  Do a 'make mrproper' followed by 'make config' 
     and the rest of the kernel build process.  'make mrproper' does
     a more thorough cleaning of the kernel tree.  For more info, look
     for David's comments in the linux-wlan-user mailing list.
   - If you are building a driver for a PCMCIA card, you will also need
     the configured PCMCIA source code for the pcmcia_cs subsystem you
     are currently running.
   - Note that AVS does not test with the kernel pcmcia support code,
     we _always_ use the pcmcia-cs package with kernel pcmcia
     completely disabled.  CAREFUL: it is very easy to accidentally
     enable the kernel pcmcia code, if you select _any_ of the
     individual pcmcia devices in the various kernel config submenus,
     kernel pcmcia will be selected.

Building linux-wlan-ng:

1)  untar the package using the command:

    tar zxvf linux-wlan-ng-X.Y.Z.tar.gz

2)  Make sure you have configured kernel and (optionally) pcmcia sources on 
    your system.  Note that if you are _only_ building the prism2_pci,
    prism2_plx, or prism2_usb drivers you don't need the pcmcia-cs 
    source tree.

3)  To clean up any unwanted files accidentally included in the tar package,
    run 'make clean'.  If make clean behaves badly (infinite loop, for
    example), you may have a date/time mismatch.  Run the command:

    find . -type f -exec touch {} \;

    to fix the date&time stamps, then run 'make clean' again.


4)  To configure the linux-wlan-ng package, run 'make config'.  The 
    following set of questions will be asked. The default answer is in
    braces (e.g. []).  Just press <Enter> to select the default answer:

 
Can you "translate" it in a more easy list of command/things to do?
Thank you very much.

---

### Post by erfahren on 2007-12-04
> **popeye6984 said:**
> Yes, in the file there is a readme with the instructions. 

 
Can you "translate" it in a more easy list of command/things to do?
Thank you very much.
umm... no. I sure can't. You'd basicaly be re-compiling the kernel with the driver for the card (not really as bad as it sounds). I've only done that with step-by-step instructions (for my video card). 

The instructions they give aren't very explanatory.

Without clear instructions on how to compile that Linux Linksys driver I'd try looking into the NdisWrapper way first.

I've never used NdisWrapper, but it's a way to use Windows drivers for the card without going through all that.

I did do some searching and found this thread: [http://ubuntuforums.org/showthread.php?t=71372](http://ubuntuforums.org/showthread.php?t=71372)

and this (for RedHat, but may be helpful) [http://linux.oldcrank.com/tips/wpc11/](http://linux.oldcrank.com/tips/wpc11/)

my google searches (you might try the same with the word "NdisWrapper" and see what you get:
[http://www.google.com/search?hl=en&q=ubuntu+linksys+WPC11+v3+PCMCIA&btnG=Search](http://www.google.com/search?hl=en&q=ubuntu+linksys+WPC11+v3+PCMCIA&btnG=Search)
[http://www.google.com/search?hl=en&q=linux+ubuntu+linksys+WPC11+v3+PCMCIA&btnG=Search](http://www.google.com/search?hl=en&q=linux+ubuntu+linksys+WPC11+v3+PCMCIA&btnG=Search)

note: they mention getting the .ini file out of the Window driver files. It would be helpful if you have access to a Windows pc to unpack the drivers. (you may already know) they are oftentimes .exe files but are actually self-extracting. In other words when you go to install the .exe they first extract somewhere, then just cancel the installation.

---

### Post by popeye6984 on 2007-12-04
OK ... I don't have the kernel sources (I suppose this could be a problem...). I looked in my install CD, but they aren't there. I can't go over the net for downloading them with a liinux machine.
Where/how to DL them?:confused:

---

### Post by erfahren on 2007-12-04
[http://packages.ubuntu.com/gutsy/](http://packages.ubuntu.com/gutsy/)

you can search it using google, ex.
*package-name* site:[http://packages.ubuntu.com/gutsy/](http://packages.ubuntu.com/gutsy/)

if what you go to download need dependencies (shown with red dots) download them as wel and iinstall them first.

good luck

---

### Post by popeye6984 on 2007-12-05
Solved!

---

### Post by erginemr on 2007-12-05
> **popeye6984 said:**
> Solved!

Great! Can you please explain how you did solve it, so that others having a similar issue may benefit? 

Also  please mark your thread as solved from the "thread tools" menu at the top of the page.

Take Care.

---

### Post by popeye6984 on 2007-12-05
I downloaded the sources, installed them and installed the linksys drivers ...

---

