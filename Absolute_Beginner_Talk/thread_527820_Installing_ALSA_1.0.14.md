---
title: "Installing ALSA 1.0.14"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by na_silu on 2007-08-17
sudo apt-get install build essential
tar xjf alsa*
cd alsa*
./configure
make
sudo make install


These are the steps I tried using from another thread to get my alsa 1.0.14 driver working. I downloaded my driver to my home folder as instructed and then opened the terminal and typed the first line and I got this result:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build

What's going wrong? I am completely new to Ubuntu and I am using version 7.04 x64 edition. I also had a problem when trying to install my motherboard drivers from a .run file. It said I needed libc development package. I would love to get my audio working.

---

### Post by schorsch on 2007-08-17
The package is called "build-essential"

```
sudo apt-get install build-essential
```

---

### Post by na_silu on 2007-08-17
Ok it worked, but when I went to type in the next line I got this error message:

bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by schorsch on 2007-08-17
What is the complete name of the file(s)?

```
ls -l alsa*
```

And I remember a few days ago I was involved in a thread with problems compiling alsa-tools from the source and we did not find a solution so you could run in the same problems, too.

[http://ubuntuforums.org/showthread.php?t=491735]("http://ubuntuforums.org/showthread.php?t=491735")

Are you sure the the alsa-drivers in the repos will not work for you; are they already installed?

```
dpkg -l | grep alsa
```

... it is a lowercase "L" by the way ...

---

### Post by na_silu on 2007-08-17
The complete name of the file is alsa-driver-1.0.14.tar.bz2 and I currently have these versions of alsa installed:

ii  alsa-base                         1.0.13-3ubuntu1             ALSA driver configuration files
ii  alsa-utils                          1.0.13-1ubuntu5             ALSA utilities
ii  gstreamer0.10-alsa       0.10.12-0ubuntu1          GStreamer plugin for ALSA
ii  libesd-alsa0                     0.2.36-3ubuntu4            Enlightened Sound Daemon (ALSA) - Shared lib
ii  libpt-plugins-alsa           1.10.3-0ubuntu1             Portable Windows Library Audio Plugin for th
ii  libsdl1.2debian-alsa      1.2.11-7ubuntu1             Simple DirectMedia Layer (with X11 and ALSA

---

### Post by schorsch on 2007-08-17
I'd guess the downloaded file is corrupt. You should try to download it again. But again: You could run in problems when compiling alsa-utils so you should try first if you can compile them without errors.

---

### Post by na_silu on 2007-08-17
Do I follow the same procedure to install alsa-utils? I downloaded a fresh copy of the alsa drivers to my desktop. Tried the tar xjf alsa* command again with the same error message.

---

### Post by schorsch on 2007-08-17
Yes, the procedure to compile the utils would be the same. And you should untar the files one by one:

```
tar xvjf alsa-driver-1.0.14.tar.bz2
```

the "v" gives you more output as it means "verbose"

---

### Post by na_silu on 2007-08-17
OK!! I don't quite know how I did it, but I got the alsa driver to install but not the utils, they needed a dependency. But now that I have the driver installed, I'm still getting no sound?

---

### Post by schorsch on 2007-08-17
Have you already checked with "alsamixer" if any channels are muted (marked by "mm" at the bottom) or if the volume is set to low value?

---

### Post by na_silu on 2007-08-17
Yup, just double checked, all volumes are turned up and not muted. Alsa is detecting my audio device as a PnP Audio Device and I'm using a Sound Blaster X-Fi card. I don't know if maybe its just not detecting, would a reboot maybe help?

---

### Post by schorsch on 2007-08-17
Perhaps .... It's worth a try ...

---

### Post by na_silu on 2007-08-17
Well a reboot did nothing lol. I think I'm screwed for sound. I might just have to wait until the next major release of Ubuntu before I can make the switch. :(

---

### Post by schorsch on 2007-08-17
> **na_silu said:**
> Alsa is detecting my audio device as a PnP Audio Device and I'm using a Sound Blaster X-Fi card.

I just checked at the alsa homepage and [there]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs") it says for you card:
```
	 [Unsupported] [PCI] Card delivered to developers. Completely new architecture. Creative actively preventing support due to no datasheets being released to ALSA developers. Reverse engineering work not started due to lack of time.
```

... sorry for that .. but hey, you compiled your first software from the sources ;-)

---

### Post by na_silu on 2007-08-17
Awwww.....oh well....like I said, I guess I'll just have to wait for those developers to get crackin. But you're absolutely right, I did compile something. I think I can apply what I've learned now, I have a better understanding of whats going on in the terminal. Thanks a lot for your help. I guess I'll have to try getting my on board audio to work for now, although I haven't been having much luck installing the drivers for that either :(

---

### Post by Patriot1776 on 2007-12-04
This is VERY similar to the problem I'm having.  In this thread:

[http://ubuntuforums.org/showthread.php?t=631774](http://ubuntuforums.org/showthread.php?t=631774)

Think I could get some help too schorsch?  I think mine can actually be solved.

---

### Post by Patriot1776 on 2007-12-04
Bumpage.

Come on, doesn't anybody have any ideas to help me?  This is the main reason why I don't like these forums!

---

### Post by Patriot1776 on 2007-12-04
Bump

---

### Post by fenian on 2007-12-04
Follow the instructions here to update[ alsa.]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by Patriot1776 on 2007-12-05
When I get to

```

sudo apt-get install linux-headers-`uname -r`
```

it returns:

```

E: Couldn't find package linux-headers-uname -r
```

Remove the single quotes?

EDIT - Never mind, I figured out what 'uname' is.  I'm running kernel 2.6.22-14-generic, but its still saying it can't find the package file for it.  Any ideas of kernel packages that could work?

/proc/cpuinfo contents:

```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 6
model name      : Intel(R) Pentium(R) D CPU 3.40GHz
stepping        : 4
cpu MHz         : 2400.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 s
s ht tm pbe nx lm constant_tsc pni monitor ds_cpl est cid cx16 xtpr lahf_lm
bogomips        : 6805.74
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 6
model name      : Intel(R) Pentium(R) D CPU 3.40GHz
stepping        : 4
cpu MHz         : 2400.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 s
s ht tm pbe nx lm constant_tsc pni monitor ds_cpl est cid cx16 xtpr lahf_lm
bogomips        : 6805.74
clflush size    : 64
```

---

### Post by Patriot1776 on 2007-12-05
Okay, discovered I had the kernel headers already.  Followed the instructions and rebooted, but still no joy, though alsaconf now works.  I've for now switched to running with my previous kernel, 2.6.20-16-generic, and I've got sound.  If I look and find that I'm using ALSA 1.0.14 with this kernel, could I perhaps do something to where I'd copy the sound initializing files with that kernel to be used with my newer kernel, 2.6.22-14-generic?

---

