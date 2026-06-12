---
title: "Installing/compiling video driver...I have no idea what I'm doing"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by k1001001 on 2006-12-24
Ok, I'm going to seem like an absolute noob, but here goes. I've been having problems with games/videos being very laggy on this computer, so it was suggested to me that I download my video card driver. For example, when I watch online videos, the audio drags behind the video (this was a problem in Windows as well), and Dark Oberon is so laggy that I cannot even play it. Other games like solitaire and Tetris work fine though. I assumed my video card driver was already loaded, since I see a display in front of me at the moment, but apparently that's not the case? 

lshw shows my video card to be a K8M800 I believe. Here is the output:
```
 *-pci:1
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz

```

Anyways, I went to the [video card manufacturer's site]("http://www.viaarena.com/default.aspx?PageID=2"), and sure enough they had a Linux non-distro-specific driver. I figured this would be the best choice since Ubuntu/Debian was not listed. So now I have this file linux-fbdev-kernel-src_20050726.tgz. I am pretty new to Ubuntu and Linux altogether, so now I have no idea how to compile and install the driver. If I could get some guidance here, that would be great.

Just to be sure, installing the video card would fix the problem of lagging games/videos right?

---

### Post by MkfIbK7a on 2006-12-24
> Just to be sure, installing the video card would fix the problem of lagging games/videos right?

probably but anyway you have to unzip the tgz file right click and select unzip

far as i know hope it helps!

---

### Post by Sef on 2006-12-24
Read [How to Install Anything]("http://monkeyblog.org/ubuntu/installing/") in Ubuntu.

---

### Post by k1001001 on 2006-12-24
Thanks for the link, very helpful. However, it didn't work.

I changed the terminal directory to the folder full of source code, then hit "make." Failed. I also tried "sudo make install", however that didn't work either. The output on both attempts was this:
```
keith@keith-laptop:~/downloads/Video_Driver$ make
Makefile:135: *** Linux kernel source not found.  Stop.
keith@keith-laptop:~/downloads/Video_Driver$ sudo make install
Password:
Makefile:135: *** Linux kernel source not found.  Stop.
```

I found that to be weird. Usually when I do similar processes, it works without a hitch. 

Here's a list of the files in the directory.
```
keith@keith-laptop:~/downloads/Video_Driver$ ls
accel.c  hwcfig.h  lcd.h               tbl1622a.h  viafb.modes
accel.h  hw.h      lcdtbl.h            tbl1622.h   via_i2c.c
chip.h   iface.c   Makefile            tbl1625.h   via_i2c.h
debug.h  iface.h   Makefile_24.kernel  tv.c        viamode.h
dvi.c    ioctl.c   Makefile_26.kernel  tv.h        vt1622a.c
dvi.h    ioctl.h   readme.txt          viafbdev.c  vt1622.c
hw.c     lcd.c     share.h             viafbdev.h  vt1625.c
```
I see three files with "makefile" in it, but they did not make. Interesting. Suggestions?

---

### Post by logos34 on 2006-12-24
you don't have the kernel source installed (linux-source-yourkernel).

Add build-essential package while you're at it.

---

### Post by spockrock on 2006-12-24
if you dont know what your kernel version is, then, 
uname -r

it should give you something like this, 2.6.17-10-generic

so then you want to
sudo apt-get install linux-source-2.6.17

---

### Post by k1001001 on 2006-12-25
```
keith@keith-laptop:~$ uname -r
2.6.15-27-386
keith@keith-laptop:~$ sudo apt-get install linux-source-2.6.15-27-386
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-source-2.6.15-27-386
```

??

EDIT: I'm dumb. It's sudo apt-get install 2.6.15 only, none of the stuff in the dashes.

EDIT 2: I installed linux-source-2.6.15, went to my Video Driver file, and I'm still getting the same error:
```
keith@keith-laptop:/usr/src/Video_Driver$ sudo make install
Makefile:135: *** Linux kernel source not found.  Stop.
```

Suggestions?

---

### Post by logos34 on 2006-12-25
"not found"?...hmm...check /usr/src directory.  Is it there?  If it's still bzipped, maybe it needs to be extracted.  

I just had a looksee at the readme.txt file for that via driver package...Looks like there are 2 parts to the install for 2.6 kernel--'Building and loading viafb device driver for Linux kernel 2.6'.  Did you build the 'fbcon' module first, then 'viafb'?  Are those the instructions you're following?

Also, I also found these drivers in the repos: 

xserver-xorg-video-via (dapper and edgy)
xserver-xorg-video-unichrome (edgy)

both of which installed by default on my machine.

The first one should work fine.  read the description.

---

### Post by k1001001 on 2006-12-25
Which repository did you download those from? It came back with no results for me. Installing from apt-get sounds a lot easier than what I'm attempting to do.

---

### Post by logos34 on 2006-12-25
here: 
[http://packages.ubuntulinux.org/dapper/x11/xserver-xorg-driver-via](http://packages.ubuntulinux.org/dapper/x11/xserver-xorg-driver-via)

i think they're both listed as  'misc - graphical (universe)'

make sure you have all the boxes checked in synaptic>repositories>software sources (ie universe, main, mutliverse, restriced and source code)

---

### Post by k1001001 on 2006-12-25
Thanks for your help. Eventually, I got it installed. After checking all the boxes in Synaptic, for some reason it still wouldn't download using apt-get or aptitude. So I went to the wiki website and installed the i386 package. It said I already had the same version installed, but I reinstalled anyways. It didn't improve anything with Dark Oberon, so I'm guessing the lag in this game is not due to the video driver. Who knows what the deal is there. Thanks for the help though.

---

### Post by Peque on 2007-01-05
> **logos34 said:**
> "not found"?...hmm...check /usr/src directory.  Is it there?  If it's still bzipped, maybe it needs to be extracted.  

I'm running into the same problems here ??? 

I'm trying to install some special INTEL NICS drivers - but get the same error about make as described - My source was Bzip - now its unpacked but still get the same error ?? 

Have you any idea about this 

THanks 
P

---

### Post by logos34 on 2007-01-05
It would probably be best if you started a new thread in networking.  But [this ]("http://monkeyblog.org/ubuntu/installing.html")might help you.

---

