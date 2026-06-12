---
title: "Will ubuntu install on a Compaq Presario V3019US?"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by Ucidalin on 2006-08-11
I have been trying to make the move over to Linux being a PC support and web developer. I just purchased the Compaq Presario V3019US, and I tried Fedora Core 5, it installed and work all except the network and sound wound not work. I tried Debian 3.1 and it did not recognize my SATA drive. I have read up and found out for myself that Grub does not work well with SATA drive. Thanks Compaq for the refresh CDs.
I have heard lots of good things about ubuntu. So I would love to try it. This notebook has:

Microprocessor: 1.6GHz AMD Turion™ 64 X2 Mobile Technology TL-50
Memory: 1024MB 533MHz DDR2 System Memory 
Video Graphics: NVIDIA GeForce Go 6150 
Hard Drive: 80GB (5400RPM) Hard Drive (SATA) 
Multimedia Drive:Super Multi 8X DVD±R/RW
Display: 14.1” WXGA High-Definition Widescreen(1280 x 800) 
Network Card: Integrated 10/100BASE-T Ethernet LAN & 802.11b/g WLAN 

Thanks in advance,
Ucidalin

---

### Post by robins_web on 2006-08-11
I've got Ubuntu running on my Presario 2200US. I don't know what kind of hard drive it has, because Compaq/HP doesn't have that information available anywhere on their website.

But I've had no problems in over a year.

---

### Post by Ucidalin on 2006-08-11
> **robins_web said:**
> I've got Ubuntu running on my Presario 2200US. I don't know what kind of hard drive it has, because Compaq/HP doesn't have that information available anywhere on their website.

But I've had no problems in over a year.

Thanks for the reply...

The 2200US seams to have:
Video Graphics:  Intel Extreme Graphics 2  
Hard Drive:      IDE40GB (4200RPM) Hard Drive
[http://h10025.www1.hp.com/ewfrf/wc/genericDocument?cc=us&docname=c00251279&lc=en&jumpid=reg_R1002_USEN]("http://h10025.www1.hp.com/ewfrf/wc/genericDocument?cc=us&docname=c00251279&lc=en&jumpid=reg_R1002_USEN")

~Ucidalin

---

### Post by patrick295767 on 2006-08-11
presario 1685 works great

only reboot / halt not working

---

### Post by Ucidalin on 2006-08-11
> **patrick295767 said:**
> presario 1685 works great

only reboot / halt not working

Thanks Patrick... :) 
 The problems I will have will be with the..
 Video Graphics:  NVIDIA GeForce Go 6150 
 Hard Drive:      80GB (5400RPM) Hard Drive (SATA)

---

### Post by fooblah on 2006-10-30
There is now a wiki for V3000 series and other hp laptops where solutions and information can be pooled.  Check out:

[http://hpwiki.cactii.net/hpwiki/Presario_V3%2A%2A%2A]("http://hpwiki.cactii.net/hpwiki/Presario_V3%2A%2A%2A")

---

### Post by Ucidalin on 2006-11-22
Thanks fooblah.  I will check this out.
I have still not gotten any version to work great on the V3019US.

---

### Post by Bachstelze on 2006-11-22
Sarge is pretty old so it's kernel lacks lots of modern hardware support. Ubuntu will be just fine, and Etch too if you still want to use Debian.

---

### Post by Delkster on 2006-11-22
> **Ucidalin said:**
> I just purchased the Compaq Presario V3019US, and I tried Fedora Core 5, it installed and work all except the network and sound wound not work.

The Ubuntu Desktop CD works both as a live CD and as an install disc. You can boot from it (it'll be slow running directly and entirely from the CD but it's usable enough to check things out) and see if the sound and network work.

---

### Post by mastapsi on 2006-12-09
Yes ubuntu will work with the V3000, but only with some love.

Sound and wired network work with out of the box. 
            Note:  Make sure that the Ethernet cable is plugged in before you boot, otherwise it will take some tweaking to get the network to work, cause it gets the local host address wrong for some reason.

Wireless takes some some love.  I myself never got it to work, but there have been new methods created since I tried that people have said works.  I would try this, but my harddrive recently failed:( .  I am actually using the Ubuntu Live CDs right now to use my laptop.

The display drivers take some love too.  I was prolly doing something wrong, but I had to manually edit Xorg.conf to display widescreen native resolutions.

Never tried Bluetooth, since I don't have any Bluetooth devices.

---

### Post by lien_meat on 2007-02-18
Yes...yes it will!  I have the V3015nr which seems to have the exact same hardware accept the HD is an 80gb sata.  I got video, wifi, AND sound(the headphone jack will NOT work out of the box so you have to do what I did) working correctly using **64 bit dapper**.  For some reason this seems not to work in ANY other distrobution I've tried or kernel.  I don't know why.  I tried 32bit dapper and it doesn't work either, neither does 32 or 64 bit edgy for me.  There are some hoops to jump through though.

I had to do this:
Use apt-get or synaptic to install the nvidia-glx drivers.

$ sudo apt-get install nvidia-glx

And then you have to edit /etc/X11/xorg.conf to use the nvidia driver instead of the nv driver.

$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
$ sudo gedit /etc/X11/xorg.conf

Make your xorg.conf look like this in the "Device" Section:
```

Section "Device"
	Identifier	"NVIDIA GEFORCE go 6150"
	Driver		"nvidia"  [COLOR="Red"]Change from nv to nvidia.[/COLOR]
	BusID		"PCI:0:5:0" 
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GEFORCE go 6150"
	Monitor		"Generic Monitor"
	DefaultDepth	24

```

Also...you probably want to add 1280x800 as a resolution to the 24 bit depth.  This way you will get this screens native resolution...

OK...on to wifi...
I'm guessing you have the Broadcom 4311 wifi in it.  This is the hardest of any broadcom card to get working.  It's absolutely terrible.  This is what I did to get it working:

    * .install all the development packages ( linux-kernel-devel & linx headers )
    * download the latest ndiswrapper source and extract it.
    * go into the extracted directory and do
          o make & sudo make install

    * . get the wireless drivers from Compaq's website as the ones on the windows partition are 32 bit ones and linux needs the compaq 64-bit versions to work. Get cabextract and get it to extract the compaq drivers exe file using the command
          o cabextract sp33008.exe

    * . there will be a bcmwl5.inf and a bcmwl5.sys file in the current foder. run the command
          o sudo ndiswrapper -i bcmwl5.inf

    * this will install the drivers and doing
          o ndiswrapper -l shows
                + Installed drivers:
                + bcmwl5 driver installed, hardware present

    * Now run
          o sudo ndiswrapper -m

    * Reboot the laptop.

    * Upon startup run
          o sudo modprobe ndiswrapper

    * the wireless modles are now working. run iwconfig and there should be a wlan0 with wireless extensions. yu can now connect to a network using
          o sudo iwconfig wlan0 essid name-of-essid
          o dhclient wlan0

I got this off of a website that I can't seem to find anymore.  It's not my own tutorial for the wireless.  I'm not trying to plagerize!  It was starfleet engineering or something like that...

I do know from my own experience that if you don't install ndiswrapper from source it doesn't work right for this card for some reason.  I used ndiswrapper version 1.31.  It works great for me. Get "wifi radar" to make wireless easier than command line.  It's not as good as some other programs, but I find it's what works best with this card.  Use synaptic to find it.

The headphone jack.  This is what doesn't work in ANY other kernel or distro I've tried.  It will break your sound completely and tell you that you have no alsa devices installed.  If you follow this on edgy or 32 bit dapper even.

1) Go to [http://www.alsa-project.org/](http://www.alsa-project.org/) and download the alsa driver: "alsa-driver-1.0.13"
2) after you untar it, go into the dirrectory and read the "INSTALL" file.  I believe I did a "./configure", then "make", then "make install"  but I feel like there was more to it than that, as I remember it being troublesome for some reason.
3) after you successfuly get the alsa driver compliled(which I hope is easy for you), you have to add a line to your /etc/modprobe.d/alsa-base file.

$ sudo gedit /etc/modprobe.d/alsa-base

At the end of the file, add the line:

options snd-hda-intel index=0 disable_msi=1

That should do it.  Reboot and see.  If not, just take that line out, and your sound should still work. (just without the headphone jack.)

If you need a better explanation of something...ask.  I MIGHT be able to help a bit more...but it's been since christmas when I did all this...

Hope I helped you.

---

