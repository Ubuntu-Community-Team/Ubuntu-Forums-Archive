---
title: "kubuntu 13.04 install on ppc nvidia g5 dual 2ghz(a sad story)"
date: 2013-05-08
forum: Apple Hardware Users
---

### Post by gusduenas on 2013-05-08
Ok first off, it will do nothing without any twitching...You might need to do something at the yaboot, thanks to @Macmichigan for his wise advice for me to finally has the live cd working and watching the kubuntu desktop

1. type at the yaboot: live video=offb:off nouveau.modeset=0 single
2, then when the graphic card is loaded it will simply stall at the white screen, then type: modprobe nvidiafb mode_option=1680x1053-32 (my resolution) be careful you will be typing on a freeze screen you won't see a thing.
3. When hit enter you will be at the terminal, just type sudo start lightdm and voila! you will be at the desktop for Kubuntu 13.04 very impresive...but problem is it doesn't install at all (usually crashes at 80%) it is a bug, here is the work around.
go terminal and type:

sudo mv /usr/share/ubiquity-slideshow/slides/index.html /usr/share/ubiquity-slideshow/slides/index.html.bak    hit enter and try the install again, now it will work, slow but it will work.
After the installation it will ask you to retire the dvd from the tray and hit enter...here is when the new problems begins...it won't restart, it freezes there, so I had to force the shutdown.


After that I though it will go normally once it is installed but...you'll have new problems:

1. At the boot in yaboot it won't go to the osx (did I mention my mac has a dual boot, actually two hd one with osx of course) it will return to the yaboot, so when I go to the linux, it will send me to the black screen, no desktop at all.
2. since it won't boot to the osx (freezes all time) I had to use the install dvdv from osx to gracefully erase the hd as usual (where Kubuntu was) and try to do something new..

well someone could help me out. I don't understand how there is people claiming to have Kubuntu or Ubuntu 13.04 working on a g4 which is generations older than mine and I cannot have this working on a G5 dual 2.0GHZ ( the last g5 made in mid 2006)


My build is: g5 dual 2GHZ nvidia 6600 pcie, 1GB ram, 150GB HD for ubuntu, and 1TB for OSX 10.5.8 screen is the regular apple cinema display resolution is 1680 x 1050 32 bit colors

Does anyone has the answer to my dilemma?


Gustavo

---

### Post by este.el.paz on 2013-05-09
> **gusduenas said:**
> Ok first off, it will do nothing without any twitching...You might need to do something at the yaboot, thanks to @Macmichigan for his wise advice for me to finally has the live cd working and watching the kubuntu desktop

1. At the boot in yaboot it won't go to the osx (did I mention my mac has a dual boot, actually two hd one with osx of course) it will return to the yaboot, so when I go to the linux, it will send me to the black screen, no desktop at all.
2. since it won't boot to the osx (freezes all time) I had to use the install dvdv from osx to gracefully erase the hd as usual (where Kubuntu was) and try to do something new..

well someone could help me out. I don't understand how there is people claiming to have Kubuntu or Ubuntu 13.04 working on a g4 which is generations older than mine and I cannot have this working on a G5 dual 2.0GHZ ( the last g5 made in mid 2006)


My build is: g5 dual 2GHZ nvidia 6600 pcie, 1GB ram, 150GB HD for ubuntu, and 1TB for OSX 10.5.8 screen is the regular apple cinema display resolution is 1680 x 1050 32 bit colors

Does anyone has the answer to my dilemma?


Gustavo

@gus:

I'm not a linux technician, but I have been checking this list and see that you have been trying to get something going for quite awhile . . . why it isn't working is a question mark.  I have now done many installs of various linux systems, and one thing I've learned is that you have to go with what works, if it isn't working find what is and use that.  For instance, right now Lubuntu 12.04 seems to be the only flavor set up for PPC . . . I haven't checked Kubuntu since when I checked the LiveDVD I had problems getting the cursor to work, I moved on--I suggest you try to get Lu 12.04 running before moving forward.

On the "Yaboot" issue--if you have two different HDs and Yaboot is going on one and OSX is on another, it MAY not be "seeing" it.  You can always use the "option" key on restart to find the OSX boot loader and select the HD that way, and then it will go to Yaboot window, etc.

Also, if you have a problem booting a linux system you can find and download "SuperGrub2" and see if that will find all the OSs and boot them . . . .  I believe I used it to boot my iMac G4 in one of the many installs, but it might have been only for Intel??  Can't remember.

I hope you find this post to be an extremely high quality and helpful post, even though there are no links provided, all of this stuff I found from 2 years of working on Linux.  This post may be "jailed" spontaneously if it's thought to be "unhelpful" . . . please post back and say if you find it helpful.  : - (

e.e.p.

---

### Post by tgalati4 on 2013-05-09
I have a powerbook G4 that I played around with using Ubuntu.  As I recall, there were partition issues with dual-boot. Use Mac's Disk Utility to make the partitions, not gparted or any other linux tool.  You have to do this while booting from the OSX DVD in Live Installer Mode. If you used any linux tools to partition the disk, then that could lead to problems on the OSX side.  I can't help with 13.04, since it is new and I don't feel like spending the agony units required to get it to run on an old, unsupported G4 machine.

---

### Post by este.el.paz on 2013-05-09
> **tgalati4 said:**
> I have a powerbook G4 that I played around with using Ubuntu.  As I recall, there were partition issues with dual-boot. Use Mac's Disk Utility to make the partitions, not gparted or any other linux tool.  You have to do this while booting from the OSX DVD in Live Installer Mode. If you used any linux tools to partition the disk, then that could lead to problems on the OSX side.  I can't help with 13.04, since it is new and I don't feel like spending the agony units required to get it to run on an old, unsupported G4 machine.

@tg4:

What you are saying does probably apply to dual boot within the same HD, but Gus has said that he has 2 HDs, one for OSX and one for "alternative" OSs.  I have suggested that he try 12.04 first, for the same reason you have mentioned . . . less agony units.  It's just easier if the whole HD is set aside for whichever flavor you select (ppc supported) . . . and choose "Guided, use whole disk" (or whatever automatic install option is available) and just let the installer do the install . . . you can always add stuff later once you get it boot-able . . . again, the choice has to be for PPC . . . .

e.e.p.

---

### Post by str8bs on 2013-05-12
@gusduenas

Could you elaborate on "OS X freezes" all the time? If you hold the alt key while booting, and select OS X, it does not boot? If that is the case, you may try resetting PRAM.

As for 13.04, it isn't how new or what generation PPC you have so much as the state of FOSS video driver support on your hardware. In your case, Nouveau for Nvidia 6600.

Can you boot successfully but to a very low color screen using:
```
live video=ofonly nouveau.modeset=0
```

If not, you will probably need to repeat the install as you stated and then follow the FAQ about adding a kernel module.

To fix the yaboot issue, I would guess the installer just got the paths mixed up to the different hard drives. You can sudo fdisk -l to see the paths and then update /etc/yaboot.conf to point at the correct path for both OS X and your Ubuntu install. More on yaboot in the faq.

I would hesitate to use OS X disk utility or Startup Disk after you have installed Ubuntu. In my experience, this can break things.

@tgalati4
Has community support for PPC been dropped? Or, do you just mean unsupported by Apple?

---

### Post by michiganmac on 2013-05-13
Apple has definitely dropped support for PPC. All iBook G4, Powerbook G4, Powermac G4 and most, if no all Powermac G5 PPC's are on the "obsolete list". Basically, all products between 5 and 7 years are considered "vintage". Seven years and older are "obsolete". Apple's official policy is here:

[http://support.apple.com/kb/ht1752](http://support.apple.com/kb/ht1752)

---

### Post by canhoto on 2013-05-14
> **gusduenas said:**
> 

Does anyone has the answer to my dilemma?


Gustavo

May I suggest something?

Install another "flavour" and then install Kubuntu 13.04. For me and my G4 (a dual-boot system with 2 hd's, like yours) it worked.

But you must follow this steps:

1. Boot a Lubuntu 13.04 live cd with the booting parameters that you already know:

```
live video=offb:off nouveau.modeset=0 single
```

then, after a while

```
modprobe nvidiafb mode_option=1680x1053-32
```

then, at the prompt:

```
start lightdm
```

2. Install Lubuntu and, when asked if you want to automatically login to your account, leave the default option checked, which is "no": do not automatically login
3. After the successful installation, when asked if you want to keep trying ubuntu or to reboot, choose to keep trying
4. Open the file manager, look for the filesystem where you installed Lubuntu (usually identified by the size of the partition; ex: "154 GB filesystem"). Mount it, look for the etc directory and choose to open it from terminal
5. At the terminal you should have a /media/longstringofnumbers/etc prompt. Type
```
sudo nano modules
``` or ```
sudo leafpad modules
```
6. Add this to the file ```
nvidiafb mode_option=1680x1053-32
``` Save it and close it

7. Then type ```
cd initramfs-tools
``` 
8. Type ```
sudo nano modules
``` and again add ```
nvidiafb mode_option=1680x1053-32
``` to the file, save and close it
9. Copy the path where you are to include the "etc" directory, but not the "initramfs-tools". You should copy something like ```
/media/longstringofcharacters/etc
```. Then cd to it: ```
cd /media/longstringofcharacters/etc
```
10. Type ```
sudo nano yaboot.conf
``` and edit the images section to include the booting parameters: ```
append="video offb:off nouveau.modeset=0"
``` Save and close
11. Type ```
sudo ybin -v - C /the/same/path/you/used/before/to/etc/yaboot.conf
``` Wait for yaboot to update

You should now be able to reboot to Lubuntu. Maybe you have to force reboot by pressing the reboot or shutdown.
Login to your Lubuntu session. Open a terminal (Ctrl+Alt+T) and type ```
sudo apt-get install kubuntu-desktop
``` After the installation is complete, you may reboot again.
Then, at the session login, choose "KDE Plasma Desktop" from the dropdown menu, instead of Lubuntu.
You shoud now have a perfect Kubuntu 13.04 on your G5.

Hope it helps. Please keep us informed.

---

### Post by ninjawarrior on 2014-01-17
Hey canhoto!

I tried to follow your advice, and while I got further than with other instructions, I can't quite get it to boot from the HD.

Steps 1-9 work great. Except that I have /media/lubuntu/longstringofnumbers/  (minor difference?)

Meaning, I boot from live cd with 
```
live video=offb:off nouveau.modeset=0 single
``` 
It takes me to a white screen, where I wait a bit before typing
```
modprobe nvidiafb mode_option=1920x1200-32
```
Which brings me to a CLI. I type "start lightdm" and it brings me to the lubuntu GUI. I install lubuntu 13.04 to disk. Once the install is complete I stay running in Live. I open the file manager, click on the 1.5TB Volume (which mounts it) and right-click the "etc" folder and open in terminal. /media/lubuntu/longstringofnumbers/etc

edit /etc/modules and /etc/initramfs-tools/modules by affixing 
```
nvidiafb mode_option=1920x1200-32
```
to the end of the file. In /etc there were a couple other options, in /etc/initramfs-tools it was the only one.


Step 10
```
append="video offb:off nouveau.modeset=0"
```
should be 
```
append="video=offb:off nouveau.modeset=0"
```

Step 11 
```
sudo ybin -v - C /the/same/path/you/used/before/to/etc/yaboot.conf
``` 
should be 
```
sudo ybin -v -C /the/same/path/you/used/before/to/etc/yaboot.conf
```

Now, when I reboot. I see it selects boot from GNU/Linux, once at the boot prompt it types in "Linux" and it brings me to the white screen where I would previously type in "modprobe nvidiafb mode_option=1920x1200-32" it hangs there for a little while, doesn't respond to any commands including typing modprobe..., and then reboots. Wtf. 

Any suggestions would be most appreciated.

I am doing this on a 1.6MHz G5 with 2.25GB RAM a 1.5TB HDD and an nVidia GeForce FX 5200

---

### Post by pauljwells on 2014-01-18
I had the same machine. I don't think there is a more difficult one on which to install Ubuntu and I've done LOTS of installations. I did manage to get Kubuntu 13.04 installed and booting from HD but it was a pita and as it was fb only graphics you can't even use vlc.
There was a kernel bug that meant it won't run any of the early 3.x kernels (Ubuntus 11.10 - 12.10), but now that the kernel bug is fixed it won't run the nouveau driver. Also, ymmv but I found it would only boot linux if it was installed on the firts HD, yaboot simply would not see the second one. I had to uninstall UbuntuOne support from the installer in the live CD before the installer would run to completion.
I sold mine. If you value your time you should too. Buy an x64 machine and get your life back... :-(
The only way to get a half-decent system would be to find someone with a different spec 64bit PPC machine, install 12.04, patch the kernel and recompile and then burn a custom installer from that installation. That *might* work, I had 12.04 running from an upgraded 11.04 installation but from an old 2.6 kernel, but that route is no longer possible because the upgrade mirrors are long gone.

---

### Post by franklynb on 2014-02-13
> **pauljwells said:**
> ...
There was a kernel bug that meant it won't run any of the early 3.x kernels (Ubuntus 11.10 - 12.10),...

 Buy an x64 machine and get your life back... :-(

The only way to get a half-decent system would be to find someone with a different spec 64bit PPC machine, install 12.04, 
patch the kernel and recompile and then burn a custom installer from that installation. That *might* work,...
 but that route is no longer possible because the upgrade mirrors are long gone.

Wow. I can't imagine a less helpful post. And it is chock full of errors.:mad:

Here's the latest [powerpc ISO]("http://cdimage.ubuntu.com/releases/12.04.4/release/ubuntu-12.04-desktop-powerpc.iso").

I've built 12.04.x FOUR times on a powerpc G5 x 2.5gHz x 4CPU "watercooled" powerpc with nvidia 6600 from the ISO! I've never had to alter the yaboot launch params, and the livecd
ALWAYS boots. Option-C boot is your friend.

And it runs quite well, thank you. _Kernel bug_. Humbug. Show me the data. The reason I've built it so many times is because I was foolish enough to try
and run 12.10 <argh! noveau!> and 13.04 <an ever worse noveau implementation, and very hard to get up off the command line.> A search will reveal others
that have had similar experiences, but run 12.04 precise pangolin on a daily basis. Even gnash works for earlier than flash 10 files.

I'll put my calculiX benchmarks up against your "X64 lifestyle" any day, any time. I own an 8xcpu-64bit-16gB-13.04 Intel, and they run about even on SMP
scientific work. Or ffmpeg conversions. totem x264. firewire, jackd, ffado.  Just try me.:guitar:

So, please. Try checking your facts before posting this sort of trashing.

--frankb
Linux waterboy 3.2.0-58-powerpc64-smp #88-Ubuntu SMP Tue Dec 3 18:35:43 UTC 2013 ppc64 ppc64 ppc64 GNU/Linux
0000:00:0b.0 PCI bridge: Apple Inc. CPC945 PCIe Bridge
0000:0a:00.0 VGA compatible controller: NVIDIA Corporation NV43 [GeForce 6600] (rev a2)
0001:00:00.0 Host bridge: Apple Inc. U4 HT Bridge
0001:00:06.0 PCI bridge: Broadcom BCM5780 [HT2000] PCI-Express Bridge (rev a3)
0001:00:09.0 PCI bridge: Apple Inc. Shasta PCI Bridge
0001:01:07.0 Unassigned class [ff00]: Apple Inc. Shasta Mac I/O
0001:01:0b.2 USB controller: NEC Corporation uPD72010x USB 2.0 Controller (rev 04)
0001:03:0c.0 IDE interface: Broadcom K2 SATA
0001:03:0d.0 Unassigned class [ff00]: Apple Inc. Shasta IDE
0001:03:0e.0 FireWire (IEEE 1394): Apple Inc. Shasta Firewire
0001:05:04.1 Ethernet controller: Broadcom Corporation NetXtreme BCM5780 Gigabit Ethernet (rev 03)

---

### Post by rsavage on 2014-02-14
There is a bug with specific machines.  See [http://forums.gentoo.org/viewtopic-t-945822.html?sid=ff5391fe39c0729ad03313a330f36ce9](http://forums.gentoo.org/viewtopic-t-945822.html?sid=ff5391fe39c0729ad03313a330f36ce9)

All it would take is for somebody with that machine to raise an SRU request with the ubuntu kernel people and it could get fixed for 12.04.

---

### Post by pauljwells on 2014-06-03
Well, just idly surfing the forums I find your reply @franklynb. Well done, you're the first person here to **** me off. READ WHAT I F*CKING WROTE and do your OWN research. I can compile kernels, I can and **do** patch code. G5x2 2.0GHz != G5x4 2.5GHz and that's the point. it was a tiny edge case. It was a machine worth less than one hour of my consultancy rate.
Oh and the bug, I could give you a lmgtfy but I'll be more helpful than that. Try this [https://lists.ozlabs.org/pipermail/linuxppc-dev/2013-March/104362.html]("https://lists.ozlabs.org/pipermail/linuxppc-dev/2013-March/104362.html")

---

### Post by pauljwells on 2014-06-03
@rsavage, old friend. I tried talking to the kernel people at debian. I got utterly nowhere...

---

### Post by rsavage on 2014-06-04
@paul your problem was actually fixed in precise - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1164646](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1164646)

I know the 12.04 iso's remain broken, but one could download a recent 12.04 kernel from launchpad and boot the cd with that. I can provide an initrd if anybody needs it.

---

### Post by pauljwells on 2014-06-05
Thanks @rsavage. You of course will realise I spent many, many, (wife-annoying) hours trying to get this machine to run, it was sweet under 10.04. I'm glad to hear 12.04 can now run, at least there's three more Linux years in these machines. In 12.04 at least the 2D graphics worked even with the 2.6 kernel (although lots of other things broke). I gave in, bought a Core i7 quad-core, passive-cooled beauty now running 14.04 and I'm happy...

---

