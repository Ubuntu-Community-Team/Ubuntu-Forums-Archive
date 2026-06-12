---
title: "Install on PowerPC G4 867Mhz, 640MB SD-RAM"
date: 2008-08-07
forum: Apple Hardware Users
---

### Post by tiny969 on 2008-08-07
hi, i'm new to ubuntu and like to install v.8.04.1 on my old G4.

first i tried to do it with the live-cd, but there was some kind of  problem with the hdd ("hdc is not ready..." or something like that). i read, that it is better to try it with the alternate-cd.

so said, i downloaded this one and came up to the installer... but my cd-rom was not found during the installation. following the hints in this forum, i tried to repeat the hardware recognition process and the cd-rom was found. during the next step (keyboard-layout, pcmcia conf, etc.) the same error message about my cd-rom went up. i tried this several times, without success.

finnally, the prompt boot: is loaded, but whatever i choose there (install, ..., install live-nosplash-powerpc video=ofonly, ...) the machine just shuts down without an error message! (both alternate and live)

what's wrong here!?

i'm not trying to setup a dual-boot system, i just want ubuntu working on this thing.
by the way, osx (which is currently installed on the g4) is booting and working correctly...

sorry if i have overlooked existing threads about this problem, but i'm really stuck at the moment!

thx for any hints and for your help!

---

### Post by tiresia on 2008-08-07
I own a PowerPC G5. And this is my experience.

1. Debian Stable (now still Etch) Installer works *always* properly
2. Debian Testing (Lenny) installer can give some problems
3. Ubuntu-alternate gives me problems with the fans (but this is a specific issue)
4. I got Ubuntu installed with the Live-CD

Therefore I would suggest you 
1. Be sure that the alternate CD you downloaded is not corrupted (make a checksum, in MacOSX you can do it with md5)
2. Try again, burning your CD with Apple Disk Utility at low speed (2:1)
3. If you haven't done, try again with the Live-CD, press TAB at the boot prompt and choose live-nosplash-powerpc. Maybe I'm wrong, but I have the impression that the Live-CD get more tests than the alternate-CD

Has your G4 just standard hardware or did you have extra graphic card, &#8230;?

---

### Post by tiny969 on 2008-08-07
hi tiresia,

thanks for your suggestions, i will try and report it later...

my g4 has an additional graphics card, on PCI slot3... it's a MaPi502 standard desktop-doubler card...

---

### Post by tiny969 on 2008-08-07
now, i've tried the following:

checked md5-sum: ok
tried with live-cd and install-nosplash-powerpc and hit enter: the system went to black screen then a white screen and does the shutdown again.

on the white screen there is some output but it shuts down much to fast... i'm not able to read anything, this output is just visible for half a second or so...

---

### Post by tiresia on 2008-08-07
Suggestions:
1. As I sad, try again with the Live-CD (using different options&#8230;)
2. Just to be sure&#8230; Can you unplug the PCI card and use the original Grafic Card (is it an NVIDIA GeForce? and it is a Quick Silver?)

---

### Post by tiny969 on 2008-08-07
wow. seems as if the additional graphics card was a problem.
i had a second pci-card in it too, a usb 2.0/firewire controller, i removed that too.

now i have the screen "Loading, please wait...". so i do.
i will let you know if everything works correctly now...

thank you again!

EDIT: yes, it's a geforce and yes, it's a quicksilver

---

### Post by tiny969 on 2008-08-07
it's really annoying... waited for 20 mins while the screen was showing "loading, please wait". nothing happened.

i did a shut down holding the powerkey and tried again: wonder, the machine did a shutdown after the boot: prompt. again tried live- and alternate-cd with the same results.

now i'm really on the verge to cancel my ubuntu-on-apple g4-project...

---

### Post by mkvnmtr on 2008-08-07
I had the same problem with 8.04.1 on my G4 IBook. I found that when I restarted with the live disk there is a short time when it says live disk 8.04.1 quickly press tab. There will come up a page of options. These are thengs you can type in to load the live disks in varios ways. The one that worked for me and some other people was [live-nosplash-powerpc=ofonly]. You will see this in the list of options. Type it in and you will see it come up on the bottom of the page. Then press enter and wait while the live disk loads. After that I had no problems clicking on the install icon and finishing the install. I think the disk has a problem bringing up the splash screen on powerpc.

---

### Post by tiresia on 2008-08-07
You don't need to wait so long. The Live-CD can take longer to load, but not more than 5 min. Anyway, don't give up right now, your G4 with Ubuntu will become a new computer.
You can try following
1. When you boot, boot in Open Firmware (press O+F+Option+Command) and do

```
reset-nvram
set-defaults
reset-all
```

2. The computer restarts. Please tell us what you get. At the *first* prompt press TAB

---

### Post by tiny969 on 2008-08-07
did so. the screen resolution changed to 1024x768.
computer rebooted and the normal osx loginscreen was there.
booted again from live-cd (restart + C), hit TAB and got the different options again. tried live-nosplash-powerpc and the system went down again. ........ *aWordIdon'tWantToWriteHere*

---

### Post by tiresia on 2008-08-07
Other options:
1. Can you please try now with the alternate-CD? 
2. If it does not work, just to understand if it has to do with the Installer or with the hardware, I would try with Debian Stable (Etch). 
You can donwload it here:
[http://www.debian.org/distrib/netinst](http://www.debian.org/distrib/netinst)
(This is a netinstaller, also you need that your computer is connected to Internet)

---

### Post by tiny969 on 2008-08-07
tried alternate: the same with shutsown.

BUT: i've tried the debian netinstall you've mentioned... and here i have the same problem! 
as my last action i downloaded FINNIX and started a boot... the same.

seems that my problem has nothing to do with ubuntu at all, but with my g4...

i wonder what the problem could be, because mac osx is running and working as it should do... is my g4 for just not able to run any linux-distro?!

---

### Post by tiresia on 2008-08-07
Ok, I have four hypotheses


1. Just to be sure: you downloaded the CD image, checked it, and burned it (with the Apple Disk Utility?) at low speed. If you have another Apple PPC you could try the cd on it, if it can boot, it does not depend on the CD&#8230;:)

2. All the distros you tried are based on Debian. You may want to try Fedora ([http://fedoraproject.org/de/get-fedora](http://fedoraproject.org/de/get-fedora)). But as I said, I never had a problem with Debian

3. Are you sure, you have removed all third parts (PCI cards,&#8230;) In general, have you ever changed anything in your G4? 

4. A problem with your CD-Driver (but it boots&#8230;)

4. It could be a Kernel Panic, as if, when the bootloader tries to load the kernel, it can't access the RAM (???). You may want to try remove all RAM-banks except one - probably you have 512+128, or 256+256+128
:popcorn:

---

### Post by tiny969 on 2008-08-08
hi again,

1 i downloaded the live-cd again under osx. calculated the checksum of the .iso with md5 in the terminal and compared it to the online one -> ok. used disk utility to burn the .iso again at low speed and did the checking -> ok.

2 booted with this cd, prompt boot: was shown.

3 used live-nosplash-powerpc option and the default option.

4 system shutdown......

i did a memtest afterwards too, without any errors. both ram-blocks seem to be ok (512 + 128 ).

i don't think that i will get a working installation with fedora, because installation failed with shutdown using debian netinstall and finnix too...

cd-rom driver seems to be ok, in my opinion it won't boot anyway if there would be a problem.

the only 2 additional cards i have built in, the 2nd graphics card and the usb/fw controller are no longer in the machine.

strange...

i will try fedora next week...

---

### Post by stream303 on 2008-08-08
> **tiresia said:**
> 3. Ubuntu-alternate gives me problems with the fans (but this is a specific issue)

Typically the screaming fans on G5's are only an issue during install - after the first reboot everything calms down, unless you are running the last rev-c version of a G5 iMac prior to them switching to Intel.  I'd have to check to see if that has been fixed yet.

Also, after talking to a dev, there was hope that the fan issue during install would be fixed for 8.04.1 respin since he also is a debian dev, which didn't have the fan issue during install for Etch.

---

### Post by tiny969 on 2008-08-11
hello again...

bringing up this thread again...
i've tried a few different linux-dists now, including fedora, i have the same problem at all.

booting from a cd, i see the boot: prompt. never mind whatever i'm typing in (from default settings to "live-nosplash-powerpc modprobe ide-core video=ofonly" for ubuntu live-cd for instance), the machine is just performing a shutdown.

i've removed all 3rd party parts (2nd graphics card, usb/fw controller), osx 10.3.9 is running as it should. i really like to have ubuntu running on that machine (and ubuntu ONLY), but whatever i try lasts in a shutdown.

does anybody have an idea what could be the problem here?!?

thx!!!

---

### Post by tiresia on 2008-08-11
Hi!
You can try to boot the installer from a USB memory stick.
Here is a link:   
[https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld](https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld)

---

### Post by stream303 on 2008-08-11
I've taken a look at the specs on everymac.com for your box, and it might take some work since some things will need to be manually modified.

The main issue will be to just get the system on the disk, and not rely on the live-cd.  Use the "alternate" installer, which relies solely upon text-mode for installation (full gui afterwards however.)

Note that if you have upgraded your hard drives, there is a 128gb partitioning limitation that means you will want to keep the entire ubuntu install at around 125gb to be safe, and use the rest as a general purpose partition.  OR, you can slice and dice up the partitions on your own, but the special apple partitions, boot and root have to be under 128/125 gb.

I'm assuming you have free space on your drive, and if so, allow Ubuntu to install to "free space" to take care of the partitioning for you.

It looks as though that Quicksilver has more than one hd-controller as standard, and this might present some difficulties forcing you to use OpenFirmware "alias" for the drives, rather than specific openfirmware paths.  There are a few threads here about using an alias in your /etc/yaboot.conf , typically when using xserve boxes.  These threads may help.

You'll need to know your monitor's vertical and horizontal freq specs, and have to manually edit them into the /etc/X11/xorg.conf file.  That quicksilver came stock with an nvidia card, and fortunately nvidia is a bit easier to get working than the ati in many cases.

Getting to this point may be tricky enough just to do the edits in the first place. :)

I'm not surprised that other distros don't seem to install well either. It can be done, but it will take a lot of time and research if this is your first ppc linux install.  With that model, it is possible you will encounter every single problem with ppc that one can.  Not for the faint-hearted.

I don't want to put you off the project, but just want to be honest so you don't throw it out the window. :)

---

### Post by tiny969 on 2008-08-11
hey, wow, thank you for your hints... this sounds like a lot of upcoming work for me... but i will do my best.

i will post results here... :)

---

