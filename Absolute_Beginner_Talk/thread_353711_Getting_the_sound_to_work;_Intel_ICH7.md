---
title: "Getting the sound to work; Intel ICH7"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by cgreer on 2007-02-05
Hello, I'm a first-time linux and ubuntu user and could not get the sound to work, I tried following the instruction on this website: [https://help.ubuntu.com/community/DebuggingSoundProblems]("https://help.ubuntu.com/community/DebuggingSoundProblems")

I was able to figure out that I had an Intel ICH7 chipset (I think) after running the lspci -v command (which I also have no clue what does).  Anways, it listed this as a device:

** Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)**

When I run aplay --list-devices it gives me this: **card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]**

I went to the alsa-project.org but got confused (because I'm a noob) and that is why I am here!

I also checked the volume and if it was muted.  One other thing, when I run "alsamixer" it gives me this: **alsamixer: function snd_ctl_open failed for default: No such device**.

I don't know if that is important or not but I thought I would include it.

Computer:
Laptop, Toshiba P100-st711 (i think)
...anything else? 

Any and all help is greatly appreciated! :)

---

### Post by renzokuken on 2007-02-05
i had sound problems on my laptop till last night. i simply upgraded the alsa-driver to a newer version and it worked perfectly. i dont know if there is a specific solution for your chipset but try compiling the latest alsa-driver

go to the alsa project webpage, go to downloads and find the latest alsa-driver file. i think the latest stable version is 0.1.13 and the latest unstable is 0.1.14rc2.

download it to your homefolder then open the terminal and do the following

```

tar xjvf alsa-whatever-the-name-of-the-file-is.tar.bz2
cd alsa*
./configure
make
sudo make install

```

if it spits out errors during the compiling you probably dont have the compilers installed so do the following

```
sudo apt-get install build-essential
```

and then try to compile alsa-driver again

reboot and see what happens

---

### Post by pseudonym on 2007-02-05
If you're running Ubuntu Edgy Eft you shouldn't need to compile ALSA. If you use Dapper Drake, however, you probably should. In either case, you should also see [this post]("http://www.ubuntuforums.org/showpost.php?p=2013895&postcount=17") for fine tuning your ALSA configuration. In many cases, this makes the difference between having sound or none at all with these Intel HD audio chips.

---

### Post by WiryLattice on 2007-02-06
Hi, 

I have installed Edgy on my Asus W2jb installed and compiled the newest alsa-drivers, utils and libraries, and, of course, have no sound. 

cat /proc/asound/card0/codec#0
Codec: Realtek ALC882

Following other posts on this problem I have added the line
"options snd-hda-intel model=3stack-dig" at the bottom of /etc/modprobe.d/alsa-base file
The 3stack-dig option seemed to be the best option under ALC882 in this guide:  
/alsa-driver/alsa-kernel/Documentation/ALSA-configuration.txt 

Under the ALC880 codec column there are a lot more model options and there are several Asus-specific models. Does this mean that the sound on my laptop won't work until they have created a model option especially for ASUS under ALC882?


I have installed and compiled the latest alsa-drivers according to this guide: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14rc2.
Compiled on Feb  6 2007 for kernel 2.6.17-10-generic (SMP).

---

### Post by cgreer on 2007-02-06
Thanks for the help, I had a few issues:

I started to update the latest drivers renzokuken, but when I put "./configure" in the terminal after running "sudo apt-get install build-essential" I get this:

checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

Any ideas?

I'm not using edgy so I figured I would try your way out first, thanks a bunch.

---

### Post by ^rooker on 2007-02-06
Maybe it's not necessary to update ALSA. I've had problems with "default: no such device", too. [Here's how I solved them]("http://www.das-werkstatt.com/forum/werkstatt/viewtopic.php?t=405").

Try re-setting "default" to point at your soundcard:

--------------------
$ asoundconf list
Names of available sound cards:
I82801CAICH3

$ asoundconf set-default-card I82801CAICH3
--------------------

---

### Post by cgreer on 2007-02-06
Thanks ^rooker, but for some reason the command alsamixer works now without doing that I think it is something else...

---

### Post by ^rooker on 2007-02-06
Just wanted to add that I've experienced exactly an error like yours several times on the same system. It disappeared and returned just like you said.

In my case it was due to randomly ordered audio-devices during boot-hardware detection. 

e.g: Having the webcam attached during boot, sometimes led to the "default: no such device" error, because the aoundsrc-settings expected sound cards in a different order.

---

### Post by r4ik on 2007-02-06
I have sound on my HDA VIAVT82xx(alsa mixer) but no trebble or bass.
Preferences shows 17 options but the most important are not there.
Anyone ?

Thanks.

---

### Post by TrAvELAr on 2007-02-07
> **^rooker said:**
> Maybe it's not necessary to update ALSA. I've had problems with "default: no such device", too. [Here's how I solved them]("http://www.das-werkstatt.com/forum/werkstatt/viewtopic.php?t=405").

Try re-setting "default" to point at your soundcard:

--------------------
$ asoundconf list
Names of available sound cards:
I82801CAICH3

$ asoundconf set-default-card I82801CAICH3
--------------------

Thank you.  My sound just recently stopped working and this took care of the issue.  It's been driving me nuts.

---

### Post by ^rooker on 2007-02-07
> **TrAvELAr said:**
> Thank you.  My sound just recently stopped working and this took care of the issue.  It's been driving me nuts.
Unfortunately, I run across this error very often - This happens mostly because the order of devices (NICs, soundcards, ...) sometimes changes randomly during bootup. This causes the system to get confused and thus the "default" alsa device won't work. 

It's still on my todo-list to figure out how to tell my system **not** to try figuring things out, since my hardware is mostly unlikely to change on-the-fly after installation.

---

