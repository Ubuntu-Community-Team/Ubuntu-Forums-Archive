---
title: "is it possible: triple boot on G5 PPC: OS X Leopard, Ubuntu, OS X Panther"
date: 2009-04-20
forum: Apple Hardware Users
---

### Post by Tommmyboy on 2009-04-20
hi all.

I've searched high and low, here and there, and come up without a speck of knowledge for my effort. I've found info on triple boot with one OS X and two Linux distros and tried to extrapolate but no go... I ain't that smart.

**Is it possible to triple boot a G5 (64 bit dontcha know!) PPC with OSX Leopard, Ubuntu, and OS X Panther? **

I'm sorta already stuck in the middle of this quandry because I made bootable disk images of my Leopard and Panther installations and then using the Leopard install CD repartitioned the drive into, logically, **three separate partitions** (which of course also leaves that lil 32kb Mac file intact because Disk Utility doesn't let you see it like gparted does).  

So having read that Macs are kinda fussy unless they are first systems installed (even though I was just laying down disk images) but also knowing Linux needed to be on the first partition, I restored my Leopard disk image and my Panther disk image to partitions 2 and 3 respectively. When it was just the two OS X disks, it was simple enough to choose a start up disk so I figured that principle would apply with the addition of Ubuntu. 

So I installed Jaunty (RC) including the boot loader and everything went well. I rebooted and got the Boot Linux, Boot OSX, Boot from CD ROM menu. I was able to boot both Ubuntu, first partition and Leopard, on the second partition without problem. Then I wanted to boot into Panther on the third partition but the boot loader defaults to I assume whatever OS X partition it runs into first. 

So not knowing too much, I went in to Leopard and changed the OS X start up disk to Panther. Booted into Panther, no problem. 

Went back to try to boot Ubuntu - got into the boot loader menu easy enough, chose Linux - but then received an error that it couldn't find the Linux kernel (I don't have a screen dump, I'm sorry, not well prepared for class, so I am not positive that was the error but am pretty sure). There's probably an easy command line fix to this (I hope) but I am command line newbie so it's beyond me.

Does anyone know of any resources that address this specific triple boot situation that I could check out. Or (here's the lazy me) does anyone have specific experience with this that they could share with me?

Ideally, I'd like to know how to deal with this problem as it currently stands (resolving the "cannot find linux kernel" error) rather than having to mess around with removing and reinstalling Ubuntu but if that's the case, no biggie as I have the OS X partitions as disk images and they are easy to restore. 

Thanks

(And thank you to all who contribute to these forums, esp. the Apple Forum - I have gleaned a wealth of information from all of you who have shared your experiences and knowledge and it has made my adoption of Ubuntu much smoother than I ever thought considering I had heard G5 PPCs were generally a difficult architecture to get up and running. And of course the Mactel support is out of this world - I had Hardy running, fully installed, configured (including wireless), and updated in about 1.5 hours on my Intel duo core MacBook eons ago thanks to all the support here.)

---

### Post by tiresia on 2009-04-20
> **Tommmyboy said:**
> 
**Is it possible to triple boot a G5 (64 bit dontcha know!) PPC with OSX Leopard, Ubuntu, and OS X Panther? **

[B]Short answer: Yes
[/B]
Before explaining how, I would like to add some infos to what you have written before.
Neither MacOSX nor GNU/Linux need to be in 'first position' in the partions' order. 
Installing a GNU/Linux on a PowerPC needs at least three partitions (+ swap area): 
1. apple_partion_map
2. apple_bootstrap_partition
3. gnu/linux system (ext3)

When you choose the guided installation, the Installer generates automatically the Bootstrap Partition (and the first as well, if there is not). This partition is a (hidden) hfs partition, where yaboot, the linux kernel bootloader, is located. It is formatted as hfs, because Open Firmware, the so called ppc-bios, can read this format (but only this!). Don't mount this partition! 
After installing, the installer sets the Open Firmware to boot from the apple_bootstrap_partition - doesn't matter where it is. The problem is that, if you need to reset nvram or pram parameters (or if the batteries in your computer are empty, and the computer has no power for a while), the Open Firmware parameters are reset to their default values - Open Firmware was so patched, that it starts from the FIRST HFS PARTITION it finds. The same happens, if you install MacOSX *after* Linux. It will overwrite the Open Firmware configuration.

Therefore is safe to install first macOSX but not on the first partition, and to install a GNU/Linux System after MacOSX - in the first free space if you choose a guided installation. Just to be clear, both configurations work:
1. apple_partion_map
2. apple_bootstrap_partition
3. gnu/linux system (ext3)
4. macosx

But also:
1. apple_partion_map
2. apple_bootstrap_partition
3. macosx
4. gnu/linux system (ext3)
_________________________________________________
The configuration file of Yaboot is /etc/yaboot.conf
There you can specify where any OS is located (see [PPC - Yaboot - How to configure the PPC Bootloader - Multibooting]("http://ubuntuforums.org/showthread.php?t=994882"))
As you can see in the link, you can set the partition, where MacOSX is located (macosx=)

Honestly, I never tried to set there a second MacOSX - because I never needed. But I guess it does not work. I think, you have two options:
1. Setting Leopard as the 'main' MacOSX, and pressing the OPT-Key at boot up, if you need to start from Panther (Open Firmware will show you three HD Icons)
2. Edit the file /etc/yaboot.conf - setting macos=path_of_your_MACOSX_Panther (if I understood correctly your configuration it should be /dev/sda6 - but please check it!) Usually the Option macos is for MacOS9, but I imagine, it COULD work.

To edit the file```
sudo nano /etc/yaboot.conf
```
Add the line macos=/dev/sda6 (again, check this path!)
Exit (Ctrl-X) and press Y (yes) to save the file.
Update the configuration of yaboot```
sudo ybin -v
```
Restart and check if it works

_________________________________________________
Since you lost the configuration of your bootloader setting via the Apple StartUp Disk Utility the Boot Disk (don't use it again, because this Utility sets different parameters in Open Firmware - use instead the Opt-Key at boot up if you got in troubles), you need to rescue your system, starting again from the Alternate Installer CD in rescue mode. At the first prompt, hit the TAB-Key, you should find there a (64-Bit) rescue option, to set again correctly the root partition.

---

### Post by Tommmyboy on 2009-04-20
hi, thanks for taking the time to write up such a thorough explanation. I got everything back in order quickstyle and you actually answered my prayers - Woo Hoo! I was hoping in the back of my mind that this sort of set up with two OS X's would be easily done with the opt key at start up but I was afraid it would mess things up like manually changing the start up Mac OS X version did - I'm too much of a fraidy cat at this point to be messing around with the files that wield the power to render your system uselessly unbootable if you mess something up because I would! 

Thanks again. :popcorn:

---

### Post by stream303 on 2009-04-22
> **Tommmyboy said:**
> ...considering I had heard G5 PPCs were generally a difficult architecture to get up and running. And of course the Mactel support is out of this world -

Glad to hear things are working out for your triple boot!  For the G5's the most problematic issues are for those PowerMac systems that have multiple drives and multiple drive-controllers.  Yaboot has gotten much smarter lately, but sometimes one has to doublecheck the UUID's in /etc/fstab etc.  Also weird things pop up once in awhile on PowerMacs by needing the video card in the top slot instead of the bottom slot (or is it the other way around?)

Generally, the G5 iMacs fare much better, especially if they use nvidia graphics. 

As for support - the forum here is great, and the MacIntel support is second to none.

---

### Post by Tommmyboy on 2009-04-25
hi Steam! Thanks for the additional commentary, I didn't know the difficulties stemmed from modified or added hardware, but that makes sense in terms of your comment about Yaboot - I wanted to audition all of the different flavors of Linux distros before I settled on one and the bootstrap partition on each and everyone had problems (except Yellowdog, but it made my fans run like crazy and it was difficult to find unpaid support or forums) which made the installation unbootable and Linux is all too foreign to me and I wasn't keen on learning by building trial and error. Ubuntu, which ironically enough was my first distro to try installed and ended up being my choice, was the only that got it right without me having to mess around at the command line. 

What I had understood was that the difficulties were based on the fact that the G5 was 64 bit.

And since you mention graphic cards... perhaps you can riddle me this... my iMac has a Nvidia GeForce FX5200 that runs at a max resolution of 1680 x 1050 in Leopard, obviously utilizing all of the screen's real estate. However, in Ubuntu 1680 x 1050 resolution distorts the screen image such that the last centimeter of the right hand side of the screen is basically sliced off and wrapped one pixel down over to the left hand side of the screen, not to mention causing some weird pixelated artifacts at the top of the screen. It drove me crazy so I ran in 1400 x 1050 resolution which reduced my real estate and left me with black bars that drive me crazy too, but less so. I found this to be a problem on all of the live CD's from Gutsy through Jaunty, not to mention the other distro live CD's I tried as well as the Yellowdog I was successful in installing.

Any idea whats up with that? I tooled around the forum and just found a couple items of people mentioning the same problem and lots of optimism of either figuring out their own fix or the community coming up with one, but never saw anything with a resolution - hahahaha - to this problem.

In any case, thanks for your input about the G5, I appreciate your time! :KS

---

### Post by stream303 on 2009-04-25
> **Tommmyboy said:**
> .....each and everyone had problems (except Yellowdog, but it made my fans run like crazy and it was difficult to find unpaid support or forums) which made the installation unbootable...

In YDL's case, it just means that they don't appear to have G5 thermal fan support built in, or if they do, not the ones needed for our G5 iMac.  If one wanted to, they could recompile the YDL kernel to get that support.

> and Linux is all too foreign to me and I wasn't keen on learning by building trial and error. Ubuntu, which ironically enough was my first distro to try installed and ended up being my choice, was the only that got it right without me having to mess around at the command line.

That has always been a problem, where installing Linux on a PPC box can present a large number of difficulties up front due to the hardware quirks, and not really the fault of any Linux installer - which can put newcomers off.  So thanks for hanging in there!  Ubuntu is a fine ppc distro, but there are some rough edges (like including the splash screen by default) that really should be sanded-down. :)

> What I had understood was that the difficulties were based on the fact that the G5 was 64 bit.

Well, not really.  We are using a 64-bit kernel on a 32-bit userland like most all other distros, however Crux-ppc is about to release a full 64-bit kernel AND userland.  But most of the problems just stem from the Apple hardware not talking back to the installer routines properly, rather than any specific 64-bit issues.

> ..However, in Ubuntu 1680 x 1050 resolution distorts the screen image such that the last centimeter of the right hand side of the screen is basically sliced off and wrapped one pixel down over to the left hand side of the screen, not to mention causing some weird pixelated artifacts at the top of the screen.

Hang tight - it is a problem in the nv driver coming from xorg itself - two lines were added to the driver to fix some geometry problems for other users, and left us with that shift.  We got feedback from the nv developer and other users and basically what we need to do is to download the nv driver source in Ubuntu, take out those two new lines, recompile the driver and install it again.  I've done it with Debian and as soon as I get some time, I'll post how to do it here.

But yeah, I went nuts too thinking it was a configuration issue, when it was in the driver itself. :)

Looks like I'll be trying to get that nv driver recompilation project going sooner than later now...

---

### Post by stream303 on 2009-04-25
EASIER solution found to recompiling nv!

Just run the "nouveau" driver instead!  It centered up perfectly on my G5 iMac.  Oh happy day....

I just downloaded it with synaptic, and made sure that I forced it in my /etc/X11/xorg.conf:

```
Section "Device"
        Identifier      "Configured Video Device"
        BusID           "PCI:240:16:0"
        Driver          "nouveau"
EndSection
```

---

### Post by Tommmyboy on 2009-05-03
STREAM!!! with that simple solution, you just resolved all my cognitive dissonance that I had remaining with installing Ubuntu on my iMac (the intent of installation being that Ubuntu would largely replace my daily use of OSX  as PPC support is being dropped with SnowLeopard). I am now 100% happy because I have a system where I don't feel I've made a compromise (which may not be such a great attitude to have, being so rigid sets me up for mucho frustration as you sensed in a post above, will need to work on that.)

Thank you for sharing your knowledge on the subtopics we deviated to on this thread and my God, I don't know what to say about having my whole screen back, intact, displayed as it should be displayed. :guitar:

I should just make the following a signature because I say it every time someone responds to one of my inquiries, and someone ALWAYS responds with some sort of helpful, enlightening information: ** My sincere gratitude and appreciation goes out to all of you here on the Apple Forum who contribute and share your knowledge, expertise, and investigative skills so freely and without want of anything in return. *When they refer to Ubuntu as a community, it really, truly is.*  **

---

