---
title: "Tip: BCM4328 wi-fi on 64-bit Linux"
date: 2007-11-18
forum: Apple Intel Users
---

### Post by Aranel on 2007-11-18
Hey there. I've recently bought one of the new Santa Rosa MacBooks (otherwise known as macbook3,1), which comes with a Broadcom 4328 wi-fi card, and installed 64-bit Gutsy on it. (I believe the new iMacs also come with this wi-fi card, but don't quote me on that.) Since the native bcm43xx driver doesn't even seem to acknowledge the card's existence, I started looking for Windows drivers for use with NdisWrapper. I found one that looked promising for 64-bit Windows and tried it with NdisWrapper, and it worked absolutely flawlessly. Just a quick *ndiswrapper -i bcmwl5.sys && modprobe ndiswrapper*, and that's it.

Anyway, I thought I'd save my fellow 64-bit users some trouble by providing them here. So see the attachment. :)

(Disclaimer: I don't know how this plays with NetworkManager--I installed the server edition of Ubuntu, which of course doesn't come with NetworkManager--but if nothing else, the driver should work with the old-fashioned CLI tools. I also haven't tried this with WPA encryption, but it functions just fine with WEP.)

I hope this helps someone!

---

### Post by Levo75 on 2007-11-18
Can anyone help me with the 32bit version?

So i tried this toturail: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-079fa9ceecfe235b6150966744c4094ef0862956](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-079fa9ceecfe235b6150966744c4094ef0862956)

But i get this when i try to unzip

01:15:08 (40.51 MB/s) - `bcm4328.zip.1' saved [617]

levent@levent-desktop:~/bcm43xx$ unzip bcm4328.zip
Archive:  bcm4328.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of bcm4328.zip or
        bcm4328.zip.zip, and cannot find bcm4328.zip.ZIP, period.
levent@levent-desktop:~/bcm43xx$

---

### Post by cyberdork33 on 2007-11-18
> **Levo75 said:**
> Can anyone help me with the 32bit version?

So i tried this toturail: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-079fa9ceecfe235b6150966744c4094ef0862956](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-079fa9ceecfe235b6150966744c4094ef0862956)

But i get this when i try to unzip

01:15:08 (40.51 MB/s) - `bcm4328.zip.1' saved [617]

levent@levent-desktop:~/bcm43xx$ unzip bcm4328.zip
Archive:  bcm4328.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of bcm4328.zip or
        bcm4328.zip.zip, and cannot find bcm4328.zip.ZIP, period.
levent@levent-desktop:~/bcm43xx$
bad file.

---

### Post by cyberdork33 on 2007-11-18
> **Aranel said:**
> Hey there. I've recently bought one of the new Santa Rosa MacBooks (otherwise known as macbook3,1), which comes with a Broadcom 4328 wi-fi card, and installed 64-bit Gutsy on it. (I believe the new iMacs also come with this wi-fi card, but don't quote me on that.) Since the native bcm43xx driver doesn't even seem to acknowledge the card's existence, I started looking for Windows drivers for use with NdisWrapper. I found one that looked promising for 64-bit Windows and tried it with NdisWrapper, and it worked absolutely flawlessly. Just a quick *ndiswrapper -i bcmwl5.sys && modprobe ndiswrapper*, and that's it.

Anyway, I thought I'd save my fellow 64-bit users some trouble by providing them here. So see the attachment. :)

(Disclaimer: I don't know how this plays with NetworkManager--I installed the server edition of Ubuntu, which of course doesn't come with NetworkManager--but if nothing else, the driver should work with the old-fashioned CLI tools. I also haven't tried this with WPA encryption, but it functions just fine with WEP.)

I hope this helps someone!
can you indicate the source of these please?

---

### Post by Aranel on 2007-11-18
> **cyberdork33 said:**
> can you indicate the source of these please?

[http://www.x-drivers.com/component/option,com_remository/func,fileinfo/id,9957/](http://www.x-drivers.com/component/option,com_remository/func,fileinfo/id,9957/)

The origin of the download appears to be in Russia, so it takes forever to download anything, at least here in the US. That page downloads a 37.6MB zipfile, which contains a .exe file, which contains the drivers themselves (among other clutter, which comprises >50MB). Only the relevant files are in my attachment to the original post. :)

---

### Post by cyberdork33 on 2007-11-18
> **Aranel said:**
> [http://www.x-drivers.com/component/option,com_remository/func,fileinfo/id,9957/](http://www.x-drivers.com/component/option,com_remository/func,fileinfo/id,9957/)

The origin of the download appears to be in Russia, so it takes forever to download anything, at least here in the US. That page downloads a 37.6MB zipfile, which contains a .exe file, which contains the drivers themselves (among other clutter, which comprises >50MB). Only the relevant files are in my attachment to the original post. :)

Thanks, I am just interested because I wanted to compare to the Dell drivers that I am using now.

---

### Post by Aranel on 2007-11-19
> **cyberdork33 said:**
> Thanks, I am just interested because I wanted to compare to the Dell drivers that I am using now.

Oh, okay. Let me know which one works better!

---

### Post by cyberdork33 on 2007-11-19
> **Aranel said:**
> Oh, okay. Let me know which one works better!

From what I have found so far, it looks like they originated from HP. Still trying to find the download on their server though. They do have machines with this chipset though.

Ok, the drivers are in this softpaq from HP, although they do not extract easily for me. (I just ran it in wine to extract).

[ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34154.exe](ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34154.exe)
which I think is used for the HP laptop model dv6254eu

```
cyberdork33@Grover-Ubuntu:~$ md5sum bcmwl5.inf bcmwl5.sys bcmwl564.sys
079041ea39dc82e95889151deb813b73  bcmwl5.inf
b89bcf0a25aeb3b47030ac83287f894a  bcmwl5.sys
feaf7ec9f38a37945b6fb169617ec859  bcmwl564.sys
```

The bcmwl564.sys file (which is really the actual driver) is the same size file as the in the Dell driver here:
[ftp://ftp.us.dell.com/network/R151517.EXE](ftp://ftp.us.dell.com/network/R151517.EXE)

---

### Post by Aranel on 2007-11-19
Cool. So I guess we have two options for a Windows driver to use. :D

---

### Post by postilion on 2007-11-24
Aranel wrote:
[INDENT]"Just a quick ndiswrapper -i bcmwl5.sys && modprobe ndiswrapper, and that's it."[/INDENT]

Not to be a stickler, but the correct command is ```
ndiswrapper -i bcmwl5.inf && modprobe ndiswrapper
```

Thanks for this tip, it saved me a ton of time.  I hope everyone in need finds this page!
      -nic

---

### Post by Aranel on 2007-11-24
> **postilion said:**
> Aranel wrote:
[INDENT]"Just a quick ndiswrapper -i bcmwl5.sys && modprobe ndiswrapper, and that's it."[/INDENT]

Not to be a stickler, but the correct command is ```
ndiswrapper -i bcmwl5.inf && modprobe ndiswrapper
```

Thanks for this tip, it saved me a ton of time.  I hope everyone in need finds this page!
      -nic

...Er, yeah, that's what I meant to say. It's confusing because NdisWrapper wants the inf file, while the bcm43xx driver wants the sys file. :p

---

### Post by cyberdork33 on 2007-11-25
> **Aranel said:**
> ...Er, yeah, that's what I meant to say. It's confusing because NdisWrapper wants the inf file, while the bcm43xx driver wants the sys file. :p

Actually, ndiswrapper needs the sys file too, you just have to specify the inf file for it to get it.

---

### Post by Gajdosik on 2007-11-30
Dear Aranel,
I thank you so much for providing a working bcm4328 64bit ndis windows driver! I am no ubuntu user (gentoo instead), but I registered to this forum right now for downloading your driver and saying thanks and gods blessings! I searched fruitlessly for a long time for this driver and now it worked right out of the box. I use Acer Ferrari 1000. Yours,
Johannes Gajdosik

---

### Post by zephyrus17 on 2007-12-10
When I try:

ndiswrapper -i bcmwl5.inf && modprobe ndiswrapper

It says "Error: no ndiswrapper utils found!"

I've downloaded ndiswapper-util-1.9 from synaptics, but it still won't work. Help?

Wait, is the method for Apple only?

---

### Post by cyberdork33 on 2007-12-10
> **zephyrus17 said:**
> When I try:

ndiswrapper -i bcmwl5.inf && modprobe ndiswrapper

It says "Error: no ndiswrapper utils found!"

I've downloaded ndiswapper-util-1.9 from synaptics, but it still won't work. Help?

Wait, is the method for Apple only?
no, not apple only, although you do need to make sure you have a bcmwl5 driver that works with your hardware.

please verify utils are installed:
```
sudo aptitude install ndiswrapper-utils-1.9
```

---

### Post by oliviervdst on 2007-12-11
Hey- I just want to say **THANKS** for sharing.

Even though I don't use Ubuntu (OpenSuse) or a Mac (Dell) the drivers worked perfectly.

Anyway, thanks for taking the time to share.

---

### Post by cyberdork33 on 2007-12-11
> **oliviervdst said:**
> Hey- I just want to say **THANKS** for sharing.

Even though I don't use Ubuntu (OpenSuse) or a Mac (Dell) the drivers worked perfectly.

Anyway, thanks for taking the time to share.

This should work for anyone with a BCM4328 card.

---

### Post by mcreel on 2008-02-01
Thanks! This rocks :guitar:

---

### Post by cyberdork33 on 2008-02-01
Just as an update, with all the changes in the linux stack for networking in 2.6.24, the updated broadcom drivers (now renamed b43 and b43legacy) still does not support the 4328 card. Looks like we will be stuck with ndiswrapper for awhile still.

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by m.musashi on 2008-03-23
I've installed the driver but it's still not recognizing the card. iwconfig shows
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

```
ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4328) present (alternate driver: ssb)
```

Is there anything else I need to do to get it to work? lspci syas my card is 
```
Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
```
so this should be the right driver.

Thanks.

---

### Post by george.talusan on 2008-03-23
I have the same problem with the kernel in Hardy.  ndiswrapper won't load the proper driver.  If I switch down to 2.6.22-14 then it works.

---

### Post by cyberdork33 on 2008-03-23
there is bug in ndiswrapper in hardy. You need to load modules in a different order. This has been mentioned recently in several threads.

[http://ubuntuforums.org/showthread.php?t=730966](http://ubuntuforums.org/showthread.php?t=730966)

---

### Post by m.musashi on 2008-03-23
Thanks for the info. I've seen some discussion about this but there didn't seem to be a good solution. I've reinstalled gutsy for now but hardy is so much nicer. I'd like to stick with hardy if possible. Is there a solution that works or more a hit and miss thing? The boot script solution seems less than ideal.

---

### Post by cyberdork33 on 2008-03-24
> **m.musashi said:**
> Thanks for the info. I've seen some discussion about this but there didn't seem to be a good solution. I've reinstalled gutsy for now but hardy is so much nicer. I'd like to stick with hardy if possible. Is there a solution that works or more a hit and miss thing? The boot script solution seems less than ideal.
Well the ideal would be a fix in Ubuntu, but that is not done yet so you have to wait.

---

### Post by m.musashi on 2008-03-25
Thanks. I went ahead and used the script. It worked fine so I have my 64 bit hardy working on a iMac g5 with the annoying broadcom 4328 chip. Fixing in hardy would be nice but even nicer would be manufactures that support Linux. Normally I avoid the "bad" ones but you are stuck if you have an apple.

---

### Post by cyberdork33 on 2008-03-25
> **m.musashi said:**
> ...you are stuck if you have an apple.Not exactly, if you can buy a replacement card that works with Linux. Apparently there are some Intel cards out there that can be used, but don't work in OSX.

---

### Post by robzon on 2008-03-25
You can also get a Atheros card. These cards were used in MacBooks gen 1 and 2, so they should work just fine under both OS X and Ubuntu.
Of course you'd need to buy the right model for OS X, but this shouldn't be a problem.

---

### Post by m.musashi on 2008-03-25
> **cyberdork33 said:**
> Not exactly, if you can buy a replacement card that works with Linux. Apparently there are some Intel cards out there that can be used, but don't work in OSX.

Well, by stuck I meant you can't order a Mac with the hardware you want - you get what they give you. Replacing the card in a iMac would be a pain too. The newer ones are not easy to open and work on. Of course you could use a USB card.

---

### Post by pwe on 2008-05-20
hello

someone install those drivers on 32bit Ubuntu Hardy?

Peter

---

### Post by cyberdork33 on 2008-05-20
> **pwe said:**
> hello

someone install those drivers on 32bit Ubuntu Hardy?

Peter
yes they work in 32 bit Hardy.
Please post in the new Apple Forum:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by joseche on 2008-05-25
Thanks, this helped me too, the only thing missing here is the sourcetype for kismet :) but I think it is not possible right ?

---

### Post by springbokmarine on 2008-05-29
Thanks for the drivers. I have a 24" iMac, 2.4 Ghz from early 2007. I had to install the ndiswapper-util-1.9 with apt-get, and simply ran:

ndiswrapper -i bcmwl5.inf && modprobe ndiswrapper


after which wireless networks started showing up in the top/right corner when you click the network icon. It connects to WPA flawlessly as well.

The problem I'm having is that after I reboot, I have to rerun the command. How do I make it stick? Where would I put a startup script that will bring it up when starting ubuntu?

---

### Post by cyberdork33 on 2008-05-30
> **springbokmarine said:**
> Thanks for the drivers. I have a 24" iMac, 2.4 Ghz from early 2007. I had to install the ndiswapper-util-1.9 with apt-get, and simply ran:

ndiswrapper -i bcmwl5.inf && modprobe ndiswrapper


after which wireless networks started showing up in the top/right corner when you click the network icon. It connects to WPA flawlessly as well.

The problem I'm having is that after I reboot, I have to rerun the command. How do I make it stick? Where would I put a startup script that will bring it up when starting ubuntu?

add 'ndiswrapper' to /etc/modules

---

### Post by unclecameron on 2008-06-05
I have everthing installed okay, ndiswrapper working (I think) and iwconfig shows:

```
wlan0     IEEE 802.11a  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:270 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

but the network manager doesn't seem to see any wireless networks...what am I missing? This is on a HP dv9812us duo AMD Turion 64 bit laptop.

edit: turn on the stupid little mechanical slide switch that's not marked which is on/off until the LED turns to blue, then try it again with a reboot...doh!

---

### Post by Punkster812 on 2008-06-11
THAN YOU THANK YOU THANK YOU.

Sorry for the yelling, I am just so excited because this is what I needed. After many hours of reading documentation on ndiswrapper's website and following countless tutorials and many various drivers (all called bcmwl564 but with diff md5's)] this is the one that worked \\:D/. I even tried compiling a new kernel and the latest ndiswrapper just to try and get my wireless card working.

Thank you for the drivers, I really appreciate it.

Oh, I should mention, I am not using Ubuntu or MAC, just so others know this can be a fix for other distros too as long as you have the right card. I did this on SuSE 10.3 with the 2.6.22.16 Kernel.

---

### Post by cyberdork33 on 2008-06-11
This forum is archived, please post new discussion in the Apple Users forum:[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by phunkedelik on 2008-06-21
im going to try the hp driver cuz im on an hp pav dv9000 and the dell one doesnt like me very much

---

### Post by cobralgato on 2008-07-07
This driver doesn't work with broadcom 4328 rev 05  and 64bit kernel 2.6.25.
You'll need the driver provided in the DVD.

---

### Post by pax131 on 2008-07-15
I bought a new mac pro at the beginning of the year and tried to get kubuntu 7.10 running. My efforts to set up a usable operating system were frustrated by the lack of wireless support.

I recently decided to give another go with 8.04 64-bit. Using ndiswrapper and your driver file the network popped right up.

I've been banging my head against this wall on the odd weekend for four months. Now I'm posting to this forum from linux for the first time.

Hats off and THANK YOU.

---

