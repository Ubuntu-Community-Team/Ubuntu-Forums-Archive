---
title: "Video Card Troubles"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by mkylman on 2007-06-04
Okay so I finally got my Ubuntu installed on my comp, I got ndiswrapper working, as well as my Netgear wireless card...But I noticed that my resolution could go no higher than 800x600...but I want to put it up to 1024x768; I realize that this is an issue with the fact that I don't have the right video driver installed; Here are my specs, hopefully they'll aid you in aiding me:

Dell Inspiron 4000
256 MB Ram
40GB HardDrive
ATI Rage Mobility 128 2x AGP (DELL) (NOTE: I fear this may be paraphrased a *bit*, but those terms are all in the name)
Pentium 3 Processor(700 Mhz I believe)

I did a few searches and could not find this driver, if anyone else knows where to find it that would be great; I can't really search for it because I have to take my final exams, plus I've spent about 20 minutes looking already -_- So any help would be GREATLY appreciated

Mkylman

---

### Post by Zzl1xndd on 2007-06-04
Try installing the driver with Envy you can get it here [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html). 

Now I will mention with using Envy you will need to re-run it everytime there is a Kernel update but its not to hard Give it a shot.

---

### Post by mkylman on 2007-06-04
Quick question, this is for NVidia it says, will it work for my ATI card? I can't test it right now cuz I'm at school, but I'm assuming that you know what you're doing;

If anyone else has anymore advice/help that would be greatly appreciated!

Mkylman

---

### Post by overdrank on 2007-06-04
> **mkylman said:**
> Quick question, this is for NVidia it says, will it work for my ATI card? I can't test it right now cuz I'm at school, but I'm assuming that you know what you're doing;

If anyone else has anymore advice/help that would be greatly appreciated!

Mkylman

Hi I have the same card on a laptop and this link worked for me
[http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/](http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/)
Just follow commands and the instructions good luck!:popcorn:
But no 3d effects for beryl

---

### Post by Zzl1xndd on 2007-06-04
Yeah it will work with ATI cards as well, It was just first used with Nvidia. It Should do the job.

---

### Post by mkylman on 2007-06-04
Yeah, I can't either to install; I have Python 2.5 on here and it keeps telling me that I need Python 2.4...but that's below the version I have now...so shouldn't I be set? I'm going to download 2.4 anyway and see if that actually changes anything, although I'm really quite skeptical that it will;

Mkylman

---

### Post by mkylman on 2007-06-04
Okay I had no luck finding 2.4 for linux; I don't think that it is an issue with the fact that I have 2.5 anyway because the python site makes it kinda clear that you can do whatever it is you need to do with the newer python that you could do before(i.e. python 2.4 will run in 2.5 and 4.0, etc.) So idk what in the hell is wrong here...Any ideas???

mkylman

---

### Post by mkylman on 2007-06-04
*bump*

Yeah I know, I'm rude ^_^

---

### Post by shae on 2007-06-04
Personally, I am a little old fashioned, but I always manually install the driver ysing the following from ati wiki: [http://wiki.cchtml.com/index.php/Ubuntu]("http://wiki.cchtml.com/index.php/Ubuntu")
> Method 2: Install the 8.37.6 Driver Manually

    * Note: This is just an alternative installation method for the section above. It might help if you still get 'DRI missing' errors. 

        * NOTE: This driver is now prepared for 2.6.20 kernels! (I have it running on 2.6.21)

Download the ATI driver installer: [ati-driver-installer-8.37.6-x86.x86_64.run]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.37.6-x86.x86_64.run")(this installer is for 32bit and 64bit systems), taking care of which version needs for your [device]("http://wiki.cchtml.com/index.php/Hardware").


Change to the download directory. Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list before doing these steps.

There is a detailed manual with screenshots at [Ubuntu Wiki]("https://help.ubuntu.com/community/Repositories/Ubuntu").

By default, Ubuntu does not enable the Universe and Multiverse repositories. But they include some important programs and codecs, so it is highly recommended to activate them.

**Install necessary tools:**

```
sudo apt-get update
sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper debconf libstdc++5 linux-headers-$(uname -r)
```

**Create .deb packages:**

```
sudo bash ati-driver-installer-8.37.6-x86.x86_64.run --buildpkg Ubuntu/feisty
```

**Blacklist old fglrx module from linux-restricted-modules:**

*Note: You only need to do this if you've installed the driver from Method 1 above. 

As ubuntu's linux-restricted-modules package includes the fglrx module from an old driver version (8.28.8), we have to blacklist this module to make sure the new kernel module which is needed by the new driver will be used instead.

```
sudo gedit /etc/default/linux-restricted-modules-common
```

Add "fglrx" to the line "DISABLED_MODULES"
File: /etc/default/linux-restricted-modules-common

[QUOTE]DISABLED_MODULES="fglrx"

**Install .deb packages:**

```
sudo dpkg -i xorg-driver-fglrx_8.37.6-1*.deb
sudo dpkg -i fglrx-kernel-source_8.37.6-1*.deb
sudo dpkg -i fglrx-amdcccle_8.37.6-1*.deb
```

**Remove any old fglrx debs from /usr/src/:**

```
sudo rm /usr/src/fglrx-kernel*.deb
```

**Fix broken dependencies**

    * Note: You only need to do this if you have installed previous versions of these drivers using this method before. 

```
sudo apt-get -f install
```

**Compile the kernel module:**

```
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a
```

**Create a symbolic link (You may have to make the directory)**

```
sudo ln -s /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko

```
IMPORTANT: You have to recompile the kernel module after each kernel update!

**Configure the Driver**

*Note: An alternative to the aticonfig --initial command is to edit /etc/X11/xorg.conf and replace the string "ati" with "fglrx" in the "Device" section. This way you won't lose your old "Screen" and "Monitor" settings. Afterwards you can use aticonfig for setting overlay etc. I suggest that you do it the manual way if you patched the module, aticonfig --initial didn't work for me. Another alternative is aticonfig --initial --force 

```
sudo aticonfig --initial
```

Then:

```
sudo aticonfig --overlay-type=Xv
```

**Finish the Installation**

Now save any open document and reboot your system:

```
sudo shutdown -r now
```

 *Note: An alternative to rebooting is to restart the X Server by pressing your CTRL+ALT+BACKSPACE keys. You must remove any old kernel modules such as "drm" "radeon" or "fglrx" using the "rmmod" command. Example: sudo rmmod fglrx [/QUOTE]

> **Troubleshooting**
** No 3D acceleration**

If you see output that looks like this:

```
$ fglrxinfo 
display: :0.0 screen: 0 
OpenGL vendor string: Mesa project: www.mesa3d.org 
OpenGL renderer string: Mesa GLX Indirect 
OpenGL version string: 1.2 (1.5 Mesa 6.4.1) 
```

Then try these two commands:

```
mkdir -p /usr/X11R6/lib/modules/dri 
ln -s /usr/lib/dri/fglrx_dri.so /usr/X11R6/lib/modules/dri 
```

If that doesn't work confirm fglrx is loaded:

```
lsmod | grep fglrx
```

If it returns nothing then try this:

```
sudo depmod -ae
sudo echo fglrx >> /etc/modules

```

or if that has a permission error:

```
sudo -s
depmod -ae
echo fglrx >> /etc/modules
exit

```



I have always had to do those two steps in trouble shooting to get direct rendering to work.  If you have any questions, please ask.

---

### Post by mkylman on 2007-06-04
Shae, I tried your method and it did not work...I still can't change anything; I try running amdcccle and it says "Segementation fault (Core Dumped)" I try to change it in the screen resolution section of Ubuntu(under system, preferences, screen resolution) and that still only goes to 800x600; I also tried running sudo aticonfig --initial, which says "found fglrx device section, nothing to do, terminating"; I also tried sudo aticonfig --resolution=1024x768 and it said "Error: Section # expected.  aticonfig: parsing the command line failed"

So I'm at a loss here;

I'm sure if I found the driver and used Envy to install it manually then I could get it working, but the thing is that ATI merged w/ AMD and their site did the same, so I cannot do a search on ATI and find MY driver, nor can I do so on versiontracker.com, or any other site; I'm going to try and locate it on archive.org's archives of ati.com and if that doesn't prove fruitful then I'll be returning in tears;

Even though I can avoid the blue screen and I run more efficiently, it sure is a bitch to find the drivers :D I'd never completely go back though ;)

Mkylman

---

### Post by mkylman on 2007-06-05
*bump* I still can't get my card working, I totally need help, I can't find the driver or anything...

---

### Post by muhdzuhri on 2007-06-05
i think the problem is your ubuntu_.iso file. please md5sum first and compare the result>>[UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes")<<. *don't resume if your download process failed. you have to start from the beginning*.

---

### Post by mkylman on 2007-06-05
I have no idea what you are talking about; How do I md5sum something? that's checking the checksum right? Do I do this in Linux? Secondly what are you talking about ubuntu_.iso file? I installed ubuntu w/ wubi, which uses a different type of iso file;

---

