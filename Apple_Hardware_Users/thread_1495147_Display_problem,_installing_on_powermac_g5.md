---
title: "Display problem, installing on powermac g5"
date: 2010-05-27
forum: Apple Hardware Users
---

### Post by dmand on 2010-05-27
Hello all,
I'm working on installing Lucid Lynx on a PowerMac g5 and have ran into a problem.
I got the right iso and burned the cd fine; the problem is when I boot up from the cd the terminal/text comes up with options to boot up. No matter what options I use after hitting enter it changes to a white screen with black text showing some information, about the video card it looks like, then the screen goes black. It continues to read the cd, and eventually stops. 

If I choose the 'live-nosplash' (possibly with others too) it eventually plays the startup sound. It looks like it is loading fine but has a problem with the display. I have seen some advice here to change the 'yaboot.conf' file, but the one on the cd only has options for different boot options, nothing with video or drivers.
Here are some of the specs on the machine, I can get more details if needed:

[LIST]
[*] Power Mac G5 (single processor, 1.8Ghz)
[/LIST]

[LIST]
[*] 1.5 GB Ram
[/LIST]

[LIST]
[*] nVidia GeForce FX5200 video card in AGP slot, 64 MB
[/LIST]

[LIST]
[*] Apple Cinema display (old, 17" I think) LCD, max resolution 1280 x 1024, connected through ADC
[/LIST]
 Any ideas how to solve it? Thanks in advance.

---

### Post by linuxopjemac on 2010-05-28
You have to also select a 64-bit version I guess. I would go for an alternate installation (not GUI). You have a running system after this and then you can tweak xorg.conf

---

### Post by linuxopjemac on 2010-06-14
any update? You can always try Debian Lenny 64-bits. Squeeze will not work at the moment at yaboot is broken.

The Xorg.conf file for Karmic Koala you will find here:
[http://mac.linux.be/content/xorgconf-g5-ppc-tower](http://mac.linux.be/content/xorgconf-g5-ppc-tower)

If you want to apply this file to Lenny, you replace "nouveau" with "nv"

---

### Post by tmad40blue on 2010-06-15
I am also attempting to install 10.04 Lucid Lynx on my Power Mac G5 (single 1.6GHz processor) and am running into the exact same problem. I have tried every command I know of when booting from the live CD, including "video=nvidiafb", "video=ofonly", etc. Nothing works. My display is actually a CRT TV with max. resolution of 1024x768.

Does anybody know what the problem may be here?

---

### Post by linuxopjemac on 2010-06-16
Ok, your card is the NVIDIA GeForce FX 5200 Ultra with 64 MB of DDR SDRAM. I am surprised that it gives problems.

I would build this system from the ground up. What I mean with that is that I would first install a minimal Lucid Lynx environment, to which you can add a graphical environment later. For that you need to go for the alternate installer.

[http://cdimage.ubuntu.com/ports/releases/10.04/release/ubuntu-10.04-alternate-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/10.04/release/ubuntu-10.04-alternate-powerpc.iso)

If you burned the CD, can you give me the output of yaboot.conf on the CD ? It gives you the various boot options. I am not familiar with 64-bits.

I would do a cli installation. It will give you a command line environment. When you accomplished that, report again. We will then add xorg.conf and a GUI.

---

### Post by pindar on 2010-06-16
> **linuxopjemac said:**
> I would do a cli installation. It will give you a command line environment. When you accomplished that, report again. We will then add xorg.conf and a GUI.

I would be interested to know if others succeed taking this route. As I wrote in a [similar thread]("http://ubuntuforums.org/showthread.php?t=1480027"), this is **NOT** a xorg problem. When I install Ubuntu 10.04, I don't even get a console (just a few lines output, then a black screen), so I'm unable to install even a CLI system. I have the same GeForce FX5200, so I suspect that the Ubuntu kernel simply doesn't work with this card. I have a Debian Lenny installation on another partition which works, but I was trying to have something a bit more modern. 

pindar

---

### Post by linuxopjemac on 2010-06-16
Pindar: interesting. I hope he goes this route and maybe we find out what the problem is.

Yes, I remember the thread you gave us.

Also interesting:
[http://ubuntuforums.org/showthread.php?p=9391259](http://ubuntuforums.org/showthread.php?p=9391259)

---

### Post by Frobber on 2010-06-16
Just a contribution to this discussion. I have an iMac G5, with the GeForce FX 5200 video. The default xserver-xorg-video-nv loads during install. I've nothing but display problems with this driver. Using synaptic I removed the nv driver and installed the nouveau driver. All works fine.

As far as an /etc/X11/xorg.conf file - starting with kernel 2.6.xx there is a move afoot to do away with .conf files and 'hot' plug devices in which category video is included. I know HAL has problems and the udev community is making strides with work arounds.

I do not have an /etc/X11/xorg.conf file and see no need for one, the display works fine with the nouveau driver and the current kernel.

---

### Post by linuxopjemac on 2010-06-16
I wish I had a G5 here, then I could try things out myself...

---

### Post by dmand on 2010-07-01
Back with an update... I haven't given up yet, just been busy.

I burned the alternate installer to a cd and it boots up fine (the gui is all text based).
When I got to the partitioning part I ran into trouble, for the time being I need to keep OSX on my drive, so I can't just reformat the whole drive.

I tried to install using the option to use the largest contiguous free space on the drive, but it said the free space was too small. I also tried to resize the main apple partition( it's about 150 GB, only 19GB is used). But after I specify the new size and all it reports the error "support for checking hfs+ file systems is not implemented yet."

So, I guess my question is, is it possible to create new partitions while leaving the existing apple partitions? Can I install ubuntu without having to wipe the whole drive?
Also, would the cli installation be done with the alternate installer?

---

### Post by svtguy88 on 2010-07-02
Not to thread jack, but it seems like a *lot* of us are having issues with the LiveCD...be it on a G4 or G5.  I experienced the same few lines of text and garbled display with Ubuntu that others are getting (after doing an alternate install with the all text installer).  

Can anyone successfully boot the live-CD (current--Lucid)?  I've read that older Live-CDs are fine and that the problem is in Lucid.  I'm not sure though.  

I finally got Debian up and running (with a **lot** of help from linxopjemac), and am compiling a custom kernel now...with hopes of getting nouveau to work for me.

---

### Post by linuxopjemac on 2010-07-02
Nouveau should work in Squeeze. I would install Lenny and upgrade to Squeeze (installation of Squeeze from scratch is not possible as yaboot is broken, although I also read in the Debian mailing lists that someone got Squeeze installed by doing a Lenny netinstall and choosing unstable as repository). But I guess that recompiling a kernel will do too ;)

dmand: resizing only works from a liveCD I think, not 100% sure though. You might want to try an older liveCD. See this thread:
[http://mac.linux.be/content/successful-osx-partition-shrink-g4-mini](http://mac.linux.be/content/successful-osx-partition-shrink-g4-mini)

---

### Post by pindar on 2010-09-15
> **linuxopjemac said:**
> Pindar: interesting. I hope he goes this route and maybe we find out what the problem is.

Yes, I remember the thread you gave us.

Also interesting:
[http://ubuntuforums.org/showthread.php?p=9391259](http://ubuntuforums.org/showthread.php?p=9391259)

I'm aware that this thread is by now pretty old, but I just wanted to mention: today, I installed a daily CD of Maverick on my G5, and lo and behold, I get a working system with a crisp display! (The only minor glitch, for those of you who might be interested: the module therm_pm72 has to be inserted manually; until you do, the fans of the G5 will run at full blast). So this looks definitely like a problem with the Jaunty kernel to me.

---

### Post by linuxopjemac on 2010-09-15
Great news Pindar that your screen seems to work automatically.

---

