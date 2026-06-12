---
title: "1st day at Linux: how to install software"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by tamoghno on 2007-11-11
Hello today is for the first time i am using linux ; so please dont get irritated for stupid question.
i have installed gutsy gibbon, dual booted with XP. But my visual effect is disabled , i was prompted for my graphics card driver(GeForce 5200) & so i downloaded "NVIDIA-Linux-x86-100.14.19-pkg1.run" ( my access to net is via mobile, so i was unable to do it in linux,  )
my question is how to install it ? i have dragged it into terminal ,added "sudo" before command & run it, but it is asking me to close "x server",how do i do that?  i dont even know if what i am doing is right.can somebody help me ?
also can anyone give me link to tutorial about how to install "*.run" & "tar.gz" pakag

helplessly for your reply :(

---

### Post by PriceChild on 2007-11-11
System > Administration > Restricted Drivers Manager

That handy utility will make instillation of your nvidia drivers a point and click affair. You can delete the file you downloaded :)

---

### Post by P4man on 2007-11-11
To exit X, open a terminal (applications/ accessories/terminal)

type:

> sudo /etc/init.d/gdm stop

Browse to the folder where you stored the driver. assuming its on your desktop type:

```
cd Desktop
sudo sh NVIDIA-etc-etc-etc (press tab key to autocomplete the name)

```

To restart X type:

> sudo /etc/init.d/gdm restart

---

### Post by P4man on 2007-11-11
> **PriceChild said:**
> System > Administration > Restricted Drivers Manager
)

That is the easy way, but apparently he has no internet connection on his ubuntu machine, so that won't work. I fear a lot of other things won't work either then.. he is going to need build-essentials I think for the nvidia drivers to install, and without internet, I have no idea how to install that.

---

### Post by PmDematagoda on 2007-11-11
In order to install the Nvidia driver manually you need the Linux kernel source code, without it, the Nvidia kernel cannot be built and the installation will fail. And the kernel source code is about 50 Mb's big. You can try installing it manually, but I have never tried this before.

---

### Post by Whiffle on 2007-11-11
Adding to what p4man says, if you use the .run file from nvidia, you'll need to edit your /etc/X11/Xorg.conf manually to use the nvidia driver.  This means doing:

```

sudo gedit /etc/X11/Xorg.conf

```

and finding the section that looks like:
```

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"        
EndSection

```

and making it look like:
```

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

```

Then, logout, hit ctrl+alt+F1 and type:
```
sudo init.d/gdm stop
``` which stops xorg and the display manager

and then when it done doing its thing, do
```

chmod +x /path/to/nvidia-*.run
sh /path/to/nvidia-*.run

```

which will compile and install both parts of your nvidia driver.

After that you can do 
```

modprobe nvidia
sudo /etc/init.d/gdm start

```

and finally you'll need to edit some file somewhere to tell it to load the nvidia module on boot, but i dont remember where.  Lastly, if you ever upgrade your kernel (like through the automatic updater), your Xorg display will cease to work.  You'll need to redo the last couple of steps when that happens to get it going again, so don't delete that nvidia-*.run

---

### Post by P4man on 2007-11-11
> **Whiffle said:**
> Adding to what p4man says, if you use the .run file from nvidia, you'll need to edit your /etc/X11/Xorg.conf manually to use the nvidia driver. 

The nvidia installer will do all that automatically I believe. But its a probably a moot point, because he won't get that far without build-essentials and kernel headers, and without internet, we need someone that knows how to install them (from his mobile phone no less LOL).

I suggest we wait for the OP to explain why he can't connect to the net. If its some problem with his network or drivers, we better solve that first.

---

### Post by Whiffle on 2007-11-11
Ah yes good point.  Darn that internet.

---

### Post by mcduck on 2007-11-11
At least build-essential is on the Alternate CD and can be installed from there. I suppose kernel headers should be on the disc as well.

---

### Post by freesitebuilder on 2007-11-11
"How to install anything in Ubuntu" is a good site:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by PriceChild on 2007-11-11
I would STRONGLY advise that you download the required packages then from packages.ubuntu.com on windows (not requiring 50mb kernel ones) and install those, rather than installing from the .run manually.

---

### Post by AnonCat on 2007-11-11
Since my Ubuntu machine doesn't have internet access yet,  I had to go through the following steps to manually install the driver on 7.10 (let me know if you need more detailed information):


1. Download the latest nVidia linux driver from the nvidia website with another computer (which you already have)

2. Boot into Ubuntu and copy the nvidia file into a folder of your choice.  After doing so Insert your Ubuntu CD and with synaptic install the "build essential" package.  You can find synaptic by going to "System" on the top menu and then going into "Administration".  On the side window in synaptic you'll see an option for using the CD.  

3. reboot into the command line only (choose recovery in Grub), do not load the GUI. 

4. go into the directory where you copied the nVidia driver setup file (for example  i.e. cd /etc/Tempfolder/)

5. type sh <name of downloaded driver>

6. Go ahead and install even if it warns not to because of the computer being at level 1 or some such thing.  When the install program asks if you want it to automatically configure the relevant files allow it.  This way you won't have to manually edit xorg.conf.

7. reboot and your card should work.  You might have to change the resolution and do other minor tweaks.

---

### Post by tamoghno on 2007-11-12
@ FREESITEBUILDER:
Many many thanks for the link i was finding that type of tutorial.

@ PriceChild

can you please explain it a bit more & give me exact link [ amd athlon 64 bit, 1gig, gForce 5200 ] , i am very confused .

regarding internet : i am from a tiny tiny city of india ; my only internet connection is through mobile EDGE ( though i can use 2mpbs cyber cafe ). so i am yet to figure out how to set up internet through mobile , right now i am more busy in making compiz work for me.

---

### Post by erginemr on 2007-11-12
> **PriceChild said:**
> I would STRONGLY advise that you download the required packages then from packages.ubuntu.com on windows (not requiring 50mb kernel ones) and install those, rather than installing from the .run manually.

+1, even ++1!

As a new user, you should avoid installing the NVIDIA deriver script, which will create more problems and results later on when you upgrade your kernel. I now, I have run into it, and have seen quite a few other people on the forums having driver compatibility problems in the long run, just becasue they have installed the binary package (*.sh) once.

Therefore, you should heed PriceChild's advice and install the graphics driver via:
System > Administration > Restricted Drivers Manager

---

### Post by P4man on 2007-11-12
IF you have bluetooth on your phone and PC, you could use it for networking.

---

### Post by erginemr on 2007-11-12
Or, you can download the binary NVIDIA driver from:
[http://packages.ubuntu.com/gutsy/misc/nvidia-glx-new](http://packages.ubuntu.com/gutsy/misc/nvidia-glx-new)

from an Internet Cafe or a friend with a faster Internet connection and install it in your computer by double-clicking on the package.

---

### Post by hammad1337 on 2007-11-12
First things first...
Even if this problem of yours is solved, sooner or later u will require an internet conction for something else...internet connection in ubuntu is a must.
a lot of things become a breeze to do if u have internet access.
Please get internet connectivity before you do any thing else. It will take a lot of pain away from you.

I m not saying Ubuntu is impossible without internet access, its just hell lot harder.
:)

---

### Post by mivo on 2007-11-12
> **hammad1337 said:**
> I m not saying Ubuntu is impossible without internet access, its just hell lot harder. :)

I agree here, and I think it is really true for most if not all Linux distros (actually, it's true for Windows as well). A bit of a compromise are the DVD versions that are offered for some distros, since they have already a lot of packages included, so you do not have to download (m)any packages, at least for some time. Binary drivers like the Nvidia drivers are a special case, though, since these are almost never included. The Ubuntu DVD can be found here:

[http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/)

---

### Post by tamoghno on 2007-11-12
> **erginemr said:**
> Or, you can download the binary NVIDIA driver from:
[http://packages.ubuntu.com/gutsy/misc/nvidia-glx-new](http://packages.ubuntu.com/gutsy/misc/nvidia-glx-new)

from an Internet Cafe or a friend with a faster Internet connection and install it in your computer by double-clicking on the package.

which version should i download ? my CPU is AMD64 but i installed X86 ubuntu !

as far fast internet , i have downloaded full ubuntu *.iso over my EDGE connection !:KS i think i am a star !

---

### Post by erginemr on 2007-11-12
> **tamoghno said:**
> which version should i download ? my CPU is AMD64 but i installed X86 ubuntu !

as far fast internet , i have downloaded full ubuntu *.iso over my EDGE connection !:KS i think i am a star !

:lolflag: But I hope you are not enrolled to your GSM provider on a fee per byte transfer basis...

I think you should install i386 version to comply with your operating system. Good luck, friend.

---

### Post by erginemr on 2007-11-12
One more thing: 

Before you start the installation I recommend you to back-up your previous xorg.conf file by issueing the following command on the console:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak

This way, you can revert to the older configuration file, in case things go wrong with the new driver. In such a bad situation, you can try restoring your previous generic graphics driver by:
sudo cp /etc/X11/xorg.bak /etc/X11/xorg.conf

---

