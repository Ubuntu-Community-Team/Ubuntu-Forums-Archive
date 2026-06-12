---
title: "Screen resolution in fiesty"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by DreamcastJack on 2007-04-19
my screen reso will only go up to 800x600?  when I manage to egt the nVIDIA driver D/Led will i be able to put it higher?

---

### Post by Perfect Storm on 2007-04-19
Highly likely. I have to install nvidia driver before I get the right res.

---

### Post by DreamcastJack on 2007-04-19
alright, that fixed my resolution!  but man getting stuff d/led it taking awhile tonight cause of all the traffic.

---

### Post by Perfect Storm on 2007-04-19
Aye, alot of upgrades/updates and feisty downloads ^_^

---

### Post by drako1011 on 2007-04-19
Hi,

I have a nvidia geforce MX4000 graphics card, and my resolution won't go past  800x600. I'm new to ubuntu, and was wondering how do i fix this.

---

### Post by jeffmetal on 2007-04-19
edit your fstab file.

```
gksu gedit /etc/X11/xorg.conf
```


SubSection "Display"
                Depth   24
                Modes           "1440x900"      "1440x1440"     "1280x1024"    "1024x768"       "832x624"       "800x600"       "720x400"       "640x480"

you will want to add your resolution in the display section there and it should then allow you to select it.

---

### Post by iPirates on 2007-04-20
simply adding the resolution didn't work for me.  i haven't installed the new drivers for my nVidia card yet, and I guess that's probably why, but it's a pain trying to figure out what method to follow in installing the drivers in fiesty...

---

### Post by Perfect Storm on 2007-04-20
```
sudo aptitude install nvidia-glx
sudo nvidia-glx-config enable
```

<ctrl>+<alt>+<backspace>

If it fails;
```
sudo nano /etc/X11/xorg.conf
```

or

```
 sudo dpkg-reconfigure -phigh xserver-xorg
```

and change "nv" to "nvidia"

(this is for newer nvidia cards

for older cards install nvidia-glx-legacy instead)

---

### Post by black_magician on 2007-04-20
is there a list where I can see which driver to use for which card?  I'm on a GeForce 6800 and am using the regular  nvidia-glx driver, but am having screen res problems.  should I be on the legacy driver?

---

### Post by Perfect Storm on 2007-04-20
GeForce 6800 uses normal nvidia driver.

Try run;
```
 sudo dpkg-reconfigure -phigh xserver-xorg
```

first if your res isn't okay.

---

### Post by DreamcastJack on 2007-04-20
I myself have 6100 onboard and the driver worked perfect for Nvidia.

---

### Post by catalyst294 on 2007-04-21
I had this same problem. I fixed it by...

-going into the "Restricted Drivers Manager" in System ->Administration.

-there I _unclicked_ the driver for my Nvidia video card (i think it only uninstalled the nividia-legacy-glx package?)

-but I rebooted and it came up with all kinds of resolution choices, I'm now using 1024x768.

I don't know how this happened or why it worked. But it did! So hopefully my aimless fumbling will help some of you out there:)

---

### Post by subi_rex on 2007-04-21
I have an intel 945g/gz video chipset. I set my resolution as stated in the thread, but the sides are chopped off and the fonts are still a little stretched out. Any help is appreciated. 

I looked in the devices section and the video chip detected was the i810. Definitely way off. 

-Michael

---

### Post by Billium on 2007-04-21
Having the same resolution problem. tried to download drivers and got this:

bill@bill-desktop:~$ sudo aptitude install nvidia-glx
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be installed:
  nvidia-glx 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 4492kB of archives. After unpacking 13.7MB will be used.
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted nvidia-glx 1:1.0.9631+2.6.20.5-15.20 [4492kB]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted nvidia-glx 1:1.0.9631+2.6.20.5-15.20
  Error reading from server. Remote end closed connection [IP: 130.239.18.159 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/nvidia-glx_1.0.9631+2.6.20.5-15.20_i386.deb:](http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/nvidia-glx_1.0.9631+2.6.20.5-15.20_i386.deb:) Error reading from server. Remote end closed connection [IP: 130.239.18.159 80]
bill@bill-desktop:~$ 

Have no clue what this all means!

Any help would be appreciated.

---

### Post by prawn on 2007-04-22
I've been having the same resolution problem. My various attempts to fix the problem (e.g. taking some of the steps above) have resulting in the system being unable to start the x-windows environment and I fall back to a non-graphical terminal. Since I don't know how to fix that, I've resorted to reinstalling ubuntu, since there doesn't seem to be a repair option. After three such attempts, it's getting a little boring, especially since I have to reinstall various apps and update various settings files as the install insists on reformatting everything.

Any suggestions would be appreciated as to:
1. How to get higher resolution without causing major collateral damage.
2. How to fix the problems without a reinstall if problems are caused.

I am using amd64 desktop install. I have an asus motherboard, amd64 chip and onboard nvidia graphics chip. The video is connected via a 4-way KVM switch.

---

### Post by prawn on 2007-04-22
P.S. I should also add that my previous environment was dapper drake and I never had any resolution problems. At this rate I'm tempted to revert to Edgy, or maybe all the way back to Dapper.

---

### Post by black_magician on 2007-04-22
> **Artificial Intelligence said:**
> GeForce 6800 uses normal nvidia driver.

Try run;
```
 sudo dpkg-reconfigure -phigh xserver-xorg
```

first if your res isn't okay.

ok, I have that driver installed.  I ran the reconfigure command but it didn't help anything.

---

### Post by prawn on 2007-04-22
Reverting to Edgy now (just finished downloading it). Interestingly, straight from the CD boot, the resolution is higher than I got from feisty. If the resolution works in Edgy and I choose to upgrade rather than a fresh install, is that likely to bork the resolution?

---

### Post by Boule on 2007-04-22
Actually I tried upgrading to Feisty from edgy, and I didn't have resolution problems, and IIRC I was using nvidia drivers.

I was able to fix the res problem by going back to the generic driver (nv), but I couldn't make it work with nvidia

---

