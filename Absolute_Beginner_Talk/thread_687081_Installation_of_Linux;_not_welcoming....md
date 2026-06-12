---
title: "Installation of Linux; not welcoming..."
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by xioSlayer on 2008-02-03
I wish to switch to Linux, however, I cannot even seem to install it.

I select the install (first option) choice, configure my graphics card, and then it says "Running local boot scripts", or something to that effect.

At this point, it just sits there.  What am i doing wrong?

---

### Post by Vadi on 2008-02-03
Is this from the CD, or have you already installed?

---

### Post by bodhi.zazen on 2008-02-03
Yea, if your hardware is not recognized it is tough.

What graphics card do you have ?

At that screen, hit the enter key, and you should have at least a command line interface.

I know that is tough, but we can likely use the vesa driver to al least get you a gui.

If you are on the live CD, enter :

```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure -phigh xserver-xorg
```

Select the vesa driver and a resonable resolution for your monitor.

Then,

```
sudo /etc/init.d/gdm start
```

You should now at least be in a graphical environment, although the resolution is likely sub-optimal. We need to know your graphics card to fix that.

---

### Post by xioSlayer on 2008-02-03
I don't know what a live CD is, I just downloaded and burned the ISO from the Ubuntu site.  64-Bit.

My graphics card is an XFX 8800GT 512MB;

should I do what you posted or do you have something else i should do once you know what my graphics card is?

---

### Post by bodhi.zazen on 2008-02-04
the "desktop" cd is the live CD, it allows you to run Linux (Ubuntu) without installing it on the hard drive first, although you can install from the live CD.

You can try the commands I gave you, the issue is your videocard is not being recognized / configured.

The only other options are to try to install the nvidia driver or try an alternate distro ....

---

### Post by xioSlayer on 2008-02-04
I tried the commands but none of them shown any response what-so-ever.  What am I to do now?

---

### Post by MockY on 2008-02-04
It sounds like you should go ahead and download the "Desktop" iso instead of the "alternative". If this is not the case, then I have nothing to contribute with.

---

### Post by jan quark on 2008-02-04
make sure your system supports 64 bit architecture

try the 32 bit version also , it run on 64 bit systems too

---

### Post by xioSlayer on 2008-02-05
> **jan quark said:**
> make sure your system supports 64 bit architecture

try the 32 bit version also , it run on 64 bit systems too

I have a Core2Duo e6750, which is 64bit if I'm not mistaken.

---

### Post by Ub1476 on 2008-02-05
You said you configured your graphic card, which in most cases, do not happen. This means that X (base graphical interface) could not start which means Ubuntu gave you the change to change the settings yourself.. When you do so, choose the **vesa** driver, and a** low** resolution as possible (basically, set everything as bad as possible). When Ubuntu has installed, you can download a program called Envy which will install the latest driver from nvidia for you, and give you correct resolution and visual effects:)

Sorry for the awkward language:lolflag:

By the way, if this do not work, hit alt+f2 and type in "startx" (maybe "sudo startx"). Tell us the output.

---

### Post by bodhi.zazen on 2008-02-05
Well, it sounds as if you are having problems with your video card, hard to be sure from your description.

You can try Ctrl-Alt-F7 and see if that brings you to a graphical interface or a screen with an error message.

Assuming the vesa driver did not work, frankly you are looking at a fairly convoluted procedure to trouble shoot this problem.

In order of complexity :

1. Make sure your CD burn is OK. Test the integrity and MD5 sum of your ubuntu desktoop iso.

Windows : [http://penguinbyte.com/software/md5filecheck/](http://penguinbyte.com/software/md5filecheck/)

	[http://ubuntuforums.org/showthread.php?&t=290339](http://ubuntuforums.org/showthread.php?&t=290339)

	[http://www.nullriver.com/index/products/winmd5sum](http://www.nullriver.com/index/products/winmd5sum)


2. Frankly, try another distro. SUSE, Fedora, Mint Linux, Mandriva would all be good options.

3. If you want to stay with Ubuntu, first make sure you do not have a hardware problem. I have seen nvidia cards fail due to the lack of a power adapter for example.

4. Next, try the 32 bit desktop version.

5. If that fails, install from the Alternate CD (64 bit should be fine)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

When you reboot I assume your gui will fail. If so, post the error message.

6. Next, install the nvidia driver. You will need to download the driver from here :

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

like this :

```
mkdir -P src/nvidia
cd src/Nvidia
wget ftp://download.nvidia.com/XFree86/Linux-ia64/1.0-5336/NVIDIA-Linux-ia64-1.0-5336-pkg1.run
```

Then :

```
sudo /etc/init.d/gdm stop && sudo apt-get remove --purge nvidia-glx
sudo apt-get install linux-headers-`uname -r` build-essential xserver-xorg-dev
```

Note those are bac tics ` by the number 1, and not single quotes '

Proceed :```
sudo sh NVIDIA*.run
```

When the script finishes, reboot.

Post any error messages.

If it works, but you do not get the proper resolution, log in and run :

```
gksu nvidia-settings
```

---

### Post by Nythain on 2008-02-05
and im surprised no one has thrown out the standards...
If at all possible, download the iso via bittorrent.
Once downloaded md5 check that bad boy, make sure its bit for bit correct.
Burn at the slowest speed freaking possible... and i mean slow.

these all sound silly, but i dont know how many corrupt iso's i've downloaded, and how many iso's i've corrupted the burn process of...
(that burn speed sounds silly till it happens to ya, then its not so silly)

another suggestion, download the "alternate install" iso, it will use a "text" installation method (wich isnt really text, more graphical terminal?) wich should at least get the system onto your computer... after witch you can work on getting everything you need installed/setup/configured and going

---

### Post by xioSlayer on 2008-02-06
ok, whenever I used the startx command, I was able to install ubuntu on my second hard drive.  Now I just need to know how to use it...  My first hard drive has windows on it, and it boots windows whenever I restart my PC.

---

### Post by yaknowwat on 2008-02-07
on 7.10, 64bit the LiveCD seems to get a lot of problems with the 8800 if you have an onboard graphics use that one to boot and install ubuntu then you should be able to install the 8800 with the Nvidia drives.

Not sure as to why the 8800 doesn't work in the LiveCD when it works in Ubuntu maybe missed update on the LiveCD part?

---

### Post by xioSlayer on 2008-02-07
> **yaknowwat said:**
> on 7.10, 64bit the LiveCD seems to get a lot of problems with the 8800 if you have an onboard graphics use that one to boot and install ubuntu then you should be able to install the 8800 with the Nvidia drives.

Not sure as to why the 8800 doesn't work in the LiveCD when it works in Ubuntu maybe missed update on the LiveCD part?

Now, however, I seem to have installed it, I just need to know how to boot it.

---

### Post by yaknowwat on 2008-02-08
When your system starts does " GRUB " load?
If it does hold the 'Esc' Key.
and it should give options of what you want to start as.

---

### Post by danbrazier on 2008-02-08
i'm having the same problem (See my other post in the noob section :))

pressing alt+f2 brings up a passage letting me type my login (Username) and password. then i get the prompt:

dan@danslaptop:~$

---

### Post by xioSlayer on 2008-02-08
> **yaknowwat said:**
> When your system starts does " GRUB " load?
If it does hold the 'Esc' Key.
and it should give options of what you want to start as.

No, GRUB doesn't display anything.  Windows just boots.

---

