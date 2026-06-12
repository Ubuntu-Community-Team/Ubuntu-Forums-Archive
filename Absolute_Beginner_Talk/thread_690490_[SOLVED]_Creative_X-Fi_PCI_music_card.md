---
title: "[SOLVED] Creative X-Fi PCI music card"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by tuxsheadache on 2008-02-07
I have a Creative X-Fi Music PCI Sound Card, and i downloaded the drivers from the Creative Website (they have only just released a Beta Version). On the Readme, it states:
2) Run one of the following commands as root in the terminal:



 ./installer

Which i did, and got:

./installer
This product only support 64-bit Operating Systems
Setup will now exit

I am using Ubuntu 7.10, the AMD64 alternative text only version. Is it just a bad driver made by Creative, or is this version of Ubuntu now supporting it.
Any help would be good

---

### Post by njparton on 2008-02-08
Ubuntu doesn't use ALSA so the driver isn't compilable.

You can (I believe) recompile the kernel with ALSA and these drivers in there but it's not easy and not many people have had success.

As it stands the best advice is that X-Fi cards are not supported by linux properly yet.

There was some news on Phoronix the other day that suggested that this may change soon, but in the meantime you'll have to suffer like the rest of us I'm afraid :(

---

### Post by kpkeerthi on 2008-02-08
> **njparton said:**
> Ubuntu doesn't use ALSA so the driver isn't compilable.

Sadly it is not true. Ubuntu and all modern linux operating systems use ALSA. 

> **tuxsheadache said:**
> 
./installer
This product only support 64-bit Operating Systems
Setup will now exit

There is a bug in the X-Fi driver installer that renders it not detect 64-bit OS properly. A fix is posted [here]("http://ubuntuforums.org/showpost.php?p=3418145&postcount=2")

---

### Post by tuxsheadache on 2008-02-08
A did the fix for the 64 bit OS bug, and have hit another problem.

sudo ./installer
Setup is unable to detect a supported product on your system
Setup will now exit

I checked through the device manager, and it does seem to realise I have a something made by Creative plugged in. Under the device manager tabs:
_Device_
**Vendor:** Creative Labs
**Device:** SB X-Fi
**Status:** Status
**Bus Type:** PCi
**Device Type:** Unknown
**Capabilities:** Unknown
_PCI_
**Vendor:** Creative Labs
**Product:** SB X-Fi
**OEM Vendor:** Creative Labs
**OEM Product:** X-Fi Platinum

And the last tab:

[[IMG]http://img518.imageshack.us/img518/9277/screenshotvr3.th.png[/IMG]](http://img518.imageshack.us/my.php?image=screenshotvr3.png)

I am not sure how this information/ if it will be useful, but I guessing i need to get Ubuntu to realised it is connected. The card is working in windows and is physically connected, so it doesn't seem to be a hardware issue. Any further help would be appreciated, and thanks for the help already.

---

### Post by njparton on 2008-02-08
> **kpkeerthi said:**
> Sadly it is not true. Ubuntu and all modern linux operating systems use ALSA. 


There is a bug in the X-Fi driver installer that renders it not detect 64-bit OS properly. A fix is posted [here]("http://ubuntuforums.org/showpost.php?p=3418145&postcount=2")

Excellent, I hadn't realised that.  I was about to try sabayon instead so hopefully this will prevent me having to change distro... :)

---

### Post by krylon on 2008-02-08
Creative's beta driver is extremely buggy. If you manage to get it working you will have nothing but issues with it.  I've been there.  I suggest trying the latest OSS v4 driver just recently released. It has beta X-Fi support.  

I assume since you are trying to install Creative's Beta that you are on 64bit Ubuntu.

Here is the correct file [http://www.4front-tech.com/release/oss-linux_v4.0-1013_amd64.deb](http://www.4front-tech.com/release/oss-linux_v4.0-1013_amd64.deb)

Install the deb file with dpkg -i oss-linux_v4.0-1013_amd64.deb and you will have a working X-Fi with OSS!  Then it is just a matter of configuring your Ubuntu and audio programs to use OSS instead of ALSA.

---

### Post by tuxsheadache on 2008-02-08
I think i need something previous to this. I tried looking for OSS drivers on the package manager, but found none. Either way, command line said:

Starting Open Sound System
/usr/sbin/soundon: 27: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/sbin/soundon: 28: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 30: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 32: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 45: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
No /usr/lib/oss/etc/installed_drivers - cannot continue
Errors were encountered while processing:
 oss-linux_v4.0-1013_amd64.deb

---

### Post by krylon on 2008-02-08
Try:
```

sudo /etc/init.d/alsa-utils stop
sudo dpkg -i oss-linux_v4.0-1013_amd64.deb
```

---

### Post by tuxsheadache on 2008-02-08
sudo: /etc/init.d/alsa-util: command not found

---

### Post by krylon on 2008-02-08
Sorry for the typo. I fixed it in my original post.  Correct command:

```
sudo /etc/init.d/alsa-util**s** stop
```

---

### Post by tuxsheadache on 2008-02-08
sudo dpkg -i oss-linux_v4.0-1013_amd64.deb
(Reading database ... 98634 files and directories currently installed.)
Preparing to replace oss-linux v4.0-1013 (using oss-linux_v4.0-1013_amd64.deb) ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing oss-linux_v4.0-1013_amd64.deb (--install):
 subprocess new pre-removal script returned error exit status 2
Building OSS Modules for Linux-unknown 2.6.22-14-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
/usr/sbin/soundon: 27: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/sbin/soundon: 28: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 30: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 32: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 45: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
No /usr/lib/oss/etc/installed_drivers - cannot continue
Errors were encountered while processing:
 oss-linux_v4.0-1013_amd64.deb

:(

---

### Post by krylon on 2008-02-08
One more thing to try, taken from [http://www.4front-tech.com/forum/viewtopic.php?p=6939&sid=bd1cd24afc9f424153009e33180bd3be](http://www.4front-tech.com/forum/viewtopic.php?p=6939&sid=bd1cd24afc9f424153009e33180bd3be) and slightly modified:


1) cd /var/lib/dpkg/info
2) sudo rm oss-linux*
3) sudo gedit /var/lib/dpkg/status and look for oss-linux
and delete the entire section that looks like:

```
Package: oss-linux
Status: install ok installed
Priority: extra
Section: alien
Installed-Size: 8440
Maintainer: root <root@dev-desktop>
Architecture: amd64
Version: v4.0rc9-999
Depends: libatk1.0-0 (>= 1.12.1), libc6 (>= 2.4-1), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.3.0), libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.10.3), libpango1.0-0 (>= 1.14.5), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxi6, libxinerama1, libxrandr2, libxrender1
Conffiles:
/etc/oss.conf 055432d38aaf37fc6de3dba4a95accc3
Description: Open Sound System sound drivers for Linux
Open Sound System for Linux (OSS/Linux) is a commercial quality sound driver
distributed by 4Front Technologies (http://www.opensound.com). OSS provides
support for practically all sound cards on the market including PnP and
many PCI ones. Installation and configuration is higly automated and easy to
perform. To obtain technical support and additional features, you will need to
order a license key from http://www.opensound.com/order.html
.
(Converted from a rpm package by alien version 8.64.)

```

5) Now you should be able to run dpkg --purge oss-linux and it should
say: dpkg - warning: ignoring request to remove oss-linux which isn't installed. 

6) sudo dpkg -i oss-linux_v4.0-1013_amd64.deb

---

### Post by tuxsheadache on 2008-02-08
sudo dpkg -i oss-linux_v4.0-1013_amd64.deb
Selecting previously deselected package oss-linux.
(Reading database ... 98358 files and directories currently installed.)
Unpacking oss-linux (from oss-linux_v4.0-1013_amd64.deb) ...
Setting up oss-linux (v4.0-1013) ...
Building OSS Modules for Linux-unknown 2.6.22-14-generic

OSS build environment set up for REGPARM kernels

    C library headers (glibc-devel or build-essential)

Error: The above Linux package(s) seem to be missing from your system.
       Please install them and then try to install OSS again.

Please refer to the documentation of your Linux distribution if you
have problems with installing the packages.

You can use the following commands to download and install all
required packages:

  apt-get install build-essentials
Starting Open Sound System
/usr/sbin/soundon: 27: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 28: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 30: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 32: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 45: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
No /usr/lib/oss/etc/installed_drivers - cannot continue


Should I look in synaptic package manager? What shall i look for exactly?
Thanks for help so far =)

---

### Post by krylon on 2008-02-08
sudo apt-get install build-essentials

---

### Post by tuxsheadache on 2008-02-08
sudo apt-get install build-essentials
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essentials

---

### Post by krylon on 2008-02-08
Apologies. Try sudo apt-get install build-essential

---

### Post by tuxsheadache on 2008-02-08
sudo apt-get install build-essentials
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essentials
eddy@Vinnie:~$ 
eddy@Vinnie:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstdc++5 libboost-date-time1.34.1 gcc-3.3-base libboost-thread1.34.1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.1-multilib gcc-4.1-doc glibc-doc
  manpages-dev libstdc++6-4.1-doc diff-doc
The following NEW packages will be installed
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev patch
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 3150kB/7417kB of archives.
After unpacking 31.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main linux-libc-dev 2.6.22-14.51 [653kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main libc6-dev 2.6.1-1ubuntu10 [2497kB]
Fetched 3150kB in 7s (426kB/s)                                                 
Selecting previously deselected package linux-libc-dev.
(Reading database ... 98634 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.22-14.51_amd64.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.6.1-1ubuntu10_amd64.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.2-16ubuntu2_amd64.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.2-16ubuntu2_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.1.2-9ubuntu2_amd64.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch/patch_2.5.9-4_amd64.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.5ubuntu16_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_amd64.deb) ...
Setting up linux-libc-dev (2.6.22-14.51) ...
Setting up libc6-dev (2.6.1-1ubuntu10) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.5ubuntu16) ...
Setting up libstdc++6-4.1-dev (4.1.2-16ubuntu2) ...
Setting up g++-4.1 (4.1.2-16ubuntu2) ...
Setting up g++ (4:4.1.2-9ubuntu2) ...

Setting up build-essential (11.3ubuntu1) ...

run sudo dpkg -i oss-linux_v4.0-1013_amd64.deb now?

---

### Post by krylon on 2008-02-08
> **tuxsheadache said:**
> 
run sudo dpkg -i oss-linux_v4.0-1013_amd64.deb now?

Yes and if you run into the same problem as your original post, follow my solution in post #12. :popcorn:

---

### Post by tuxsheadache on 2008-02-08
sudo dpkg -i oss-linux_v4.0-1013_amd64.deb
Selecting previously deselected package oss-linux.
(Reading database ... 100113 files and directories currently installed.)
Unpacking oss-linux (from oss-linux_v4.0-1013_amd64.deb) ...
Setting up oss-linux (v4.0-1013) ...
Building OSS Modules for Linux-unknown 2.6.22-14-generic

OSS build environment set up for REGPARM kernels

Building module osscore
Building module ali5455
Building module allegro
Building module als300
Building module als4000
Building module apci97
Building module atiaudio
Building module audigyls
Building module audioloop
Building module audiopci
Building module cmi8788
Building module cmpci
Building module cs4280
Building module cs4281
Building module digi32
Building module digi96
Building module emu10k1x
Building module envy24
Building module envy24ht
Building module fm801
Building module geode
Building module hdaudio
Building module hdsp
Building module ich
Building module imux
Building module lynxone
Building module lynxtwo
Building module maestro
Building module neomagic
Building module ossusb
Building module riptide
Building module s3vibes
Building module sblive
Building module sbxfi
Building module softoss
Building module solo
Building module sonorus
Building module trident
Building module via8233
Building module via97
Building module vmix
Building module vortex
Building module ymf7xx
depmod -a
-----------------------------
Detected Creative SB X-Fi *EARLY BETA*
Detected ATI High Definition Audio (SB600)
Detected Generic USB audio device (BETA)
Detected OSS Transparent Virtual Mixing Architecture
-----------------------------

Starting Open Sound System
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_pcm is in use by snd_hda_intel
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm
Failed to disable conflicting sound drivers
Reboot and try running soundon again

Also check that you have not compiled sound support statically
into the kernel.

---

### Post by krylon on 2008-02-08
Looks like you have onboard sound enabled which is now conflicting with your X-Fi.  Reboot and disable your onboard sound in the bios.

---

### Post by njparton on 2008-02-08
I got this working - excellent, made my day :) :) :) 

Is there an oss configuration application or something I can control the volume levels with?

---

### Post by tuxsheadache on 2008-02-08
sudo dpkg -i oss-linux_v4.0-1013_amd64.deb
Selecting previously deselected package oss-linux.
(Reading database ... 100113 files and directories currently installed.)
Unpacking oss-linux (from oss-linux_v4.0-1013_amd64.deb) ...
Setting up oss-linux (v4.0-1013) ...
Building OSS Modules for Linux-unknown 2.6.22-14-generic

OSS build environment set up for REGPARM kernels

Building module osscore
Building module ali5455
Building module allegro
Building module als300
Building module als4000
Building module apci97
Building module atiaudio
Building module audigyls
Building module audioloop
Building module audiopci
Building module cmi8788
Building module cmpci
Building module cs4280
Building module cs4281
Building module digi32
Building module digi96
Building module emu10k1x
Building module envy24
Building module envy24ht
Building module fm801
Building module geode
Building module hdaudio
Building module hdsp
Building module ich
Building module imux
Building module lynxone
Building module lynxtwo
Building module maestro
Building module neomagic
Building module ossusb
Building module riptide
Building module s3vibes
Building module sblive
Building module sbxfi
Building module softoss
Building module solo
Building module sonorus
Building module trident
Building module via8233
Building module via97
Building module vmix
Building module vortex
Building module ymf7xx
depmod -a
-----------------------------
Detected Creative SB X-Fi *EARLY BETA*
Detected Generic USB audio device (BETA)
Detected OSS Transparent Virtual Mixing Architecture
-----------------------------

Starting Open Sound System

---

### Post by krylon on 2008-02-08
> **njparton said:**
> I got this working - excellent, made my day :) :) :) 

Is there an oss configuration application or something I can control the volume levels with?

Try ossmix


tuxsheadache:

Your sound should now work, try osstest.

---

### Post by tuxsheadache on 2008-02-08
Sound seems to be coming from Front left, centre, and side right.(7.1 speakers)
Is this just Rhythmbox?
At least i have sound though =D

---

### Post by krylon on 2008-02-08
I think only ALSA can be configured for surround sound or duplicating channels.  Have you tried XMMS or Amarok?  Does the same speaker configuration sound properly in Windows?

---

### Post by tuxsheadache on 2008-02-08
How do i use the oss configuration? I think its not the media player, just how the sound card is mapping, since all sound is only coming out of them.

---

### Post by krylon on 2008-02-08
Can you confirm that your speakers are connected properly by running the speaker test in Windows?

---

### Post by tuxsheadache on 2008-02-08
They work perfectly in windows =)

---

### Post by krylon on 2008-02-08
Try ossxmix

---

### Post by tuxsheadache on 2008-02-08
How do I start ossmix?

---

### Post by krylon on 2008-02-08
```
/usr/bin/ossxmix
```

---

### Post by tuxsheadache on 2008-02-08
Seems to be only able to do stereo :(

---

