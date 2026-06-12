---
title: "Instruction for Install Ubuntu &amp; sons on PowerMac G5 Quad with Radeon HD"
date: 2015-04-21
forum: Apple Hardware Users
---

### Post by luigiburdo on 2015-04-21
Ok guys because many people ask me here and there and on youtube and on g+ the same info i make this thread .
Please read this instruction and do exactly the same thing.

This guide is for install Lubuntu, Ubuntu Mate 14.04 on Quad G5 with Apple Flashed GPU and RadeonHD (in couple)
This guide is not for other distro not for debian , gento or opensuse is only for Lubuntu and Mate for the 14.04.2 release
This is the video of Lubuntu run with RadeonHD performance and speed for your considerations! 
[https://www.youtube.com/watch?v=so35SrThHUs](https://www.youtube.com/watch?v=so35SrThHUs)  (if you like subscribe ;-) )

NOTE: i had been test only the:
 RadeonHD 4650 512mb DDr3 64bit (working) 
RadeonHD 5450 1GB DDr3 64bit (working) 
RadeonHD 6570 2GB DDr3 128bit (working) 

If you success with other cards please report!


This is the release link of lubuntu :

[http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/) 

this is the release link for Mate:

[https://ubuntu-mate.org/blog/ubuntu-mate-trusty-powerpc/](https://ubuntu-mate.org/blog/ubuntu-mate-trusty-powerpc/)


INSTRUCTIONS :

Download your prefer distro ... Mate or Lubuntu (PPC )
Burn the iso at lower Speed on a dvd and from the burner of your powermac G5
Run it form a cd pressing the "c" on keyboard when turn on your powermac.

you will have the yaboot screen and at promt write 

```

live video=offb:off video=radeonfb:off video=nouveaufb:off radeon.modeset=1 nouveau.modeset=0

```

you will have the video on radeonhd inizialized and see the desktop.

Make attention dont move the mouse on the border left or on the bottom of the screen because a strange bug on fbdev.

Click to install  ... start the installation ... end.... machine reset

when the machine turn on again at promt write :

```

Linux video=offb:off video=radeonfb:off video=nouveaufb:off radeon.modeset=1 nouveau.modeset=0
```

When the user credential will exit push fast (without insert the credential) on the keyboard .
"ctrl+alt+f1" and you will go in tty1

insert there your users id and password 
and there write

sudo apt-get install aptitude.

sudo /etc/init.d/lightdm stop

sudo aptitude remove xserver-xorg-video-fbdev.

after....

sudo nano /etc/yaboot.conf 

where the "append line" add exactly (ADD NOT SWAP or CHANGE ADD):

```

video=offb:off  radeon.modeset=1 nouveau.modeset=0

```

save with ctrl+o and exit

after... 

sudo ybin -v

and 

sudo reboot...


now your machine is full linux ppc funtional!


For have the 3D right working : 

You need to install the Xeno74 (Christian)  Mesa Patch for X1000 but work perfect On Quad G5 and read the readme with instruction inside the 
archive to install it !

Thankyou Christian for This!

[http://www.xenosoft.de/Xorg_and_unofficial_Mesa_for_ubuntu_MATE_15.04_AMIGA_one_X1000.tar.gz](http://www.xenosoft.de/Xorg_and_unofficial_Mesa_for_ubuntu_MATE_15.04_AMIGA_one_X1000.tar.gz)


I STRONG SUGGEST to install my optimized kernel 4.00-rc3 for G5 because better performance  with radeonhd and much stable compared with 
stock distro kernel
[URL="http://www.dropbox.com/sh/m8c9p3v99gsher3/AADP5l6UGWbroFrbXlqKBFyAa?dl=0"]
[/URL]
[https://www.dropbox.com/sh/m8c9p3v99gsher3/AADP5l6UGWbroFrbXlqKBFyAa?dl=0](https://www.dropbox.com/sh/m8c9p3v99gsher3/AADP5l6UGWbroFrbXlqKBFyAa?dl=0)


about video board setup
Use the Apple PPC flashed in Pcie 16x and the radeonhd on pcie 8x (usually the 3rd from the bottom)
you need 2 monitors or a monitor who have two video exit because one is for the apple flashed the other is for the radeonhd 
Is not possible have the video on the not flashed video board from beginning because open firmware access to the flashed bios video board 

ISSUES FIX 
For not have problems with the partitioner the best is have a blank hd attached as the primary master sata or ata

Dont forget to make a 100mb NewWorld partition and the Swap partition the good of swap partition will be half of your Ram eg: 8gb ram 4gb swap, 4gb Ram 2gb swap etc etc


bye 
Luigi

---

### Post by rican-linux on 2015-04-21
Thanks Luigi!

---

### Post by luigiburdo on 2015-04-21
> **rican-linux said:**
> Thanks Luigi!

No prob my friend :)

---

### Post by cg-reklame on 2015-04-21
Thanks! I'm a newbie to this, so if I may ask you a follow up question? When is this "When the user credential will exit push fast (without insert the credential) on the keyboard .
"ctrl+alt+f1" and you will go in tty1". Just after hiting enter at the boot prompt, or after the login picture? I've installet Ubuntu Mate 14.04 on a PowerBook G4, but it freezes when I try to open Firefox or a terminal session. Is there a YouTube video I can watch?

Cheers, Cato

---

### Post by luigiburdo on 2015-04-21
Cato.
On powerbook g4 is different with G5
You need to put ONLY the line the other instuction is only on G5 with RadeonHD
```

Linux video=offb:off video=radeonfb:off video=nouveaufb:off radeon.modeset=1 radeon.agpmode=-1 

```

---

### Post by cg-reklame on 2015-04-21
Thanks Luigi!
I was looking for a way to make it a permanent setting so that I don't have to write it everytime I reboot. Any leads?
Also, is it safe to update the Ubuntu install, or will I get packages that break my system?

Cato

---

### Post by luigiburdo on 2015-04-21
> **cg-reklame said:**
> Thanks Luigi!
I was looking for a way to make it a permanent setting so that I don't have to write it everytime I reboot. Any leads?
Also, is it safe to update the Ubuntu install, or will I get packages that break my system?

Cato

Nope cato just edit your yaboot.conf adding where append is with :

```
[COLOR=#000000][FONT=Ubuntu Mono]"video=offb:off video=radeonfb:off video=nouveaufb:off radeon.modeset=1 radeon.agpmode=-1"[/FONT][/COLOR]
```

be sure you dont make wrong nothing there or you will be not more able too boot in linux

after editing 

do :

sudo ybin -v

and reboot

---

### Post by cg-reklame on 2015-04-21
Thanks again, Luigi!
One final question, if I may; how do I go about to get my wifi working? I found this command "sudo apt-get install b43-firmware-installer" but it doesn't work. Any ideas?

---

### Post by luigiburdo on 2015-04-21
i found only this about  google help too much :P
sudo apt-get install firmware-b43legacy-installer

---

### Post by Jos_Antonio_agro on 2015-04-21
Hello Luigi, congrats for the post, great idea.

I´ve tried with Ubuntu Mate, i can´t start with live parameters, it gets stucked on white scrren. after kernel and ramdisk.
Then i´ve tried with live (no parameters), it show desktop, then start installation, let me choose language and then mouse pointer gets freeze and then i have to reboot.

Going to try Lubuntu.

---

### Post by luigiburdo on 2015-04-21
White screen? is normal when white screen exit you have to switch on the radeonhd monitor.
check here [https://www.youtube.com/watch?v=NyShy_ey7Ds](https://www.youtube.com/watch?v=NyShy_ey7Ds)

The mouse pointer freeze or disappear ? if disappear it is the fbdev bug i described in the beginning in the tutorial how to avoid it

---

### Post by Jos_Antonio_agro on 2015-04-21
Hello, i´ve tried with Lubuntu 14 and the same result.

Kernel loaded
Ramdisk loaded

found display
copying of device tree
building drt strings

and then, nothing............

---

### Post by luigiburdo on 2015-04-21
but you write exactly the lines i wrote before in yaboot screen ?

```

[COLOR=#000000][FONT=Ubuntu Mono]live video=offb:off video=radeonfb:off video=nouveaufb:off radeon.modeset=1 nouveau.modeset=0[/FONT][/COLOR]

```

---

### Post by Jos_Antonio_agro on 2015-04-22
Yes my friend, exactly. i will take a piture for you to see

---

### Post by luigiburdo on 2015-04-22
but you have insert the radeon on 8x slot? and the Nvidia in the 16x? ...
can you test without the offb: off option?
can you please write here how is your HD setup?

---

### Post by Jos_Antonio_agro on 2015-04-24
NEWSSSSs¡¡¡ (with lubuntu 14.04 PowerMAC G5)

Luigi, radeon is on 8x slot and Nvidia in the 16x

If i try:

[B][COLOR=#ff0000]
[/COLOR][/B]```
**[COLOR=#ff0000]live video=offb:off video=radeonfb:off video=nouveaufb:off radeon.modeset=1 nouveau.modeset=0[/COLOR]**
```

then, i can not get desktop, it freezes.

But, if i try 

```
[COLOR=#008000]**live  video=radeonfb:off video=nouveaufb:off radeon.modeset=1 nouveau.modeset=0 (without video=offb:off)**[/COLOR]
```

I HAVE RADEONHD video, i can see the desktop ok, but 1 problem, i can only see desktop icons, but no characters....................

RADEONHD finally working¡¡¡¡¡¡¡¡¡ How can i fix characters problem?

---

### Post by luigiburdo on 2015-04-24
umm ... it is the Raden Fb bug  strange you are facing it in lubuntu 14.0.4. 2 and more strange the machine boot without video=offb: off ... 
how to fix ? ... switch on the console and disinstall the xserver-xorg-video-radeon  but first you need to install aptitude . after close lightdm and start it again you will run in fbdev mode make the installation and do again the procedure after you will need to install the mesa patch of Xeno74 and re install the radeon

---

### Post by Jos_Antonio_agro on 2015-04-24
Hi Luigi, i´ve tried to install after booting only with "live".
Desktop initiates well on Nvidia, and then i start installation procedure (odd mouse behavior), all goes well until "Hardware detection" then installation freezes.

Going to take off RADEONHD and try again.

---

### Post by luigiburdo on 2015-04-25
Jos , o dont think the installation freeze because the radeonhd , i think is more relative to the hd detection ....it is really strange what you are facing.... for sure the not opportunity to turn off the open firmware detection make me really courious about .

---

### Post by xeno74 on 2015-04-25
> **Jos_Antonio_agro said:**
> 

I HAVE RADEONHD video, i can see the desktop ok, but 1 problem, i can only see desktop icons, but no characters....................

RADEONHD finally working¡¡¡¡¡¡¡¡¡ How can i fix characters problem?

I had also the problem that the fonts were not displayed. The solution is to set the option "RenderAccel" to "false" in the xorg.conf file.

[Lubuntu 14.04 PowerPC - forum.hyperion-entertainment.biz]("http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=2176")

---

### Post by Jos_Antonio_agro on 2015-04-27
Hello, i will try again a new installation.

Right now i have:

1. MACOS X 10.5.8
2. Debian 7.8 Wheezy ( i can install this without problems, and it is working right, that´s the reason i don´t understand problems i´m facing with Lubuntu or Mate, maybe kernel?)

I´m going to delete debian partition, make new partition for lubuntu and try again. I can´t change xorg.conf because is a live version, i need to install first.

---

### Post by luigiburdo on 2015-04-28
My hope will be you will have success my friend

---

### Post by Jos_Antonio_agro on 2015-05-01
Hello, no luck with lubuntu.
I have also tried Jessie Stable Version, everything goes well during installation, but when i reboot, i only get a black screen (with radeon) or a mess of colors freeze with nvidia. I can acess tty1 in comand line. Something to do with graphical drivers.
Any ideas?

---

### Post by luigiburdo on 2015-05-01
With Debian not Radeon or better you can use radeon in resterized mode only with wheezy.

Jessie have bug with Xorg it crash and is not usable on Nvidia because glitched graphic and wrong colors.

---

### Post by Jos_Antonio_agro on 2015-05-01
Back to Wheezy then.
I´m going to buy a mac mini (intel based) to install windows (bootcamp).........works well? or goes slowly?

---

### Post by luigiburdo on 2015-05-01
> **Jos_Antonio_agro said:**
> Back to Wheezy then.
I´m going to buy a mac mini (intel based) to install windows (bootcamp).........works well? or goes slowly?

This was my macmini 2011 i5 upgraded with SSD . Windows was running on parallel ... on bootcamp is much faster :)


[https://www.youtube.com/watch?v=LLp2nJYrI8Q](https://www.youtube.com/watch?v=LLp2nJYrI8Q)

---

### Post by Jos_Antonio_agro on 2015-05-01
wowwwwwwwwwwwwwwwwwww. I´m loving it
How many macs do you have?

---

### Post by luigiburdo on 2015-05-01
Now only the Quad and the MacBook pro retina i7 ... sold the mini i5 and the Mini G4
I had the Imac i7 27 , 5 mini g4 and 3 mini i5 ... in past.
the best continue be my wonderful Quad :)

---

### Post by miklos3 on 2015-05-03
Hi Luigi,

I install Linux to my Quad. Install was easy and quick, but have a little problem. After restart:

First stage Linux bootsrap

Press "L" for GNU/Linux
        "C" for CDROM

Stage 1 boot:

Loading second stage bootstrap...


But nothing happened. Just mac smile icon and "?" (I just used the guided partition on the linux install and selected the entire disk /Intel 320 SSD/)[FONT=Verdana, Arial, Helvetica, sans-serif][COLOR=#000000].[/COLOR][/FONT]

---

### Post by luigiburdo on 2015-05-03
Umm do you make the newworld partition ?

---

### Post by miklos3 on 2015-05-03
hmmm i d know :-) but same prob like this (mate, lubuntu, debian don't want to boot) [http://forums.debian.net/viewtopic.php?f=17&t=51280](http://forums.debian.net/viewtopic.php?f=17&t=51280)

---

### Post by luigiburdo on 2015-05-03
Make a small partition NewWorld 10mb or 100mb (is not necessary have a big one) a Swap as the half of your Ram and the / partition.
Remeber the Hd with linux have to be the first one on the top of the g5 (A) :)

---

### Post by miklos3 on 2015-05-04
ok, all good now :-)
how to fix a good resolution on my samsung (1920/1080) display with 6600LE? Just a simple codes my friend if possible. :-)

---

### Post by luigiburdo on 2015-05-05
umm ... it will be by defoult at 1080p x 32

---

### Post by miklos3 on 2015-05-05
:-) I do not activate the radeon card, first I want to see Lubuntu, Mate and Debian, a little test U know, but my desktop know only 1024x768, but not to all my display, just half, maybe bc no good nvidia driver... my monitor 24" samsung 16:9, I need a little bit better resolution, but stable :-)

---

### Post by franklynb on 2015-05-06
Hi Luigi

I also have a quad G5 PPC. I've been running 12.04 for some time now. My G5 has an NVIDIA GeForce 6600.
I've been able to 'live' boot 15.04 MATE using the following boot variation on your instructions:

[HTML]boot: live video=radeonfb:off video=nouveaufb:off nouveau.modeset=0 video=fbdev:1920x1080[/HTML]

The color map is wrong for some reason. I am able to 

$ setterm -background yellow

in a MATE terminal and have the color correct. "foreground" colors are always wrong regardless of setting.

I will probably still stick with 12.04 since I use this quad as an audio workstation. It took quite a bit of work to sort out
FFADO and JACK; and I do not hold out hope that the new ALSA audio will be ported to PPC. But I thought having a
boot sequence for NVIDIA that uses nouveau/fbdev/kms might provide further hints and aid your progress.

[Note: KMS appears to unload since DRM isn't loading. I think.]

Here's my Xorg.0.log:

[INDENT][    75.461] 
X.Org X Server 1.17.1
Release Date: 2015-02-10
[    75.461] X Protocol Version 11, Revision 0
[    75.461] Build Operating System: Linux 3.2.0-76-powerpc64-smp ppc Ubuntu
[    75.461] Current Operating System: Linux ubuntu-mate 3.19.0-15-powerpc64-smp #15-Ubuntu SMP Thu Apr 16 23:51:08 UTC 2015 ppc64
[    75.461] Kernel command line: ro ramdisk_size=1048576 file=/cdrom/preseed/ubuntu-mate.seed boot=casper quiet splash --- video=radeonfb:off video=nouveaufb:off nouveau.modeset=0 video=fbdev:1920x1080@67.5
[    75.461] Build Date: 19 March 2015  09:29:38AM
[    75.461] xorg-server 2:1.17.1-0ubuntu3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    75.461] Current version of pixman: 0.32.6
[    75.461] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    75.461] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    75.461] (==) Log file: "/var/log/Xorg.0.log", Time: Thu May  7 01:23:03 2015
[    75.463] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    75.622] (==) No Layout section.  Using the first Screen section.
[    75.622] (==) No screen section available. Using defaults.
[    75.622] (**) |-->Screen "Default Screen Section" (0)
[    75.622] (**) |   |-->Monitor "<default monitor>"
[    75.622] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    75.623] (==) Automatically adding devices
[    75.623] (==) Automatically enabling devices
[    75.623] (==) Automatically adding GPU devices
[    76.029] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    76.029] 	Entry deleted from font path.
[    76.029] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    76.029] 	Entry deleted from font path.
[    76.029] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    76.029] 	Entry deleted from font path.
[    76.152] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    76.152] 	Entry deleted from font path.
[    76.152] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    76.152] 	Entry deleted from font path.
[    76.152] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    76.152] (==) ModulePath set to "/usr/lib/powerpc-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    76.152] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    76.152] (II) Loader magic: 0xf8000688
[    76.152] (II) Module ABI versions:
[    76.152] 	X.Org ANSI C Emulation: 0.4
[    76.152] 	X.Org Video Driver: 19.0
[    76.152] 	X.Org XInput driver : 21.0
[    76.152] 	X.Org Server Extension : 9.0
[    76.156] (--) PCI:*(0:10:0:0) 10de:0141:10de:0010 rev 162, Mem @ 0xa1000000/16777216, 0x90000000/268435456, 0xa0000000/16777216, BIOS @ 0x????????/131072
[    76.156] (II) LoadModule: "glx"
[    76.160] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    76.711] (II) Module glx: vendor="X.Org Foundation"
[    76.712] 	compiled for 1.17.1, module version = 1.0.0
[    76.712] 	ABI class: X.Org Server Extension, version 9.0
[    76.715] (==) AIGLX enabled
[    76.716] (==) Matched nvidia as autoconfigured driver 0
[    76.716] (==) Matched nouveau as autoconfigured driver 1
[    76.716] (==) Matched modesetting as autoconfigured driver 2
[    76.716] (==) Matched fbdev as autoconfigured driver 3
[    76.716] (==) Assigned the driver to the xf86ConfigLayout
[    76.716] (II) LoadModule: "nvidia"
[    76.718] (WW) Warning, couldn't open module nvidia
[    76.718] (II) UnloadModule: "nvidia"
[    76.718] (II) Unloading nvidia
[    76.718] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    76.718] (II) LoadModule: "nouveau"
[    76.718] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    76.914] (II) Module nouveau: vendor="X.Org Foundation"
[    76.914] 	compiled for 1.17.1, module version = 1.0.11
[    76.914] 	Module class: X.Org Video Driver
[    76.914] 	ABI class: X.Org Video Driver, version 19.0
[    76.914] (II) LoadModule: "modesetting"
[    76.914] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    76.992] (II) Module modesetting: vendor="X.Org Foundation"
[    76.992] 	compiled for 1.17.1, module version = 1.17.1
[    76.992] 	Module class: X.Org Video Driver
[    76.992] 	ABI class: X.Org Video Driver, version 19.0
[    76.993] (II) LoadModule: "fbdev"
[    76.993] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    77.025] (II) Module fbdev: vendor="X.Org Foundation"
[    77.025] 	compiled for 1.17.1, module version = 0.4.4
[    77.025] 	Module class: X.Org Video Driver
[    77.025] 	ABI class: X.Org Video Driver, version 19.0
[    77.026] (==) Matched nvidia as autoconfigured driver 0
[    77.026] (==) Matched nouveau as autoconfigured driver 1
[    77.026] (==) Matched modesetting as autoconfigured driver 2
[    77.026] (==) Matched fbdev as autoconfigured driver 3
[    77.026] (==) Assigned the driver to the xf86ConfigLayout
[    77.026] (II) LoadModule: "nvidia"
[    77.027] (WW) Warning, couldn't open module nvidia
[    77.027] (II) UnloadModule: "nvidia"
[    77.027] (II) Unloading nvidia
[    77.027] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    77.027] (II) LoadModule: "nouveau"
[    77.027] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    77.027] (II) Module nouveau: vendor="X.Org Foundation"
[    77.027] 	compiled for 1.17.1, module version = 1.0.11
[    77.027] 	Module class: X.Org Video Driver
[    77.027] 	ABI class: X.Org Video Driver, version 19.0
[    77.027] (II) UnloadModule: "nouveau"
[    77.027] (II) Unloading nouveau
[    77.027] (II) Failed to load module "nouveau" (already loaded, 0)
[    77.027] (II) LoadModule: "modesetting"
[    77.028] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    77.028] (II) Module modesetting: vendor="X.Org Foundation"
[    77.028] 	compiled for 1.17.1, module version = 1.17.1
[    77.028] 	Module class: X.Org Video Driver
[    77.028] 	ABI class: X.Org Video Driver, version 19.0
[    77.028] (II) UnloadModule: "modesetting"
[    77.028] (II) Unloading modesetting
[    77.028] (II) Failed to load module "modesetting" (already loaded, 0)
[    77.028] (II) LoadModule: "fbdev"
[    77.029] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    77.029] (II) Module fbdev: vendor="X.Org Foundation"
[    77.029] 	compiled for 1.17.1, module version = 0.4.4
[    77.029] 	Module class: X.Org Video Driver
[    77.029] 	ABI class: X.Org Video Driver, version 19.0
[    77.029] (II) UnloadModule: "fbdev"
[    77.029] (II) Unloading fbdev
[    77.029] (II) Failed to load module "fbdev" (already loaded, 0)
[    77.029] (II) NOUVEAU driver Date:   Thu Aug 28 03:57:48 2014 +0200
[    77.029] (II) NOUVEAU driver for NVIDIA chipset families :
[    77.029] 	RIVA TNT        (NV04)
[    77.029] 	RIVA TNT2       (NV05)
[    77.029] 	GeForce 256     (NV10)
[    77.029] 	GeForce 2       (NV11, NV15)
[    77.029] 	GeForce 4MX     (NV17, NV18)
[    77.029] 	GeForce 3       (NV20)
[    77.029] 	GeForce 4Ti     (NV25, NV28)
[    77.029] 	GeForce FX      (NV3x)
[    77.029] 	GeForce 6       (NV4x)
[    77.029] 	GeForce 7       (G7x)
[    77.029] 	GeForce 8       (G8x)
[    77.029] 	GeForce GTX 200 (NVA0)
[    77.029] 	GeForce GTX 400 (NVC0)
[    77.029] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    77.029] (II) FBDEV: driver for framebuffer: fbdev
[    77.029] (++) using VT number 7

[    77.071] (EE) [drm] KMS not enabled
[    77.071] (EE) [drm] KMS not enabled
[    77.071] (EE) open /dev/dri/card0: No such file or directory
[    77.071] (EE) open /dev/dri/card0: No such file or directory
[    77.071] (WW) Falling back to old probe method for modesetting
[    77.071] (EE) open /dev/dri/card0: No such file or directory
[    77.071] (EE) open /dev/dri/card0: No such file or directory
[    77.071] (II) Loading sub module "fbdevhw"
[    77.071] (II) LoadModule: "fbdevhw"
[    77.072] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    77.072] (II) Module fbdevhw: vendor="X.Org Foundation"
[    77.073] 	compiled for 1.17.1, module version = 0.0.2
[    77.073] 	ABI class: X.Org Video Driver, version 19.0
[    77.073] (**) FBDEV(2): claimed PCI slot 10@0:0:0
[    77.073] (II) FBDEV(2): using default device
[    77.073] (EE) Screen 0 deleted because of no matching config section.
[    77.073] (II) UnloadModule: "modesetting"
[    77.073] (EE) Screen 0 deleted because of no matching config section.
[    77.073] (II) UnloadModule: "modesetting"
[    77.073] (II) FBDEV(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 8/8
[    77.073] (==) FBDEV(0): Depth 8, (==) framebuffer bpp 8
[    77.073] (==) FBDEV(0): Default visual is PseudoColor
[    77.073] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    77.073] (II) FBDEV(0): hardware: OFfb NVDA,Displ (video memory: 2160kB)
[    77.073] (II) FBDEV(0): checking modes against framebuffer device...
[    77.073] (II) FBDEV(0): checking modes against monitor...
[    77.073] (--) FBDEV(0): Virtual size is 1920x1080 (pitch 1920)
[    77.073] (**) FBDEV(0):  Built-in mode "current": 100.0 MHz, 51.0 kHz, 45.6 Hz
[    77.073] (II) FBDEV(0): Modeline "current"x0.0  100.00  1920 1936 1944 1960  1080 1096 1104 1120 -hsync -vsync -csync (51.0 kHz b)
[    77.073] (==) FBDEV(0): DPI set to (96, 96)
[    77.073] (II) Loading sub module "fb"
[    77.073] (II) LoadModule: "fb"
[    77.073] (II) Loading /usr/lib/xorg/modules/libfb.so
[    77.076] (II) Module fb: vendor="X.Org Foundation"
[    77.076] 	compiled for 1.17.1, module version = 1.0.0
[    77.076] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    77.076] (**) FBDEV(0): using shadow framebuffer
[    77.076] (II) Loading sub module "shadow"
[    77.076] (II) LoadModule: "shadow"
[    77.076] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    77.077] (II) Module shadow: vendor="X.Org Foundation"
[    77.077] 	compiled for 1.17.1, module version = 1.1.0
[    77.077] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    77.180] (==) FBDEV(0): Backing store enabled
[    77.181] (==) FBDEV(0): DPMS enabled
[    77.181] (==) RandR enabled
[    77.418] (II) SELinux: Disabled on system
[    77.420] (II) AIGLX: Screen 0 is not DRI2 capable
[    77.420] (EE) AIGLX: reverting to software rendering
[    78.268] (II) AIGLX: Loaded and initialized swrast
[    78.268] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    78.621] (II) XKB: generating xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    79.321] (II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event0)
[    79.321] (**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    79.322] (**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "keyboard defaults"
[    79.322] (II) LoadModule: "evdev"
[    79.322] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    79.418] (II) Module evdev: vendor="X.Org Foundation"
[    79.418] 	compiled for 1.16.0, module version = 2.9.0
[    79.418] 	Module class: X.Org XInput Driver
[    79.418] 	ABI class: X.Org XInput driver, version 21.0
[    79.418] (II) Using input driver 'evdev' for 'Mitsumi Electric Apple Extended USB Keyboard'
[    79.418] (**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
[    79.418] (**) evdev: Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event0"
[    79.418] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Vendor 0x5ac Product 0x204
[    79.418] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Found keys
[    79.418] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
[    79.418] (**) Option "config_info" "udev:/sys/devices/pci0001:00/0001:00:08.0/0001:01:0b.0/usb2/2-2/2-2.1/2-2.1:1.0/0003:05AC:0204.0001/input/input0/event0"
[    79.418] (II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD, id 6)
[    79.418] (**) Option "xkb_rules" "evdev"
[    79.418] (**) Option "xkb_model" "pc105"
[    79.418] (**) Option "xkb_layout" "us"
[    79.418] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[    79.430] (II) XKB: generating xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[    79.468] (II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event1)
[    79.468] (**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    79.468] (**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "keyboard defaults"
[    79.468] (II) Using input driver 'evdev' for 'Mitsumi Electric Apple Extended USB Keyboard'
[    79.468] (**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
[    79.468] (**) evdev: Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event1"
[    79.468] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Vendor 0x5ac Product 0x204
[    79.468] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Found keys
[    79.468] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
[    79.468] (**) Option "config_info" "udev:/sys/devices/pci0001:00/0001:00:08.0/0001:01:0b.0/usb2/2-2/2-2.1/2-2.1:1.1/0003:05AC:0204.0002/input/input1/event1"
[    79.468] (II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD, id 7)
[    79.468] (**) Option "xkb_rules" "evdev"
[    79.468] (**) Option "xkb_model" "pc105"
[    79.468] (**) Option "xkb_layout" "us"
[    79.468] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[    79.469] (II) config/udev: Adding input device Fujitsu Takamisawa Component Apple Optical USB Mouse (/dev/input/event2)
[    79.469] (**) Fujitsu Takamisawa Component Apple Optical USB Mouse: Applying InputClass "evdev pointer catchall"
[    79.469] (II) Using input driver 'evdev' for 'Fujitsu Takamisawa Component Apple Optical USB Mouse'
[    79.469] (**) Fujitsu Takamisawa Component Apple Optical USB Mouse: always reports core events
[    79.469] (**) evdev: Fujitsu Takamisawa Component Apple Optical USB Mouse: Device: "/dev/input/event2"
[    79.524] (--) evdev: Fujitsu Takamisawa Component Apple Optical USB Mouse: Vendor 0x5ac Product 0x302
[    79.524] (--) evdev: Fujitsu Takamisawa Component Apple Optical USB Mouse: Found 1 mouse buttons
[    79.524] (--) evdev: Fujitsu Takamisawa Component Apple Optical USB Mouse: Found relative axes
[    79.524] (--) evdev: Fujitsu Takamisawa Component Apple Optical USB Mouse: Found x and y relative axes
[    79.524] (II) evdev: Fujitsu Takamisawa Component Apple Optical USB Mouse: Configuring as mouse
[    79.524] (**) evdev: Fujitsu Takamisawa Component Apple Optical USB Mouse: YAxisMapping: buttons 4 and 5
[    79.524] (**) evdev: Fujitsu Takamisawa Component Apple Optical USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    79.524] (**) Option "config_info" "udev:/sys/devices/pci0001:00/0001:00:08.0/0001:01:0b.0/usb2/2-2/2-2.2/2-2.2:1.0/0003:05AC:0302.0003/input/input2/event2"
[    79.524] (II) XINPUT: Adding extended input device "Fujitsu Takamisawa Component Apple Optical USB Mouse" (type: MOUSE, id 8)
[    79.524] (II) evdev: Fujitsu Takamisawa Component Apple Optical USB Mouse: initialized for relative axes.
[    79.525] (**) Fujitsu Takamisawa Component Apple Optical USB Mouse: (accel) keeping acceleration scheme 1
[    79.525] (**) Fujitsu Takamisawa Component Apple Optical USB Mouse: (accel) acceleration profile 0
[    79.525] (**) Fujitsu Takamisawa Component Apple Optical USB Mouse: (accel) acceleration factor: 2.000
[    79.525] (**) Fujitsu Takamisawa Component Apple Optical USB Mouse: (accel) acceleration threshold: 4
[    79.526] (II) config/udev: Adding input device Fujitsu Takamisawa Component Apple Optical USB Mouse (/dev/input/mouse0)
[    79.526] (II) No input driver specified, ignoring this device.
[    79.526] (II) This device may have been added with another device file.[/INDENT]

---

### Post by luigiburdo on 2015-05-07
It means you meke it working on nvidia with Fbdev... softresterized interesting will try with RadeonHD

---

### Post by franklynb on 2015-05-08
> **luigiburdo said:**
> It means you meke it working on nvidia with Fbdev... softresterized interesting will try with RadeonHD

Yes, it does render in software. The fonts are not very crisp. This might be why the color map is wrong. But at least it boots. I can do some other
profiling in terminal if that is helpful. I still do not have a console but --might-- be able to get ssh working.

--frankb

---

### Post by luigiburdo on 2015-05-08
Thankyou frank im starting making some tests on my machine too . and ll report

---

### Post by luigiburdo on 2015-05-08
Here, nothing to do ...totally glitched colors and gfx on my 7800gtx or Xorg crash on RadeonHD ...
For my configuration Mate 15.04 continue be unusable.

---

### Post by Artemis3 on 2015-05-11
> **luigiburdo said:**
> Cato.
On powerbook g4 is different with G5
You need to put ONLY the line the other instuction is only on G5 with RadeonHD
```

Linux video=offb:off video=radeonfb:off video=nouveaufb:off radeon.modeset=1 radeon.agpmode=-1 

```

Thanks Luigi, i just did this on a Powerbook G4 using 14.04 and it worked :)
(fbdev was doing 8 bit but lightdm doesn't work at all in that mode).

And now the audio...

---

### Post by chdrsto on 2015-05-20
Hi Luigi
I followed your guide, unfortunately no 3D Acc is running. X is up and running, but no Acceleration.
Ive also copied the files according to the Mesa instruction you've posted (from the Readme file)

Hardware is exactly the same as you're running: PM G5 Quad, GT6600 (Apple original) on 16x PCIe (first),  ATI Radeon HD 6570 (2048 MB) on the second (8x) slot
Lubuntu 14.04.2 LTS version

when I start glxgears i get following error:

chdrsto@PowerMac:~/Downloads$ vblank_mode=0 glxgears
glxgears: symbol lookup error: /usr/lib/powerpc-linux-gnu/mesa/libGL.so.1: undefined symbol: _glapi_Dispatch

---

### Post by luigiburdo on 2015-05-21
hi my friend. 
try with with instruction and run glxgears .
let me know.  
If you find some errors in coping the files let me know 


The installation is very simple.

Unofficial Mesa packages downloads: [http://www.supertuxkart-amiga.de/ami...nofficial.html]("http://www.supertuxkart-amiga.de/amiga/mesalib-unofficial.html")

_**Install instructions for example for Mesa 10.0.3 unofficial**_: 



[LIST=1]
[*] Unpack the archive MesaLib-10.0.3-powerpc-unofficial.tar.bz2
[*] Copy it as root to the directory **/usr/local/** -> sudo cp -R mesa10 /usr/local/
[*]Set up the new library path -> export LD_LIBRARY_PATH=/usr/local/mesa10/lib
[*]Test it with **glxgears**. When you see the correct colors then you use the new version of Mesa. After that you can start some games for example **Neverball**.
[/LIST]


If you want that Mesa works system wide then you have to add the line **export LD_LIBRARY_PATH=** to the **.profile** file in your home directory.

SuperTuxKart needs a special **run_game.sh** for the new Mesa: LD_LIBRARY_PATH=./bin/:/usr/local/mesa10/lib bin/supertuxkart

Another thread: [http://forum.hyperion-entertainment....hp?f=35&t=2359]("http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=2359")

---

### Post by chdrsto on 2015-05-21
Hi Luigi

I've followed your instructions without success.
I get following error message when I try to start glxgears:

chdrsto@PowerMac:~$  LIBGL_DEBUG=verbose glxgears
libGL: OpenDriver: trying /usr/local/mesa10/lib/dri/r600_dri.so
libGL: driver does not expose __driDriverGetExtensions_r600(): /usr/local/mesa10/lib/dri/r600_dri.so: undefined symbol: __driDriverGetExtensions_r600
libGL: Can't open configuration file /home/chdrsto/.drirc: No such file or directory.
libGL: Can't open configuration file /home/chdrsto/.drirc: No such file or directory.
libGL error: failed to load driver: r600
libGL: OpenDriver: trying /usr/local/mesa10/lib/dri/swrast_dri.so
libGL: driver does not expose __driDriverGetExtensions_swrast(): /usr/local/mesa10/lib/dri/swrast_dri.so: undefined symbol: __driDriverGetExtensions_swrast
libGL: Can't open configuration file /home/chdrsto/.drirc: No such file or directory.
libGL: Can't open configuration file /home/chdrsto/.drirc: No such file or directory.
libGL error: failed to load driver: swrast
Error: couldn't get an RGB, Double-buffered visual

---

### Post by luigiburdo on 2015-05-21
Umm... something goes wrong during the installation of the patched mesa, reinstall it but 
use this Xeno74 version [MesaLib-1.0.0.4-Lubuntu_14.10-powerpc-test.tar.bz2]("http://www.xenosoft.de/MesaLib-1.0.0.4-Lubuntu_14.10-powerpc-test.tar.bz2") and follow the instruction in the read me of the X1000 mesa that you had already installed


ah during the copy of the files there is a issue in one file name ... just the name is upper char and in the instruction is lower char.. if i remember good.

Let me know

---

### Post by chdrsto on 2015-05-21
What I've tried so far, without success.

Followed these two Instructions:

1. Extract MesaLib-10.0.4-powerpc-unofficial.tar.bz2
2. Rename the original r600_dri.so to r600_dri.so.bak: sudo mv /usr/lib/powerpc-linux-gnu/dri/r600_dri.so /usr/lib/powerpc-linux-gnu/dri/r600_dri.so.bak
3. Copy the patched r600_dri.so to /usr/lib/powerpc-linux-gnu/dri: sudo cp mesa-10.0.4/lib/dri/r600_dri.so /usr/lib/powerpc-linux-gnu/dri
4. Rename the original LibGL.so.1.2.0 to LibGL.so.1.2.0.bak: sudo mv /usr/lib/powerpc-linux-gnu/mesa/libGL.so.1.2.0 /usr/lib/powerpc-linux-gnu/mesa/libGL.so.1.2.0.bak
5. Copy the patched LibGL.so.1.2.0 to /usr/lib/powerpc-linux-gnu/mesa: sudo cp mesa-10.0.4/lib/libGL.so.1.2.0 /usr/lib/powerpc-linux-gnu/mesa
6. You can test it with glxgears: vblank_mode=0 glxgears

ERROR:
glxgears: symbol lookup error: /usr/lib/powerpc-linux-gnu/mesa/libGL.so.1: undefined symbol: _glapi_Dispatch


and :

1. Copy the whole folder as root to the directory **/usr/local/** -> sudo cp -R mesa10 /usr/local/
2. Set up the new library path -> export LD_LIBRARY_PATH=/usr/local/mesa10/lib

ERROR:
chdrsto@PowerMac:~$  LIBGL_DEBUG=verbose glxgears
libGL: OpenDriver: trying /usr/local/mesa10/lib/dri/r600_dri.so
libGL: driver does not expose __driDriverGetExtensions_r600():  /usr/local/mesa10/lib/dri/r600_dri.so: undefined symbol:  __driDriverGetExtensions_r600
libGL: Can't open configuration file /home/chdrsto/.drirc: No such file or directory.
libGL: Can't open configuration file /home/chdrsto/.drirc: No such file or directory.
libGL error: failed to load driver: r600
libGL: OpenDriver: trying /usr/local/mesa10/lib/dri/swrast_dri.so
libGL: driver does not expose __driDriverGetExtensions_swrast():  /usr/local/mesa10/lib/dri/swrast_dri.so: undefined symbol:  __driDriverGetExtensions_swrast
libGL: Can't open configuration file /home/chdrsto/.drirc: No such file or directory.
libGL: Can't open configuration file /home/chdrsto/.drirc: No such file or directory.
libGL error: failed to load driver: swrast
Error: couldn't get an RGB, Double-buffered visual

---

### Post by xeno74 on 2015-05-22
> **chdrsto said:**
> 
ERROR:
glxgears: symbol lookup error: /usr/lib/powerpc-linux-gnu/mesa/libGL.so.1: undefined symbol: _glapi_Dispatch


libGL.so.1 should be a link to libGL.so.1.2.0. Could you check it, please?

```

lrwxrwxrwx 1 root root     14 Mar 30 08:10 libGL.so.1 -> libGL.so.1.2.0

```

---

### Post by chdrsto on 2015-05-22
Hi guys.

Its weird, but it workes somehow.
I didnt change anyting just booted the system today and got 3D acc. Thanks to you all.
[B]
@Luigi[/B]
Is it possible to run it without having a screen on card 1 connected? I have two screens on the card 2 (radeon) and one on card 1 (apple) just to be able to boot the system ... I guess I've read somewhere a how to about setting up apples open firmware to disable the video check during boot precedure.
Second ... do you know if a R7 260X will work with the same setup? I'm planning to buy one, but I'm actually not sure if it will work. Any advice is appreciated.

---

### Post by luigiburdo on 2015-05-22
About Point one, one guy here write about the openfirmware not checking commands and was in one of the last ppc threads but i dont remember the thread ... im really sorry about . try to make a search probably you will be lucky ;-)
About Point two... it can work,it is in the kernel supported video boards list but im not sure about and if the Xeno patch will work there too. if you have one available there in your home lets make a test. If you have to buy it ... i can suggest you dont do it since the ppc issue with xorg and new distro will be fixed. 
Another suggestion: the 6570 is a good gpu for run the available ppc software enjoy it . for upgrade you have time :-p

---

### Post by chdrsto on 2015-05-22
Hi Luigi

Thanks for the advice.
Just to let you know ... I've found the thread about running Linux on G5 without having a useless monitor on Card 1. >> [CLICK ME]("http://askubuntu.com/questions/266333/how-to-boot-without-monitor-with-12-04-on-a-powerpc-yaboot") <<

Shortly :
You have to boot into openfirmware (boot and press ALT+CMD+O+F) and run the comand ***setenv boot-device hd:X,yaboot*** (with X = number of the yaboot partition, in my case 3)
After you have to enter ***boot*** and hit enter

Than you can remove the Monitor from the card and boot into X.

---

### Post by luigiburdo on 2015-05-23
Perfect , when you have spare time check if finally we will have MAte 15.x run on G5 ;-)

---

### Post by chdrsto on 2015-05-23
Sure, but at the moment I'm still trying to get the tripple Monitor configuration up and running. Compiz is already up and running with wobbling windows. :-D

---

### Post by rican-linux on 2015-05-25
I followed your instructions for my iBook G4 I see it using the patch mesa files for r300 however I am getting this as well.

```
rican-linux@iBookG4-Debian9:~$ LIBGL_DEBUG=verbose glxinfo |grep render
libGL: OpenDriver: trying /usr/local/mesa-10.0.4/lib/dri/r300_dri.so
libGL: driver does not expose __driDriverGetExtensions_r300(): /usr/local/mesa-10.0.4/lib/dri/r300_dri.so: undefined symbol: __driDriverGetExtensions_r300
direct rendering: Yes
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
OpenGL renderer string: Gallium 0.4 on ATI RV350
    GL_NV_blend_square, GL_NV_conditional_render, GL_NV_fog_distance, 
    GL_OES_depth_texture, GL_OES_element_index_uint, GL_OES_fbo_render_mipmap, 
rican-linux@iBookG4-Debian9:~$ 
```

---

### Post by luigiburdo on 2015-05-25
Rican , the Xeno74 patch work with r600 i think on r300 you will face issue

---

### Post by rican-linux on 2015-05-25
I feared that..I just wanted to see if it would work. The mesa r300 patch that I normally used is starting to fail beginning with version 10.5.5

---

### Post by luigiburdo on 2015-09-06
For All if you need to install Lubuntu lastest or Mate 15.10 ecc you need to make Xorg -configure and replace where the nouveau is the fbdev ... on Quad G5 the only way for make run the last distros on radeonhd is software resterized ... letz hope the devs will wake up and fix this on our machines!

---

### Post by luigiburdo on 2015-09-21
News About Install the Mate ad Lubuntu 15.10 .
For have the X working but with software resterized radeon 
just swap on terminal  and 

sudo /etc/init.d/lightdm stop 
sudo Xorg -configure 
sudo nano xorg.conf.new 
Change the driver with radeon and the right pcie slot (eg 10:0:0) you can know it with lspci
... save
sudo cp xorg.conf.new /etc/X11/xorg.config 

sudo /etc/lightdm start ...


you will have the X running ... note only in softrware resterized mode... but working on radeonHD gpus

---

### Post by opepe on 2016-01-19
Helo front spain!
I try to install Ubuntu 15.10 on PowerPC quad with nvidia 7800gtx. I do the instructions on this tutorial [http://ubuntuforums.org/showthread.php?t=2143402](http://ubuntuforums.org/showthread.php?t=2143402) , I see perfectly live cd, and I install, but when reboot I see a white screen with some parameters and Ubuntu not start. I see that you have the same graphic card. What's wrong with my yaboot.conf ??
thanks for your time

---

### Post by luigiburdo on 2016-01-19
> **opepe said:**
> Helo front spain!
I try to install Ubuntu 15.10 on PowerPC quad with nvidia 7800gtx. I do the instructions on this tutorial [http://ubuntuforums.org/showthread.php?t=2143402](http://ubuntuforums.org/showthread.php?t=2143402) , I see perfectly live cd, and I install, but when reboot I see a white screen with some parameters and Ubuntu not start. I see that you have the same graphic card. What's wrong with my yaboot.conf ??
thanks for your time

I think is not a yaboot the problem , but some modules not loaded. I never use Mate or Lubuntu form 7800gtx i use a radeon because i have issue on it because the kernel .  In any way try to boot without noaccel and nomodeset

---

### Post by opepe on 2016-01-19
Ok, thank you. I have a ati x1900xt 512 Mac edition. Can works with Ubuntu 15.10?

---

### Post by opepe on 2016-01-20
Hello again!. Now Ubuntu works !!!! When I started appear a with screen , but if i wait a few moments and type " modprobe nvidiafb mode_option=1920x1200-64 , appear a black screen with the command. Now I write exit, enter and works!!!!! With nvidia 7800gtx 512!!!

But I want to know if is possible skip the step of modprobe......
I only modified the parameters that explains in the forum I write before

---

### Post by luigiburdo on 2016-01-21
It was working for me too ... but only console tty. did it works on Xorg is it hw accelerate?
for have it from beginning you need to edit the yaboot.conf 
nvidiafb:???

where nouveau?

Kernel 4.4 stable optimized for G5 Quads with RadeonHD . The nuoveau module is not compiled for not have issue with RadeonHD (drm-kms-helper)
[https://www.dropbox.com/s/eqw6nhr6pxd6tim/kernel4.4.tar.gz?dl=0](https://www.dropbox.com/s/eqw6nhr6pxd6tim/kernel4.4.tar.gz?dl=0)

---

### Post by bernhard7 on 2016-01-25
Hi i have installed by your instructions for 14.04.3 ubuntu with 6570 radeon hd.
I habe problems with the 3d mesa driver. I cant alone repair that. Can you help me? I have powermac quad 4 gb ram 7800 gtx 512 radeon hd 6570 2 gb

Du you not in an irc channel?

---

### Post by luigiburdo on 2016-01-25
Hi,no not on irc... did you make a reboot on the machine after intalling the patches for 3d?

---

### Post by bernhard7 on 2016-01-25
glxgears: symbol lookup error: /usr/lib/powerpc-linux-gnu/mesa/libGL.so.1: undefined symbol: _glapi_Dispatch

That is the problem. I have mesa 10.0.4 from your link. R600_dri.so is 31 mb much larger then original has 7 mb libGL.1.2.0 has 2,5 mb ist right.

Yes i have boot the machine. No 3d.

---

### Post by luigiburdo on 2016-01-25
this are all the xeno patches [http://www.supertuxkart-amiga.de/amiga/mesalib-unofficial.html](http://www.supertuxkart-amiga.de/amiga/mesalib-unofficial.html)
try this [MesaLib-10.0.4-powerpc-unofficial.tar.bz2]("http://www.xenosoft.de/MesaLib-10.0.4-powerpc-unofficial.tar.bz2")
if not work this:[MesaLib-1.0.0.4-Lubuntu_14.10-powerpc-test.tar.bz2]("http://www.xenosoft.de/MesaLib-1.0.0.4-Lubuntu_14.10-powerpc-test.tar.bz2")

please report if ok :)

Luigi

ah forget to say: make a sys update just for sure tar program is ok

---

### Post by bernhard7 on 2016-01-25
I have mesa 10.0.3 installed with the export ....

Glxgears says errror: couldnt get rgb, doublebuffered visual

In the archive from 10.0.4 is not a redmefile to install this.

Sorry in archive 10.0.0.4 mesa

Can i install kernel 4.4 in 14.04.3 lubuntu?

---

### Post by luigiburdo on 2016-01-25
yes

> **bernhard7 said:**
> I have mesa 10.0.3 installed with the export ....

Glxgears says errror: couldnt get rgb, doublebuffered visual

In the archive from 10.0.4 is not a redmefile to install this.

Install is the same , use the old readme

---

### Post by bernhard7 on 2016-01-25
I Reinstalled original Mesa.

I Installed your 4.4 Kernels on my system but his not boot with them. Always i have kernel 3.16.0.60 lol

Good night. Tomorrow i come soon.

---

### Post by luigiburdo on 2016-01-26
> **bernhard7 said:**
> I Reinstalled original Mesa.

I Installed your 4.4 Kernels on my system but his not boot with them. Always i have kernel 3.16.0.60 lol

Good night. Tomorrow i come soon.
> **bernhard7 said:**
> I Reinstalled original Mesa.

I Installed your 4.4 Kernels on my system but his not boot with them. Always i have kernel 3.16.0.60 lol

Good night. Tomorrow i come soon.

this means you are not with 3D accelerations :-P

about kernel after installing with: sudo dpkg -i *.deb
you need to edit :  sudo nano /etc/yaboot.conf . add the new lines with the new kernel and do
sudo ybin -v
make attention because if you do something wrong the machine will not boot any moore.

---

### Post by bernhard7 on 2016-01-26
There are a lot of kernels in this download. Ther a big file with 35 mb or the 10 mb file. I copy paste the yaboot.conf and you can resend this correct please. Thanks that you help me. With 3d is to heavy. When i start 15.10 ubuntu from cd then come the ubuntu logo on radeon hd but later is the screen black and i can change in tty1 modus and return in black screen. In tty1 modus can not login there. What can i do?

```
## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot="/dev/disk/by-id/ata-WDC_WD1500AHFD-00RAR5_WD-WMAP41493261-part2"
device=/ht@0,f2000000/pci@9/k2-sata-root@c/@ffffffffffffffff/@0
partition=3
root="UUID=a889234e-c449-4cd5-844e-fa146967876e"
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash video=offb:off radeon.modeset=1 nouveau.modeset=0"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash vodeo=offb:off video=radeonfb:off video=nouveaufb:off"
```

```
libGL error: unable to load driver: r600_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: r600
ATTENTION: default value of option vblank_mode overridden by environment.
ATTENTION: default value of option vblank_mode overridden by environment.
618 frames in 5.0 seconds = 123.435 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 1386 requests (93 known processed) with 0 events remaining.
```

---

### Post by luigiburdo on 2016-01-26
My yaboot.conf ... i have more kernel installed for the testing


```


# yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot="/dev/disk/by-id/ata-ST1000DX001-1CM162_Z1DAP76W-part3"
device=/ht@0,f2000000/pci@9/k2-sata-root@c/@ffffffffffffffff/@0
partition=4
root="UUID=54a985d3-9da5-40e9-9295-13dc4dbc4832"
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx="/dev/disk/by-id/ata-INTEL_SSDSA2CW120G3_CVPR4152000G120LGN-part3"


image=/boot/vmlinux-4.4.0
        label=Linux44
        read-only
        initrd=/boot/initrd.img-4.4.0
        append="quiet splash"


image=/boot/vmlinux-4.3.0-rc5
        label=Linux43
        read-only
        initrd=/boot/initrd.img-4.3.0-rc5
        append="quiet splash"

image=/boot/vmlinux-4.4.0-rc8
        label=Linux448
        read-only
        initrd=/boot/initrd.img-4.4.0-rc8
        append="quiet splash"



```


about mesa do exactly this:

> 
sudo cp mesa-10.0.4/lib/dri/r600_dri.so /usr/lib/powerpc-linux-gnu/dri
sudo cp mesa-10.0.4/lib/libGL.so.1.2.0 /usr/lib/powerpc-linux-gnu/mesa




Kernel 4.5-rc1 For Quad G5 with RadeonHD ... tested and working :) 

[https://www.dropbox.com/s/jzyi39dr3iw3b1t/kernel45rc1.tar.gz?dl=0](https://www.dropbox.com/s/jzyi39dr3iw3b1t/kernel45rc1.tar.gz?dl=0)

Good News today i have OSX  Panther working running on my Quad G5 with  Mol-Kvm :-)

---

### Post by bernhard7 on 2016-01-26
your kernel 4.4 is running, but the fans going full speed and the installed mesa driver run not. I have reinstalled 3.16.0.60 kernel
What can i do?

only Rasterized Mesa running but to slowly

---

### Post by luigiburdo on 2016-01-26
> **bernhard7 said:**
> your kernel 4.4 is running, but the fans going full speed and the installed mesa driver run not. I have reinstalled 3.16.0.60 kernel
What can i do?

sudo nano /etc/modules
and add there:  i2c-powermac

this will make fan not spin...

about the mesa ... really strange . for me Lubuntu working great.
did you insert the radeon on 8x pci?

---

### Post by bernhard7 on 2016-01-26
I have ad this Line but it run full speed away
A lot of video cards from many factorys have the HD 6570 2GB version. Is there a problem. I have put the gtx in 16x and radeon in 8x Slot. What Make your Kernel better than the others One?

I have allways installed 10.3.2 mesa in this correkt?
or must installed the older one from packages for the x1000 write in readme file?

---

### Post by xeno74 on 2016-01-27
> **bernhard7 said:**
> I have allways installed 10.3.2 mesa in this correkt?
or must installed the older one from packages for the x1000 write in readme file?


[LIST=1]
[*]Install the default Mesa packages from your distribution 
[*]_Download_ the unofficial Mesa: [MesaLib-10.0.4-powerpc-unofficial.tar.bz2]("http://www.xenosoft.de/MesaLib-10.0.4-powerpc-unofficial.tar.bz2") 
[*]_Extract_ it in your home folder 
[*]_Rename_ the original **r600_dri.so** to **r600_dri.so.bak**: 

```
sudo mv /usr/lib/powerpc-linux-gnu/dri/r600_dri.so /usr/lib/powerpc-linux-gnu/dri/r600_dri.so.bak

``` 
[*]_Copy_ the patched **r600_dri.so** to **/usr/lib/powerpc-linux-gnu/dri**:

```
sudo cp mesa-10.0.4/lib/dri/r600_dri.so /usr/lib/powerpc-linux-gnu/dri

``` 
[*]Copy the whole Mesa directory to **/usr/local**:

```
sudo cp -R mesa-10.0.4 /usr/local

``` 
[*]Reboot your Power Mac G5 
[/LIST]

---

### Post by bernhard7 on 2016-01-27
I have install all this. Then i start test glxgears. is runs Good with Raden hd on 60 frames. Then i restartet powermac G5. Then Chrashes by start glxgears in black screen with blinking cursor. The system send report messages too. i hav ereboot, and automatically i have no 3D. Its Rasterized. What can i do?

bernhard@bernhard-desktop:~$ glxgears
libGL error: unable to load driver: r600_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: r600
477 frames in 5.0 seconds = 94.692 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 1647 requests (1002 known processed) with 0 events remaining.

I have reinstalled libGL.so.1 (in the old one was a link to libGL.1.2.0.bak), but is not right file 700 kb)
I have reinstalled libGL.so.1 from your mesa it is 2,4 mb great in right folder in my system.

Then i start glxgears and his run with accelerated Hd radeon. So good. But when i restart lost 3d accelerated feauture.....What is wrong by me?

---

### Post by vlotho on 2016-01-27
I just tried with sapphire radeon hd 5450 1 gb and I had a beautiful black screen. I tested the card on a PC and it works. Mac ports also work. It is mandatory radeon hd a brand "ati"?

---

### Post by luigiburdo on 2016-01-27
> **vlotho said:**
> I just tried with sapphire radeon hd 5450 1 gb and I had a beautiful black screen. I tested the card on a PC and it works. Mac ports also work. It is mandatory radeon hd a brand "ati"?

i have exactly it :-) Sapphire radeonhd 5450 1Gb.

did you swap with tty and check if you have the terminal cursor there ?

> **bernhard7 said:**
> I have reinstalled libGL.so.1 (in the old one was a link to libGL.1.2.0.bak), but is not right file 700 kb)
I have reinstalled libGL.so.1 from your mesa it is 2,4 mb great in right folder in my system.

Then i start glxgears and his run with accelerated Hd radeon. So good. But when i restart lost 3d accelerated feauture.....What is wrong by me?

Nothing wrong my friend , we need only the new mesa on ppc...
but  belive me ... all is much faster than the fastest apple board gpu.
I have the 7800gtx too

---

### Post by vlotho on 2016-01-27
there is absolutely nothing that is displayed on the screen, from power. no shadow of a yaboot. I do not even get into the open firmware. I tested on the PCI-E x8 and x16, and the result is the same.

---

### Post by luigiburdo on 2016-01-27
> **vlotho said:**
> there is absolutely nothing that is displayed on the screen, from power. no shadow of a yaboot. I do not even get into the open firmware. I tested on the PCI-E x8 and x16, and the result is the same.

what distro you are using there ?

---

### Post by vlotho on 2016-01-27
debian but it would surprise me very much that ca come distribution.
there is no particular change to the graphics card or the motherboard?

---

### Post by luigiburdo on 2016-01-27
> [COLOR=#000000]debian but it would surprise me very much that ca come distribution.[/COLOR]
debian dont work with radeonhd in ppc.
only sid seems working but i dont tested it. with radeon hd works Mate 14, lubuntu 14.04,3 an mate 15.10

---

### Post by vlotho on 2016-01-28
anyway, I have to do the installation with the original card? for nothing that starts when I boot with sapphire.

---

### Post by luigiburdo on 2016-01-28
> **vlotho said:**
> anyway, I have to do the installation with the original card? for nothing that starts when I boot with sapphire.

use my instruction from the beginning of this thread. you will have video on sapphire from very beginning . Only the yaboot exit on original card . there is needed to push just "return"

---

### Post by bernhard7 on 2016-01-28
I have completely anew installed 14. 04. 2 and afterwards have explained the automatic update. now is kernel 3. 16. 0. 59 on it. And then I have come along again to 3d patch from xeno74. I have obeyed the exactly N instructions meticulously. The result was sobering. So nothing functions. RGB stands in for buffer mistake. . . . I have noted this my system on/usr/lib/powerpc linux gnu/mesa/libGL_dri. so. 1 a file linking to libGL_dri. so. 1. 2. 0. bak produces instead of on libGL_dri. so. 1. 2. 0. I cannot change this file linking. The linking changes them every time by the new start of the system automatically. Have you never had with the quad such problem? I had to me this really easy vorgestelt. According to the descriptions this is also easy. But it is really difficult if mistake appear for inexperienced benutzer. vieleicht it is not to be installed from kernelversion to next already any more possibly correctly. I already have kernel 4. 4 and 4. 5 run. But there nothing also changes. Except this the fans and pump full pot run.

Sorry all path lines is libGL.so.1 or libGL.so.1.2.0

---

### Post by xeno74 on 2016-01-28
> **bernhard7 said:**
> I have completely anew installed 14. 04. 2 and afterwards have explained the automatic update. now is kernel 3. 16. 0. 59 on it. And then I have come along again to 3d patch from xeno74. I have obeyed the exactly N instructions meticulously. The result was sobering. So nothing functions. RGB stands in for buffer mistake. . . . I have noted this my system on/usr/lib/powerpc linux gnu/mesa/libGL_dri. so. 1 a file linking to libGL_dri. so. 1. 2. 0. bak produces instead of on libGL_dri. so. 1. 2. 0. I cannot change this file linking. The linking changes them every time by the new start of the system automatically. Have you never had with the quad such problem? I had to me this really easy vorgestelt. According to the descriptions this is also easy. But it is really difficult if mistake appear for inexperienced benutzer. vieleicht it is not to be installed from kernelversion to next already any more possibly correctly. I already have kernel 4. 4 and 4. 5 run. But there nothing also changes. Except this the fans and pump full pot run.

Sorry all path lines is libGL.so.1 or libGL.so.1.2.0

Hi Bernhard7,

Please reinstall the packages **libgl1-mesa-dri **and **libgl1-mesa-glx **and then copy the patched **r600_dri.so** to **/usr/lib/powerpc-linux-gnu/dri**:

```
sudo cp mesa-10.0.4/lib/dri/r600_dri.so /usr/lib/powerpc-linux-gnu/dri
```

Cheers,

Christian

---

### Post by bernhard7 on 2016-01-28
I have allready installed mesa libgl1-mesa-dri-lts-utopic 10.3.2 packages on my system . When i installed libgl1-mesa-dri and libgl-mesa-glx version 10.1.3 deletet my other packages. Can i do this?

---

### Post by vlotho on 2016-01-29
in fact we must put both cards into it? !!! I'm sorry, I did not understand. I am French ... and yes, I'm not perfect.

Offb freeze at home also

Mon système est un debian sid avec un kernel 1.16. J'essaye d'installer le patch x1000. Donc il faut que je désinstalle xvideo-xorg-core du système pour réinstaller celui de l'archive, sauf que là j'ai un problème de dépendance. Il me demande le fichier libgcypt11 qui n'est pas dans les dépôts. Il n'y a qu'un paquet -dev, mais ce n'est pas ce qu'il veut.

---

### Post by luigiburdo on 2016-01-29
> **vlotho said:**
> in fact we must put both cards into it? !!! I'm sorry, I did not understand. I am French ... and yes, I'm not perfect.

Offb freeze at home also
.

Exactly the Radeonhd have to go in the 3rd pci slot it is the 8x the apple in the 16x 
this works only on the distros i had been write the guide

note: im italian dont understand france ... english a bit :P

---

### Post by bernhard7 on 2016-01-29
Luigiburdo or xeno74:

Hi i habe installed the libs  libGL.so.1.2.0 and r600_dri.so in the right folder.
I have 3d accelerated befor i reboot. When i reboot, i cant open display infos in system profiler, black screen with cursor and in secoonds reboot to user option with password. The libs allways in right folder wir 2,4 mb and the radeon driver 29,6 mb. In tty come error message when i run glxgears: error couldnt open display (null)
I think that i finish I must reinstalled mesa and glx pakages to remove them proplem. I think im allmost there, but i dont know what could i do?

---

### Post by luigiburdo on 2016-01-29
> ave 3d accelerated befor i reboot. When i reboot, i cant open display  infos in system profiler, black screen with cursor and in secoonds  reboot to user option with password.
This is bad...  i was face this issue too when i had been made many tests in past ... my solution was reinstall everything and make all again for have a clean sys.
this was been face by Lubuntu .. 
In any way close lightdm 
switch to console "ctrl+alt+F1"
insert you passwords and stop lightdm

sudo /etc/init.d/lightdm stop
start again it 
sudo /etc/init.d/lightdm start

check if 3d are working ... if not ... too bad

ah dont forget to check if the fbdev is unistalled.

---

### Post by bernhard7 on 2016-01-29
I have make this commands, and when i start lightdm come a long list in tty. And tty is not ayailible with blinking cursor. I have a radeon hd 6770 1 gb. I test it.

The same problem with 6770 hd. Lol i. Is a sftware bug. But when i reinstalled mesa and glx packages and install the two libs then i have 3d accelerated and games ala doom, tuxkart rinning fast with cards. After reboot i have some problems. Mhmmmm.

---

### Post by xeno74 on 2016-01-29
> **bernhard7 said:**
> Luigiburdo or xeno74:

Hi i habe installed the libs  libGL.so.1.2.0 and r600_dri.so in the right folder.


Could you please install _**only**_ the patched r600_dri.so?

Before, please reinstall the packages **libgl1-mesa-dri **and [B]libgl1-mesa-glx.

[/B]German: Bernhard, versuche mal nur die r600_dri.so zu ersetzen. Davor mußt du aber die beiden o.g. Pakete nochmal neu installieren.

---

### Post by bernhard7 on 2016-01-29
zes im understand all. I have make zour commands. i intallec completly another mesa pagages 10.1.3 on synaptic. and copy file from your mesa-10.0.4. nothing 3D accelereated. 

 glxgears
libGL error: failed to load driver: r600
libGL error: failed to load driver: swrast
Error: couldn't get an RGB, Double-buffered visual

Luigiburdo: 

If I xserver-xorg-video-fbdev-lts-utopic enterne, then my graphics issue breaks, nevertheless, or. Or what does make this package? I have another 3d accelerated to me the calculator again switches off.

3D acellerated is working. I removed xorg fbdeb.lts.utopia from synaptic.
Thanks luigiburdo and xeno74. After reboot i have no errors. 3d acceleated 3.0 mesa direkt rendering in system profiler. The 6770 radeon hd i cant build in g5. Cant closes case with the big cooler ripps lol. Can i put radeon on x16 slot? Then is much faster?

---

### Post by luigiburdo on 2016-01-30
> **bernhard7 said:**
> 3D acellerated is working. I removed xorg fbdeb.lts.utopia from synaptic.
Thanks luigiburdo and xeno74. After reboot i have no errors. 3d acceleated 3.0 mesa direkt rendering in system profiler. The 6770 radeon hd i cant build in g5. Cant closes case with the big cooler ripps lol. Can i put radeon on x16 slot? Then is much faster?

using of 16x make me face system freezing. i can suggest to left everything like is right now. because you will not increase too much the performances. what make differece is the optimized xorg and better mesa. with last distros only the 4xxx serie are working with 3D.

---

### Post by vlotho on 2016-01-30
yet it is well on the 8x ... Pardon, but your English is difficult to understand, in addition, do not put any punctuation, it's complicated. I think I better understand if you wrote in Italian

---

### Post by bernhard7 on 2016-01-30
Yes its freezing system with other slots pluged in. I remove them.the kernel has the libGL.so.1 link to libGL.so.1.2.0.bak. Lol, i make sudo cp -P option to repair that link. 3D ready.

Luigiburdo: i have seen you have an amiga 4000T with fastest cyberstom. Lol. I have amiga 4000t with cyberstomppc 060 50 and 200 mhz ppc a long time . Lol, run luluntu on it? Its a great machine. Has you a fpga arcade board? X1000 is very nice, but under ubuntu. Scenedemos on Amiga was my hobby. It was great graphics and music coded features.

---

### Post by luigiburdo on 2016-01-30
> [COLOR=#000000] have an amiga 4000T with fastest cyberstom.[/COLOR]
No that was a a 4000D in desktop ultra hacked check the end of the 3rd part of my video.
for sure on 604e you can have apus on amiga 4000 ;-) and O4.1 FE too

---

### Post by bernhard7 on 2016-01-30
Has your powermac quad a sata2 card? When yes boot it?

---

### Post by vlotho on 2016-01-30
the link for ubuntu mate is dead everywhere

---

### Post by luigiburdo on 2016-01-30
> **bernhard7 said:**
> Has your powermac quad a sata2 card? When yes boot it?

Im using internal Sata. 
the SSD is a Intel SSD 320 120GB (Slot B)
The SSHD is a Segata 1TB (Slot a) 

Linux is on a partition of SSHD

---

### Post by bernhard7 on 2016-02-01
hi, im having no onboard sound. What can i do. I have no HDMI Monitor with Speakers. The radeon HD killed my Onboard Sound?

---

### Post by vlotho on 2016-02-01
there, I try to install ubuntu 14.04. the beginning of the startup procedure done properly, I arrive on the desktop ... without the fonts. if I stop "lightdm" I generates xorg.conf and I put RenderAccel false, by re starting lightdm I get a black screen and I can no longer switch to the tty.

---

### Post by luigiburdo on 2016-02-01
> [COLOR=#000000]e starting lightdm I get a black screen and I can no longer switch to the tty.[/COLOR]

check some time xorg make wrong pcie configuration.
what video board are you using?

> **bernhard7 said:**
> hi, im having no onboard sound. What can i do. I have no HDMI Monitor with Speakers. The radeon HD killed my Onboard Sound?

install kmix , and try to force the sound-pmac output
and yes the audio will exit for sure from hdmi

---

### Post by vlotho on 2016-02-01
sapphire radeon HD 5450
how check this configuration. where i can to look that ? it's a good port into the mac.

---

### Post by luigiburdo on 2016-02-02
> **vlotho said:**
> sapphire radeon HD 5450
how check this configuration. where i can to look that ? it's a good port into the mac.
I have this board too inside my quad and is working.

how?

Swap to console 
sudo /etc/lightdm stop
sudo Xorg -configure
sudo nano xorg.conf.new 

check if the radeo is running on pci 8:0:0 (8x) and not on 10:0:0(16x)

---

### Post by vlotho on 2016-02-02
i have 
BusID "PCI:10:0:0" for nvidia and
BusID "PCI:6:0:0" for radeon ...

---

### Post by bernhard7 on 2016-02-02
I have installed kmix. But Sound is nothing. in Systemprofiler is Apple onboard audio enabled. How i can use it? Thanks for help.

Hi when i open kmix....

cation may misbehave.
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
kbuildsycoca4 running...
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QSystemTrayIcon::setVisible: No Icon set
Object::connect: No such signal org::freedesktop::UPower::DeviceAdded(QDBusObjectPath)
Object::connect: No such signal org::freedesktop::UPower::DeviceRemoved(QDBusObjectPath)
QDBusConnection: name 'org.kde.kglobalaccel' had owner '' but we thought it was ':1.53'

---

### Post by luigiburdo on 2016-02-02
> **vlotho said:**
> i have 
BusID "PCI:10:0:0" for nvidia and
BusID "PCI:6:0:0" for radeon ...

umm probably that was , i was remember good the 14.04 was gave the pcie 8x at 6:0:0 but on my machine it is on 8:0:0

do an lspci and check what resource is using the pci 8:0:0

pls do and sudo nano /etc/modules  and see if snd-powermac is inserted without a #

---

### Post by bernhard7 on 2016-02-02
this is my /etc/modules

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

# snd-powermac
snd-aoa
snd-aoa-fabric-layout
snd-aoa-soundbus
snd-aoa-i2sbus
snd-aoa-codec-tas


No sound anywhere

---

### Post by vlotho on 2016-02-03
there is none that uses the "8"
i can force to change the busid into the xorg.conf ?

are you sure you've put the video card on the 8x port?

---

### Post by luigiburdo on 2016-02-04
> **bernhard7 said:**
> this is my /etc/modules

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

# snd-powermac
snd-aoa
snd-aoa-fabric-layout
snd-aoa-soundbus
snd-aoa-i2sbus
snd-aoa-codec-tas


No sound anywhere
pull out the the # from [COLOR=#000000]# snd-powermac[/COLOR]

> **vlotho said:**
> there is none that uses the "8"
i can force to change the busid into the xorg.conf ?

are you sure you've put the video card on the 8x port?

im sure like my name is Luigi ;-)

on 16x the system freeze.

about bus id... 16x is 10:0:0 , on last distros the 8x is 8:0:0 and if i remember good on old is 6:0:0

---

### Post by bernhard7 on 2016-02-04
I have change to  snd-powermac. And reboot.
Allways no sound. On all my conections.

---

### Post by vlotho on 2016-02-04
So, if the "bus" is good, what is blocking desktop display?

---

### Post by luigiburdo on 2016-02-04
> **vlotho said:**
> So, if the "bus" is good, what is blocking desktop display?

without RenderAccel "false" is working ?

> **bernhard7 said:**
> I have change to  snd-powermac. And reboot.
Allways no sound. On all my conections.

What kernel have you installed? the distro original or my 4?

---

### Post by vlotho on 2016-02-05
> **luigiburdo said:**
> without RenderAccel "false" is working ?

No, the desktop displays a black screen and stays locked.

---

### Post by luigiburdo on 2016-02-05
> **vlotho said:**
> No, the desktop displays a black screen and stays locked.

Umm... did you make some system update ? in case yes probably something goes not right ..
in case not : change the xorg.conf where is radeon swap fbdev . 
install it again : sudo aptitude install xserver-xorg-video-fbdev 
run again lightdm

another thing: remove the xorg nouveau video: sudo aptitude  remove xserver-xorg-video-nouveau

lets see if something change

---

### Post by vlotho on 2016-02-05
if I want to remove "nouveau", the system propose to delete "xserver-xorg-video-all" as.
here displays properly with fbdev, but I did not uninstall the "nouveau" for now. I await your answer.

once installed the system, I uninstall "fbdev" and "nouveau"?  or I leave fbdev? but suddenly, I would have no acceleration?

by cons I just saw it offered me an upgrade to "radeon"

---

### Post by bernhard7 on 2016-02-05
Hi luigiburdo:

I have installed 3.16.0.60 kernel original. Vour kernel v4 has the fans full speed trouble. Lol.

---

### Post by vlotho on 2016-02-05
I updated the driver. Then I changed the file "yaboot.conf", I added "radeon.modeset nouveau.modeset = 1 = 0" and I wanted to test a xorg.conf with the radeon driver, then black screen, keyboard locked . I restart, thinking I would pass automatically on the screen of the Radeon but it happened anyway on the screen of the nvidia, and there can not have the second screen. I restart due by adding the line "video = offb: off ..." to prompt yaboot and now I do not even happen to me logger. I can get my login but the line asking me the password no longer appears ...

I have not uninstalled Radeon, nouveau or fbdev, for now.

by cons, I have an error message, after the hard disk installation, where it is written:
Oops Kernel access of bad area.
My kernel is version "3.13.0-24-powerpc64-smp"

I'll try to chroot the system from the CD and put the kernel that you have proposed.

---

### Post by luigiburdo on 2016-02-05
> **bernhard7 said:**
> Hi luigiburdo:

I have installed 3.16.0.60 kernel original. Vour kernel v4 has the fans full speed trouble. Lol.

ahah ... Bernhard :P

open a terminal and do 
sudo modprobe i2c-powermac
and after 
just need to add in modules
```


sudo nano /etc/modules 
i2c-powermac 

```
and the fan will stop spin ;-)

> **vlotho said:**
> I updated the driver. Then I changed the file "yaboot.conf", I added "radeon.modeset nouveau.modeset = 1 = 0" and I wanted to test a xorg.conf with the radeon driver, then black screen, keyboard locked . I restart, thinking I would pass automatically on the screen of the Radeon but it happened anyway on the screen of the nvidia, and there can not have the second screen. I restart due by adding the line "video = offb: off ..." to prompt yaboot and now I do not even happen to me logger. I can get my login but the line asking me the password no longer appears ...

I have not uninstalled Radeon, nouveau or fbdev, for now.

by cons, I have an error message, after the hard disk installation, where it is written:
Oops Kernel access of bad area.
My kernel is version "3.13.0-24-powerpc64-smp"

I'll try to chroot the system from the CD and put the kernel that you have proposed.

ummm... lets see again
boot the cdrom with :

```

live video=offb:off video=radeonfb:off video=nouveaufb:off radeon.modeset=1 nouveau.modeset=0

```
make attention if you make just little wrong the system will boot with default config.
If you dont have the right fonts ... yes you need the noaccel in xorg
Option          "RenderAccel" "off"
let me know if start working

---

### Post by bernhard7 on 2016-02-05
luigiburdo:

You have many kernels to download. What for kernel is for me good?

ok, i installed your kernel 4.4.0 rc8, works fine. But what is better with the kernel?

Ok Sound running with kmix on apple onboard device. Thanks.

---

### Post by vlotho on 2016-02-05
With the radeon driver, it does not work, with or without acceleration, juste with fbdev driver

---

### Post by luigiburdo on 2016-02-05
> **bernhard7 said:**
> ok, i installed your kernel 4.4.0 rc8, works fine. But what is better with the kernel?

perfect :-)
is more stable and did for radeonhd

> **vlotho said:**
> With the radeon driver, it does not work, with or without acceleration, juste with fbdev driver

it is really strange... did you change the kernel with one of mine?

---

### Post by vlotho on 2016-02-06
no, I was thinking of doing it now with a chroot system.

This time the bootstrap jumped, I will not start. I understand nothing ...
look into the "xorg.conf" file, there is no other problem in the file?

[https://bugs.freedesktop.org/show_bug.cgi?id=89886](https://bugs.freedesktop.org/show_bug.cgi?id=89886)

---

### Post by luigiburdo on 2016-02-07
Last experiment :-P [IMG]http://i1249.photobucket.com/albums/hh511/tlosm/Schermata-1_zps72ot6y2f.png[/IMG]

---

### Post by vlotho on 2016-02-07
it is very frustrating

you is which distrib there?

---

### Post by luigiburdo on 2016-02-07
> **vlotho said:**
> it is very frustrating

you is which distrib there?

That is Mate 15.10 but the Gpu is a radeonhd 4650 512mb and on 16x but some time it freeze 
the others 6570 and 5450 dont go in 3d ... have a  ring error and no audio

the only distro working without problems is the Lubuntu 14.04.3 ... strange you continue have errors there :-/ im really unhappy because i cant gave you a solutions i say all i know about :-/

---

### Post by bernhard7 on 2016-02-07
Hi, the game sauerbraten run but make gfx errors transparent walls and rooms. Unplayable. On 6570 radeon. I have 14.04.3 lubunt with kernel 3.16.0.61 and 4.4.8 kernel. By supertuxkart, tyres from cars transparent. But other games run good.

Xeno74 can write new mesa for amiga/powerpc and radeon 600 driver.?

---

### Post by luigiburdo on 2016-02-07
> **bernhard7 said:**
> Xeno74 can write new mesa for amiga/powerpc and radeon 600 driver.?

christian did a great job with that patch ... but a better driver is needed by amd ... not by pivate users

---

### Post by vlotho on 2016-02-07
among the kernels that you propose, which advises you?

---

### Post by luigiburdo on 2016-02-07
> **vlotho said:**
> among the kernels that you propose, which advises you?

check my 44.rc8 .

ps:a guy on my youtube channel advice me that with gentoo the radeons are working great without patches .
i will test it and report

---

### Post by vlotho on 2016-02-08
for the installation package "Xorg ...." must be followed exactly the procedure of the readme? install upstart ...?

---

### Post by bernhard7 on 2016-02-08
Luigiburdo:

No WebGL on firefox. What can i do? On your youtube videos run it.

On firefox. about:support

synchrones Wischen und Zoomen    none
GPU-beschleunigte Fenster    0/1 Basic Wurde auf Grund Ihrer Grafiktreiberversion blockiert. Versuchen Sie, Ihren Grafiktreiber auf mindestens Version <Anything with EXT_texture_from_pixmap support> zu aktualisieren.
Karten-Beschreibung    GLXtest process failed (received signal 11)
WebGL-Renderer    Wurde auf Grund Ihrer Grafikkarte blockiert, da ungelöste Treiberprobleme bestehen.
windowLayerManagerRemote    false
AzureCanvasBackend    cairo
AzureContentBackend    cairo
AzureFallbackCanvasBackend    none
AzureSkiaAccelerated    0

3D games running but no webGL. What can i do?

---

### Post by luigiburdo on 2016-02-08
Probably Firefox crashed and blacklist the webgl. ... about:config in the browser web address 
i suggest you to 
download qupzilla browser : first is fast compared firefox and is less buggy .

> **vlotho said:**
> for the installation package "Xorg ...." must be followed exactly the procedure of the readme? install upstart ...?

There is the geek is Xeno74 ;-) 
for sure if he write to install probably is needed

---

### Post by bernhard7 on 2016-02-08
hi, qupzilla window opening and closed automatically. What that?

Luigiburdo: can i install mesa 11.0.7 mesa driver on quad g5 with 14.04.3 lts ? Or is incompatible?

---

### Post by vlotho on 2016-02-09
> **luigiburdo said:**
> 
There is the geek is Xeno74 ;-) 
for sure if he write to install probably is needed

The problem is that it breaks a lot of dependencies ...

---

### Post by luigiburdo on 2016-02-09
> **bernhard7 said:**
> Luigiburdo: can i install mesa 11.0.7 mesa driver on quad g5 with 14.04.3 lts ? Or is incompatible?

No you need to install first in sytem mesa 11.7 if available after upgrading with xeno patch .

about qupzilla , yes you true i forget there was a bug on 14.04.x and it wasnt not working :-( sorry.

> **vlotho said:**
> The problem is that it breaks a lot of dependencies ...
umm... i dont know , i never downgrade because testing cdrom distros if working or gave issue.
Lastest distro gave big issues with radeonhd up 4xxx series ... im try to find a way for fix the r600 ring test failed that break the gpu accelerations.

Luigi

---

### Post by bernhard7 on 2016-02-09
Luigiburdo: i installed a lot of browser fol 14.04.3 but no webgl for all browser. You have it in your videos on youtube. With lubuntu 14.04? I have installed distro mesa 10.3.2. is this the problem? Is it better when i make a downgrade with the mesa libs, drivers, 10.1.... Too? 16.04 alpha 2 distro run not on g5?

---

### Post by luigiburdo on 2016-02-09
> **bernhard7 said:**
> Luigiburdo: i installed a lot of browser fol 14.04.3 but no webgl for all browser. You have it in your videos on youtube. With lubuntu 14.04? I have installed distro mesa 10.3.2. is this the problem? Is it better when i make a downgrade with the mesa libs, drivers, 10.1.... Too? 16.04 alpha 2 distro run not on g5?

I was using the mesa patch from Christian Xeno 74 , i dont think webgl dont work because your mesa ... i think was blacklisted by firefox.
did you makde about:config in firefox? 

16:04 dont work at all to no one with G5

---

### Post by bernhard7 on 2016-02-09
Yes i have make about:config they came a long list from configs. But can i was configure there?

---

### Post by vlotho on 2016-02-09
I succeeded to start with the kernel 4.4rc8 and I replaced the r600.so file with that of Christian. by cons when I re starts I feel in software rastererizer and I do not see the 10.0.0.4 version in the glxinfo .... I can look in the other thread page, the problem can already be had encountered.
I have replaced my driver "fbdev" by the "amdgpu" in the "xorg.conf".

I just look at my log Xorg and I feel still fbdev, yet I have changed the driver in "xorg.conf"

may be that I must Force uninstalling fbdev ? ...

it is always the same, if I try to uninstall fbdev,nouveau or radeon, the system requires me to uninstall also xserver-xorg-video-all and I think it's going to break my all.

gilles@gilles-desktop:~$ LIBGL_DEBUG=verbose glxinfo | grep render
libGL: screen 0 does not appear to be DRI3 capable
libGL: screen 0 does not appear to be DRI2 capable
libGL: OpenDriver: trying /usr/lib/powerpc-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/powerpc-linux-gnu/dri/swrast_dri.so
libGL: Can't open configuration file /home/gilles/.drirc: No such file or directory.
direct rendering: Yes
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
OpenGL renderer string: Software Rasterizer
    GL_NV_blend_square, GL_NV_conditional_render, GL_NV_depth_clamp

---

### Post by luigiburdo on 2016-02-09
> Identifier  "Amdgpu"
	Driver      "amdgpu

Identifier have to be Card1
Driver Radeon

---

### Post by vlotho on 2016-02-10
Driver "radeon" freezes the system every time. With or without acceleration.
I am forced to put me in "fbdev"

---

### Post by luigiburdo on 2016-02-10
Freeze you mean that you have freezing of the X or black screen and cursor blinking?

---

### Post by vlotho on 2016-02-10
black screen and cursor blinking.
this is the old log file, with the radeon driver.

```
gilles@gilles-desktop:~$ cat /var/log/Xorg.0.log.old | grep EE
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.227] Initializing built-in extension MIT-SCREEN-SAVER
[    29.255] (EE) [drm] KMS not enabled
[    29.255] (EE) No devices detected.
[    29.256] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    29.257] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    29.258] (EE) Failed to load module "modesetting" (module does not exist, 0)
[    29.271] (EE) [drm] KMS not enabled
[    29.371] (EE) RADEON(G0): [XvMC] Failed to initialize extension.
[    29.372] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    29.372] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    29.372] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    29.372] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    29.372] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    29.377] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    29.377] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    29.377] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    29.403] (EE) AIGLX: reverting to software rendering
[    29.520] (EE) 
[    29.520] (EE) Backtrace:
[    29.521] (EE) 0: /usr/bin/X (xorg_backtrace+0x68) [0x202b9018]
[    29.521] (EE) 1: /usr/bin/X (0x200b9000+0x204fa0) [0x202bdfa0]
[    29.521] (EE) 2: (vdso) (__kernel_sigtramp_rt32+0x0) [0x100420]
[    29.521] (EE) 3: /usr/bin/X (RRSetChanged+0x80) [0x20200a20]
[    29.521] (EE) 4: /usr/bin/X (defaultScreenSaverAllowExposures+0x0) [0x2031eb24]
[    29.521] (EE) 5: /usr/bin/X (RRScreenSetSizeRange+0x74) [0x20205cf4]
[    29.521] (EE) 6: /usr/bin/X (xf86RandR12CreateScreenResources+0x30c) [0x201b139c]
[    29.521] (EE) 7: /usr/bin/X (0x200b9000+0xe8158) [0x201a1158]
[    29.521] (EE) 8: /usr/bin/X (0x200b9000+0x5c3ac) [0x201153ac]
[    29.521] (EE) 9: /usr/bin/X (0x200b9000+0x42504) [0x200fb504]
[    29.521] (EE) 10: /lib/powerpc-linux-gnu/libc.so.6 (0x1fabe000+0x23294) [0x1fae1294]
[    29.521] (EE) 11: /lib/powerpc-linux-gnu/libc.so.6 (0x1fabe000+0x23454) [0x1fae1454]
[    29.521] (EE) 
[    29.521] (EE) Segmentation fault at address 0x58
[    29.521] (EE) 
[    29.521] (EE) Caught signal 11 (Segmentation fault). Server aborting
[    29.521] (EE) 
[    29.522] (EE) 
[    29.522] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    29.522] (EE) 
[    29.565] (EE) Server terminated with error (1). Closing log file.
```



it is necessary, perhaps, I load the module "dri" in "xorg.conf" to activate the file christian, for the mesa.

---

### Post by vlotho on 2016-02-12
the problem looks like this one :
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=671103](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=671103)

---

### Post by luigiburdo on 2016-02-12
nope the bug is different you have a crash of X ... if you use fbdev you face the same crash? can you post your xorg.conf?
i had that crash on debian 8 and up with radeonhd. same was with 15.04

---

### Post by vlotho on 2016-02-12
with fbdev there not a crash or bug.
xorg.conf is [here]("http://ubuntuforums.org/showthread.php?t=2274612&p=13437171#post13437171") .
I only replaces fbdev by radeon, when I test.
but I did not load dri and  drm module in xorg.conf. I do not know if it will change anything.

---

### Post by luigiburdo on 2016-02-12
please write too
dmesg | grep drm 
dmesg | grep radeon 
dmesg | grep vga 
and 
lspci

if possible too lsmod

---

### Post by vlotho on 2016-02-12
```
gilles@gilles-desktop:~$ dmesg | grep drm
[   13.949284] [drm] Initialized drm 1.1.0 20060810
[   15.894817] [drm] radeon kernel modesetting enabled.
[   15.895532] [drm] initializing kernel modesetting (CEDAR 0x1002:0x68F9 0x174B:0xE127).
[   15.895568] [drm] register mmio base: 0x80140000
[   15.895570] [drm] register mmio size: 131072
[   16.011801] [drm] GPU not posted. posting now...
[   16.015416] [drm] Detected VRAM RAM=1024M, BAR=256M
[   16.015419] [drm] RAM width 64bits DDR
[   16.015687] [drm] radeon: 1024M of VRAM memory ready
[   16.015690] [drm] radeon: 1024M of GTT memory ready.
[   16.015713] [drm] Loading CEDAR Microcode
[   16.931981] [drm] GART: num cpu pages 262144, num gpu pages 262144
[   16.974401] [drm] PCIE GART of 1024M enabled (table at 0x000000000025D000).
[   16.976396] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   16.976399] [drm] Driver supports precise vblank timestamp query.
[   16.976526] [drm] radeon: irq initialized.
[   16.993936] [drm] ring test on 0 succeeded in 1 usecs
[   16.994118] [drm] ring test on 3 succeeded in 3 usecs
[   17.179479] [drm] ring test on 5 succeeded in 1 usecs
[   17.179487] [drm] UVD initialized successfully.
[   17.180133] [drm] Enabling audio 0 support
[   17.180199] [drm] ib test on ring 0 succeeded in 0 usecs
[   17.180303] [drm] ib test on ring 3 succeeded in 0 usecs
[   17.330298] [drm] ib test on ring 5 succeeded
[   17.331420] [drm] Radeon Display Connectors
[   17.331424] [drm] Connector 0:
[   17.331427] [drm]   DVI-I-1
[   17.331429] [drm]   HPD4
[   17.331432] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[   17.331434] [drm]   Encoders:
[   17.331437] [drm]     DFP1: INTERNAL_UNIPHY
[   17.331439] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   17.331441] [drm] Connector 1:
[   17.331443] [drm]   DVI-I-2
[   17.331445] [drm]   HPD2
[   17.331448] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[   17.331450] [drm]   Encoders:
[   17.331452] [drm]     DFP2: INTERNAL_UNIPHY1
[   17.331455] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   17.350025] [drm] Internal thermal controller with fan control
[   17.361754] [drm] radeon: dpm initialized
[   17.416859] [drm] fb mappable at 0x9045E000
[   17.416863] [drm] vram apper at 0x90000000
[   17.416865] [drm] size 7299072
[   17.416867] [drm] fb depth is 24
[   17.416869] [drm]    pitch is 6912
[   17.464614] radeon 0001:06:00.0: fb0: radeondrmfb frame buffer device
[   17.464627] [drm] Initialized radeon 2.36.0 20080528 for 0001:06:00.0 on minor 0

```

```
gilles@gilles-desktop:~$ dmesg | grep radeon
[    0.000000] Kernel command line: root=UUID=9e43c22c-c287-4746-b917-e389e6cceace ro quiet splash video=offb:off video=radeonfb:off video=nouveaufb:off radeon.modeset=1 nouveau.modeset=0 
[   15.894817] [drm] radeon kernel modesetting enabled.
[   15.894944] radeon 0001:06:00.0: enabling device (0004 -> 0007)
[   15.895557] radeon 0001:06:00.0: Using 32-bit DMA via iommu
[   16.015405] radeon 0001:06:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[   16.015410] radeon 0001:06:00.0: GTT: 1024M 0x0000000040000000 - 0x000000007FFFFFFF
[   16.015687] [drm] radeon: 1024M of VRAM memory ready
[   16.015690] [drm] radeon: 1024M of GTT memory ready.
[   16.974647] radeon 0001:06:00.0: WB enabled
[   16.974656] radeon 0001:06:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xc000000011664c00
[   16.974661] radeon 0001:06:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0xc000000011664c0c
[   16.976380] radeon 0001:06:00.0: fence driver on ring 5 use gpu addr 0x000000000005c418 and cpu addr 0xd00008008241c418
[   16.976402] radeon 0001:06:00.0: radeon: MSI limited to 32-bit
[   16.976472] radeon 0001:06:00.0: radeon: using MSI.
[   16.976526] [drm] radeon: irq initialized.
[   17.361754] [drm] radeon: dpm initialized
[   17.464614] radeon 0001:06:00.0: fb0: radeondrmfb frame buffer device
[   17.464618] radeon 0001:06:00.0: registered panic notifier
[   17.464627] [drm] Initialized radeon 2.36.0 20080528 for 0001:06:00.0 on minor 0
```

```
gilles@gilles-desktop:~$ dmesg | grep vga
[    0.144586] vgaarb: device added: PCI:0000:0a:00.0,decodes=io+mem,owns=none,locks=none
[    0.144610] vgaarb: device added: PCI:0001:06:00.0,decodes=io+mem,owns=none,locks=none
[    0.144623] vgaarb: loaded
[    0.144624] vgaarb: bridge control possible 0001:06:00.0
[    0.144626] vgaarb: bridge control possible 0000:0a:00.0
[   42.868840] vgaarb: device changed decodes: PCI:0001:06:00.0,olddecodes=io+mem,decodes=none:owns=none
```

```
gilles@gilles-desktop:~$ lspci
0000:00:0b.0 PCI bridge: Apple Inc. CPC945 PCIe Bridge
0000:0a:00.0 VGA compatible controller: NVIDIA Corporation G70 [GeForce 7800 GT] (rev a1)
0001:00:00.0 Host bridge: Apple Inc. U4 HT Bridge
0001:00:01.0 PCI bridge: Broadcom BCM5780 [HT2000] PCI-X bridge (rev a3)
0001:00:02.0 PCI bridge: Broadcom BCM5780 [HT2000] PCI-X bridge (rev a3)
0001:00:03.0 PCI bridge: Broadcom BCM5780 [HT2000] PCI-Express Bridge (rev a3)
0001:00:04.0 PCI bridge: Broadcom BCM5780 [HT2000] PCI-Express Bridge (rev a3)
0001:00:05.0 PCI bridge: Broadcom BCM5780 [HT2000] PCI-Express Bridge (rev a3)
0001:00:06.0 PCI bridge: Broadcom BCM5780 [HT2000] PCI-Express Bridge (rev a3)
0001:00:07.0 PCI bridge: Apple Inc. Shasta PCI Bridge
0001:00:08.0 PCI bridge: Apple Inc. Shasta PCI Bridge
0001:00:09.0 PCI bridge: Apple Inc. Shasta PCI Bridge
0001:01:07.0 Unassigned class [ff00]: Apple Inc. Shasta Mac I/O
0001:01:0b.0 USB controller: NEC Corporation OHCI USB Controller (rev 43)
0001:01:0b.1 USB controller: NEC Corporation OHCI USB Controller (rev 43)
0001:01:0b.2 USB controller: NEC Corporation uPD72010x USB 2.0 Controller (rev 04)
0001:03:0c.0 IDE interface: Broadcom K2 SATA
0001:03:0d.0 Unassigned class [ff00]: Apple Inc. Shasta IDE
0001:03:0e.0 FireWire (IEEE 1394): Apple Inc. Shasta Firewire
0001:05:04.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5780 Gigabit Ethernet (rev 03)
0001:05:04.1 Ethernet controller: Broadcom Corporation NetXtreme BCM5780 Gigabit Ethernet (rev 03)
0001:06:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series]
0001:06:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series]
```

```
gilles@gilles-desktop:~$ lsmod
Module                  Size  Used by
bnep                   24236  2 
rfcomm                 88583  0 
bluetooth             503935  10 bnep,rfcomm
radeon               2016698  2 
mac_hid                 6264  0 
nouveau              1517128  0 
ttm                   125874  2 radeon,nouveau
drm_kms_helper         67075  2 radeon,nouveau
snd_hda_codec_hdmi     60484  1 
drm                   404986  4 ttm,drm_kms_helper,radeon,nouveau
snd_hda_intel          62962  1 
snd_hda_codec         268105  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13211  1 snd_hda_codec
shpchp                 46667  0 
uninorth_agp           12119  0 
binfmt_misc            12904  1 
snd_aoa_codec_onyx     17337  0 
rtc_generic             2751  0 
snd_aoa                25242  1 snd_aoa_codec_onyx
uio_pdrv_genirq         6408  0 
uio                    17378  1 uio_pdrv_genirq
parport_pc             59112  0 
ppdev                  12524  0 
lp                     15658  0 
parport                55347  3 lp,ppdev,parport_pc
snd_powermac           95066  0 
snd_pcm               150899  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_powermac
snd_seq_midi           10103  0 
snd_seq_midi_event     11249  1 snd_seq_midi
snd_rawmidi            35813  1 snd_seq_midi
snd_seq                96002  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         11036  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              34645  2 snd_pcm,snd_seq
snd                   110527  15 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_aoa,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_powermac,snd_aoa_codec_onyx,snd_seq_midi
soundcore               2122  1 snd
snd_page_alloc         11517  2 snd_pcm,snd_hda_intel
windfarm_cpufreq_clamp     3309  1 
hid_generic             1922  0 
windfarm_max6690_sensor     4113  1 
windfarm_lm75_sensor     4628  1 
windfarm_smu_sensors     7693  1 
firewire_ohci          53420  0 
usbhid                 67486  0 
windfarm_smu_controls     7669  9 
firewire_core          96205  1 firewire_ohci
hid                   128106  2 hid_generic,usbhid
windfarm_pm112         15193  0 
crc_itu_t               1950  1 firewire_core
windfarm_smu_sat        8064  9 windfarm_pm112
windfarm_pid            3441  1 windfarm_pm112
windfarm_core          15556  7 windfarm_cpufreq_clamp,windfarm_pm112,windfarm_smu_sensors,windfarm_smu_sat,windfarm_lm75_sensor,windfarm_max6690_sensor,windfarm_smu_controls
tg3                   216343  0 
ptp                    15983  1 tg3
pps_core               17064  1 ptp
```


by against, although the radeon driver does not work, I get all the same to benefit from the acceleration of the graphics card with fbdev.
```
gilles@gilles-desktop:~$ glxinfo | grep direct
direct rendering: Yes
```

in terms of sound, there are only the HDMI output that works? the connectors of the motherboard is not functional?

---

### Post by luigiburdo on 2016-02-12
> by against, although the radeon driver does not work, I get all the same  to benefit from the acceleration of the graphics card with fbdev.
The video 2d will run good but have the accelerations will make all better.
Sound you can have the internal too but have to enablae snd-powermac

---

### Post by vlotho on 2016-02-12
and you still do not understand what is wrong with the radeon driver?

```
gilles@gilles-desktop:~$ cat /var/log/Xorg.0.log.old | grep drm
[193338.066] (II) xfree86: Adding drm device (/dev/dri/card0)
[193338.086] (EE) [drm] KMS not enabled
[193338.103] (EE) [drm] KMS not enabled
[193338.104] (II) FBDEV(0): hardware: radeondrmfb (video memory: 7128kB)
```

```
gilles@gilles-desktop:~$ cat /var/log/Xorg.0.log.old | grep radeon
[193338.063] Kernel command line: root=UUID=9e43c22c-c287-4746-b917-e389e6cceace ro quiet splash video=offb:off video=radeonfb:off video=nouveaufb:off radeon.modeset=1 nouveau.modeset=0 
[193338.072] (II) LoadModule: "radeon"
[193338.072] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[193338.072] (II) Module radeon: vendor="X.Org Foundation"
[193338.104] (II) FBDEV(0): hardware: radeondrmfb (video memory: 7128kB)
```

can you make me see your xorg.conf to lubuntu ?

did you read my "xorg.log.old" ?

the "(EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy" is a problem with the kernel.

---

### Post by luigiburdo on 2016-02-13
> 
the "(EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy" is a problem with the kernel.
it was reported time ago to Xorg and Radeon developers 

my Xorg.log is about Mate 15.10 with 4650 if you need i can share it

---

### Post by vlotho on 2016-02-13
No, I wanted to see your xorg.conf to see a little, the modules that you have loaded, etc ...
it annoys me that radon problem, I do not understand.

---

### Post by miltoncsl on 2016-02-13
Hi,

My name is Milton César. I had read this thread and I have same problem for make to work my PowerMac 2.0 GHz dual G5 late 2005 with XFX Radeon HD 5450 and ATI Radeon X1900 GT Mac Edition. 
One observation: in Mac OS X the Mac Edition GPU is showing how ATI Radeon X1900 GT but in Ubuntu-Mate it is showing how Radeon X1950 XTX (?). 

I am attaching the files:

dmesg-drm.txt,
 dmesg-radeon.txt,
 lsmod.txt,
 lspci.txt,
 Xorg.0.log and
 xorg.conf

Whose names indicate its contents.

What is wrong and how can I fix?

---

### Post by miltoncsl on 2016-02-13
Hi,

I missed to send the remaining files.

---

### Post by vlotho on 2016-02-13
luigi ! i have another problem with sound. 
apparently for the g5 quad, aoa manage the sound. i have put the # in the blacklist.local.conf and put 
# snd-powermac
snd-aoa
snd-aoa-i2sbus
snd-aoa-soundbus
snd-aoa-fabric-layout
# snd-aoa-codec-tas
snd-aoa-codec-onyx
# snd-aoa-codec-toonie

into the /etc/modules but that dont work.follow this file [http://lxr.free-electrons.com/source/sound/aoa/fabrics/layout.c ]("http://lxr.free-electrons.com/source/sound/aoa/fabrics/layout.c")
it should put the onyx codec for g5 quad but i have :
gilles@gilles-desktop:~$ dmesg | grep aoa
[   14.875546] snd-aoa-codec-onyx: created and attached onyx instance
[   14.877216] snd-aoa-codec-onyx: created and attached onyx instance
[   15.416431] snd-aoa-fabric-layout: Using PMF GPIOs
[   15.418195] snd-aoa-fabric-layout: can use this codec
[   15.447293] snd-aoa-codec-onyx: attached to onyx codec via i2c
[   15.447442] snd-aoa-fabric-layout: platform-onyx-codec-ref doesn't match!
[   15.447445] snd-aoa: fabric didn't like codec onyx

the modules have been properly compiled?

I saw that there was this patch, but I do not know if it will solve the problem.

[ http://mailman.alsa-project.org/pipermail/alsa-devel/2009-April/016046.html]("http://http://mailman.alsa-project.org/pipermail/alsa-devel/2009-April/016046.html")


in your "kernel44rc8", you have customize only .config file, or you have do others modifications ?

there is that too :
[https://bugs.launchpad.net/ubuntu/+source/hw-detect/+bug/1296373](https://bugs.launchpad.net/ubuntu/+source/hw-detect/+bug/1296373)

---

### Post by luigiburdo on 2016-02-13
[COLOR=#000000]dho! i dont understand why you have all this issue :-P 

# snd-powermac <-- have to be not blacklisted have to stay in modules if your intention have the original audio of quad .

about my config i disabled the not necessary (for the quad) modules and add what is need for have kvm working , radeon, and amdgpu working , radeon audio working . 


Edit: without the radeon module running you will not have radeon audio on
[/COLOR]

---

### Post by vlotho on 2016-02-15
dmesg | grep powermac :

[   14.916313] snd-powermac no longer handles any machines with a layout-id property in the device-tree, use snd-aoa.

---

### Post by vlotho on 2016-02-19
luigi, 
know you where I can find 2 GB memory modules for power mac g5, and that is 100% functional ?

---

### Post by luigiburdo on 2016-02-20
standard pc not ecc are working on my quad without problems.
in any way note: only 2gb can be assigned for a app this because the 32bit oses (osx,linuxppc) it means you can have 16gb but one app will use max 2gb

---

### Post by rsalvaterra on 2016-04-18
> **luigiburdo said:**
> Use the Apple PPC flashed in Pcie 16x and the radeonhd on pcie 8x (usually the 3rd from the bottom)
you need 2 monitors or a monitor who have two video exit because one is for the apple flashed the other is for the radeonhd 
Is not possible have the video on the not flashed video board from beginning because open firmware access to the flashed bios video board 
Hi, Luigi!

Have you tried using the Radeon on the PCIe x16 slot? I'm using Ubuntu MATE 16.04 on a Power Mac G5 (DC 2,3 GHz), and the Open Firmware GeForce 6600 works perfectly (with the usual nouveau caveats) on an 8x slot. Still, if I install a Radeon HD 6450 (CAICOS) on the x16 slot, it fails initialisation with:```
[drm:.r600_ring_test [radeon]] *ERROR* radeon: ring 0 test failed (scratch(0x8504)=0xCAFEDEAD)
```I haven't tried yet using the Radeon on another slot. If it works, I'd wager it's probably related to the DART IOMMU (while the other slots are connected to a PCIe bridge on the HyperTransport bus, the x16 slot is directly connected to the U4 northbridge, and 64-bit DMA capable devices on that slot can bypass the DART) and/or some endianness issue, and a kernel (DRM?) fix should be sought after. I really wouldn't want to use the Radeon on a slot other the x16, as it would be rather crippled by the DART and the lack of bandwidth (the Mac is PCIe 1.0, let's not forget).
I also found this bug report: [https://bugs.freedesktop.org/show_bug.cgi?id=89886](https://bugs.freedesktop.org/show_bug.cgi?id=89886), which seems to be related, but misattributed to the X11 DDX driver.

Thanks,

Rui

---

### Post by kotzen.hank on 2016-05-07
> **vlotho said:**
> the link for ubuntu mate is dead everywhere

Hi Vlotho,you have the iso of Ubuntu Mate 14.04 powerpc ?  The link on the official website is Dead!

---

### Post by luigiburdo on 2016-05-08
> **rsalvaterra said:**
> Hi, Luigi!

Have you tried using the Radeon on the PCIe x16 slot? I'm using Ubuntu MATE 16.04 on a Power Mac G5 (DC 2,3 GHz), and the Open Firmware GeForce 6600 works perfectly (with the usual nouveau caveats) on an 8x slot. Still, if I install a Radeon HD 6450 (CAICOS) on the x16 slot, it fails initialisation with:```
[drm:.r600_ring_test [radeon]] *ERROR* radeon: ring 0 test failed (scratch(0x8504)=0xCAFEDEAD)
```I haven't tried yet using the Radeon on another slot. If it works, I'd wager it's probably related to the DART IOMMU (while the other slots are connected to a PCIe bridge on the HyperTransport bus, the x16 slot is directly connected to the U4 northbridge, and 64-bit DMA capable devices on that slot can bypass the DART) and/or some endianness issue, and a kernel (DRM?) fix should be sought after. I really wouldn't want to use the Radeon on a slot other the x16, as it would be rather crippled by the DART and the lack of bandwidth (the Mac is PCIe 1.0, let's not forget).
I also found this bug report: [https://bugs.freedesktop.org/show_bug.cgi?id=89886](https://bugs.freedesktop.org/show_bug.cgi?id=89886), which seems to be related, but misattributed to the X11 DDX driver.

Thanks,

Rui

Hi Rui i sow your post in bugtracker :-) 
... after all my test i understand many things we have to fix many walls there
First : RadeonHD 4650 work with 3d too on lastest kernels and now only in 16x slot but is really unstable ... system keep freezing after some time .
the others radeonhd o last kernels works only in 16x but have the drm error.
Second wall: Xorg become buggy with two video boards take the append variable but make exactly the opposite ... eg if i write radeon.modeset=1 ... xorg understand like i been appended radeon.modeset=0
this make no video working .
Third wall lastest kernel ... 4.6 rcs are more worst then oldest kernels : my radeonhd 6570 dont work on 4.6 but work my 5450 but with drm error.
With Lubuntu 14.0.4.3 all the video boards tested by me was working... without any issues.... we are facing a big regression on ppc ...

---

### Post by Wai_Ho on 2016-06-25
I want to say a big thank you, a year after your original post.
Today I booted and installed, after struggling for a week, Ubuntu Mate 16.04 powerpc on my PowerMac G5 (PowerMac 11,2) dual 2.3 GHz, Nividia Geforce 6600 graphic card with the yaboot 
Live video=offb:off video=nouveaufb:off video=radeonfb:off nouveau.modeset=1 radeon.modset=0

---

### Post by luigiburdo on 2016-06-27
Really glad about,
enjoy :-)

---

### Post by chdrsto on 2016-08-06
Hi luigi
Did you (somehow) manage to run Ubuntu (>14.04.2) with 3D acceleration on Radeon HD Graphics?

---

### Post by luigiburdo on 2016-08-08
> **chdrsto said:**
> Hi luigi
Did you (somehow) manage to run Ubuntu (>14.04.2) with 3D acceleration on Radeon HD Graphics?
 
i been try all the way but nothing to do, i dont understand where is the issue if in drm or in xorg or in the radeon driver.
if acceleration is enabled lightdm freeze and system become unusable

---

### Post by chdrsto on 2016-08-21
Hi luigi. I have a three Display setup on my G5 with two graphics (a Apple-nvidia and ATI HD6770) . All displays are the same size and run @1920x1080. One display is plugged via DVI on the still existing nvidia card, the other two are plugged on the radeon HD6770.

Last week i have installed 16.10 alpha and I was able to setup a clear picture on the nvida screen. Even 3D acceleration is working on this card.

But when I activate the two other screens via display center, I get a scrambled screen.
[ATTACH=CONFIG]270782[/ATTACH]

[ATTACH=CONFIG]270783[/ATTACH]

Im sure this must be a fixable issue but I dont know where to look at.

---

### Post by luigiburdo on 2016-08-23
hi Chdrstro
just today i made a test . and i have ubuntu mate 15.10 full 3d accelerated with audio working on RadeonHD 4650 
i can play 360g video on youtube at 1080p  too:-P
Im using my own kernel here . this is my xorg.conf check it on 16.10 if you are lucky.
after i will share my 47 kernel if you have issue there hope will fix
[IMG]https://scontent-mxp1-1.xx.fbcdn.net/t31.0-8/14115618_10206981680362067_4321787905399049322_o.jpg[/IMG]


```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
    Load "dri3"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                "1"
        #Option     "ShadowFB"               # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "WrappedFB"              # [<bool>]
        #Option     "GLXVBlank"              # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "PageFlip"               # [<bool>]
        #Option     "SwapLimit"              # <i>
        #Option     "AsyncUTSDFS"            # [<bool>]
        #Option     "AccelMethod"            # <str>
    Option "Dri" "1"
    Option "Dri3" "1"
    Option "RenderAccel" "0"
    Identifier  "Card0"
    Driver      "radeon"
    BusID       "PCI:10:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "Accel" "1"
        #Option     "SWcursor"               # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "ColorTiling"            # [<bool>]
        #Option     "ColorTiling2D"          # [<bool>]
        #Option     "RenderAccel"            "0"
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "AccelMethod"            # <str>
        #Option     "ShadowPrimary"          # [<bool>]
        #Option     "EXAVSync"               # [<bool>]
        #Option     "EXAPixmaps"             # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "DeleteUnusedDP12Displays"     # [<bool>]
        #Option     "DRI3"                   # [<bool>]
        #Option     "DRI"                    "1" 
        #Option     "TearFree"               # [<bool>]
    Identifier  "Card1"
    Driver      "radeon"
    BusID       "PCI:10:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    Defaultdepth 24
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    #Defaultdepth 24
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


```

---

### Post by chdrsto on 2016-08-23
Hi Luigi.

Wow, sounds great.
Can you give me a link to the kernel you've used? What kind of boot options do you use?

---

### Post by luigiburdo on 2016-08-23
i will share my last kernel on drop box tomorrow i will build the 4.8, test and share.
im using the usual appends in the beginning of my guide.
note the radeon is on 16x now ... on 8x dont work.

---

### Post by chdrsto on 2016-08-23
Thanks for your support.
Do I still have to do the task with removing[COLOR=#000000] xserver-xorg-video-fbdev, etc.?[/COLOR]

---

### Post by luigiburdo on 2016-08-24
> **chdrsto said:**
> Thanks for your support.
Do I still have to do the task with removing[COLOR=#000000] xserver-xorg-video-fbdev, etc.?[/COLOR]

no isnt needed now.

---

### Post by luigiburdo on 2016-08-24
Bad news, the 3d continue only working on 4650 i tested on 5450 and there continue be the fence error . itt means you will have only fbdev mode

---

### Post by chdrsto on 2016-08-24
Hi Luigi.
This sounds bad.
But could you still share the kernel youre using or at least the .config file. I will give it a try.
With the fences-error, you mean the issue I've posted on [#171]("https://ubuntuforums.org/showthread.php?t=2274612&p=13533939#post13533939") or is it differently?

---

### Post by luigiburdo on 2016-08-24
no, issue is different.
with  a fence ring error you have video 2d on radeonhd working but not 3d acceleration. 
the video work ok only in fbdev, this become because this kind of error made the gpu reset all the time because the composition dont run right.

---

### Post by Casey_C on 2016-09-02
Hey Luigi, 
Have you written installation procedure for 15.10?  Is it the same as for 14.04?  
I've been trying and trying 16.04 but no luck, I think resulting from issue with systemd and vga arbiter :( 

> **luigiburdo said:**
> Ok guys because many people ask me here and there and on youtube and on g+ the same info i make this thread .
Please read this instruction and do exactly the same thing.
...
Luigi

---

### Post by luigiburdo on 2016-09-02
[ATTACH=CONFIG]270967[/ATTACH]

this is my 15.10 append (or live) 

     append="nouveau.modeset=0 video=nouveaufb:off radeon.modeset=1 video=radeonfb:off pci=realloc radeon.agpmode=-1 radeon.dpm=1 quiet splash"

im using the 4650 hd on pcie 16x and nv 7800gtx on 8x

On 15.10 the only difference is there is not need to delete the xserver-fbdev

kernel link attached 
[URL="https://www.dropbox.com/s/tle6q3te9n7ip8b/Quad-kernel48-4.tar.gz?dl=0"]https://www.dropbox.com/s/tle6q3te9n7ip8b/Quad-kernel48-4.tar.gz?dl=0

[/URL]

---

### Post by Casey_C on 2016-09-02
Awesome thanks! I'll try it out this weekend :)

---

### Post by apple-apple on 2016-09-11
Hey Luigiburdo just wanted to give you a big thank you! You've inspired me to get Linux running on my ppc with all your YouTube videos. Now Ive got Ubuntu Mate up and running with 16.04 and a Radeon hd 4550 on my late 2005 dual core 2ghz g5 powermac.

---

### Post by luigiburdo on 2016-09-11
> **apple-apple said:**
> Hey Luigiburdo just wanted to give you a big thank you! You've inspired me to get Linux running on my ppc with all your YouTube videos. Now Ive got Ubuntu Mate up and running with 16.04 and a Radeon hd 4450 on my late 2005 dual core 2ghz g5 powermac.

happy to read this :-)

---

### Post by chdrsto on 2016-09-14
Hi Luigi

I still assume that this is only going to work with a HD4x graphic card. ... I use an 6770 and this will be an issue, right?

---

### Post by luigiburdo on 2016-09-14
> **chdrsto said:**
> Hi Luigi

I still assume that this is only going to work with a HD4x graphic card. ... I use an 6770 and this will be an issue, right?

from 14.0.3 of lubuntu i dont find a distro who is gave 3d acceleration working with 5xxx to 6xxx and 7xxx . with 6xxx i suggest use the lubuntu 14.0.3 is working good and is updated with firefox 47 and you can build there lastest mesa too ... just hope someone will made finally working again xorg ... because xorg is gaving  issues on lastest distros.

---

### Post by Casey_C on 2016-09-15
Luigi, 
Do you think xorg is broken or systemd? If it is xorg broken, I think X1000, X5000 and Sam would have the same problem?  I was thinking maybe problems are something to do with systemd.  With sysvinit and upstart I've always been able to make Ubuntu and Debian distros work with Radeon HD 4650.  Now they've switched to systemd I can get Ubuntu working only on OF nvidia, but not Radeon.  Perhaps something to do with how systemd starts driver modules or how it interacts with vga arbiter?  Not sure...  
Have you tried using systemd-shim with upstart-core or sysvinit-core on 16.04 or 16.10?  I wanted to try because on Debian 7 I made an echo boot script that removed the pci slot with the OF nvidia card so xorg saw only the radeon but it only works with sysvinit.

---

### Post by apple-apple on 2016-09-17
Luigiburdo- I spoke too soon, I've got a huge favor to ask of you. If I remember correctly you have 16.04 installed on your amiga. Is there any way that you could upload your working r600_dri.so and libGL.so.1.2.0 for me? I think it may work on my powermac. Turns out I have the wrong color problem after all, and I am having no luck with the unofficial patches. Probably because the mesa version is wrong, I'm on 11.2.0-1

Hmmm..... Looks like you now have 16.10 installed. It looks like Yakkety runs mesa 12.0.1. Did you do anything else with mesa when you upgraded? Or did it work out of the box?

I'm thinking I may add the testing repos from ubuntu and try mesa 12.0.1 out.

---

### Post by luigiburdo on 2016-09-17
> **apple-apple said:**
> Luigiburdo- I spoke too soon, I've got a huge favor to ask of you. If I remember correctly you have 16.04 installed on your amiga. Is there any way that you could upload your working r600_dri.so and libGL.so.1.2.0 for me? I think it may work on my powermac. Turns out I have the wrong color problem after all, and I am having no luck with the unofficial patches. Probably because the mesa version is wrong, I'm on 11.2.0-1

Hmmm..... Looks like you now have 16.10 installed. It looks like Yakkety runs mesa 12.0.1. Did you do anything else with mesa when you upgraded? Or did it work out of the box?

I'm thinking I may add the testing repos from ubuntu and try mesa 12.0.1 out.

Hi, 
no i have only 15.10 and 14.0.3 installed on my quad g5 where on 15.10 im running it with fbdev because radeonhd 4650 freeze after some time on 15.10 and up.
i have 16.10 on X5000.
from mesa 11.x you dont need to patch it any more ... just build and install 
i build like this:

```

./configure
--enable-gallium-llvm    --enable-va  --enable-vdpau  --enable-xvmc --enable-gbm  --enable-gallium-osmesa   --with-gallium-drivers=r600,swrast  --with-dri-drivers=swrast,radeon  --with-egl-platforms=x11,drm --enable-texture-float  --enable-glx-tls 

```

---

### Post by ernsteiswuerfel on 2016-09-18
> **apple-apple said:**
> 
Hmmm..... Looks like you now have 16.10 installed. It looks like Yakkety runs mesa 12.0.1. Did you do anything else with mesa when you upgraded? Or did it work out of the box?
mesa-12.0.x fixed the color problem and another severe bug ([https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1432949](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1432949)) for me, and it did work just out of the box. But my machine is an AGP PowerMac G5 with an older r300-class radeon.

Xenial 16.04.2 LTS will have the same driver stack like 16.10, therefore mesa-12.0.x. At least that's the way it goes on amd64.

---

### Post by luigiburdo on 2016-09-19
> **ernsteiswuerfel said:**
> mesa-12.0.x fixed the color problem and another severe bug ([https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1432949](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1432949)) for me, and it did work just out of the box. But my machine is an AGP PowerMac G5 with an older r300-class radeon.

Xenial 16.04.2 LTS will have the same driver stack like 16.10, therefore mesa-12.0.x. At least that's the way it goes on amd64.

Honestly,
mesa fixes are only in OpenGL, gles1 and gles2 have and continue have wrong colors ... and there is not a working patch or fix for it.

---

### Post by ernsteiswuerfel on 2016-09-22
> **luigiburdo said:**
> Honestly,
mesa fixes are only in OpenGL, gles1 and gles2 have and continue have wrong colors ... and there is not a working patch or fix for it.
Ah i see. Which programs/games use  gles1 or gles2? I am curious to test around a little bit.

---

### Post by apple-apple on 2016-09-23
Well, looks like I was wrong. I kept messing with the drivers. In fact I did learn how to build and install newer versions of the mesa drivers. Yay! Never thought I'd be doing that. But the colors kept showing up wrong. So I tried a different game; Open Arena and it worked great! Then I kept messing around until I broke my install and reinstalled the Mate all over again. But guess what? The radeon displayed the correct colors from the start. The entire time it was just a problem with Alien Arena.

This is a short video of Open Arena on my system:
[http://youtu.be/G0Ojss_abSw](http://youtu.be/G0Ojss_abSw)

---

### Post by apple-apple on 2016-09-23
BTW, has anybody gotten a current version of Minecraft to run?

---

### Post by luigiburdo on 2016-09-24
Alien Arena use egles or egles2 there the color are wrog and never fixed ... we are screeming from years for have this endianess fixed.

---

### Post by csae2608 on 2017-02-25
Hello ,

i have installed Debian Wheezy 7.11 on ma Powermac G5 Quad with Nvidia GTX7800 and it got installed easily and sound now works after 

blacklisting
snd-powermac in /etc/modules/
all the modules in /etc/modprobe.d/blacklist.local.conf

as show in this great video [https://www.youtube.com/watch?v=c8q2WWkuvbc](https://www.youtube.com/watch?v=c8q2WWkuvbc)


now i have installed on top of the nvidia gtx7800 (uses 2slots) a radeon hd6570 , maybe that was bad idea, as the fans are full spinning now. why should i use the radeonhd and should i put it in the uppest slot (for better cooling)? is it true that i cannot use the radeonhd with debian?

Thanks

---

### Post by luigiburdo on 2017-02-27
Hi my friend,
you can use the radeonhd in the 16x slot but without gpu acclerations : 
only fedora,suse,ubuntu debian sid works .

I been opened a msg bug about : 
radeon 5xxx and 6xxx serie
[https://bugs.freedesktop.org/show_bug.cgi?id=99851](https://bugs.freedesktop.org/show_bug.cgi?id=99851)

radeon 7xxx and Rx serie:
[https://bugs.freedesktop.org/show_bug.cgi?id=99859](https://bugs.freedesktop.org/show_bug.cgi?id=99859)

mesa color issue on gles and gles2 
[https://bugs.freedesktop.org/show_bug.cgi?id=99638](https://bugs.freedesktop.org/show_bug.cgi?id=99638) 

I hope you will join the bugzilla and add your issue too :)
Luigi

---

### Post by csae2608 on 2017-03-05
hello luigi,

thanks, i tried once more with

lubuntu 14.04.05 LTS powerpc image

and your line "[COLOR=#000000][FONT=Ubuntu Mono]live video=offb:off video=radeonfb:off video=nouveaufb:off radeon.modeset=1 nouveau.modeset=0"[/FONT][/COLOR][COLOR=#000000]

it would show bootscreen on radeonhd6570 (hooked to 2nd vga monitor) instead of nvidia (hooked to 1st vga monitor) but after finishing booting, it would show black screen on both monitor.

i still have a debian stretch powerpc image on dvd, do you mean that one as debian sid?

don't have any experience with fedora or suse, therefore id' stick with debian & ubuntu atm.
[/COLOR]
[COLOR=#000000][/COLOR]

it would work, but only with 14.04.02 image and not with 14.04.5 LTS, but now i don't have internal audio, just ati hdmi ; but i don't have any hdmi speaker or monitor. what to do to get sound?

it would work, but only with 14.04.02 image and not with 14.04.5 LTS, but now i don't have internal audio, just ati hdmi ; but i don't have any hdmi speaker or monitor. what to do to get sound?

---

### Post by luigiburdo on 2017-03-05
> **csae2608 said:**
> it would work, but only with 14.04.02 image and not with 14.04.5 LTS, but now i don't have internal audio, just ati hdmi ; but i don't have any hdmi speaker or monitor. what to do to get sound?

install kmix and pulse. Radeon have is audio card running from hdmi ;-) in any way snd-oae powermac works too but you have to switch the mixer configurations

---

### Post by csae2608 on 2017-03-05
i got sound after using dp to hdmi adapter and hooking everything up to a tv with hdmi ... yes, and only after installing pulseaudio (which i#d like to avoid) ... but the system is still very unstable ... and it shows up on alsamixer only s/pif digital hdmi and no internal soundcard, maybe i blacklisted accidentally .

now i think of installing debian and then later hooking on the monitor on the radeon ... but don't know how to accomplish this; in fact there is no "live" option in the debian installer so your walkthrough won't work with debian wheezy ... i used xbmc on wheezy but the graphics is very weak , but at least i can listen to ansa news via internal speaker very good. output via hdmi on the tv is very poor ... don't know why, though.

---

### Post by luigiburdo on 2017-03-06
> **csae2608 said:**
> i got sound after using dp to hdmi adapter and hooking everything up to a tv with hdmi ... yes, and only after installing pulseaudio (which i#d like to avoid) ... but the system is still very unstable ... and it shows up on alsamixer only s/pif digital hdmi and no internal soundcard, maybe i blacklisted accidentally .

now i think of installing debian and then later hooking on the monitor on the radeon ... but don't know how to accomplish this; in fact there is no "live" option in the debian installer so your walkthrough won't work with debian wheezy ... i used xbmc on wheezy but the graphics is very weak , but at least i can listen to ansa news via internal speaker very good. output via hdmi on the tv is very poor ... don't know why, though.

Did you installed the card on the 8x slot and the apple firmware on 16x?
Strange you have this issue what gpu are you using my friend?

---

### Post by csae2608 on 2017-03-07
yes, i think so, i have nvidia gtx7800 (256mb, uses 2 lanes) as apple card, and in the next lane i have radeon hd 6570 (1gb, 3rd lane from down).
i got the sound working after installing pulseaudio and tinkering with blacklists ... but today i updated by accident and now i am on 14.04.5 LTS and can no longer access the Graphical User Interface.
Do i need to install your kernel 4.4? How can i do that? Or do i need to refresh the settings for Xorg? i am quite newbie to linux.

now i have another problem , i installed alongside osx and lubuntu 14.04.02 (now 14.04.5 LTS after udpate) on a second harddrive (intel ssd) a fresh debian jessie install (new boot, ext4, swap) , but when i restart, and at yaboot choose linux, i can not start, neither lubuntu nor debian. what need i do to have multi-linux-osx setup?

---

### Post by luigiburdo on 2017-03-11
> **csae2608 said:**
> yes, i think so, i have nvidia gtx7800 (256mb, uses 2 lanes) as apple card, and in the next lane i have radeon hd 6570 (1gb, 3rd lane from down).
i got the sound working after installing pulseaudio and tinkering with blacklists ... but today i updated by accident and now i am on 14.04.5 LTS and can no longer access the Graphical User Interface.
Do i need to install your kernel 4.4? How can i do that? Or do i need to refresh the settings for Xorg? i am quite newbie to linux.


umm really a big problem xorg on 14.4.5 made issue with 6570 the only way now is work in fbdev

---

### Post by luigiburdo on 2017-03-11
> **csae2608 said:**
> now i have another problem , i installed alongside osx and lubuntu 14.04.02 (now 14.04.5 LTS after udpate) on a second harddrive (intel ssd) a fresh debian jessie install (new boot, ext4, swap) , but when i restart, and at yaboot choose linux, i can not start, neither lubuntu nor debian. what need i do to have multi-linux-osx setup?

you need to mod yaboot.conf or press tab in yaboot screen  . when boot: appear

---

### Post by este.el.paz on 2017-05-11
Fellow PPC users . . . slight adjustment to the topic, but, it seems like my PowerMac 3,1 running U-MATE 16 . . . has passed to the great computer junkyard in the sky . . . .  Even though PPC has been mercilessly dropped from support, I still like the PPC machines . . . but, it seems like trying to find robust G5 PPC machines might be a challenge as many are getting close to ten years old--I'm wondering if there are any reliable sources for used AmigaOne's that might be "reasonable" and available in the US???

Feasible?  Or, there are plenty of G5's that are healthy and very zippy still available for . . . cheap??

TIA

e.e.p.

---

### Post by ernsteiswuerfel on 2017-05-18
> **este.el.paz said:**
> I'm wondering if there are any reliable sources for used AmigaOne's that might be "reasonable" and available in the US???

Feasible?  Or, there are plenty of G5's that are healthy and very zippy still available for . . . cheap??

I would go for the PowerMac G5 11,2 air cooled models. Faster and by far cheaper than used AmigaOne X1000's would be. ;) The are robust, more silent than the 7,2/7,3 models and got PCIe-slots.

---

### Post by este.el.paz on 2017-05-18
> **ernsteiswuerfel said:**
> I would go for the PowerMac G5 11,2 air cooled models. Faster and by far cheaper than used AmigaOne X1000's would be. ;) The are robust, more silent than the 7,2/7,3 models and got PCIe-slots.

@ernst:

Hey bud, long time no hear, etc, and thanks for the post . . . I'll look into it, I have a bunch of data on an IDE HD running PPC apps that needs a home.  Long live PPC!!!  :confused::mad::(:)

e.e.p.

---

### Post by ernsteiswuerfel on 2017-05-19
@este.el.paz:

The G5's have SATA HDs (keep in mind to use ideally SATA-1 drivers or SATA-2 at most, the SATA-controller is very picky with SATA-3 HDs). There is IDE, but only used for connecting the DVD drive. Of course you can plug it off to copy the data from the IDE HDs, but I doubt there is enough space to run the DVD drive and an IDE HD simultaneously.

I am less active on the Ubuntu side as the only machine left where I regularly run Ubuntu MATE is my PG G4. The G5's are much better off with Gentoo, as the software stack is much more recent and they are fast enough for the compiling stuff.

---

### Post by este.el.paz on 2017-05-19
> **ernsteiswuerfel said:**
> @este.el.paz:

The G5's have SATA HDs (keep in mind to use ideally SATA-1 drivers or SATA-2 at most, the SATA-controller is very picky with SATA-3 HDs). There is IDE, but only used for connecting the DVD drive. Of course you can plug it off to copy the data from the IDE HDs, but I doubt there is enough space to run the DVD drive and an IDE HD simultaneously.

I am less active on the Ubuntu side as the only machine left where I regularly run Ubuntu MATE is my PG G4. The G5's are much better off with Gentoo, as the software stack is much more recent and they are fast enough for the compiling stuff.

@ernst:

Appreciate the further details . . . it probably would be "too much" to expect that the hardware would remain "consistent" in apple products from year to year . . . obviously they are trying to build obsolescence into everything, making it "cheaper" to buy new than to try to retrofit stuff into a platform.  But, no worries . . . have to decide whether I will buy back into PPC line or finally drop it and move forward.  Only working PPC is my iBook . . . cpu too slow and RAM way under the minimum--Lubuntu is loaded on that one.

But, HD's aren't too expensive, so if I would just copy the data over to whatever drive comes with any G5er I might go for, not too much of a loss . . . .  I see that I have a "GenToo AMD" DVD burned, but, possibly the install process was too "obtuse" for me, or they said they were "dropping support for PPC" ???  so I didn't move forward with the switch; but advice taken, if I get to G5 then I'll try to check it out again . . . for the "newness."

I have now a '12 MacPro with a 1TB regular HD which I have sliced up, 10.9 in one partition, 10.12 in another, and then various Ubuntu-MATE, as well as OpenSuse stable . . . right now my favorite squeeze is Gecko MATE . . . very clean interface, simple . . . nice distro of OpenSuse that works out of the box . . . for the Intel side of linux I do like OpenSuse . . . might check out the "Tumbleweed" side of things coming up later in the year . . . just for "kicks."

Take care,
e..

---

