---
title: "Webcam: ov51x-jpeg drivers. Help please."
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by skrimpy on 2007-04-28
I have a Creative Live cam Vista IM and I'm having a hard time with it.   I followed instructions for installing the ov51x-jpeg drivers on this page: [http://www.rastageeks.org/ov51x-jpeg...gHackedInstall](http://www.rastageeks.org/ov51x-jpeg...gHackedInstall)

I installed from the debian package and didn't seem to get any errors. However, I'm still getting no response whatsoever from my webcam.

I am very confused about what to do and where to look next. All the webcam instructions I read are cryptic and hard to understand for me

I get this output if I try and run xawtv:

```
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-15-generic)
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available
```

I know these drivers can at least somewhat operate my webcam from reading here: 
[http://www.rastageeks.org/ov51x-jpeg/index.php/Testing_IM_Live_Support](http://www.rastageeks.org/ov51x-jpeg/index.php/Testing_IM_Live_Support)

Any suggestions?

---

### Post by deadgobby on 2007-04-28
[https://help.ubuntu.com/community/EasyCam?highlight=%28cam%29](https://help.ubuntu.com/community/EasyCam?highlight=%28cam%29)
[https://help.ubuntu.com/community/Webcam?highlight=%28cam%29](https://help.ubuntu.com/community/Webcam?highlight=%28cam%29)

---

### Post by skrimpy on 2007-04-28
I already tried Easycam - I get this error message: "No camera, or compatible camera, found"

I have also tried using the info on the webcam page and it didn't work for me.  

Anymore help out there?

---

### Post by loell on 2007-04-28
looking at those pages above

have you already tried installing the module?

```
insmod ./ov51x-jpeg.ko
```


maybe try compiling from source.

---

### Post by loell on 2007-04-28
oh and in the default fiesty repository

there is already, 

```
ov511-source
```

no need for external repository.

---

### Post by skrimpy on 2007-04-30
I'm confused still :/  I'm not allowed to do the command insmod ./ov51x-jpeg  - I get an error saying it's already there.  

I am pretty sure I have tried compiling from the source - right from the download I got from the rastageeks site.  I unpackaged the tarball and followed directions.  I'm not sure what to make of it... This is output from what I do in compiling it:

```
local@local:~/Webcam$ cd ov51x-jpeg-1.0.0
local@local:~/Webcam/ov51x-jpeg-1.0.0$ make
make -C /lib/modules/2.6.20-15-generic/build M=/home/local/Webcam/ov51x-jpeg-1.0.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/local/Webcam/ov51x-jpeg-1.0.0/ov51x-jpeg-core.o
/home/local/Webcam/ov51x-jpeg-1.0.0/ov51x-jpeg-core.c: In function &#8216;ov51x_init_isoc&#8217;:
/home/local/Webcam/ov51x-jpeg-1.0.0/ov51x-jpeg-core.c:5284: warning: assignment from incompatible pointer type
  CC [M]  /home/local/Webcam/ov51x-jpeg-1.0.0/ov511-decomp.o
  CC [M]  /home/local/Webcam/ov51x-jpeg-1.0.0/ov518-decomp.o
  CC [M]  /home/local/Webcam/ov51x-jpeg-1.0.0/ov519-decomp.o
  LD [M]  /home/local/Webcam/ov51x-jpeg-1.0.0/ov51x-jpeg.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/local/Webcam/ov51x-jpeg-1.0.0/ov51x-jpeg.mod.o
  LD [M]  /home/local/Webcam/ov51x-jpeg-1.0.0/ov51x-jpeg.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
local@local:~/Webcam/ov51x-jpeg-1.0.0$ sudo make install
Password:
make -C /lib/modules/2.6.20-15-generic/build M=/home/local/Webcam/ov51x-jpeg-1.0.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make -C /lib/modules/2.6.20-15-generic/build M=/home/local/Webcam/ov51x-jpeg-1.0.0 modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  INSTALL /home/local/Webcam/ov51x-jpeg-1.0.0/ov51x-jpeg.ko
  DEPMOD  2.6.20-15-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
local@local:~/Webcam/ov51x-jpeg-1.0.0$ sudo depmod -a
local@local:~/Webcam/ov51x-jpeg-1.0.0$ sudo modprobe ov51x-jpeg
local@local:~/Webcam/ov51x-jpeg-1.0.0$ sudo insmod ./ov51x-jpeg.ko
insmod: error inserting './ov51x-jpeg.ko': -1 File exists

```

I get no output after the depmod and modprobe commands.  I'm not sure if this is normal or not - but my camera still doesn't function.

I need help understanding the comment about the repository.  Does this mean I can somehow try and compile from the Feisty repositories?  I am still learning Linux and Ubuntu and I need directions on how to do this.  Any help :( ?

---

### Post by loell on 2007-05-01
i'm starting to believe that this problem is common in fiesty.

---

### Post by chemtut on 2007-05-01
try camstream via synaptic
it works for my Phillips

---

### Post by skrimpy on 2007-05-02
> **chemtut said:**
> try camstream via synaptic
it works for my Phillips
 
; ; that didn't work either.  I'm starting to think this is impossible, though I know from reading on the rastageeks wiki that other ubuntu users have gotten this camera working.

Here is my error code from trying camstream:

```
local@local:~$ camstream
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Failed to open configuration file for reading.

```

/sigh

Any other suggestions?

---

### Post by chemtut on 2007-05-02
yes, Iget the same errors but then a grey window opens
I click on file and the small picture window opens

---

### Post by skrimpy on 2007-05-02
> **chemtut said:**
> yes, Iget the same errors but then a grey window opens
I click on file and the small picture window opens

Nothing happens for me when I click file ; ;  I try to "open viewer" and pretty much get no response from the program no matter what option I choose.

---

### Post by skrimpy on 2007-05-03
has anyone gotten this driver to work with ANY camera in ubuntu?

---

### Post by oscarand on 2008-01-06
Hi. I also searched for modules to load to use Creative Webcam Vista. Since a problem with ov511 module, you need to use ov51x-jpeg module. I don't remember the link to website (try to search Ov51xJpegHackedInstall on the web), so I copy instructions below.
==============================================================
Ov51xJpegHackedInstall
From Ov51x JPEG hacked Wiki
Jump to: navigation, search
Contents
[hide] [hide]

    * 1 Preliminaries
    * 2 Compilation and installation
    * 3 Force a parameter at load
    * 4 Install debian module package
    * 5 Installation on OpenSuse 10.x
    * 6 Upgrading from oldest releases


Warning: These are installation instructions for 1.0.0 release. See FAQ for differences with 0.5.x releases
Preliminaries

The module ov511 shipped with default kernel for ov511/ov518 webcams is broken. When you plug your camera, the kernel may load it in first place so the ov51x-jpeg cannot be used later on.

You may unload the module:

rmmod ov511

and then remove the module from /lib/modules/`uname -r`
Compilation and installation

First, you must have a working kernel module build and the videodev module compiled. In most distributions, this you may need some kernel headers corresponding to your kernel. See the command uname -r to get your kernel version.

Basically, you need a kernel with its headers, and the videodev module built with video4linux option (try modprobe videodev as root).

Then, as normal user, type in the ov51x-jpeg-x.x.x directory:

% make

and, as root:

# make install
# modprobe ov51x-jpeg

or if this fails for any reason:

# modprobe videodev
# insmod ./ov51x-jpeg.ko

from the source directory. the 'videodev module may already be loaded.

That's it, you got your camera ready to work with your favorite v4l application!
Force a parameter at load

It can be usefull to force the use of a parameter when the module is loaded, as with the kopete issue.

A clean way to do so is to add this as an option in the file /etc/modprobe.d/options. Simply apend a line of that form to this file:

options ov51x-jpeg force_palette=13


Install debian module package

First, see Ov51xJpegHackedSource for how to add the correct sources to your sources.list

A quick way to build the module is to issue those commands, prefixed by sudo if you are in Ubuntu:

apt-get update
apt-get install ov51x-jpeg-source module-assistant
module-assistant a-i ov51x-jpeg 

If this fails first try the same with -t to look at log:

module-assistant -t a-i ov51x-jpeg 

And then read more documentation on module-assistant.

If then you still think it comes from the package, please mail the issue to [email]ov51x-jpeg@rastageeks.org[/email]

If everything worked so far, then you have a working module installed... You may simply unplug/plug the webcam, or modprobe ov51x-jpeg to see it working !
Installation on OpenSuse 10.x

Install package "kernel-source", "linux-kernel-headers" and "usbvision-kmp-bigsmp" and "usbvision-kmp-default". usbvision is a Linux device driver for video grabbing with USB-onöly connected "webcam" devices.

Then proceed with section "compilation and installation", i.e. uncompress as normal user files in the ov51x-jpeg-x.x.x directory and change directory and replace x.x.x by version number:


% cd /.../path2mydir/ov51x-jpeg-x.x.x
% make

and, as root:

# make install
# modprobe ov51x-jpeg

Finished.
Upgrading from oldest releases

If you are updating from 0.5.x releases, you have to remove first the remaining modules. A quick and dirty command would be:

# find /lib/modules/`uname -r` -name "ov51x.ko" -exec rm -f {} \;

You may also remove loaded module using lsmod and rmmod
Retrieved from "http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall"

---

### Post by martinjochimsen on 2008-05-10
Hi

I have had the same problems with my Creative Vista Live webcam, but after a LOT of searching i finally found the solution.
Here is the link.
[https://help.ubuntu.com/community/Ov51x](https://help.ubuntu.com/community/Ov51x)
Hope it helps.

Martin :-)

---

