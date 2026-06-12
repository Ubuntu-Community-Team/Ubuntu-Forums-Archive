---
title: "Help Configuring Nvidia GeForce FX 5200 Ubuntu 6.10"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by somar on 2007-01-01
I'm having issues configuring my Nvidia card.  I followed the instructions listed here:

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#METHOD_2](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#METHOD_2)

and also tried:

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/graphics-cards.html#nvidia](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/graphics-cards.html#nvidia)

When I try to select the driver, while configuring the xserver, I do not see "nvidia" from the list of drivers.  After restarting gdm my screen goes blank/dark.  Could someone please help me troubleshoot?

Thanks,

MS

---

### Post by K.Mandla on 2007-01-02
Have you tried installing the [nvidia-glx]("http://packages.ubuntu.com/edgy/x11/nvidia-glx") drivers from the repositories? The latest drivers are generally more for cutting edge cards, and a 5200 should work great with the Ubuntu package.

Install with *sudo aptitude install nvidia-glx*, then edit your xorg.conf file with *sudo nano -w /etc/X11/xorg.conf*. Change "nv" to "nvidia" and reboot.

---

### Post by somar on 2007-01-02
K,

I ran 

```
sudo aptitude install nvidia-glx
```

The xorg.conf file showed "nvidia" as the driver so no change was necessary. 

I rebooted and got the "Failed to start the X server..." blue screen

more...


FATAL: Could not open '/lib/modules/2.6.17-10-generic/volatile/nvidia.ko' No such file or directory
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): ***Aborting***
(EE) Screen(s) found but none have a usable configuration.

Fatal server error:
no screens found


MS

---

### Post by K.Mandla on 2007-01-02
For some reason, you seem to still be using the generic kernel. The nvidia drivers need the 386 kernel, but it's odd that they weren't installed when you pulled in the nvidia-glx driver. :-k

Try this:

```
sudo aptitude install linux-386
```
Then reboot, and hopefully it should work. [-o< If you get a boot options screen at startup, make sure Grub is loading the 386 kernel.

---

### Post by somar on 2007-01-02
K,

I loaded the 2.6.17-10-386 kernel in the GRUB menu but I'm still getting the "Failed to start X server ..." and 

FATAL: Could not open '/lib/modules/2.6.17-10-generic/volatile/nvidia.ko' No such file or directory
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): ***Aborting***
(EE) Screen(s) found but none have a usable configuration.



What now?


Thanks for your help,

MS

---

### Post by Cariboo1938 on 2007-01-02
> **K.Mandla said:**
> For some reason, you seem to still be using the generic kernel. The nvidia drivers need the 386 kernel, but it's odd that they weren't installed when you pulled in the nvidia-glx driver. :-k

Try this:

```
sudo aptitude install linux-386
```
Then reboot, and hopefully it should work. [-o< If you get a boot options screen at startup, make sure Grub is loading the 386 kernel.I'm having the same problem as 'somar', except I have installed Ubuntu [COLOR="DarkOrchid"]6.10-amd64[/COLOR] and /boot/grub/menu.lst tells me that this kernel is installed > title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd          /initrd.img-2.6.17-10-generic
quiet
savedefault
boot
What kernel would I need to get?

---

### Post by K.Mandla on 2007-01-02
I'm a little confused now, too. When you install nvidia-glx, it should draw in the linux-386 package as a requirement -- the nvidia.ko module isn't in the generic package. Installing either one should give you the option to boot 2.6.17-10-386 from the grub menu list. 

When you start your computer and you see the three-second warning for the grub bootloader, press escape and make sure you're picking the 386 kernel. 

Weird stuff. ... :-k

---

### Post by K.Mandla on 2007-01-02
> **Cariboo1938 said:**
> I'm having the same problem as 'somar', except I have installed Ubuntu [COLOR="DarkOrchid"]6.10-amd64[/COLOR] and /boot/grub/menu.lst tells me that this kernel is installed What kernel would I need to get?
I'm not 100 percent sure; I've never had the pleasure of working with an AMD64 machine that had an Nvidia card in it. Perhaps someone can chime in on that.

---

### Post by spockrock on 2007-01-02
I run the generic kernel with nvidia-glx, make sure you have the restricted modules installed for your kernel.

linux-restricted-modules-generic,  linux-restricted-modules-common, linux-restricted-modules-2.6.17-10-generic, linux-restricted-modules-2.6.17-10-386

are the packages I have for both the 386 and generic 2.6.17-10 kernels.

---

### Post by mahiyar on 2007-01-02
I also have fx 5200 card and have installed Nvidia drivers (and Beryl also :) ), but the way I went about installing the Nvidia drivers is one as shown here [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29) . This method has worked for me and has very few steps hence feweer chabces of errors.

---

### Post by FisherPrice on 2007-01-02
Hi,

I have my 5200 working by inserting the lines 

Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"
Option "AllowGLXWithComposite" "Off"
Option "Accel" "Off"

into the Device section but the NVIDIA logo doesn't show and I am not able to start any OpenGL programs :(

---

### Post by K.Mandla on 2007-01-02
Well, I'm afraid a night's sleep hasn't made this any clearer for me. I was under the impression that linux-generic was installed by default, regardless of the video chipset. Installing the proprietary nvidia-glx package drew in linux-386, which brought in the nvidia module that it needs.

I'll double-check my numbers on this, but I'm afraid I'm not much closer to understanding. I apologize if I've given any bad advice on this. Cheers. :-k

---

### Post by somar on 2007-01-02
Hi K,

After you requested that I install the 386 kernel, I followed your directions from the command line, installed the 386 kernel, rebooted, escape to manually select the 386 kernel, selected it and got the "X failed to blah blah blah" (see previous post) same error message as before.

I greatly appreciate your time, knowledge and patience as I've been grappling with getting a decent resolution and or even a working screen for 4 weeks now ([http://www.ubuntuforums.org/showthread.php?t=326094&highlight=G400+Matrox](http://www.ubuntuforums.org/showthread.php?t=326094&highlight=G400+Matrox))

Do you have any further suggestions?


MS

---

### Post by K.Mandla on 2007-01-02
Not really. I'm afraid I'm a bit flummoxed by this. You might try getting a hold of tseliot or perhaps drawing his attention to this thread; he's the in-house nvidia expert. ;)

My only fear at this point is if you have more than one version of a driver installed or partly installed, and it's causing either X or the kernel to freak out. You might try stripping everything out again, purging out nvidia-glx and even that kernel I suggested, and trying to get back as close to scratch as possible.

I don't know if you're keen on a rebuild, but from my vantage point, I would be interested in seeing if a pure and fresh system makes any of it work cleaner. Just a suggestion; not a requirement, of course. :D Personally, I learn by breaking things, trying to fix them and then starting over from scratch again. Probably a bad habit. :rolleyes:

---

### Post by pross on 2007-01-02
rae you sure the module has even loaded?

```

pross@pross-desktop:~$ dmesg | grep NVIDIA
[    0.000000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x0000000000000000
[   37.761182] nvidia: module license 'NVIDIA' taints kernel.
[   38.018864] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  1.0-9746  Fri Dec 15 10:19:35 PST 2006

```

if it doesnt load at boottime try 'sudo modprobe nvidia'

this is all i have in xorg.conf:

```

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection
Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by somar on 2007-01-03
**CORRECTION!!!**

I was tired when I posted last night, my apologies.

Here is what the BSO X server failure reads:

FATAL: Could not open '/lib/modules/2.6.17-10-386/volatile/nvidia.ko': No such file or directory
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): ***Aborting***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

The 386 kernel was selected from the GRUB menu and loaded correctly.

---

### Post by somar on 2007-01-03
**I have a freakin' screen with 1024 x 768 resolution!!! **:D :D :D


Just for sh*ts and giggles I changed my xorg.conf driver setting from "nvidia" to "nv" and rebooted.

The screen's not pretty @ a refresh rate of 60 Hz- but hey...  it's working.

I need to find a way, if it's possible to install the nvidia.ko in the /lib/modules/2.6.17-10-386/volatile/ directory because that's what the Xserver failure is not happy with when "nvidia" is selected as the driver. :-k 



MS

---

### Post by pross on 2007-01-03
I think i know where the problem is... you are booting into the 386 kernel...and the module is installed into the generic folder maybe?

what happens if you do:
```
pross@pross-desktop:~$ ls -l /lib/modules/
drwxr-xr-x 6 root root 4096 2006-12-27 21:27 2.6.17-10-generic
total 4

```
and for reference...
```

pross@pross-desktop:~$ ls -l /lib/modules/2.6.17-10-generic/volatile/
total 23288
-rw-r--r-- 1 root root  280695 2007-01-03 00:56 ath_hal.ko
-rw-r--r-- 1 root root 1161706 2007-01-03 00:56 fcdsl2.ko
-rw-r--r-- 1 root root 1161225 2007-01-03 00:56 fcdslsl.ko
-rw-r--r-- 1 root root 1150220 2007-01-03 00:56 fcdslslusb.ko
-rw-r--r-- 1 root root 1152022 2007-01-03 00:56 fcdslusb2.ko
-rw-r--r-- 1 root root 1004796 2007-01-03 00:56 fcdslusb.ko
-rw-r--r-- 1 root root  896398 2007-01-03 00:56 fcpci.ko
-rw-r--r-- 1 root root  807929 2007-01-03 00:56 fglrx.ko
-rw-r--r-- 1 root root 9954619 2007-01-03 00:56 nvidia.ko
-rw-r--r-- 1 root root 6149895 2007-01-03 00:56 nvidia_legacy.ko

```

---

### Post by somar on 2007-01-04
> I think i know where the problem is... you are booting into the 386 kernel...and the module is installed into the generic folder maybe?


Good call pross!

No such luck. :(


I'm attaching a file to show that there are some nvidia files (drivers?) in

/lib/linux-restricted-modules/2.6.17-10-386/nvidia    AND
/lib/linux-restricted-modules/2.6.17-10-386/nvidia_legacy

but they are not the same as the ones in your last post.

---

### Post by pross on 2007-01-04
tell me have you tried to install using the nvidia installer from nvidia.com?

if so it looks like you might have to re-install it. i can show you my sources.list and give you a walk-thru, but right now its 8:10 and i'm trying to get a 5yr old dressed and ready for school, so it'll be a little later :p

---

### Post by pross on 2007-01-04
Right this is how i'd do it:
[You could choose to follow some or all of these notes]

1st reboot you PC and choose the default generic kernel, when its booted check in a console:
```

pross@pross-desktop:~$ uname -a
Linux pross-desktop 2.6.17-10-generic #2 SMP Tue Dec 5 21:16:35 UTC 2006 x86_64 GNU/Linux

```

[this part adds an outside repo to your sources.list to get the latest stable nvidia module]

sudo nano /etc/apt/sources.list
add the following:
deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable
save and exit nano with CTRL+O then CTRL+X

you have to import the key for the repo so apt does not spit out an error:
```

wget http://nvidia.limitless.lupine.me.uk/ubuntu/root@lupine.me.uk.gpg -O- | sudo apt-key add -

```
(its all one line)
now do apt-get update
then apt-get install nvidia-glx

all being good that should install the driver to the correct folder for the running kernel (generic)
now go for a reboot, remember to select generic...

assuming your still using xorg's NV driver it should boot to the graphical login
so login and open a terminal and try the following:
```

pross@pross-desktop:~$ dmesg | grep NVIDIA
[    0.000000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x0000000000000000
[   33.563720] nvidia: module license 'NVIDIA' taints kernel.
[   33.820603] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  1.0-9746  Fri Dec 15 10:19:35 PST 2006

```
the above will check to see if the module loaded at bootime..it might not have done as you have NV selected in xorg.conf
if it didnt appear:
do a sudo modprobe nvidia
then check again

if it did appear to load you can go ahead and edit your xorg.conf and select "nvidia" instead of "nv" in the driver section, then logout, do a CTRL+ALT+BCKSPACE and you 'should' see the nvidia splash screen!

if it didnt load post the error messages and i'll do my best to help ;)

good luck

---

### Post by Cariboo1938 on 2007-01-04
M> **K.Mandla said:**
> I'm not 100 percent sure; I've never had the pleasure of working with an AMD64 machine that had an Nvidia card in it. Perhaps someone can chime in on that.Thanks for your help, Mandla, 
I gave up the idea to install NVidia driver version 9631 on Edgy Eft. 
Instead, as you recommended, I used ```
sudo apt-get install --reinstall linux-restricted-modules-`uname -r` nvidia-glx
```to install nvidia drivers. 
I also had to edit /etc/X11/xorg.conf where I replaced "nv" by "nvidia". 
After reboot, during a split of a second I saw the nVidia  Logo and after that the X server started. 
I wonder how I could check which driver version I have installed now? 
Is there an upgrade possible for newer driver versions?

---

### Post by mahiyar on 2007-01-05
run nvidia-settings from the terminal if u do not have nvidia-setting shortcut from the system tab in the panel.

---

### Post by Cariboo1938 on 2007-01-06
> **mahiyar said:**
> run nvidia-settings from the terminal if u do not have nvidia-setting shortcut from the system tab in the panel.Cool, Thanks man...```
sudo nvidia-settings
```in terminal opens a lot of possibilities to adjust the Xserver settings... 

I found it, it's NVIDIA Driver Version 1.0-8776...

---

### Post by somar on 2007-01-09
pross,

I want to make sure I'm doing this correctly, so I will proceed cautiously and ask many questions.


QUOTE=pross;1965666]Right this is how i'd do it:
[You could choose to follow some or all of these notes]

1st reboot you PC and choose the default generic kernel, when its booted check in a console:
```

pross@pross-desktop:~$ uname -a
Linux pross-desktop 2.6.17-10-generic #2 SMP Tue Dec 5 21:16:35 UTC 2006 x86_64 GNU/Linux

```
[/QUOTE]

This is what my GRUB menu looks like:

```

Ubuntu, kernel 2.6.17-10-386
Ubuntu, kernel 2.6.17-10-386-(recovery mode)
Ubuntu, kernel 2.6.17-10-generic
Ubuntu, kernel 2.6.17-10-generic (recovery mode)
Ubuntu, memtest86+ 
```

When I start Ubuntu it defaults to generic mode. 

When I run this command from the console:

```
$ uname -a
```

I get this result:
```
 Linux svemir 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux
```

Is the above generic kernel correct? 

Your generic kernel reads differently:
```
 ... x86_64 GNU/Linux
```

Does it not matter which kernel it is as long as it is generic? The i686 is what throws me... since I have a dual Pentium III machine.

---

### Post by pross on 2007-01-09
yes thats the right one

---

### Post by somar on 2007-01-10
> 
now do apt-get update
then apt-get install nvidia-glx

all being good that should install the driver to the correct folder for the running kernel (generic)

I successfully followed your instructions up to the ```
apt-get install nvidia-glx
``` 
step

now I'm getting this error:

```
The following packages have unmet dependencies:
nvidia-glx: Depends: nvidia-kernel-1.0.9746
E: Borken packages

```

---

### Post by somar on 2007-01-12
pross

did you give up on me? :-|

---

