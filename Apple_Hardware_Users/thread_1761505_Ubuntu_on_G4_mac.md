---
title: "Ubuntu on G4 mac?"
date: 2011-05-18
forum: Apple Hardware Users
---

### Post by H16 on 2011-05-18
Hello,
I own old G4 mac with a CD-RW and 2 hdd'&#273; (each of them has 32 GB)
How can i install this port of ubuntu on it?
[COLOR="Red"]--->[Ubuntu 10.04]("http://cdimage.ubuntu.com/ports/releases/10.04/release/")<---[/COLOR]
do i have to upgrade to some special firmware?
i have downloaded desktop and server install iso images and burned them on a CD.
I m going to try it on saturday

---

### Post by rg4w on 2011-05-18
I haven't installed on a Mac except in a VM, so I can't offer any insights on drivers, etc.

But be sure to use the PowerPC build, since of course your G4 is using a PowerPC chip:
[http://cdimage.ubuntu.com/ports/releases/10.04/release/](http://cdimage.ubuntu.com/ports/releases/10.04/release/)

---

### Post by H16 on 2011-05-18
i have downloaded "Mac (PowerPC) and IBM-PPC (POWER5) desktop CD"
I m not sure if it will work with standard mac bios/firmware/whatever it is

---

### Post by jigzat on 2011-05-18
I am trying to install the same version but the server flavor. It is very straight forward process but for some reason it doesn't start up as it should. All I get is an orange display. I can't even get into the command line, I tried to boot with the "Linux single" parameter at yaboot but there is no change. I have made several fresh installs using the entire disk (I don't need Mac OS X on this machine) but there is no change. Any ideas of what can be wrong?

---

### Post by H16 on 2011-05-19
so installation worked but it doesn't boot?

---

### Post by jigzat on 2011-05-19
Yes, installation finished fine. I even tried 11.04 and 10.10 desktop. I know is asking too much to run it on a 10 year old machine after all Ubuntu must advance but it used to install fine in previous versions.

---

### Post by avtolle on 2011-05-19
@OP: how much RAM does your G4 have? 
@jigzat: have you tried ```
Linux video=ofonly
```at the second yaboot prompt?

Another thought: did you check the md5sum of the downloaded iso before burning to cd?

---

### Post by H16 on 2011-05-19
how many RAM do you have? try CTRL+ALT+F1 or F2, F3....
it should enter console

---

### Post by jigzat on 2011-05-19
Hey thank you very much for your fast answer. My machine has 768MB and yes I tried all those key combos and nothing the display remains orange I also tried video=ofonly

---

### Post by avtolle on 2011-05-19
> **jigzat said:**
> Hey thank you very much for your fast answer. My machine has 768MB and yes I tried all those key combos and nothing the display remains orange I also tried video=ofonly

OK, do you know what video chip/card the g4 has? I feel I'm getting to the edge of my expertise here, but that information might be helpful to someone with more knowledge, or it may trigger a memory of a prior thread. TIA

---

### Post by jigzat on 2011-05-19
It has an Nvidia GForce 2 MX 32MB of ram. I know there are a lot of issues with Nvidia cards.

---

### Post by H16 on 2011-05-19
try that server install, it shouldn't install gnome

---

### Post by avtolle on 2011-05-19
> **H16 said:**
> try that server install, it shouldn't install gnome

It doesn't, nor does it install X. I've come to a tentative hypothesis that the cause of the orange screen is due to the video device, and there must be a kernel parameter that can be passed at boot, i.e., at the second yaboot prompt, something like ```
Linux video=*something to do with nvidia*
```but I don't know what that *something* is.

---

### Post by jigzat on 2011-05-19
By the way when I boot the system I can see the ubuntu logo with 4 dots beneath it and after that it goes orange.

---

### Post by Azyx on 2011-05-19
May this be the problem? [http://ubuntuforums.org/showthread.php?t=1640062](http://ubuntuforums.org/showthread.php?t=1640062)

cheers

---

### Post by H16 on 2011-05-20
> **jigzat said:**
> By the way when I boot the system I can see the ubuntu logo with 4 dots beneath it and after that it goes orange.

cool, are you using standard mac firmware/ROM/whatever? :KS

---

### Post by Azyx on 2011-05-20
> **H16 said:**
> cool, are you using standard mac firmware/ROM/whatever? :KS

Yes, but how do I change?
Beside the gfx are slow, the screen does not go really to sleep. The back light are still on when the screen go to sleep.

---

### Post by H16 on 2011-05-20
i asked because i wanted to know if it will work on standard G4 rom

---

### Post by Azyx on 2011-05-20
> **H16 said:**
> i asked because i wanted to know if it will work on standard G4 rom

Yes, but it was not easy and it was poor preformas on newer ubuntu.

PS. not easy is compared to install och x86. It's little confusing with Yaboot for instance and that os-x hdd just to have a lot of very small partitions. Its mostly the grafic thats slow and little ugly compared to os-x. and that the sceen don't really turn of wheh idle.
Have just installed the alternate powerpc natty as cli-powerpc so I just get command line.
One problem i had was when the installer ask for
Ubuntu archive mirror hostname :
there should you type: ports.ubuntu.com
next qestion is:
Ubuntu archive mirror directory :
but there should a defalt appera and work.
After that you get a command line environment

---

### Post by jigzat on 2011-05-20
Well in my case I gave up on installing Ubuntu and went back to Debian. It is not as neat and pretty but it is working.

---

### Post by H16 on 2011-05-20
does anyone know if it is possible to run wine with qemu on G4? (CPU emulation, not system emulation)

---

### Post by Azyx on 2011-05-20
> **jigzat said:**
> Well in my case I gave up on installing Ubuntu and went back to Debian. It is not as neat and pretty but it is working.

After cli-install i installed gnome, ```
sudo apt-get install gnome
``` So now I have some mixed apperance of gnomes standard and Ubuntu. 
What is the problems with Debian?
The reason I want Natty was that i really wanted clementine music player, but I could not get it work on Lucid Lynx LTS for powerpc :( And I also hoped that the powersaving of the screen should have being fixed, o the screen really turn off when idle. Backlight are still on, so I is not totally black.

---

### Post by jigzat on 2011-05-20
Well Debian comes with a pretty much normal gnome desktop environment without the cool ubuntu themes and icons among other things like splashy boot. I have been trying to customize the UI to look more like Ubuntu but right now I don't seem to find a way to add Ubuntu repos, it might be because it is PowerPC.

The latest debian installer doesn't have any issue with the Imac except the one with the NVidia card which I fixed with a pre-configured xorg.conf file for this computer and the eject button doesn't seem to work to close the tray. The rest is fine including power saving features and sound.

What do you mean with "some mixed apperance of gnomes standard and Ubuntu"  I dont know how did you installed Debian but the DVD comes with all the Desktop Managers and installs GNOME by default,  did you installed the first CD only?

---

### Post by Azyx on 2011-05-21
I have now ```
sudo apt-get install ubuntu-desktop
```
 Gnome hade some trouble with  Synaptic. When i click on system-->admin--synaptic, and ttyp  password, it get always wrong. So I need to run sudo synaptic. I hade  the same problem when i tried Debian-freebsd. When i  installed  Ubuntu-desktop that problem get fixed. Do you want to have my repositories  that i have on my powerpc )iLamp)?

cheers

---

### Post by H16 on 2011-05-21
I have tried to put ubuntu desktop CD into my G4, i have found out that i have to install yaboot :D (this is the first time i m installin linux on mac)

can someone help me with installing yaboot? when i googled yaboot, on their website is only source tarball, how to install it?

---

### Post by Azyx on 2011-05-21
> **H16 said:**
> I have tried to put ubuntu desktop CD into my G4, i have found out that i have to install yaboot :D (this is the first time i m installin linux on mac)

can someone help me with installing yaboot? when i googled yaboot, on their website is only source tarball, how to install it?

yaboot are instead of grub. it is on the ubuntu powerpc-cd. other ways it can't boot the cd.

I had problem to manually install boot loader (yaboot) during install, so I erased all big partitions (over 1MB) ecept my OS-X partition.

How far have you come? do the cd boot when you press down 'c' during start? other ways you may first reset nvram.

---

### Post by H16 on 2011-05-21
it doesnt boot from CD correctly, it changes color of mouse to white but keeps coming to boot selection screen (i hold ALT key because when i hold C it booted OS 9.2 from hard disk)

Video:
[http://www.youtube.com/watch?v=Iu71QVTZUhk](http://www.youtube.com/watch?v=Iu71QVTZUhk)

---

### Post by Azyx on 2011-05-21
> **H16 said:**
> it doesnt boot from CD correctly, it changes color of mouse to white but keeps coming to boot selection screen (i hold ALT key because when i hold C it booted OS 9.2 from hard disk)

Video:
[http://www.youtube.com/watch?v=Iu71QVTZUhk](http://www.youtube.com/watch?v=Iu71QVTZUhk)

Hi. I don't recognize the mac?  Are that an g4 with ctr-screen. how much RAMy do you have?

First. Are you sure you burned a boot-cd and not just copied the iso to the cd-r?
If you are sure you have burned in right way, it seems that the nvram (simulare to bios) are change, and not use 'c' for boot cd.
If you dont know the exactly name on you computer so are [http://lowendmac.com/imacs/index.shtml](http://lowendmac.com/imacs/index.shtml) a way to get information about the most thing. what kind of gfx and other kind of things about your mav. Apple change a lot in there hardware and firmware.

---

### Post by H16 on 2011-05-21
> **Azyx said:**
> Hi. I don't recognize the mac?  Are that an g4 with ctr-screen. how much RAMy do you have?

First. Are you sure you burned a boot-cd and not just copied the iso to the cd-r?
If you are sure you have burned in right way, it seems that the nvram (simulare to bios) are change, and not use 'c' for boot cd.
If you dont know the exactly name on you computer so are [http://lowendmac.com/imacs/index.shtml](http://lowendmac.com/imacs/index.shtml) a way to get information about the most thing. what kind of gfx and other kind of things about your mav. Apple change a lot in there hardware and firmware.

It has ati rage 128 MB graphics
512 MB RAM (2x 256 MB rams)
and yes, it is burned correctly, you can see penguin icon in down-right corner of that CD at boot selection
it looks exactly like this one :D
(photo is not by me)
[IMG]http://www.lifeaftercoffee.com/wp-content/uploads/2007/09/img_0499.jpg[/IMG]

---

### Post by Azyx on 2011-05-21
Ahh. nice. I whanted that for a time, but it has soundy fans?

Seems to be this? [http://lowendmac.com/ppc/quicksilver-2002-power-mac.html](http://lowendmac.com/ppc/quicksilver-2002-power-mac.html)

I think.

What OS do you have? I think that If you should install 10.4 Tiger on older mac, you have to upgrade cmos (type bios) with an macos 9 applications. I can remember wrong so you maybee already have the leatast cmos?

---

### Post by H16 on 2011-05-21
i have OS 9.2
about processors, it has two 450 MHz cpu's
and yea, fans are pretty loud :D

---

### Post by Azyx on 2011-05-21
I think you need to change cmos(firmare for the motherboard) so you can run NIX (linux and OS-X) I  have only had iMacs and I don't know if it the same thing with Power  Mac, but probably...  There are a much more differens betwen PowerMac than between iMac. some have agp-grafics and some pci-gfx, so you really need to know your hardware, i think.  [www.lowendmac.com]("http://www.lowendmac.com") [http://lowendmac.com/ppc/yikes-power-mac-g4-pci.html](http://lowendmac.com/ppc/yikes-power-mac-g4-pci.html) are a good place to start with. Also they have some email-group you may join and there are people who have good knolage about mac, even if they may think OS-X is the best ;) But now, that OS-X you can run are Tiger, that are very old, so they are maybe little more open för linux;)

I did not recognize the  boot seqence you showed in the video, so your probably have an old firmvare and not openfirmvare.

here is some firmvare for diffent macs.
[http://support.apple.com/kb/ht1395](http://support.apple.com/kb/ht1395)

cheers and good luck

---

### Post by H16 on 2011-05-21
i have downloaded powermac G4 update 4.2.8 and when i tried to update, it wrote that it is up to date and it is 4.2.8f1 :KS
and yes, it is openfirmware, when i pressed programming button it wrote something about it :D

---

### Post by Azyx on 2011-05-21
> **H16 said:**
> i have downloaded powermac G4 update 4.2.8 and when i tried to update, it wrote that it is up to date and it is 4.2.8f1 :KS
and yes, it is openfirmware, when i pressed programming button it wrote something about it :D

the problem seems to be that you don't det in to openfirmvare, cos ju don't go to the terminal, only pictures and symbol? tried to reset

seing this:
[http://support.apple.com/kb/HT1379](http://support.apple.com/kb/HT1379)

and this:
[http://support.apple.com/kb/TS1812?viewlocale=en_US](http://support.apple.com/kb/TS1812?viewlocale=en_US)

?

---

### Post by H16 on 2011-05-21
it has openfirmware, these pictures and symbols on video is what i see when i hold ALT at boot, it is like graphical boot select menu
when i press programming button at boot, it goes into openfirmware console
by programming button i mean that button under mac's power-on button next to reset button

-i have tried to reset nvram with alt-apple-p-r and still nothing :(

btw: i made picture what it says when i boot into openfirmware console
[IMG]http://imageshack.us/m/862/2695/dsc04058k.jpg[/IMG]

---

### Post by npadger on 2011-05-21
Installing lucid lynx on a powerbook was simple for me. Delete all big partitions except for mac osx, boot from disk (Hold c at startup), run live, install, tell it to use largest free space, wait. It will automatically install and configure yaboot.

---

### Post by Azyx on 2011-05-21
H16.

Good you come in to openfirmware :)
have you tried my second apple.supprt- link upp over?
It says:

If the message still appears after you reset PRAM, reset the Open Firmware settings: 
[LIST=1]
[*]Instead of typing "mac-boot" at the Open Firmware prompt, type: reset-nvram
[*]Press Return.
[*]At the Open Firmware prompt, type: reset-all
[*]Press Return.
[/LIST]
 Example:
 0 > reset-nvram
Press Return
0 > reset-all
Press Return

I just done it on my iLampc, and now my mac always boot from cd then i type 'c' during start.

---

### Post by Azyx on 2011-05-21
by the way, I don't know if I already told yo?, but your mac don't boot to cd?, are you sure you burned the ubuntu.iso and not just copied the ubuntu.iso to the disk?

---

### Post by jigzat on 2011-05-21
yes please, thank you very much, maybe that would help. I am actually setting up a web server but a nice GUI is always welcome.

> **Azyx said:**
> I have now ```
sudo apt-get install ubuntu-desktop
```
 Gnome hade some trouble with  Synaptic. When i click on system-->admin--synaptic, and ttyp  password, it get always wrong. So I need to run sudo synaptic. I hade  the same problem when i tried Debian-freebsd. When i  installed  Ubuntu-desktop that problem get fixed. Do you want to have my repositories  that i have on my powerpc )iLamp)?

cheers

---

### Post by jigzat on 2011-05-21
did you installed Debian-freebsd on your Imac? How? As far as I know is a x86 distro.

> **Azyx said:**
>  I hade  the same problem when i tried Debian-freebsd. When i  installed  Ubuntu-desktop that problem get fixed. Do you want to have my repositories  that i have on my powerpc )iLamp)?

cheers

---

### Post by Azyx on 2011-05-21
> **jigzat said:**
> did you installed Debian-freebsd on your Imac? How? As far as I know is a x86 distro.

No, it was on a pc.

---

### Post by jigzat on 2011-05-22
Yes that would be great, thanks!

> **Azyx said:**
>  Do you want to have my repositories  that i have on my powerpc )iLamp)?

cheers

---

### Post by H16 on 2011-05-22
> **Azyx said:**
> H16.

Good you come in to openfirmware :)
have you tried my second apple.supprt- link upp over?
It says:

If the message still appears after you reset PRAM, reset the Open Firmware settings: 
[LIST=1]
[*]Instead of typing "mac-boot" at the Open Firmware prompt, type: reset-nvram
[*]Press Return.
[*]At the Open Firmware prompt, type: reset-all
[*]Press Return.
[/LIST]
 Example:
 0 > reset-nvram
Press Return
0 > reset-all
Press Return

I just done it on my iLampc, and now my mac always boot from cd then i type 'c' during start.
I will try this next weekend, and yes, it is burned correctly :guitar:

---

### Post by Azyx on 2011-05-22
> **jigzat said:**
> Yes that would be great, thanks!

Here it is. It is placed in /etc/apt/sources.list.  
```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release powerpc (20110426)]/ natty main restricted
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release powerpc (20110426)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ports.ubuntu.com/ubuntu-ports/ natty main restricted
deb-src http://archive.ubuntu.com/ubuntu natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ports.ubuntu.com/ubuntu-ports/ natty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ports.ubuntu.com/ubuntu-ports/ natty universe
deb-src http://archive.ubuntu.com/ubuntu natty universe
deb http://ports.ubuntu.com/ubuntu-ports/ natty-updates universe
deb-src http://archive.ubuntu.com/ubuntu natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ports.ubuntu.com/ubuntu-ports/ natty multiverse
deb-src http://archive.ubuntu.com/ubuntu natty multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ natty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ports.ubuntu.com/ubuntu-ports/ natty-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu natty-backports main restricted universe multiverse

deb http://ports.ubuntu.com/ubuntu-ports/ natty-security main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports/ natty-security main restricted
deb http://ports.ubuntu.com/ubuntu-ports/ natty-security universe
deb-src http://ports.ubuntu.com/ubuntu-ports/ natty-security universe
deb http://ports.ubuntu.com/ubuntu-ports/ natty-security multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports/ natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main

```

---

### Post by H16 on 2011-05-23
i have borrowed tiger CD version from my friend, i will try to install it :D

---

### Post by Azyx on 2011-05-23
> **H16 said:**
> i have borrowed tiger CD version from my friend, i will try to install it :D

nice. if it work, you know that the cd are alright :) By the way..even if i'm not really belive in it, I always burn cd to mac with on lowers speed..(all my mac are old).

---

### Post by H16 on 2011-05-23
> **Azyx said:**
> nice. if it work, you know that the cd are alright :) By the way..even if i'm not really belive in it, I always burn cd to mac with on lowers speed..(all my mac are old).

i m always burning with 4x speed, i don't know why xD

---

### Post by avtolle on 2011-05-23
@H16; your screenshot reveals your date/time are off, which suggests the need for a new battery. [https://help.ubuntu.com/community/UbuntuDateBug](https://help.ubuntu.com/community/UbuntuDateBug) may help you, but IIRC, you will need to reset the date and time through Open Firmware, a process I've not done. I'm sure Google can be your friend here. Good luck.

---

### Post by Azyx on 2011-05-23
> **avtolle said:**
> @H16; your screenshot reveals your date/time are off, which suggests the need for a new battery. [https://help.ubuntu.com/community/UbuntuDateBug](https://help.ubuntu.com/community/UbuntuDateBug) may help you, but IIRC, you will need to reset the date and time through Open Firmware, a process I've not done. I'm sure Google can be your friend here. Good luck.

Deos loss of battery power problem for the mac to boot?

---

### Post by avtolle on 2011-05-23
> **Azyx said:**
> Deos loss of battery power problem for the mac to boot?
Yes, as to booting into Ubuntu, at least. Really, the problem is that the battery problem prevents the correct date from being stored in the CMOS with the power off; this causes boot problems. To boot, the date/time needs to be set correctly (as I said, seems to me this needs to be done from Open Firmware), then when that is done, reboot. Also, a reset of the PRAM may be needed.

---

### Post by avtolle on 2011-05-23
I know the link says this is no longer a problem with Ubuntu. Maybe so, but it seems to me this has occurred post-Gutsy to me, and by resetting the PRAM, I got it to boot, then reset the date/time.

---

### Post by avtolle on 2011-05-23
[http://mauroandres.wordpress.com/2010/04/02/setting-system-time-date-on-debian-gnu-linux-and-open-firmware/](http://mauroandres.wordpress.com/2010/04/02/setting-system-time-date-on-debian-gnu-linux-and-open-firmware/)

Look towards the end of the post for  how to set the time and date from the Open Firmware prompt. HTH.

---

### Post by jigzat on 2011-05-23
How did you manage the issue where it tries to delete the kernel??


> **Azyx said:**
> Here it is. It is placed in /etc/apt/sources.list.  
```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release powerpc (20110426)]/ natty main restricted
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release powerpc (20110426)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ports.ubuntu.com/ubuntu-ports/ natty main restricted
deb-src http://archive.ubuntu.com/ubuntu natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ports.ubuntu.com/ubuntu-ports/ natty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ports.ubuntu.com/ubuntu-ports/ natty universe
deb-src http://archive.ubuntu.com/ubuntu natty universe
deb http://ports.ubuntu.com/ubuntu-ports/ natty-updates universe
deb-src http://archive.ubuntu.com/ubuntu natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ports.ubuntu.com/ubuntu-ports/ natty multiverse
deb-src http://archive.ubuntu.com/ubuntu natty multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ natty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ports.ubuntu.com/ubuntu-ports/ natty-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu natty-backports main restricted universe multiverse

deb http://ports.ubuntu.com/ubuntu-ports/ natty-security main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports/ natty-security main restricted
deb http://ports.ubuntu.com/ubuntu-ports/ natty-security universe
deb-src http://ports.ubuntu.com/ubuntu-ports/ natty-security universe
deb http://ports.ubuntu.com/ubuntu-ports/ natty-security multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports/ natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main

```

---

### Post by H16 on 2011-05-24
do i need any activation key for tiger installation?

---

### Post by Azyx on 2011-05-24
> **H16 said:**
> do i need any activation key for tiger installation?

No that is Windoze madness ;)

---

### Post by H16 on 2011-05-24
> **Azyx said:**
> No that is Windoze madness ;)

cool :D

---

### Post by Azyx on 2011-05-25
> **jigzat said:**
> How did you manage the issue where it tries to delete the kernel??. 

[jigzat]("http://ubuntuforums.org/member.php?u=65726") Well. i really don't know about that.  I installed cli (command line interface) cli from 11.04 natty (alternative) and then installed different gui, that gnome was the first that work. now I have ubuntu-desktop, but the unity-2d have ****** up colours, that is a bugg. but classic-desktop work fine. but there is a big problem and that are that the music drops out then the cpu work to much. If it's puls-audio or other processes i don't know. 

Compared to OS-X tiger here are little more cpu-activity, but the real problems are that impossible to listen to music and do other thing on the computer cos the drop-out :(

Edit. I have now find that the problem with sound-dropout is bigger when I listen from a samba-share with Clementine. Have now put 2000m buffer, but when I open windos or switching work-space it still being drops in sound. Have also only a usb 1.1 to ethernet-adaptor cos the onboard ethernet are broken.

---

### Post by Azyx on 2011-05-25
> **H16 said:**
> cool :D

Tell me how it goes with os-x tiger. 
/cheers

---

### Post by H16 on 2011-05-26
i will get access to my mac in the weekend :KS

---

### Post by H16 on 2011-05-28
I have put installation CD 1 into drive, and it didn't boot from it when i hold C... so i booted into OS 9.2 and started install mac OS X app on CD, it wrote that it was unable to set CD as startup drive :/
can i somehow copy files from CD to hard disk and start installation from it?

---

### Post by H16 on 2011-05-28
rofl, i erased second hard disk, and now it doesn't boot even into openfirmware... WTF? :KS

---

### Post by Azyx on 2011-05-28
> **H16 said:**
> I have put installation CD 1 into drive, and it didn't boot from it when i hold C... so i booted into OS 9.2 and started install mac OS X app on CD, it wrote that it was unable to set CD as startup drive :/
can i somehow copy files from CD to hard disk and start installation from it?

Very strange. I don't know if there are a possibiliy to install and boot on the disk. Do you have Mac 9 CD and can you boot from them? If you can I think there is something with your open-firmware. Another thing is than you probamby can get more help on Low End Mac, especiallt to install OS-X.


I remember you talked about firmware 4.8.2f1, but are that for Power Mac?

[http://support.apple.com/kb/DL1126?viewlocale=en_US](http://support.apple.com/kb/DL1126?viewlocale=en_US)  they talked about 4.8.2 there not 4.8.2f1 as i have in my iMac.

/cheers

---

### Post by H16 on 2011-05-28
[IMG]http://imageshack.us/m/862/2695/dsc04058k.jpg[/IMG]
it is 4.2.8f1 - look at first line of that screenshot

---

### Post by H16 on 2011-05-28
> **H16 said:**
> rofl, i erased second hard disk, and now it doesn't boot even into openfirmware... WTF? :KS


about this problem - i removed 1 RAM (now i have only 256 MB left) and it started to work again

---

### Post by H16 on 2011-05-28
i haven't got os 9 cd, but i tried OS 8, result was the same, it booted OS 9.2 from hard disk

---

### Post by Azyx on 2011-05-31
> **H16 said:**
> about this problem - i removed 1 RAM (now i have only 256 MB left) and it started to work again

seems little strange. have you read about the power mac on lowendmac?

---

### Post by H16 on 2011-06-01
yep, seems like i have powermac G4 dual 450 gigabit ethernet :D

---

### Post by Azyx on 2011-06-01
> **H16 said:**
> yep, seems like i have powermac G4 dual 450 gigabit ethernet :D

And also it must bee Sawtooth with AGP gfx.

---

### Post by Azyx on 2011-06-01
> **H16 said:**
> i haven't got os 9 cd, but i tried OS 8, result was the same, it booted OS 9.2 from hard disk

Does it work with MacOS 8???

---

### Post by H16 on 2011-06-02
it didn't worked with OS 8

---

### Post by oswaldkelso on 2011-06-02
**Unplug** the second HD. Then install Debian job done.

---

### Post by Azyx on 2011-06-02
> **H16 said:**
> it didn't worked with OS 8

..as they said on lowendmac and apples support page..if you hade the last firmware.

---

### Post by Azyx on 2011-06-02
> **oswaldkelso said:**
> **Unplug** the second HD. Then install Debian job done.

How can he install debian, if he cannot boot from cd?

---

### Post by Azyx on 2011-06-02
> **H16 said:**
> rofl, i erased second hard disk, and now it doesn't boot even into openfirmware... WTF? :KS

The disc you erased was it with OS9 on it? It's not good to first erase, it had being better if you unplugged the drive I think. A motherboard with 2 cpu:s are probably quite complicated and many 'norma'l tips are maybee not applieable? How many DRAM-slot do you have? Maybee you haeto move them around? I don't remember if I already told you. but trie to find a e-maillist for your dual cpu-powerpc on for instance on lowendmac there people have the same hardware.

cheers

ps. this g-mac list seems to bee nearest your hardware. [http://lowendmac.com/lists/g-list.shtml](http://lowendmac.com/lists/g-list.shtml) Be specific about your hardware ..dual cpu g4. agp-gfx firmware version and so on and maybe they can help you better?

---

### Post by H16 on 2011-06-03
> **Azyx said:**
> The disc you erased was it with OS9 on it? It's not good to first erase, it had being better if you unplugged the drive I think. A motherboard with 2 cpu:s are probably quite complicated and many 'norma'l tips are maybee not applieable? How many DRAM-slot do you have? Maybee you haeto move them around? I don't remember if I already told you. but trie to find a e-maillist for your dual cpu-powerpc on for instance on lowendmac there people have the same hardware.

cheers

ps. this g-mac list seems to bee nearest your hardware. [http://lowendmac.com/lists/g-list.shtml](http://lowendmac.com/lists/g-list.shtml) Be specific about your hardware ..dual cpu g4. agp-gfx firmware version and so on and maybe they can help you better?
it was the second unused disk, i will use it in my windoze PC :D
i m not going to make another attempts to install ubuntu, i have tried it just for fun :D
thanks for help everyone&#328;
btw, graphics was AGP

---

### Post by oswaldkelso on 2011-06-05
> **Azyx said:**
> How can he install debian, if he cannot boot from cd?

I discovered that one of my G4's was very picky about booting with a second drive connected. I have to unplug it including the power feed to enable boot! I did find some documentation somewhere about my scsi card having trouble with two drives connected.
I spend ages zapping pram, removing batteries, etc. As it can be intermitent I now just unplug the second drive and after a few power up it starts?

---

### Post by H16 on 2011-06-06
> **oswaldkelso said:**
> I discovered that one of my G4's was very picky about booting with a second drive connected. I have to unplug it including the power feed to enable boot! I did find some documentation somewhere about my scsi card having trouble with two drives connected.
I spend ages zapping pram, removing batteries, etc. As it can be intermitent I now just unplug the second drive and after a few power up it starts?

this doesn't boot from CD even without any hard disk

---

### Post by Azyx on 2011-06-06
> **oswaldkelso said:**
> I discovered that one of my G4's was very picky about booting with a second drive connected. I have to unplug it including the power feed to enable boot! I did find some documentation somewhere about my scsi card having trouble with two drives connected.
I spend ages zapping pram, removing batteries, etc. As it can be intermitent I now just unplug the second drive and after a few power up it starts?

Does any g4-mac have scsi-hdd?

---

### Post by Azyx on 2011-06-06
> **H16 said:**
> this doesn't boot from CD even without any hard disk

Have you checked that the cd-drive have right jumper settings? master, slave or cable-select or tested with another cd-player?

---

### Post by H16 on 2011-06-06
> **Azyx said:**
> Have you checked that the cd-drive have right jumper settings? master, slave or cable-select or tested with another cd-player?

yep, i can see CD in OS 9.2, so it should be good

---

### Post by Azyx on 2011-06-06
> **H16 said:**
> yep, i can see CD in OS 9.2, so it should be good

I think MacOS maybe can fixit, if it's wrong, but maybe not the firmware during boot?

---

### Post by H16 on 2011-06-06
> **Azyx said:**
> I think MacOS maybe can fixit, if it's wrong, but maybe not the firmware during boot?

next weekend i will try to change them :popcorn:

---

### Post by H16 on 2011-06-14
it didn't worked

---

