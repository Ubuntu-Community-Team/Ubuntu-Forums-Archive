---
title: "PowerMac G4 tower: 8.10 sound problems"
date: 2008-12-12
forum: Apple Hardware Users
---

### Post by PhDLinux on 2008-12-12
Hello, I'm trying to install 8.10 on a PowerMac G4 tower (466 MHz with ATI Rage Pro AGP video). My first attempt was to do a "Distribution Upgrade" from 8.04. That worked, but not perfectly, so I tried a completely fresh install from the CD. I made it past the unrecognized CD-drive problem, and fortunately had a usable xorg.conf file kicking around to get past the crashing X server. (It uses the "fbdev" driver, not "ati" or "r128".) The next challenge is the sound system.

At first nothing would work. Then, somewhere online, I found the idea of giving the command
   sudo modprobe snd_powermac
That seemed like a good move. It changed things so that the command-line tool "alsamixer" would at least admit that it had found a sound device. However, standard alsa sources (like "speaker-test") produce no audible output. Other writers suggest completely eradicating pulseaudio from the system, but when I ask synaptic to do that, it says that I will have to sacrifice the gnome desktop to complete the transaction. That gives me cold feet, so I cancel the removal. 

I'd love to hear from anyone with a working 8.10 installation on comparable hardware, and particularly about how you got the sound to work. Thanks!

---

### Post by stream303 on 2008-12-12
You may have struck gold!  Could you post your /etc/X11/xorg.conf here?  And possibly pass on any special kernel parameters you may have entered at the 2nd-stage yaboot boot: prompt or in your /etc/yaboot.conf file?  Man, that might really help out a lot of ati users out here with Intrepid...

As for sound - I've run into weirdness before with pulseaudio, and for the time being I can only suggest seeing how far you'd get with totally unscientific methods of working with alsamixer in a terminal:

make sure pcm is up to at least 80 - 90 percent.  Be sure to unmute both the speaker and headphones if present (use the M key to toggle mute/unmute) and bring up the master.  I had a strange interaction where the gui controls and tests would not work properly, but alsamixer in a terminal did.  Not very scientific I know, but maybe ....

I'm dying to see that fbdev entry, not just for Intrepid users, but for all ppc users that might face this very same issue with newer X servers...

---

### Post by PhDLinux on 2008-12-12
Thanks. Video deserves its own thread, but since you asked ...

I spent many more hours doing trial-and-error than the following simple-looking result might suggest. The resulting file /etc/X11/xorg.conf is shown here in its entirety:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fbdev"
        BusID           "PCI:0:16:0"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
        Subsection "Display"
                Depth   24
                Modes "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "DRI"
        Mode    0666
EndSection
```
It seems that both Depth settings are required.

In the boot phase, I edited the file /etc/yaboot.conf to turn off the splash screen at startup. The block of lines that applies to the usual linux kernel now looks like this:
```
image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="vga=795 nosplash"
```
The other entries in this file are unchanged. Apparently yaboot.conf serves only as some kind of mirror of the real boot configuration. Editing it has no effect unless one later says "sudo ybin -v". This command writes the configuration into the mysterious location where the bootloader actually looks for directives.

The vga=795 phrase might very well be redundant or ignored. I didn't try removing it. It does hint at my desire for a 1280x1024 framebuffer console, however. To achieve that, I installed the package fbset. Now I can log out of X, grab a console (CTRL-ALT-F1) and enter these three commands:
```
sudo /etc/init.d/gdm stop
sudo fbset -fb /dev/fb0 -depth 24 1280x1024-70
sudo /etc/init.d/gdm start
```
These stop the GUI, fix the framebuffer settings, and start the GUI back up again. One of life's little mysteries is why this cleans up only console number 1. Other consoles remain stuck at 1024x768 unless I activate them and give the fbset command there, too.

If this helps someone, I will be very satisfied.

---

### Post by Leslie Viljoen on 2008-12-12
Oh, the fbdev entry is well-known. I run that on my MacMini. I wiki'd it a while back here: [http://www.ppclinux.info/wiki/maclin/SDL_on_Radeon](http://www.ppclinux.info/wiki/maclin/SDL_on_Radeon)

Darn I hope I don't get shot at some point for all the references I make to that website!

Anyway, FBDEV fixes the SDL problems I was having, and 2D works very nicely, it just becomes very slow with 3D because FBDEV has no hardware acceleration.

---

### Post by stream303 on 2008-12-12
Thank you for posting that.  At least it can get others up and running with 2D until we find tweaks to get those ati cards to behave again.

And specifying the default depth twice was always a good idea, I think one for the "virtual" size and another for the real one solved issues I had on a different box.

---

### Post by PhDLinux on 2008-12-12
Leslie, Congratulations on getting the video working. I wish I had found your solution before groping toward my own. Back on the topic of this thread, do you have audio working on your 8.10 installation? If so, I'd love to know what (if anything) you had to do to make it happen.

On the principle of posting only when I have a nugget of actual technical content to contribute, let me mention two things. First, I tried stream303's advice without success. (I am relying on the G4's internal speaker, and ran through all possible permutations in alsamixer.) Second, the detailed instructions at [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
appear not to work for the powerpc: they rely on packages that are not in the community-supported repositories for 8.10. Perhaps I should add that I'm not fussy about how the audio gets achieved: basic functionality will suffice. Thanks.

---

### Post by theZoid on 2008-12-13
My sound starting working in Ubuntu 8.10 (64 bit) when I enabled "surround" channel....not sure why....same problem in MEPIS 8

HTH

---

### Post by PhDLinux on 2008-12-13
Thanks, that did help -- indirectly. 

[SIZE="5"][FONT="Arial Black"]Sound works now ... yippee![/FONT][/SIZE]

alsamixer doesn't offer the 'surround' option for my Tumbler audio hardware, but I re-interpreted your idea as "just turn on anything and everything, whether it seems to make sense or not!" That seems to have done the job. With Bob Marley jammin' through the speakers, I am not about to go back and touch whatever settings I achieved, so I can't report on the precise details of a working combination of settings. All I remember is that I took some care to disable ("MM") the Auto Muting feature, to turn on the PC Speaker, and to un-mute both (!) options for Headphones.

EDIT: Perhaps alsamixer wasn't the only relevant change I made. I also looked at the instructions on the page [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) about getting a working package of ppc-codecs directly from this address: [http://www.mplayerhq.hu/MPlayer/releases/codecs/all-ppc-20061022.tar.bz2](http://www.mplayerhq.hu/MPlayer/releases/codecs/all-ppc-20061022.tar.bz2) Unzipping that archive and putting the files it contained into a new local directory named /usr/local/lib/codecs may have contributed, too. (Earlier attempts to get ppc-codecs from the medibuntu repository had failed, and left me with broken packages. The page just cited does warn that the package in the repository is not intended for 8.10.)

I'm moving on to other issues. Thanks to all who helped; good luck to all who come after.

---

### Post by theZoid on 2008-12-13
> **PhDLinux said:**
> Thanks, that did help -- indirectly. 

[SIZE="5"][FONT="Arial Black"]Sound works now ... yippee![/FONT][/SIZE]

alsamixer doesn't offer the 'surround' option for my Tumbler audio hardware, but I re-interpreted your idea as "just turn on anything and everything, whether it seems to make sense or not!" That seems to have done the job. With Bob Marley jammin' through the speakers, I am not about to go back and touch whatever settings I achieved, so I can't report on the precise details of a working combination of settings. All I remember is that I took some care to disable ("MM") the Auto Muting feature, to turn on the PC Speaker, and to un-mute both (!) options for Headphones.

EDIT: Perhaps alsamixer wasn't the only relevant change I made. I also looked at the instructions on the page [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) about getting a working package of ppc-codecs directly from this address: [http://www.mplayerhq.hu/MPlayer/releases/codecs/all-ppc-20061022.tar.bz2](http://www.mplayerhq.hu/MPlayer/releases/codecs/all-ppc-20061022.tar.bz2) Unzipping that archive and putting the files it contained into a new local directory named /usr/local/lib/codecs may have contributed, too. (Earlier attempts to get ppc-codecs from the medibuntu repository had failed, and left me with broken packages. The page just cited does warn that the package in the repository is not intended for 8.10.)

I'm moving on to other issues. Thanks to all who helped; good luck to all who come after.

Yep, it's channel selection for some reason.  I had nothing till I turned on the Surround channel, then BAM !

---

