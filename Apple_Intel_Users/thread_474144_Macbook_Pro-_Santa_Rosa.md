---
title: "Macbook Pro- Santa Rosa"
date: 2007-06-14
forum: Apple Intel Users
---

### Post by trouble1313 on 2007-06-14
***UPDATED EDIT***

Special thanks to Elv13 for this great, straight to the point howto on getting most capabilities working on the Santa Rosa Based MacBook Pro. We've come a long way in just over a month!

MBP Rev 3 HOWTO:

To install ubuntu on your macbookpro santa rosa:
1- downlaod the alternate cd 32 or 64bit
2- burn it under OSX/Windows/linux as an image
3- downlaod and install bootcamp or rEFI
4- boot on the ubuntu cd by holding the c key during boot
5- install ubuntu

To use ubuntu:
1- restart your mac and hold the alt key
2- press escape
3- boot on the failsafe kernel
4- edit the /etc/X11/xorg.conf file (nano /etc/X11/xorg.conf) and change "nv" for "vesa"
5- start X (/etc/init.d/gdm start)
6- download the lastet nvidia driver from the internet (you need to be wired) and patch it using this link [https://cbg.dyndns.org/wiki/ReadingCorner/LinuxOnMacbookPro#graphics](https://cbg.dyndns.org/wiki/ReadingCorner/LinuxOnMacbookPro#graphics)
*dont forget to install build-essential before
7- follow the rest of this link to get things working

To install pommed (powermanagement and driver):
1- cd /usr/src/modules
2- grab it svn co svn://svn.debian.org/pommed
3- downlaoad deps sudo apt-get build-dep pommed
4- cd pommed
5- make
6- follow instruction in INSTALL (file) to install it
7- get the init script from a .deb or the web and copy it to /etc/init.d

To install wireless:
1- sudo apt-get install build-essential
cd /usr/src/modules/
svn checkout [http://svn.madwifi.org/trunk](http://svn.madwifi.org/trunk) madwifi
cd madwifi
make;make install
modprobe ath_pci


To install alsa driver (sound):
1- install deps of alsa (automake, autotools, autoconf ans some other (please provide the list if you do this, i dont remermber it)
cd /usr/src/modules/
rsync -avz --delete rsync://alsa.alsa-project.org/hg/alsa-driver alsa
rsync -avz --delete rsync://alsa.alsa-project.org/hg/alsa-kernel alsa
[download patch_realtek.c.diff]  [https://bugtrack.alsa-project.org/alsa-bug/file_download.php?file_id=2097&type=bug](https://bugtrack.alsa-project.org/alsa-bug/file_download.php?file_id=2097&type=bug)
cd alsa/alsa-kernel
patch -p1 < ../../patch_realtek.c.diff
cd ../alsa-driver
./hgcompile
make
make install
/etc/init.d/alsasound stop
lsmod [verify all snd modules are unloaded]
modprobe snd-hda-intel


*** Original Thread Post***
Just starting a thread to document what works and what doesn't on my new Santa Rosa based MBP. Ok, it's been out all of two weeks now and here's how it stands with Feisty. System was installed and all updates added. 
-
Installation:
-
rEFIt, which allows you to boot more than two OS's (ala Bootcamp) has been fixed and now does work just fine on the SR MBPs. Stellar piece of software!
-
I was unable to boot/install the standard 64 bit desktop CD. I had to use the alternate installer CD. This was strange since an old feisty beta (rev 3?) DID boot just fine. 
-
After installation:
-
Booting: Issue- Leaving splash turned on seems to hang the machine. Since the screen is black, I have no idea what happens. Turning splash off in grub lets the machine boot (likely a vga=xxx added as a boot option would fix this.)
-
Ethernet: Works just fine with sky2. This is a good thing! I've had many a problem with the Yukon drivers on other platforms. The MBP implementation of the card seems to be top notch with great Ethernet features available (jumbos, flow control, offload etc). 
-
Wifi: Does not work out of the box - and be careful here. I grabbed the svn trunk of madwifi and it still didn't work right. I ended up grabbing a snapshot of the 6/13/07 tree and it's working just fine. Power management and all settings seem great. Be advised, todays (6/14/07) snapshot would not compile for me. Madwifi is working with WPA-PSK and running just fine for me.
-
Keyboard and trackpad: Overall working. I am unable to get keyboard backlighting. I installed gsynaptic and it got rid of the terrible tap. I did have to turn on the shared memory setting and set up the xorg.conf as detailed by many other people on the net. I am unable to middle or right click even with F11/F12. This is frustrating.
-
NVidia driver (latest): BROKEN - Crazy colors though X does start. This issue with the 'nvidia' driver has also been noted on nvnews.net. There does not seem to be a solution yet. The 'nv' driver does not work for me at all. I am currently running the 'vesa' driver.
-
Screen: Works but no screen control features. By default, pressing the brightness up and down keys did nothing. I took a look at the hal devices and saw that this new MBP is defined as a 'MacBook Pro3,1 1.0' and the manufacturer is now 'Apple Inc.' instead of 'Apple Computer, Inc' I made changes to the hal devices xml files and now I get the pop up showing that I am hitting the brightness up/down but it doesn't change anything. It still runs full brightness.  This also applies to the light sensor and keyboard backlight as it seems they are defined by hal.
-
Sound: Broken - Device appears correctly but no sound comes out of the speakers. Researching this leads to an issue with the revision of alsa that is available through the repository.  This is also noted with a fix here in this forum (upgrade the alsa version). I have not upgraded alsa yet.
-
Power management: Mostly broken - Suspend does suspend the computer and completely turn off the LCD but it is not able to resume. I've found no option other than turning the system off with the power button. Hibernate is also not working. Upon hitting hibernate, the system tries to hibernate but immediately comes back. 
-
Superdrive: Not working correctly - Though the system installed from CD just fine, the system does not see the CD drive at this point.  I'm guessing with a bit of playing I can get this going but as it stands, it doesn't work.  There are no /dev/cd* , /dev/dvd*, /dev/hd* or /dev/sd* (other than sda which is the hard drive). 

iSight: Sort of works- Honestly I've spent little time playing with this. Since Ekiga is installed by default, I checked it out to see if the video worked. Video does start but it's very choppy and unusable. After ~5 seconds the program crashes. the iSight was configured as V4L2 with both PAL and NTSC settings. Both behaved identically. This could totally be an issue with Ekiga rather than the isight driver. 


Hopefully, some of you have some work arounds and we can share our fixes!

-Trouble

---

### Post by yanaventer on 2007-06-15
Just to clarify, you used the "Ubuntu v7.04 (Feisty Fawn) Alternate AMD64 ISO" to do your installation?

---

### Post by TrekkieGod on 2007-06-15
> **yanaventer said:**
> Just to clarify, you used the "Ubuntu v7.04 (Feisty Fawn) Alternate AMD64 ISO" to do your installation?

I have almost the exact same nvidia problem as trouble1313, and I did use "Ubuntu v7.04 (Feisty Fawn) Alternate AMD64.iso for my installation.  The difference is that although the splash screen and trying loading X with "nv" driver cause my system to hang, I get a "could not open the device file /dev/nvidia0 (Input / Output Error)" when I try to use the nvidia driver.  Vesa works fine.

I should also point out that although the splash screen also made the system hang with the live cd, the video card problem wasn't the only thing preventing me from using it.  When I took the quiet and splash options out of the boot parameters, I got a "can't access tty" error.  Alternate cd worked perfectly though, I just have to disable the splash screen and I can't use nv or nvidia drivers after it's installed.

---

### Post by trouble1313 on 2007-06-15
Yes, I used the alternate amd64 desktop CD. I had exactly the same issues as Trekkiegod with the regular desktop CD. I believe it has something to do with the drivers for CD and HD and libata? I faced similar issues with an Asus P5B recently. 

-Trouble

---

### Post by trouble1313 on 2007-06-15
Solution for the CDROM

Load the piix module.

I figured it was something this simple :)


(put piix in /etc/modules)


-Trouble

---

### Post by TrekkieGod on 2007-06-15
> **trouble1313 said:**
> Solution for the CDROM

Load the piix module.

I figured it was something this simple :)


(put piix in /etc/modules)


-Trouble

Cool, thanks for hunting that down, trouble.  Now if we can only fix that nvidia problem...

I'm wondering if the nvidia hardware in the apple laptops is significantly different from their standard hardware so that modified drivers will be needed.  Other thing I can think of is that the video bios isn't getting initialized properly.  I installed windows as well though, and if refit was somehow screwing that up I probably would be seeing problems with 3d acceleration in windows too.

---

### Post by xpaulbettsx on 2007-06-16
I collected some kernel info info for anyone who is interested (lspci, lshal, dmesg, etc)

[http://blog.paulbetts.org/index.php/2007/06/16/santa-rosa-macbook-pro-hardware-info/](http://blog.paulbetts.org/index.php/2007/06/16/santa-rosa-macbook-pro-hardware-info/)

---

### Post by trouble1313 on 2007-06-18
Ok folks, I still cant get sound working. I've recompiled from the actual alsa release (several times!) vs. the rc versions and it just isn't working.  Have any of you gotten sound to work? It bums me out that the device is identified correctly but I just can't get any audio out of headphones or speakers. I'm kind of  ok with Nvidia picking their wedgies before they release a fix since vesa works but I just can't get alsa to work. Have any of you gotten it to work? What am I missing?


On a side note, my keyboard backlight seems to work now. I noticed a  hal update and applied it though it may not be the cause (not enough time in bright rooms vs. dark rooms to tell). However, it seems to be an either on or off setup. Either the backlighted keyboard is on, or it's off. To the point of me not being able to tell whether it was something in my environment causing it not to come on previously.  The keyboard backlight controls are totally dead for me.


I've noticed over time that CPU throttling does seem to be working effectively, scaling CPU from 800MHz up to the 2.3xx that it does at full tilt. The FSB speed doesn't seem to change though the multiplier does.  Vista seems to be able to throttle FSB whether it's due to it knowing about Santa Rosa or a platform driver on the Bootcamp 1.3 drivers disk, I don't know, but it does a bit better. I don't think that HD spindown is working and of course, the screen never really turns off. I find myself coming out of closed lid scenario at around 61 degrees C. That ain't great. I come out of closed lid 'suspend' in Vista at ~12C (room temp give or take).


Lets see some input.

-Trouble

---

### Post by trouble1313 on 2007-06-21
Bumping because I see too many of the same questions looking for resolution (Santa Rosa or other that directly apply)  mentioned on this forum but I've yet to see much in terms of solutions except from a few. We really need solutions. Concatenate into a single thread, I don't care, I just want stuff to work and I've got no more answers or time to play as of yet.


-Trouble

---

### Post by ivesjd on 2007-06-21
One thing you could try Trouble, is actually messing with the alsa settings, and the system sound settings. It might be trying to push the sound through something else. That's what was happening on my MacBook 1st gen.

---

### Post by ronocdh on 2007-06-21
> **ivesjd said:**
> One thing you could try Trouble, is actually messing with the alsa settings, and the system sound settings. It might be trying to push the sound through something else. That's what was happening on my MacBook 1st gen.
I too went mad trying to get sound on my MBP, and in the end it was just a simple Sound Preferences change. Sigh.

---

### Post by trouble1313 on 2007-06-21
Aha! LIFE! Thank you for the replies. Unfortunately, no, trying to push sound out through OSS or the ALC device itself doesn't seem to work. Everything possible  (front, speaker, iec, etc) has also been unmuted. No sound comes out of the machine. Again, I've recompiled based on the threads in this and other forums but just don't get a peep. I have no confirmation that anyone has any sound out of a SR chipset MBP under Feisty or any other distro. 

-To update on the nvidia driver based on the nvnews.net discussion....Well it's certain there's a problem but it's kind of unknown what the cause is. 

-As for the screen brightness and keyboard backlight- I have not gotten either to work any further with hal config changes.

---

### Post by chem on 2007-06-22
> **trouble1313 said:**
> AI have no confirmation that anyone has any sound out of a SR chipset MBP under Feisty or any other distro. 


Is this really the case?  What audio chipset is in the SR MBP?  Not integrated Intel sound?  What of reports of people recompiling alsa from the dev tree and getting it working, were those just rumors?  How long do you think it would be until the alsa folks got this working, if it's still broken?

I am trying to decide between a new MBP and a new T61 or T61p.  It's not an easy decision.

---

### Post by trouble1313 on 2007-06-23
I'd love to be wrong here! No sound is the killer for me right now. I've recompiled the alsa driver (and lib) but still get nothing. The device is identified apparently correctly and I can futz with volume and the like but I get nada. I even put some headphones in just to see if it was a speaker issue but still...nothing. Now of course I can't say that NOBODY has gotten this working but I've yet to find any confirmation that somebody has :(


-Trouble

---

### Post by saserlite on 2007-06-24
Got Santa Rosa Macbook 17" yesterday.

Current status: 
[LIST]
[*]No luck with standard 7.04 (AMD64) client install, alternate 7.04 (AMD64) client installed ok using the "text install" option.
[*]Gutsy Gibbon alternate version installs ok, but appears to have even more serious graphics issues: i can't even get vesa working for graphics.
[*]no sound - have tried alsa mixer to no avail
[*]no nvidia drivers work - although vesa is effective (and surprisingly the open gl screensavers work fine)
[*]i can't for the life of me get the wifi working with madwifi (i get compilation errors) - any help here would be appreciated
[*]wired ethernet is fine though
[*]no hibernate/suspend yet
[*]cd-rom - doesnt work out of box, but adding piix to the modules list fixes this
[/LIST]

---

### Post by ronocdh on 2007-06-25
> **saserlite said:**
> Got Santa Rosa Macbook 17" yesterday.

Current status: 
[LIST]
[*]No luck with standard 7.04 (AMD64) client install, alternate 7.04 (AMD64) client installed ok using the "text install" option.
[*]Gutsy Gibbon alternate version installs ok, but appears to have even more serious graphics issues: i can't even get vesa working for graphics.
[*]no sound - have tried alsa mixer to no avail
[*]no nvidia drivers work - although vesa is effective (and surprisingly the open gl screensavers work fine)
[*]i can't for the life of me get the wifi working with madwifi (i get compilation errors) - any help here would be appreciated
[*]wired ethernet is fine though
[*]no hibernate/suspend yet
[*]cd-rom - doesnt work out of box, but adding piix to the modules list fixes this
[/LIST]
Could you guys run **sudo update-pciids** and **lspci** so we know your soundcard info?

---

### Post by adcurtin on 2007-06-25
> **ronocdh said:**
> Could you guys run **sudo update-pciids** and **lspci** so we know your soundcard info?

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
seems to be the only this pertaining to audio.

I used an UbuntuStudio install dvd, which worked fine, it's a text installer. I tried getting rid of the splash and quiet options in the 32bit feisty livecd/installer, and setting the graphics mode to 1280x1024, but neither worked.

---

### Post by chem on 2007-06-25
> **adcurtin said:**
> 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
seems to be the only this pertaining to audio.


If that's the Intel integrated (Santa Rosa) audio, then some people with the Thinkpad T61 have been able to download dev tree alsa and get it to work (Thinkpad has intel, too).  I don't know if it's the same audio, though.  Good luck.

---

### Post by ivesjd on 2007-06-25
> **adcurtin said:**
> 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
seems to be the only this pertaining to audio.

I used an UbuntuStudio install dvd, which worked fine, it's a text installer. I tried getting rid of the splash and quiet options in the 32bit feisty livecd/installer, and setting the graphics mode to 1280x1024, but neither worked.

If your having problems with Ubuntu Studio. You might consider reinstalling with fiesty. Wireless didnt work in US out of the box for me. Dont know what else didnt work cause I installed Fiesty after that. But you can install all the meta packages for US afterword. Let me know, I've got a how-to saved somewhere if you want it.


Here's my sound info for my MacBook 1st gen (just for reference) 
Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
So it seems that they are using a newer sound chip in the SR MBP. Hope you guys can get it working. :)

---

### Post by ronocdh on 2007-06-25
> **adcurtin said:**
> 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
seems to be the only this pertaining to audio.

I used an UbuntuStudio install dvd, which worked fine, it's a text installer. I tried getting rid of the splash and quiet options in the 32bit feisty livecd/installer, and setting the graphics mode to 1280x1024, but neither worked.
Interesting. Welcome and aboard and please remember to post your hardware info so people can better understand your issue. So that you know, there's also a text-based Feisty installation CD called the "alternate," but I can't attest to its working on the SR MBPs.

---

### Post by saserlite on 2007-06-26
> **ronocdh said:**
> Could you guys run **sudo update-pciids** and **lspci** so we know your soundcard info?

Here's the output from my 17" Santa Rosa Macbook Pro:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0407 (rev a1)
0b:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)
0c:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 436a (rev 13)
0d:03.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 02)

---

### Post by saserlite on 2007-06-26
Instructions on how to get a graphical install of Ubuntu on a Santa Rosa MBP:

[LIST=1]
[*]Install Ubuntu Alternate AMD64 7.04 via text install (note must be the Alternate version)
[*]Once installed, at the grub loader press "Esc"
[*]Choose recovery mode (this is because the GUI doesn't work out of the box)
[*]Type in: "sudo dpkg-reconfigure xserver-xorg", choose the vesa driver, leave all the defaults, but ensure the native resolution of your macbook is selected
[*]Once returned to the shell prompt, type "gdm", this will launch gnome
[/LIST]

When I log-in using Gnome I get an error: "Internal Error, failed to initialise HAL!"

Also the hardware information applet doesn't work on my system

Your mileage may vary.

---

### Post by chem on 2007-06-28
No replies here in a couple of days...

For people with sound or suspend problems, have you tried the solutions listed in the Feisty w/ T61 thread?  [http://ubuntuforums.org/showthread.php?t=471563](http://ubuntuforums.org/showthread.php?t=471563)

There are quite detailed instructions on how to get audio working with the alsa cvs tree, and kernel command line tips for suspend.  Also general tips about backporting gutsy's kernel.

As both the MBP and the T61 use the same chipset and (I think) same audio, this should work... right?

---

### Post by russell.h on 2007-06-28
My 15" MBP is supposed to ship next week! Ahh, can't wait that long!

Er... Back on topic.

---

### Post by chem on 2007-06-29
Silly question, but... does right clicking work in Ubuntu with a MBP?  The two-finger touchpad right click?  Any special configuration required?
And for those just joining us, I'm still hoping someone tries out the sound/suspend stuff I mention a couple posts up.  -.-

EDIT: To get sound, suspend, or nvidia video working, it may be worthwhile to **file bugs in the ubuntu database**.  I have been reading through that a bit, and it looks like the ubuntu devs actually respond to reports and fix them (even for MacBook Pro specific bugs!).  As Gutsy Tribe 2 was just released, this would be a great time to install that and file bugs against gutsy.  Maybe everything will work out of box by gutsy-release!

[https://bugs.launchpad.net/ubuntu/+bugs](https://bugs.launchpad.net/ubuntu/+bugs)
[https://wiki.ubuntu.com/DebuggingProcedures](https://wiki.ubuntu.com/DebuggingProcedures)
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by pepe# on 2007-07-02
nvidia: [http://www.nvnews.net/vbulletin/showpost.php?p=1301201](http://www.nvnews.net/vbulletin/showpost.php?p=1301201)
alsa: modprobe snd_hda_intel model=w2jc 

No headphones, but mic and front speaker.

Sensors, keyboard illumination and shortcuts work with patches from mactel-linx and current pommed.

If you have information about iSight or other updates, please mail me, pepe "at" cbg.dyndns.org.

[https://cbg.dyndns.org/wiki/ReadingCorner/LinuxOnMacbookPro](https://cbg.dyndns.org/wiki/ReadingCorner/LinuxOnMacbookPro)


/pepe

---

### Post by trouble1313 on 2007-07-04
Pepe, thank you! I actually had come here to post your alsa modprobe option that I found over at nvnews.net (I figure you're the same pepe ;) ) and saw you put it up....Great find man, made a huge diff for me to stop booting Vista and get back in here to Feisty on this sexy little machine.
Thanks again!


Just to expand and document how everyone can make it work at reboot:


Put the following line in /etc/modprobe.d/options:

options snd_hda_intel model=w2jc



-Trouble

---

### Post by trumpcool on 2007-07-05
To get a right and middle click you can install mouseemu. By default, F12 is right click and F11 is middle click. The button mappings are supposed to be configurable by editing the /etc/default/mouseemu file but I haven't had any luck so far.

edit> A side effect is that the lights for caps lock and num lock no longer work.

---

### Post by cyberdork33 on 2007-07-05
> **trumpcool said:**
> To get a right and middle click you can install mouseemu. By default, F12 is right click and F11 is middle click. The button mappings are supposed to be configurable by editing the /etc/default/mouseemu file but I haven't had any luck so far.

edit> A side effect is that the lights for caps lock and num lock no longer work.

Thanks, that was annoying since I didn't need it.

---

### Post by Elv13 on 2007-07-05
Hi, i am looking for a new laptop and the santa rosa MBP is an interesting choice. I just have few questions:

Do synaptic is able to enable 2 finger scrolling, multi finger tapping and all these options on the mac book pro (it work on my pc)

Do sensor (accelerometer and light sensor) work? They are probably the same since power book so did someone wrote a driver for them?

Did someone found a way to fix the brightness control?

What about the NouVeau driver? It is an alternative (in early development) nvidia driver. They do support up to 7950, but who know, there is some developer working on 8*** support since month, it can load.

Is it a good laptop or it start to do some overheating out of the box.

---

### Post by detjoe on 2007-07-05
Hey folks, thanks for all the hints. I got sound working as described by pepe. Weird thing is that headphones/external speakers work with the INPUT jack. Its still kind of low volume and a white noise but it works. Front speakers are not muted though.

---

### Post by chem on 2007-07-05
> **detjoe said:**
> Hey folks, thanks for all the hints. I got sound working as described by pepe. Weird thing is that headphones/external speakers work with the INPUT jack. Its still kind of low volume and a white noise but it works. Front speakers are not muted though.

That's a really weird observation about the headphones.  Maybe you (or... anyone with a SR MBP) could work with the alsa-user mailing list to get headphones properly / fully working?  My MBP should arrive in 3 weeks!  I will help out then :P

[http://www.alsa-project.org/](http://www.alsa-project.org/)
[http://news.gmane.org/gmane.linux.alsa.user](http://news.gmane.org/gmane.linux.alsa.user)

---

### Post by detjoe on 2007-07-06
Oh, I should have mentioned that this only works with 6ch activated in the alsa mixer. There is some other stuff you can try like enable/disable optical IO (which works for me). Found all that at [http://wiki.debian.org/MacBookPro](http://wiki.debian.org/MacBookPro) and [http://wiki.debian.org/MacBook](http://wiki.debian.org/MacBook) . The Volume control for the headphones with the line in and muting the internal speakers didn´t work.

---

### Post by ilmarw on 2007-07-10
I got the NVIDIA drivers working, external screen and all, by following this guide: [http://albertomilone.com/latest_nvidia_udsf_edgy.html](http://albertomilone.com/latest_nvidia_udsf_edgy.html)

---

### Post by trouble1313 on 2007-07-10
Ilmarw, you got me excited but after looking at that page, are you sure you're on a MBP with the 8600GT M graphics card? I see no reference to it, it seems to discuss older drivers that don't work with the card at all and the SR MBP   has specific problems. Did I miss something?

---

### Post by alephsmith on 2007-07-10
I can't get the nvidia drivers working even with the external screen->sleep->wake->reboot hack.

I think I'll just wait till the next release and give it another go then. Vesa is killing my eyes.

---

### Post by ilmarw on 2007-07-10
100% positive...

Plus, now I got the sound working, too. Recompiled alsa from CVS, followed the instructions here: [http://alsa.opensrc.org/index.php/AlsaCVS](http://alsa.opensrc.org/index.php/AlsaCVS)

---

### Post by chem on 2007-07-10
> **ilmarw said:**
> 100% positive...

Plus, now I got the sound working, too. Recompiled alsa from CVS, followed the instructions here: [http://alsa.opensrc.org/index.php/AlsaCVS](http://alsa.opensrc.org/index.php/AlsaCVS)

Did  you use the model=w2jc option for snd_hda_intel ?  Or does the latest alsa CVS correctly autodetect the SR MBP's sound chipset?  That would be a first report of this.  Does your headphone jack work, volume control and all?

---

### Post by Elv13 on 2007-07-10
> **ilmarw said:**
> 100% positive...

Plus, now I got the sound working, too. Recompiled alsa from CVS, followed the instructions here: [http://alsa.opensrc.org/index.php/AlsaCVS](http://alsa.opensrc.org/index.php/AlsaCVS)

About graphic card
Do you use the 32 or 64 bit version and you did the second method unmodified? And you are using edgy of feisty (the guide talk about edgy)?

---

### Post by Paerez on 2007-07-10
Hey all. I am running on a new MBP santa rosa with 8600m GT, as you all are.

I installed with the amd64 alt cd and edited my grub/menu.lst to turn off splash. I am using the vesa driver for xorg.

I was able to get the close-lid switcheroo to work but it was a pain so I am back to vesa (I used the envy app in feisty to get it to work).

My sound half-worked out of the box. When I plug headphones in and turn all volumes all the way up I can faintly hear music I am playing, but my speakers don't work.

My wifi worked once I upgraded fiesty.

I have not yet tackled suspend or right clicking (I am using a usb mouse for now).


Mainly I am just saying hi and subscribing to the thread, and I will post my victories as I achieve them. I am sure that support will come along for the major components (like sound and video) but the niceties may take a whie (auto-illuminated keyboard).

---

### Post by ahaller on 2007-07-10
Hi, 

unfortunatly i have no sound  using Gutsy Gibbon Testing. Neither through the internal speakers nor through the headphones (or line input). 

I tried *modprobe snd_hda_intel model=w2jc *. I also tried fumbling around with the also-mixer but no success.
Anyone s testing Gutsy and got sound to work?

Bye,
 Andreas

---

### Post by ilmarw on 2007-07-11
> **Elv13 said:**
> About graphic card
Do you use the 32 or 64 bit version and you did the second method unmodified? And you are using edgy of feisty (the guide talk about edgy)?

Sorry, I should have been more spesific. I am using Feisty 32-bit version, and I used the second method from the guide mentioned.

---

### Post by ilmarw on 2007-07-11
> **chem said:**
> Did  you use the model=w2jc option for snd_hda_intel ?  Or does the latest alsa CVS correctly autodetect the SR MBP's sound chipset?  That would be a first report of this.  Does your headphone jack work, volume control and all?

Yes, I use model=w2jc. I tried it earlier, but it didn't work until I used the CVS version. I still do not get jack, and the channels are not right, but I got sound, and that I am happy with.

---

### Post by trouble1313 on 2007-07-11
Ilmar, please help us out on the Nvidia front...You say you used the directions at the site you mentioned...That site references older drivers, that's cool...But those drivers totally don't handle the MBP SR vidcard...The latest Nvidia drivers supposedly support the 8600GT M but are rather broken by default on the MBP SR for whatever reason and have multiple people reporting 'crazy colors' (which is a good way to describe it, and I'd describe what I get out of them similarly). So how are you getting things to work when the rest of us can't? 

Are you using Pepe's (the guy I saw post this hack first) 'use an external keyboard and monitor to set it up' workaround?

Then I say ok, cool, PITA workaround but seems to work I guess...

Are you saying that you just installed the driver and it works just dandy?

If that's the case, I have to call shenanigans because it seems nobody else has been able to get it working properly.

Fill us in!

-Trouble

---

### Post by csaldan on 2007-07-12
I also just bought a new MBP , Santa rosa.

Im pretty new to linux so im not sure how to solve my problem. i tried installing feisty but i get stuck at this one point. During installation when it asks me to start the installation it loads some of the drivers and other stuff and at one point the screen jus goes black and i dont know whts goin on.

Can someone help me with this problem? 

Thanks:confused:

---

### Post by red star on 2007-07-12
Which os are you using? I had the same problem but it was in the iso. I downloaded another copy and it was fine. That could be your problem, or you need to turn splash off.

---

### Post by pepe# on 2007-07-12
hi all,


I got two reports that the current version of xfree-nv driver from git is working, but not at the native resolution it seems.

nvidia color problem is reported by everyone so far. One guy in the nvidia forums said it's going to be fixed in the next version. Full 3d support+external display etc. work with the mentioned workaround. Also note that this works without external keyboard if you are fast enough and close your display before osx wakes up and detects the screens.

I got no further feedback from alsa-dev concerning the audio problem. It looks like a simple problem, as if the channels are mixed up a little. The driver source doesn't look that complicated but I have no time to investigate this further...

trouble1313: I just noticed that I didn't reply to your pm. I read it in the email notification and got motivated enough try again and got iSight working with the mplayer compiled from svn. so cudos to you :)

csaldan: maybe your installer tries to start X? Current nv drivers give a blank display. Try installing without X or with VESA...

Paerez: sound, keyboard backlight, video, s2ram, iSight, touchpad all *sort of* work. If you or anyone find additional information or patches it would be great if you leave a small note in [https://cbg.dyndns.org/wiki/ReadingCorner/LinuxOnMacbookPro](https://cbg.dyndns.org/wiki/ReadingCorner/LinuxOnMacbookPro)

/pepe

---

### Post by csaldan on 2007-07-12
I tried using the x86_64 iso. Could you tell me how to change it to "vesa"?

Thanks a lot

---

### Post by Elv13 on 2007-07-12
use the alternate install cd to boot in rescue mode, mount your partition following instruction on screen, write:
nano /etc/X11/xorg.conf 

and replace nv with vesa

---

### Post by asoare on 2007-07-12
Hello,

I am a new owner of a Santa Rosa MBP and am trying to install ubuntu. As you all said, booting from the live cd doesn't work, something about tty, I don't know. 

So I read I must install from Ubuntu Alternate AMD64 7.04 ? But why not Ubuntu i386 alternate ? MBP is intel-based, not AMD.

Also, can you please direct me in detail on how to install from the command line? I am a linux newbie (windows all my life) and want to make the switch and I need some help.

And is it possible to make the graphical install work ? from the live cd ? also I would like to make the gparted live cd work, since it also doesn't work.

Thank you.

---

### Post by ahaller on 2007-07-12
hi,

yes, the new MBP has an intel cpu, but the core 2 duo is a 64bit cpu, so the "AMD64" release should fit best. Dont get irritated by the "AMD"-name. The "64" is the interesting part of it.
On the download page ([http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)) the 64bit relase is correctly describes as for "64bit AMD and Intel computers".
You can also use the 32bit version ("i368") version as i do. But i think 64bit should be the better choice. 
(i dont really know about this stuff well, i only use 32bit because i am currently testing the unstable gutsy relase, and the development usually seems to be a bit slower for 64bit platforms compared to "standard" 32 bit.)

As for the installtion, have you already tried the alternate cd? The installation process is not really more difficult than the grafical installation.

Here's a short description of what i did: 
[LIST=1] Install OSX
Since the standart installation of OSX came with a few things i did not want to be installed (like dozends of additional language packs i dont use), i reinstalled OSX. During installation i partitoned the harddisk to get some space free for ubuntu (sth like 70gb in my case). You cannot choose the ext3 filesystem, so i just chose "free space" or sth like that.
[*] Use the alternate cd to install Ubuntu linux.
I just chose "use free space" or so, when being ask where to install it. 
[/LIST]

Just one thing for you as a beginner. Don't expect everything to run out of the box (like with OSX). Since the new MBP is very new (new chipset, new graphics card) there are issues with getting 3d graphics and sound to work. But, as with every problem for ubuntu, there are (or will be) people who help with finding solutions for these issues.

---

### Post by Elv13 on 2007-07-12
i386 = 32bit
AMD64= 64bit

core 2 duo are 64 bit, it is why you can install ubuntu AMD64. If you want to install Ubuntu i386, you can, you will have flash more easily but you will not take adventage of the power of your hardware.

And dont worry about the alternate installer, it is very easy, all information will be on screen and you will be able to make your partition like with gparted, just without mouse.

---

### Post by pepe# on 2007-07-12
for the 64bit people:

do the drivers work? all of them? nvidia probably not, so no 3d accel?

---

### Post by csaldan on 2007-07-12
> **Elv13 said:**
> use the alternate install cd to boot in rescue mode, mount your partition following instruction on screen, write:
nano /etc/X11/xorg.conf 

and replace nv with vesa

I m using the ubuntu 7 amd64 iso, i hope this is wht u r talking about. I m sorry but i dont noe where to put in those instructions which u jus gave me. How do i get into rescue mode?

Thanks

---

### Post by csaldan on 2007-07-13
so im downloading the alternate version now and this is wht i think im gonna do

At installation command line, i type in

boot: linux rescue 

and then follow instructions for mounting the CD-rom and then i change the videocard driver from nv to vesa in the xorg.conf file?

thanks :)

---

### Post by detjoe on 2007-07-13
Hi. I  used the normal 32bit version.

Boot from the CD. 
Choose "save graphics mode" and press F6.
Remove "splash", "quiet" and "--" then add "all_generic_ide"

That worked for me.

---

### Post by asoare on 2007-07-13
Isn't 32bit more likely to be compatible than 64bit ? Aren't more drivers available and more things working for 32bit ?

@detjoe: nice, it worked for me too, but can you please explain what quiet, -- and all_generic_ide mean ? And why it works this way and not the normal way ?

I used gparted to create a fifth partition (ntfs) for data storage but it doesn't work in vista, it is considered unallocated space, because it is the fifth primary partition. How do I create it without making it primary ?

Also, can you please guide me in installing from graphical ? i want a triple boot and read in the guide :

> For triple boot, make a swap file because of partion number limit explained
on [http://wiki.onmac.net/index.php/Trip...t_via_BootCamp](http://wiki.onmac.net/index.php/Trip...t_via_BootCamp)
Open a terminal. (Application>Accessories>Terminal)
Quote:
sudo su
mkdir /mnt/linux
mount -t ext3 /dev/sda3 /mnt/linux
sudo dd if=/dev/zero of=/mnt/linux/swap bs=1024 count=2097152
mkswap /mnt/linux/swap
swapon /mnt/linux/swap

sudo dd if=/dev/zero of=/mnt/linux/swap bs=1024 count=2097152 --> doesn't do anything ... what is it supposed to do and how do I make it work ? and how do I choose swap as file ?

---

### Post by alephsmith on 2007-07-13
> **pepe# said:**
> for the 64bit people:

do the drivers work? all of them? nvidia probably not, so no 3d accel?

**Nvidia**: (+twinview) works using the sleep & external screen thing. Compiz-fusion is working fine. I'm using packages from uPure64 repos.

**alsa**: works from after compiling from latest snapshot.

**madwifi**: works, but not from svn. I took an older snapshot and I can't remember the exact date. Was a bit of pot luck. Also setting up WPA2 was a pain.

Haven't tried iSight yet.

**Flash**: works via nspluginwrapper

---

### Post by alephsmith on 2007-07-13
I just received a Software update in OS X:

```
Macbook Pro EFI Firmware Update 1.3
```

Will this screw up my dual boot setup? Should I be wary?

---

### Post by pepe# on 2007-07-13
> Will this screw up my dual boot setup? Should I be wary?

It could overwrite the refit bootloader, see here what to do: [http://refit.sourceforge.net/doc/c1s4_osxupdates.html](http://refit.sourceforge.net/doc/c1s4_osxupdates.html)

The enable-script is somewhere in /efi/refit or so, do not use the one from the install package. installing again will probably work too...

> alsa: works from after compiling from latest snapshot.

Works as in 'works' or do you mean with model=w2jc?
I've seen nothing at alsa-devel that would fix santa-rosa mbp during the last days.

Latest status is w2jc + seperate front and linout mute switches as described in [http://article.gmane.org/gmane.linux.alsa.devel/47539](http://article.gmane.org/gmane.linux.alsa.devel/47539). Just browse the realtek_patch.c for where the w2jc mixer settings are defined and you'll see what you need to change.

---

### Post by csaldan on 2007-07-13
> **csaldan said:**
> so im downloading the alternate version now and this is wht i think im gonna do

At installation command line, i type in

boot: linux rescue 

and then follow instructions for mounting the CD-rom and then i change the videocard driver from nv to vesa in the xorg.conf file?

thanks :)


i still cannot install it , once i boot in rescue mode, it starts asking me for my keyboard type and after it s done doing the network configurations it doesnt do anything after tht , it jus gives me a blue screen with rescue mode written on the top

---

### Post by Elv13 on 2007-07-13
> **csaldan said:**
> so im downloading the alternate version now and this is wht i think im gonna do

At installation command line, i type in

boot: linux rescue 

and then follow instructions for mounting the CD-rom and then i change the videocard driver from nv to vesa in the xorg.conf file?

thanks :)

When to boot with the alternate cd, you will have this option right on your screen. Then follow instruction.

---

### Post by alephsmith on 2007-07-13
@pepe

Yes, you are right. It works when set to model=w2jc
I've done so many things trying to get everything to work  I tend to the steps I've taken.

---

### Post by Corvias on 2007-07-14
OK. So I just spent the last hour posting bugs relating to gutsy and the macbook pro. Let's get to work and make sure that the final release of gutsy works flawlessly on the MBP SR! Being active on launchpad is the only way that we'll get things working by default, rather than having to jump through hoops to get a fully functioning system

I'll even make it easy on you. Below are the links to launchpad of the six bugs I posted. Please add comments and details, so the devs know that there is an interest!

[https://bugs.launchpad.net/ubuntu/+bug/125911](https://bugs.launchpad.net/ubuntu/+bug/125911)
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/125914](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/125914)
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/125915](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/125915)
[https://bugs.launchpad.net/ubuntu/+bug/125916](https://bugs.launchpad.net/ubuntu/+bug/125916)
[https://bugs.launchpad.net/ubuntu/+bug/125918](https://bugs.launchpad.net/ubuntu/+bug/125918)
[https://bugs.launchpad.net/ubuntu/+bug/125919](https://bugs.launchpad.net/ubuntu/+bug/125919)

these refer to the display brightness, the default nv xorg module, the mvidia-glx package, the "crazy colors" bug under feisty, the keyboard light sensors, and the wifi adapter.

Lastly, there's also a bug posted related to the sound problems someone posted recently. It can  be found here:

[https://bugs.launchpad.net/ubuntu/+bug/125332](https://bugs.launchpad.net/ubuntu/+bug/125332)

Make some noise!

---

### Post by isitbreakfastyet on 2007-07-14
Well done for doing that.

I have a brand new Santa Rosa MBP and have had to switch to OSX until this is fixed. :-(  , and have to say that although OSX is a nice OS, I really miss alot of Linux apps, such as Amarok, Rosegarden and Konqueror. Being in OSX feels like being in a mercedes with a 1.0 litre engine.

I have got Kubuntu installed fine after disabling the splash screen etc.

Any developments and I will be happy to test them out.

---

### Post by amonsul on 2007-07-15
Hi!
Im in New York Applestore thinking about buying a Macbook. I need Final Cut Pro. But i work with Ubuntu too so reading yor post im getting a little afraid. It seems that we have a lot of Problem running Ubuntu on a Macbookl. 

Maybe it would be nice to develop a Ubuntuversion especially created for macbook pros. 

Bye

---

### Post by cyberdork33 on 2007-07-15
> **amonsul said:**
> Hi!
Im in New York Applestore thinking about buying a Macbook. I need Final Cut Pro. But i work with Ubuntu too so reading yor post im getting a little afraid. It seems that we have a lot of Problem running Ubuntu on a Macbookl. 

Maybe it would be nice to develop a Ubuntuversion especially created for macbook pros. 

Bye

It's not a problem of a special version, it is a problem of getting things to work at all... in any version of linux.

---

### Post by dpope on 2007-07-16
Hi All,

I currently own a MacBook Pro 15" rev 2 (merom core 2 duo and ATI X1600 card) but this laptop has many problems under linux.  I'm planning to sell it and get a new laptop, either a rev 3 with a Nvidia card or maybe some other laptop.  I've skimmed over all the posts on this thread and see that the santa rosa MBP is not spectacularly well supported under linux but things seem to be improving.  I would appreciate it if someone could explain/list what the major open issues are and if they think these will be resolved.  

My impression is that Nvidia, unlike ATI, makes decent, albeit closed-source, driver for linux so, even if they don't work right now they likely will improve soon.  One of the major problems with the rev 2 MBP is the very high power consumption which many people think is related to the fact that the X1600 on the rev2 (unlike the rev1) could not be powered down to a lower clock rate.  Does power management currently work for the GPU on the Santa Rosa MBPs?  What kind of battery life are people currently getting in Linux (vs OS X)?  Does the machine run much hotter in Linux and does it consume much more power.

Two issues which I don't think have been fixed in the SR MBP are the low dpi (1440 at 15" is not impressive) and the limited tilt angle of the screen which makes it hard to read things on your lap quite often.  If anyone knows of a laptop with similar specs/weight as the MBP but has a higher res screen please let me know.

thanks

---

### Post by ahaller on 2007-07-16
hi dope,
i can say that the rev. 3 MBP is not getting as hot as the rev. 2. One Problem i had with the rev. 2. was that the fan was spinning almost always. The fan of the rev. 3 does not spin all the time. Eventually i would say the fan spins like in osx - so you dont care about it.

In spite of that, i cannot say that the power consumption has improved very much. The gpm-applet says that the fully charged battery "provides 1 hour 55 minutes battery runtime". But i did not test these numbers. 

I am running the vesa driver, because the nvidia driver does not work at the moment, as you mentioned.
I dont know any laptop with a better screen. I hope and believe, that the linux situation of the MBP will improve. So i say one of the most steadfast arguments against the MBP is the lack of a second mouse button... (and maybe the price)

---

### Post by ilmarw on 2007-07-17
> **trouble1313 said:**
> Ilmar, please help us out on the Nvidia front...You say you used the directions at the site you mentioned...That site references older drivers, that's cool...But those drivers totally don't handle the MBP SR vidcard...The latest Nvidia drivers supposedly support the 8600GT M but are rather broken by default on the MBP SR for whatever reason and have multiple people reporting 'crazy colors' (which is a good way to describe it, and I'd describe what I get out of them similarly). So how are you getting things to work when the rest of us can't? 

Are you using Pepe's (the guy I saw post this hack first) 'use an external keyboard and monitor to set it up' workaround?

Then I say ok, cool, PITA workaround but seems to work I guess...

Are you saying that you just installed the driver and it works just dandy?

If that's the case, I have to call shenanigans because it seems nobody else has been able to get it working properly.

Fill us in!

-Trouble

It just worked out of the box, I never attached an external monitor or keyboard to it until it worked. What you sais got me thinking. I hardly ever use OSX, so I tried to reboot Linux after I had started OSX. It seems that I experienced the same problem as you guys, sorry to get you excited.

The only explanation for this would be that I entered the state that pepe described not in the exact way he did, but through waking up my machine using the remote control (i did that once). I haven't tried to reproduce that (haven't got the time).

ilmar

---

### Post by [woodstock] on 2007-07-18
> **ahaller said:**
> hi dope,
In spite of that, i cannot say that the power consumption has improved very much. The gpm-applet says that the fully charged battery "provides 1 hour 55 minutes battery runtime". But i did not test these numbers.

Close to 2 h battery life with a fully charged battery? That isn't much indeed.
Has anyone tried a kernel > 2.6.21 (Gutsy for instance or a self patched kernel) yet? I have read somewhere that there should be some improvements concerning the power consumption under linux. Can anyone confirm that?

---

### Post by dpope on 2007-07-18
> **ahaller said:**
> hi dope,
i can say that the rev. 3 MBP is not getting as hot as the rev. 2. One Problem i had with the rev. 2. was that the fan was spinning almost always. The fan of the rev. 3 does not spin all the time. Eventually i would say the fan spins like in osx - so you dont care about it.

In spite of that, i cannot say that the power consumption has improved very much. The gpm-applet says that the fully charged battery "provides 1 hour 55 minutes battery runtime". But i did not test these numbers. 

I am running the vesa driver, because the nvidia driver does not work at the moment, as you mentioned.
I dont know any laptop with a better screen. I hope and believe, that the linux situation of the MBP will improve. So i say one of the most steadfast arguments against the MBP is the lack of a second mouse button... (and maybe the price)

Thanks for the response.  I think there is a lot that can be done to improve power management.  First, once the nvidia driver works (open source or closed source) it should provide power states that can reduce power usage.  Second, as I understand, you can't dim the screen yet and that will obviously have a big effect. Third, the new kernel >2.6.21 has a feature (whose name I've forgotten now) that lets the cpu take better advantage of its deep sleep states so that should also help.  If you look on the mactel-users mailing list you should see that people with rev 1 macbook pros were able to get pretty decent power consumption on their machines.  You can compare you linux and os x power usage directly by comparing the "Power" section in the OS X system profiler with the output of some file in /proc/power/BAT0/ under linux (exact path might be wrong but its something like that).  You have to do this while running on battery and then you can see how much power you're eating up.

Just the fact that the fans aren't spinning all the time is encouraging for me though because this is a serious problem on my MBP rev 2.

How about any other hardware -- does anything else seem like its not going to work anytime soon?  I have potential buyers for my MBP rev 2 so I want to find out ASAP if I should let go of it and get the rev 3.

Incidentally I find the trackpad two and three tap options a nice replacement for having multiple buttons though the linux implementation of two-finger scrolling still needs some work (though the appletouch driver seems to be getting better every time I try it).  

The screen on these machine IMHO is not very impressive.  I had a 17" sony with 1920x1200 res and that is still the most amazing screen.  It can be read from any angle, even on top, is extremely crisp and has superb colors.  I think a 15" should at least be available at 1600x1200.  This is one of my major hold-ups in replacing my rev 2 MBP with a rev 3 (and the limited tilt angle of the screen).  If anyone has interesting alternatives please let me know.

---

### Post by chem on 2007-07-18
> **Corvias said:**
> 
I'll even make it easy on you. Below are the links to launchpad of the six bugs I posted. Please add comments and details, so the devs know that there is an interest!

[https://bugs.launchpad.net/ubuntu/+bug/125911](https://bugs.launchpad.net/ubuntu/+bug/125911)
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/125914](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/125914)
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/125915](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/125915)
[https://bugs.launchpad.net/ubuntu/+bug/125916](https://bugs.launchpad.net/ubuntu/+bug/125916)
[https://bugs.launchpad.net/ubuntu/+bug/125918](https://bugs.launchpad.net/ubuntu/+bug/125918)
[https://bugs.launchpad.net/ubuntu/+bug/125919](https://bugs.launchpad.net/ubuntu/+bug/125919)

these refer to the display brightness, the default nv xorg module, the mvidia-glx package, the "crazy colors" bug under feisty, the keyboard light sensors, and the wifi adapter.

Lastly, there's also a bug posted related to the sound problems someone posted recently. It can  be found here:

[https://bugs.launchpad.net/ubuntu/+bug/125332](https://bugs.launchpad.net/ubuntu/+bug/125332)

Make some noise!

Very nice post Corvias!  Hopefully this will lead to things like ALSA and the nv driver being updated so that they "just work" on gutsy.



Also, regarding dpope and lowering linux laptop power consumption:  [http://www.linuxpowertop.org/results.php](http://www.linuxpowertop.org/results.php)

I think the new feature you're talking about is the dynamic tick (tickless?) kernel, which may or may not be in gutsy (I don't know) for x86-64.  Anyway, that website has a bunch of good tips.

Let's try to keep the chat here related to linux/ubuntu and the rev.3 MBPs, not general ranting and chat about screen resolutions, eh?  :)

---

### Post by 0deuce0 on 2007-07-18
Hey everyone...


What we really need is the first post of this thread to summarize the installation process.  What do to...


For example:

- Installation.   Use the XXX CD.
- Video   
   Instructions for the VESA / or the nvidia
- Sound
- Camera ...


Kind of how the first post is, but maybe keep it upto date with what people have found...


Just a thought... because Im going through all of this thread wondering where to begin...

---

### Post by chem on 2007-07-20
I received my MBP today.  Partitioned with diskutil, installed refit, and tried gutsy tribe 3.  Desktop cd refused to install, but alternate worked.  Had all the same bugs everyone else reported, plus the Superdrive refused to read an audio disc (didn't try data disc) after ubuntu was installed.  One other person had already reported that in launchpad.  I added comments to the other bugs in launchpad.

In short, no improvement with gutsy tribe 3.  I am going to just use mac OS X for a while;  the BSD shell in there + fink is pretty good anyway.

---

### Post by buti on 2007-07-22
> **Corvias said:**
> 
... Below are the links to launchpad of the six bugs I posted. Please add comments and details, so the devs know that there is an interest!

[https://bugs.launchpad.net/ubuntu/+bug/125911](https://bugs.launchpad.net/ubuntu/+bug/125911)
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/125914](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/125914)
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/125915](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/125915)
[https://bugs.launchpad.net/ubuntu/+bug/125916](https://bugs.launchpad.net/ubuntu/+bug/125916)
[https://bugs.launchpad.net/ubuntu/+bug/125918](https://bugs.launchpad.net/ubuntu/+bug/125918)
[https://bugs.launchpad.net/ubuntu/+bug/125919](https://bugs.launchpad.net/ubuntu/+bug/125919)

these refer to the display brightness, the default nv xorg module, the mvidia-glx package, the "crazy colors" bug under feisty, the keyboard light sensors, and the wifi adapter.

Lastly, there's also a bug posted related to the sound problems someone posted recently. It can  be found here:

[https://bugs.launchpad.net/ubuntu/+bug/125332](https://bugs.launchpad.net/ubuntu/+bug/125332)

Make some noise!

what about the dvd drive? does it work on your gutsy-system? it doesn't work for me. i'm booting through refit, might this be a cause?

---

### Post by Paerez on 2007-07-22
buti, are you loading the module piix? You can "sudo modprobe piix" or add the text "piix" to the end of "/etc/modules".

---

### Post by Corvias on 2007-07-22
> **buti said:**
> what about the dvd drive? does it work on your gutsy-system? it doesn't work for me. i'm booting through refit, might this be a cause?

Actually I submitted that one a few days ago:   :)

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126908](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126908)

---

### Post by Baladahn on 2007-07-22
> **asoare said:**
> Hello,

So I read I must install from Ubuntu Alternate AMD64 7.04 ? But why not Ubuntu i386 alternate ? MBP is intel-based, not AMD.


If you want the 64 bit version of the OS, AMD64 is for both Intel and AMD CPUs, as AMD made the current standard x86-64 instruction set.

---

### Post by pepe# on 2007-07-23
little word of warning: After updating the EFI firmware with OSX, the workaround for the current nvidia driver doesn't seem to work anymore. As nv has no xv support, I'm now waiting for the new nvidia driver... :-/

---

### Post by grabbies200 on 2007-07-23
hello, 
i am trying to install ubuntu on my MBP. I d like to install ubuntu on an external usb hard drive. I know grub doesn't support efi/mbr hybrid and i was wondering is someone knows how to install grub2 or eilio so i can boot from my exteranl HD. right now refit sees i have an external hd with linux, but if i try to boot it it tells me that the firmware doesn't support booting from an external hard drive. 
:confused:

---

### Post by Elv13 on 2007-07-23
with the darwin (not bootcamp) bootloader it is possible i think, but i cant test, i dont have mine yet.

---

### Post by alephsmith on 2007-07-24
> **pepe# said:**
> little word of warning: After updating the EFI firmware with OSX, the workaround for the current nvidia driver doesn't seem to work anymore. As nv has no xv support, I'm now waiting for the new nvidia driver... :-/

Unfortunately, I have found the same thing.

I am leaving Ubuntu on my MBP for the time being. I may return when the things start working out of the box. I don't have the time to tinker too much at the moment.

---

### Post by trouble1313 on 2007-07-25
Great news today from nvnews.net! A simple trick to get the NVidia binary official drivers to work on the SR MBP! 

Start X with the nv driver

quit X

change your xorg.conf from the nv driver to the nvidia driver

start X

viola!

All functionality seems to work, xv, glx etc. Beryl runs great.

I automated the starting, stopping, changing driver, restarting with a simple script and have it run on startup in place of /etc/init.d/gdm. It adds maybe 15 seconds to the startup process but I have a good 10 seconds of sleeps in there. I didn't mess with the timing, just guessed so I'll bet it can be cut down a bit. 

Running under the nvidia driver seems to have dropped my coretemp a good 10 degrees and I think shaved ~6 watts off battery usage. (I'm going based on my memory here). My coretemp is at 56 now during usage, was 65 idling. The external heat difference has been very noticeable.

In other words, I'm pretty stoked!

-Trouble

---

### Post by axlsd on 2007-07-25
Hello guys,

can anyone tell me how to install nv drivers?? ..so I can do the nv->nvidia workaround!
now I have just installed the nvidia drivers (with the crazy-colors problem..).

Someone help me please!
Thanks!
ps: I'm an italian user :) , please forgive my mistakes..

---

### Post by dpope on 2007-07-25
Hi Trouble,

What is your power usage and battery life now (you said it dropped six watts but you didn't say from what value)?  Also, do the fans not run much?

thanks

---

### Post by Corvias on 2007-07-25
Great news about that little trick! Ummm. Any chance of sharing that script? 

This is going to sound newbish, but how exactly do you quit x?

---

### Post by alephsmith on 2007-07-26
> This is going to sound newbish, but how exactly do you quit x?

```
sudo /etc/init.d/gdm stop
```

> can anyone tell me how to install nv drivers?? ..so I can do the nv->nvidia workaround!
[http://www.nvnews.net/vbulletin/showpost.php?p=1314378&postcount=73](http://www.nvnews.net/vbulletin/showpost.php?p=1314378&postcount=73)

---

### Post by dpope on 2007-07-26
> **dpope said:**
> Hi Trouble,

What is your power usage and battery life now (you said it dropped six watts but you didn't say from what value)?  Also, do the fans not run much?

thanks

Actually, a more specific question: can you run beryl without your temp going up and your fans running at higher speeds?

---

### Post by axlsd on 2007-07-26
I downloaded xorg-dev, downloaded xorg tarball from the official site, installed it (./configure, make, make install)..
but there is no sub-directory drivers on /usr/local/lib/xorg/modules/
Where is the mistake?

---

### Post by alephsmith on 2007-07-26
I used the tarball from here:

[http://lists.freedesktop.org/archives/xorg-announce/2007-July/000324.html](http://lists.freedesktop.org/archives/xorg-announce/2007-July/000324.html)

---

### Post by pepe# on 2007-07-26
> I downloaded xorg-dev, downloaded xorg

Not needed anymore, gimli posted a patch to the glue-code of the nvidia driver.
I'm unable to download the attachment of his mail in the list archive, so I linked it:

[https://cbg.dyndns.org/wiki/ReadingCorner/LinuxOnMacbookPro#graphics](https://cbg.dyndns.org/wiki/ReadingCorner/LinuxOnMacbookPro#graphics)

Patch, including short hotwo: [https://cbg.dyndns.org/store/config/nv_macbook.diff](https://cbg.dyndns.org/store/config/nv_macbook.diff)


have fun :)

---

### Post by trouble1313 on 2007-07-26
Sorry, I'm away from my laptop right now so I'll try to post that script later...but it really doesn't do anything other than copy an xorg.conf.xxx with nv or nvidia defined into xorg.conf  and do gdm start and stop.


From a power aspect, in testing yesterday, I was idling at about 24 watts. I was at 30 with nv or vesa. Idle temp with nvidia was down to 51 degrees. I ended up with 2 hours and 23 minutes before shutdown on battery BUT I worked it pretty good...compiled a few things, looked at youtube a bit, AND BURNED A DVD! Burning the DVD pushed power up to like 35 watts! 2.5 hours under normal easy use should be no issue at all. Not great, but better and in line with what I see in Vista. During all of this time, Beryl was running and I was playing with it. I don't think the fans ever kicked up to be honest. Beryl doesn't seem to be adding much of a load to the system at all. 


Suspend is still broken. I didn't try hibernating.
For some reason I've lost my keyboard backlight...I don't know if it was due to a normal feisty kernel upgrade or due to nvidia.
-Trouble

---

### Post by axlsd on 2007-07-26
Thanks for your help! 
I finally found my error and now all seems ok! nv->nvidia workaround works fine.
Anyway.. maybe can help someone.. so, the right procedure to install nv drivers is:
apt-get install xorg-dev
then download the following pkg: [http://xorg.freedesktop.org/archive/individual/driver/xf86-video-nv-2.1.2.tar.gz](http://xorg.freedesktop.org/archive/individual/driver/xf86-video-nv-2.1.2.tar.gz)
extract it, go into the directory just created and type:
sudo ./configure
sudo make
sudo make install
if you read the last rows of the installation process you can see that the new module is installed in the local directory : /usr/local/lib/xorg/modules/drivers/
so.. rename the current nv  module and create a symbolic link to the module just builded:
cd /usr/lib/xorg/modules/drivers
sudo mv nv_drv.so nv_drv.su.backup
ln -s /usr/local/lib/xorg/modules/drivers/nv_drv.so

Last steps (nv->nvidia workaround), stop gdm, change the xorg.conf so it can load first the nv driver then type startx and log-out.
Change again  the xorg.conf so it can load the nvidia driver then type startx.
That's all.

Ps: again, forgive  my bad english writing..

---

### Post by pepe# on 2007-07-26
You can start X directly:

Xorg  -novtswitch -config ~root/nv-driver.conf
sleep 5
killall Xorg


Anyways, restarting X/gdm is not neccessary with the patch by gimli I posted above. No need screwing around with latest x11 tarballs.

Edit:

There is now a patch for alsa and a tool for backlight control:

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3242](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3242)
[http://felipe-alfaro.org/blog/2006/09/11/basic-backlight-support-for-macbook-pro/](http://felipe-alfaro.org/blog/2006/09/11/basic-backlight-support-for-macbook-pro/)

Together with the modified nvidia driver, the macbook gets quite useable.

trouble1313, you said you have no suspend. If you mean s2ram, I have this working with the nvidia driver. However, the text consoles are broken afterwards and vbetool doesn't seem to help. Just make sure to unload alsa,madwifi and the sky2 module.  Then execute this:

chvt -t 9
echo mem > /sys/power/state
chvt -t 7
chvt -t 9
chvt -t 7

---

### Post by Paerez on 2007-07-26
I used the diff patch in a previous post and my MBP is now compiz-fusion-tastic!

---

### Post by trouble1313 on 2007-07-26
Awesome...that patch worked great! Great find.

---

### Post by axlsd on 2007-07-27
The diff patch works fine, I installed compiz-fusion.. It seems a little heavy sometimes.. in particular way if I try to rotate the cube when reflex are activated, the framerate is lower.  Has anyone the same "problem"?

---

### Post by Paerez on 2007-07-27
It's probably just because you're asking for it to do a lot of work, so it's laggy.

Remember compiz technology is so new it may not do effects you're used to in video games as quickly as a video game can do them.

I haven't played with compiz much, but it seemed pretty snappy to me.

---

### Post by epaulin on 2007-07-27
> **pepe# said:**
> > I downloaded xorg-dev, downloaded xorg

Not needed anymore, gimli posted a patch to the glue-code of the nvidia driver.
I'm unable to download the attachment of his mail in the list archive, so I linked it:

[https://cbg.dyndns.org/wiki/ReadingCorner/LinuxOnMacbookPro#graphics](https://cbg.dyndns.org/wiki/ReadingCorner/LinuxOnMacbookPro#graphics)

Patch, including short hotwo: [https://cbg.dyndns.org/store/config/nv_macbook.diff](https://cbg.dyndns.org/store/config/nv_macbook.diff)


have fun :)


hi, pepe, tnx for your great infomation.

Could your mail it to me, seems my network can't access it neither through tor.

epaulin _AT_ gmail dot com

---

### Post by cyberdork33 on 2007-07-27
> **Paerez said:**
> It's probably just because you're asking for it to do a lot of work, so it's laggy.

Remember compiz technology is so new it may not do effects you're used to in video games as quickly as a video game can do them.

I haven't played with compiz much, but it seemed pretty snappy to me.

Yea it is actually one of the suprising things that people catch, compiz-fusion seems to have a much faster response than beryl does.

---

### Post by axlsd on 2007-07-27
Still another thing, I installed Ubuntu with lilo bootloader (I read somewhere that linux boots only with it).. but I can boot with splashscreen and framebuffer with a good resolution.. Does anyone boot linux with grub? ..and can give me a hand to configure it?:)
Thanks!

---

### Post by pepe# on 2007-07-27
pommed now includes the display control code from above in svn rev 346:

svn co svn://svn.debian.org/pommed


Automatic keyboard backlight was also updated in v1.8.
Debian/unstable still has an older version, don't know for ubuntu.

if you find something new with how the alsa driver is working or is supposed to, please post it here: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3242](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3242)

---

### Post by epaulin on 2007-07-27
I got a error when I was following instruction to build NVIDIA module which is a link from pepe 

Is here any one got it work on Ubuntu gutsy with  AMD64 version, gcc 4.1.3 20070718, 2.6.22-8-generic?

here is the error msg:
{{{
   r/src/nv/nvacpi.c:15:
   include/asm/compat.h: In function ‘compat_alloc_user_space’:
   include/asm/compat.h:202: warning: pointer of type ‘void *’ used in arit
   hmetic
     ld -m elf_x86_64  -r -o /media/tmp/software/NVIDIA-Linux-x86-100.14.11-pkg
   1/usr/src/nv/nvidia.o /media/tmp/software/NVIDIA-Linux-x86-100.14.11-pkg1/us
   r/src/nv/nv-kernel.o /media/tmp/software/NVIDIA-Linux-x86-100.14.11-pkg1/usr
   /src/nv/nv.o /media/tmp/software/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv/
   nv-vm.o /media/tmp/software/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv/os-ag
   p.o /media/tmp/software/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv/os-interf
   ace.o /media/tmp/software/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv/os-regi
   stry.o /media/tmp/software/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv/nv-i2c
   .o /media/tmp/software/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv/nvacpi.o
   ld: Relocatable linking with relocations from format elf32-i386 (/media/tmp/
   software/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv/nv-kernel.o) to format e
   lf64-x86-64 (/media/tmp/software/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv/
   nvidia.o) is not supported
   make[3]: *** [/media/tmp/software/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv
   /nvidia.o] Error 1
   make[2]: *** [_module_/media/tmp/software/NVIDIA-Linux-x86-100.14.11-pkg1/us
   r/src/nv] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
:

}}}

---

### Post by macmatt on 2007-07-27
How to lose a Mac's original UI beauty....

Install Ubuntu...

UGHH!!!!:(

Does Linux community not "get it" like us Mac OS users do?. I want my car to drive, but I don't wanna stop every 1/2 mile to repair it!. Mac OS X... yummy, powerful AND simple to run. When Leopard comes, you bunnies better get ya cloning hats on, like you did with Expose ;)

---

### Post by pepe# on 2007-07-27
ld: Relocatable linking with relocations from format elf32-i386 (/media/tmp/software/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv/nv-kernel.o) to format elf64-x86-64 (/media/tmp/software/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv/nvidia.o) is not supported

Looks like you are trying to combine 32bit and 64 bit. Both files are from x86, so maybe your system is x64?


> How to lose a Mac's original UI beauty....

Some day, somebody need to explain to me how in the world people came up using a mouse-driven GUI for laptops. Devices which don't even have a mouse most of the time..

And...you know...some people need more that chat and paint. Have you ever tried to use your home/end keys in the console? Or partitioning your drives with OSX' fdisk?

But I agree that OSX is nice for painting. Of course, a pencil would do, too...

---

### Post by macmatt on 2007-07-27
> **pepe# said:**
> ld: Relocatable linking with relocations from format elf32-i386 (/media/tmp/software/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv/nv-kernel.o) to format elf64-x86-64 (/media/tmp/software/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv/nvidia.o) is not supported

Looks like you are trying to combine 32bit and 64 bit. Both files are from x86, so maybe your system is x64?


> How to lose a Mac's original UI beauty....

Some day, somebody need to explain to me how in the world people came up using a mouse-driven GUI for laptops. Devices which don't even have a mouse most of the time..

And...you know...some people need more that chat and paint. Have you ever tried to use your home/end keys in the console? Or partitioning your drives with OSX' fdisk?

But I agree that OSX is nice for painting. Of course, a pencil would do, too...

You evidently don't "get it" then! lol.

Mouse-driven GUI?. Uhhm most GUIs are, by their very nature, mouse-operated; even Ubuntu - what on earth was that meant to mean?!!.

---

### Post by pepe# on 2007-07-27
Ubuntu is no gui. And yes, ubuntu features many window managers that are not primarily mouse-operated.

Please go back to painting.

---

### Post by trouble1313 on 2007-07-27
Folks, don't feed the troll fanbois that are out of their element. You degrade yourselves and feed their foolishness.

-Trouble

---

### Post by epaulin on 2007-07-27
>> Looks like you are trying to combine 32bit and 64 bit. Both files are from x86, so maybe your system is x64?


I'm so stupid, I downloaded x86 32 version driver from NVIDIA site.

Now my Macbook Pro works sweet:

 * sound: alsa-driver from CVS
 * backlight: pommed 0.18
 * wifi: madwifi
 * 8600GT: patch from pepe's link

tnx a lot, pepe.

---

### Post by alephsmith on 2007-07-28
> **pepe# said:**
> pommed now includes the display control code from above in svn rev 346


Thanks pepe#. Works great at my end. Although what is the purpose of wmpomme? Currently it just sits in an irritating window.

Tried compiling alsa with the patch but can't seem to get it working.

Gimlis nvidia patch works well.

One thing that keeps bugging me is that if I kill X (crtl+alt+bksp) I am faced with my desktop background rather than restarting gdm like it used to. I have no idea where to go looking to fix the problem. Currently I'm forced to do a hard reboot.

---

### Post by macmatt on 2007-07-28
> **pepe# said:**
> Ubuntu is no gui. And yes, ubuntu features many window managers that are not primarily mouse-operated.

Please go back to painting.

Did you ever hear of 'Darwin'?. I assume you'd know what that was. If I were putting ANY Linux on my MacBook Pro, it would be Linux Mint; IMHO a vast improvement on Ubuntu, and BASED upon it.

---

### Post by epaulin on 2007-07-28
NVIDIA driver failed toinitialize when I were restart my computer, I look up the dev dir, the nvidia and nvidiactl devices was created, I don't know what I'm doing wrong.


It works when I start the computer and reinstall the nvidia drivers, I assume this is a devfs or udev setting issue, but really don't know how to fix it.

{{{
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
}}}

---

### Post by alephsmith on 2007-07-28
I had something similar and needed to explicitly stop the nv and nvidia_new modules from loading.

```
sudo nano /etc/default/linux-restricted-modules-common
```

changing

```
DISABLED_MODULES=""
```
to 
```
DISABLED_MODULES="nv nvidia_new"
```

---

### Post by pepe# on 2007-07-28
epaulin:
> sound: alsa-driver from CVS

Suppose you mean alsa from cvs(hg, in fact) and patched with [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3242](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3242)


aleph:
> Although what is the purpose of wmpomme? 

Huh? Its made for nextstep-style window managers. They include these little apps in bars: [http://malison.org/uploads/Screenshots/2004-11-23-2_1024x768.png](http://malison.org/uploads/Screenshots/2004-11-23-2_1024x768.png)

> Tried compiling alsa with the patch but can't seem to get it working.

Wanted to buy chocolate yesterday but all shops were closed.


clueless fanboy:
> Did you ever hear of 'Darwin'?

Nice. Now go back to my first answer and notice that I already gave examples about the amazing usablity of the BSD subsystem in OSX.

And yes, I have no doubt you would install linux-mint. But with your requirements(painting, 3d eye-candy, clueless), you should just stay with OSX. And please don't assume everyone has your requirements. I'll recommend OSX to my girlfriend(painting, chat,..) at any time, its a great solution there. But please, not for me...

---

### Post by cyberdork33 on 2007-07-28
Please stop. there is no need to argue about this.

---

### Post by ahaller on 2007-07-28
> **axlsd said:**
> Still another thing, I installed Ubuntu with lilo bootloader (I read somewhere that linux boots only with it).. but I can boot with splashscreen and framebuffer with a good resolution.. Does anyone boot linux with grub? ..and can give me a hand to configure it?:)
Thanks!

hi. i think the lilo-only thing has been solved some time ago.
i installed feisty on the rev. 2 MBP and gutsy on the rev. 3 / santa-rosa just with the alternate cd  (after having installed refit). 
so i always use grub. but i cannot tell you, how to change from lilo to grub.
my assumption would be just to install the grub package, and the do a *grub-install*, but i really don't know.

maybe these pages help
[https://wiki.ubuntu.com/MacBookProFeisty](https://wiki.ubuntu.com/MacBookProFeisty)
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by pliz on 2007-07-29
Guys, was anyone successful with suspend/resume on MBP 3? My machine goes to sleep without a problem, but I do not have both screen and keyboard alive after it wakes up. Can log into it by ssh with no problem though.

If you have suspend working at your machine can you share the steps you took, please?

---

### Post by epaulin on 2007-07-30
alephsmith :
>> I had something similar and needed to explicitly stop the nv and nvidia_new modules from loading.

>> sudo nano /etc/default/linux-restricted-modules-common
>> DISABLED_MODULES="nv nvidia_new"

tnx, this works.

pepe#:
>>Suppose you mean alsa from cvs(hg, in fact) and patched with [https://bugtrack.alsa-project.org/al...ew.php?id=3242](https://bugtrack.alsa-project.org/al...ew.php?id=3242)

No, My system is gutsy, what I'm doing is compiled alsa-driver component which sync from alsa cvs, and with the option you post it before:
options snd_hda_intel model=w2jc

I haven't alsa bug track account yet, so I don't what exactly the bug is.

---

### Post by pepe# on 2007-07-30
> If you have suspend working at your machine can you share the steps you took, please?

- do it manually
- and again
- try something else
- ...
- find out that you need to remove some modules like alsa and madwifi and that you need to switch to console and back to X two times and load usb afterwards because otherwise you have no keyboard, like posted above

> I haven't alsa bug track account yet, so I don't what exactly the bug is.

Give it a try when you feel like using the headphone output...there's a guest account..

---

### Post by pliz on 2007-07-30
Thanks, pepe#

So I assume you do all the steps with a script? When keyboard is not working switching back and forth between console and X seems problematic. Do you mind sharing the script?

Thanks again!

---

### Post by Paerez on 2007-07-30
Sorry if I am asking something already mentioned ....

I am attempting to install alsa. I have rsynced the alsa-driver and alsa-kernel. I patched alsa-kernel with the patch linked by pepe#.

Then I ran:
./hgcompile --with-cards=hda-intel
sudo make install
sudo modprobe snd_hda_intel model=w2jc

and I got:
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

modprobe without the card specified returns the same thing.

dmesg | tail:
[ 1223.200000] snd_hda_intel: Unknown symbol snd_hda_parse_generic_codec

Did I miss something?

---

### Post by Dhjiz on 2007-07-30
Hi,

I think maybe I've found another workaround for the Nvidia drivers.

Everytime I reboot now, the drivers launches withouth any problem and I can launch Beryl after that.

I run under a MacBook Pro 15", 2,2ghz, with the TwinView mode activated.

Here's my xorg.conf file :

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:40:26 PDT 2007

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:39:30 PDT 2007
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"stylus"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection
#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"eraser"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection
#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"cursor"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection

Section "ServerLayout"

#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "fr"
    Option         "XkbOptions" "lv3:rwin_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 72.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Apple Color LCD"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic E651-3"
    HorizSync       30.0 - 56.0
    VertRefresh     50.0 - 120.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GT"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard0"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1440x900 +0+0; DFP: 1024x768 +0+0; DFP: 800x600 +0+0; DFP: 640x480 +0+0"
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "CRT: 1024x768_60 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1024x768_60 +0+0, DFP: 1440x900 +1024+0; DFP: 1024x768 +0+0; DFP: 800x600 +0+0; DFP: 640x480 +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


```

Here's the configuration :

MacBook Pro 15", 2,2ghz with the lateste nvidia drivers obtained via the Envy script. I'm running under Kubuntu Feisty Fawn, and I used the TwinView mode from the Nvidia Settings gui. I configured everything with the gui and I copy and paste the code from the gui to my xorg.conf file (because the nvidia-settings aren't launch as root, so it cannot write directly to the file). The other screen is a ViewSonic E651 located at the left of my laptop, with a resolution of 1024x768.

Everytime I boot under Kubuntu, after the splash screen, I can see a broken nvidia logo (the logo isn't recognizable) and after login, I can enjoy 3D desktop directly. I didn't patch the drivers.

Under Max OS X, sometimes I use the dual screen mode, and sometime I don't, and when I reboot under Linux I always get the nvidia drivers working.

EDIT: you may say what happens when I start Linux without the other screen ? Xorg consider I'm using a huge resolution (2464x900) as if the second screen was present. But, because the CRT screen is at the left, every window I launch doesn't appear on the screen but in the hidden part. But the driver still launches successfully.

EDIT2: I installed the 386 version of Ubuntu, not the AMD64 one.

---

### Post by pepe# on 2007-07-30
> Did I miss something?

You need to reboot.

hehe, just kidding. Try to reload all alsa modules...

> When keyboard is not working switching back and forth between
> console and X seems problematic.

But does not matter, because if it would work, you'd still have no input devs..

kbd and touchpad are usb devices, you need to take care that the corresponding drivers are either unloaded and reloaded correctly or surrive the suspend. My script does not reload usb drivers, so they probably can surrive. Stil, it may be that I oversaw some obscure script shipped with the distro. I'm sure I've seen the default acpi scripts to reload usb. So try it manually first and/or be sure to disable possible interference..

/etc/init.d/pommed stop
/etc/init.d/alsasound stop
/etc/init.d/alsa unload
ifconfig eth1 down
ifconfig ath0 down

rmmod snd_page_alloc snd soundcore
rmmod sky2 i2c_i801 ohci1394 ieee1394
rmmod ath_pci ath_hal ath_rate_sample wlan_scan_sta wlan

chvt -t 9
echo mem > /sys/power/state
chvt -t 7
chvt -t 9
chvt -t 7


/etc/init.d/alsasound start
/etc/init.d/pommed start
modprobe snd_hda_intel
modprobe ath_pci
modprobe sky2

this is probably not all needed, firewire and basic snd modules may surrive too..

---

### Post by Paerez on 2007-07-30
pepe - after installing i did reboot, since I wasn't sure what modules and init scripts had to be reloaded. And I get the same errors when i modprobe.

People do have sound working right?

---

### Post by trouble1313 on 2007-07-30
I can confirm that it does work, at least based on the day I checked out the code. I compiled it, re insmod'd it with the module option and all was well. Now if I understand correctly, the more recent posts have alluded to not needing the kernel option and better/full support of the devices themselves.
-Trouble

---

### Post by bluemoth on 2007-07-31
Hi,

I tried to reinstall alsa both unpatched and patched from hg and get the unknown symbol errors:
 >> modprobe snd_hda_intel model=w2jc
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

So either something has changed since the fi was posted or I'm dong the same mistake. It would be nice to hear from someone who successfully go sound going this way recently.

 Just to update the curious, I was able to install the feisty desktop (32bit) using the "all_generic_ide" boot option. Got graphics going using the nv driver and got the wifi going using madwifi.

I plan to wait for the nvidia drivers and am still trying to get sound going. I also plan to test gutsy tribe 4 when it's released.

Cheers.

---

### Post by pepe# on 2007-07-31
>> modprobe snd_hda_intel model=w2jc
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)


what does dmesg say?

With the patched alsa tree, you don't need the model=w2jc option, a new model mbp3 is introduced with the patch and the device is recognised automatically.

And please check that the provided patch applies correctly, that you download the newer of the two postet patches and that you followed the instructions for patching.

---

### Post by Paerez on 2007-07-31
[EDIT] I got it by doing this:

then I went into a temp directory I made and typed:
```
wget https://bugtrack.alsa-project.org/alsa-bug/file_download.php?file_id=2097&type=bug
rsync -avz --delete rsync://alsa.alsa-project.org/hg/alsa-kernel .
rsync -avz --delete rsync://alsa.alsa-project.org/hg/alsa-driver .
cd alsa-kernel
patch -p1 < ../patch_realtek.c.diff
cd ../alsa-driver
./hgcompile --with-cards=hda-intel --with-card-options=all
sudo make install
sudo /etc/init.d/alsasound restart
sudo modprobe snd-hda-intel
```

Then I turned up PCM and Front in gnome's volume manager. and I got sound out the front. Can't figure out headphones though ...

It was the hgcompile option that was messing it up for me the first time.

---

### Post by pepe# on 2007-07-31
You have to use a kernel with fully modular alsa support. Anyway..

cd /usr/src/modules/
rsync -avz --delete rsync://alsa.alsa-project.org/hg/alsa-driver alsa
rsync -avz --delete rsync://alsa.alsa-project.org/hg/alsa-kernel alsa
[download [patch_realtek.c.diff](https://bugtrack.alsa-project.org/alsa-bug/file_download.php?file_id=2097&type=bug)]
cd alsa/alsa-kernel
patch -p1 < ../../patch_realtek.c.diff
cd ../alsa-driver
./hgcompile
make
make install
/etc/init.d/alsasound stop
lsmod [verify all snd modules are unloaded]
modprobe snd-hda-intel

---

### Post by Paerez on 2007-07-31
ok now how do I get my headphones to play?

EDIT: Also anyone know how to get two-finger (or three finger, I don't care) right click working? Here is an excerpt from xorg.conf:

```
Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "SHMConfig" "on"
    Option         "AccelFactor" "0.1"
	Option "SendCoreEvents" "true"
        Option "Device" "/dev/psaux"
        Option "Protocol" "auto-dev"
        Option "MaxTapTime" "150"
        Option "MaxTapMove" "220"
        Option "MaxDoubleTapTime" "180"
        Option "LockedDrags" "on"
        Option "VertTwoFingerScroll" "1"
        Option "TapButton1" "1"
        Option "TapButton2" "2"
        Option "TapButton3" "3"
        Option "Emulate3Buttons" "true"

EndSection
```

---

### Post by scottptsn on 2007-07-31
Hi guys I am a brand new Linux user (as in one week to date exactly). I have a new 15’ macbook pro that I have installed the 64bit Ubuntu onto. Thanks to reading these forums I have the wifi, CD, and touchpad working. I am now trying to get the graphics fix to work. I am trying to use the fix pepe posted. Everthing worked until I got to the last simple command. “./nvidia-installer –aN”. I get a “No such file or directory” error. I am root and the group and permissions look right and it is an executable file. Even ls shows that it’s there, but I can’t run it. A co-worker thought it could be a problem with the shell and had me switch from /bin/bash to /bin/ksh however the problem is still there. I am stuck so if anyone has any ideas I would be very grateful. If you need any more info just ask and please remember I am a noob J

---

### Post by Paerez on 2007-07-31
ok well here are a couple things to check. I am covering ALL the bases, so please don't be offended if you think I am being condescending:

1) Are you in the directory with the file? If you type "ls" (thats an L), it should show the name of the script.

2) Is the script executable? if you type "ls -l nvidia-installer" there should be some Xs in the permissions.

3) Is the name right? Did you spell it correctly, correct capitalization, etc

If none of that works, post the output of "ls -l" so we can see the file.

EDIT:
here is my ls -l:
```
total 236
-r--r--r-- 1 nick nick   5725 2007-06-13 21:59 LICENSE
-rwxr-xr-x 1 nick nick 214488 2007-06-13 21:59 nvidia-installer
-rw-r--r-- 1 nick nick   8076 2007-06-13 22:26 pkg-history.txt
drwxr-xr-x 8 nick nick   4096 2007-06-13 21:59 usr

```

---

### Post by scottptsn on 2007-07-31
No offense taken I am new, but I did already try those things so here is my ls &#8211;l

-r&#8212;r&#8212;r&#8212;	1  root root	5725      2007-06-13 18:59  LICENSE
-rwxrwxrwx	1  root root	214488  2007-06-13 18:59  nvidia-installer
-rw-r&#8212;r--	1  root root	8076      2007-06-13 19:26  pkg-history.txt
drwxr-xr-x	8  root root	4096      2007-06-13 18:59  usr

The reason the file is rwx to all is that I changed the permissions just to make sure.

---

### Post by Paerez on 2007-07-31
OK and it is a single . before the /?

So its:
./nvidia-installer

not
../nvidia-installer?

Also the terminal has a nice auto-complete feature done by hitting tab. So if you type in ./ and then hit tab twice it will show you everything you could type after that.

Try typing ./n  and then hitting tab and see if it shows nvidia.

I've got to admit this is weird :-D

---

### Post by cyberdork33 on 2007-07-31
> **Paerez said:**
> OK and it is a single . before the /?

So its:
./nvidia-installer

not
../nvidia-installer?

Also the terminal has a nice auto-complete feature done by hitting tab. So if you type in ./ and then hit tab twice it will show you everything you could type after that.

Try typing ./n  and then hitting tab and see if it shows nvidia.

I've got to admit this is weird :-D

.. means back a directory, . is the current directory. So, if you are in the terminal at ~/Desktop/myfolder you could run a script in your home folder by typing "../../myscript" you put the ./ in front a script because bash will get confused sometimes. You can also use the script's command to run it. This is often done for perl scripts and the like more often than bash scripts:

$ perl myperlscript.pl

---

### Post by scottptsn on 2007-07-31
That’s very cool about the tab I am sure I will use that a lot and yes it’s ./ that I am using. I wonder if maybe I installed it wrong or something and it’s trying to access something that’s in the wrong place or there is a dependency I don’t have?

---

### Post by Dieter@be on 2007-07-31
> **Dhjiz said:**
> Hi,

I think maybe I've found another workaround for the Nvidia drivers.

Everytime I reboot now, the drivers launches withouth any problem and I can launch Beryl after that.

I run under a MacBook Pro 15", 2,2ghz, with the TwinView mode activated.

Here's my xorg.conf file :

(...)
.

Hello Ubuntu people.  I don't use ubuntu (my boxes run Arch and Gentoo, the servers I administer run Debian) but I would like to participate in this discussion, and more importantly I want to confirm that the xorg.conf posted by Dhjiz *works* !  It uses an external display at the left, and the mbp display is the right.  And like he said, the nvidia logo is borked but after that everything looks fine.

I have the binary drivers version 100.14.11-4, and I run a i686 system (similar to i386 but with some optimizations for newer architectures not important in this context).  My xorg is version 11R7.0-1
I didn't patch anything or did no fancy tricks like running with another driver first.  I do have to say I took the xorg.conf exactly the way it was, so I'll need to change settings to my likings (eg: I don't use an external display so I can hope to alter the config without it ceasing to work), and I'll do some more testing (e.g. rebooting, booting OSX in between, I could even try an opengl game but my time is limited right now)

edit: first test results:
rebooting into Linux seems to give no problems
trying to get rid of second screen: setting TwinView to 0 gives the "crazy colors" on the external screen, no image on the mbp screen.  Gonna try some more methods to fix it , I'm even considering leaving the twinview as it is and configuring my DE to not use the left space

---

### Post by Paerez on 2007-07-31
Here is my twinview xorg.conf.

---

### Post by pepe# on 2007-07-31
> ok now how do I get my headphones to play?

It should just work if you plugin HP into the HP output. The speakers will automatically be muted and the HP out will be unmuted.

Note that the line-in can still be switched to lineout and has seperate volume control, so your girlfriend can listen, too.

> EDIT: Also anyone know how to get two-finger (or three finger, I don't care)
> right click working? Here is an excerpt from xorg.conf:

>        Option "Emulate3Buttons" "true"

This one is not in my config and not in the synaptics manpage. Other than that I can see no errors. TwoFinger or even Threefinger tapping with linux was very bitchy, so I decided to use the corner-buttons, which still sucks, but less..

I don't know if the appletouch module from mactel-patches is required. I have it.

You also want 'GrabEventDevice' so you can define an additional generic mouse device for usb mice to work.

---

### Post by trouble1313 on 2007-07-31
Yeah I have to concur that the trackpad sucks. I've also gone to the corner or an external mouse for right clicking. If I could just do the 2 finger plus button click I'd be a happy man. Anyway, I took the emulate3buttons out as well and it does not affect the situation. Really, make sure you have Gsynaptics or QSynatpics or whatever uninstalled. Until I got rid of GSynatpics, things were screwy and the clicking didn't work.
-Trouble

---

### Post by scottptsn on 2007-07-31
I have been doing some more researcher on my problem and the only thing I can find is that if the binary is hard coded to point to an object and that object is not were it is supposed to be then you can get my error. I have no experience with editing binary is there anyway some one could help me out and let me know if the file points to something that maybe I moved or didn't install in the correct place? Thanks for all your help guys.

I got my track pad working with the previously discussed qsynaptics and the xorg edit and it works great I use two finger tap for right click and the circle drag for scrolling.

---

### Post by Paerez on 2007-08-01
Sorry to be such a pain pepe, but I turn my volume up, play a song (it plays fine) plug my headphones in, and it just keeps playing out the speakers. I also can't get the line-out playing to work.

---

### Post by vaiden on 2007-08-01
I use Fedora but I've heard that this is the place when it comes to quick answers ;) I've been using linux for some time but I've never used svn. How do I grab the right snapshot of madwifi and compile it, so it will work with my new macbook pro?

thank you!

---

### Post by Paerez on 2007-08-01
> **vaiden said:**
> I use Fedora but I've heard that this is the place when it comes to quick answers ;) I've been using linux for some time but I've never used svn. How do I grab the right snapshot of madwifi and compile it, so it will work with my new macbook pro?

thank you!

[http://madwifi.org/wiki/UserDocs/GettingMadwifi](http://madwifi.org/wiki/UserDocs/GettingMadwifi)

---

### Post by vaiden on 2007-08-01
Thank you, but which one should I grab? "trouble" said in the first post that the 13/06/07 snapshot worked, so how do I get it? Honestly I'm kind of new to the whole compiling thing :P Another question (maybe stupid): why doesn't gdm load automatically when I start the computer? How do I fix it? Thanks.. :)

---

### Post by pepe# on 2007-08-01
> Sorry to be such a pain pepe

It would be less painful if you would provide some more details.

did the patch apply okay? did make finish successfully? the new modules are in an 'asound' subdirectory, the original ones should've been deleted by 'make install'? when loading the module, syslog should report that model mbp3 was detected? what else did syslog say? what mixer controls did it get you? What did you try to get line-out to work?


> Thank you, but which one should I grab?

Follow the instructions for svn checkout. The downloaded archive will contain some README/INSTALL files, read them. make && make install  should do the job. IF it works, be happy. But keep in mind that the latest svn snapshot can be buggy and could crash your kernel. So if you get a working copy, stick with it and be very careful with updates.

---

### Post by vaiden on 2007-08-01
pepe#: thank you... but when I try the 'make' command, I get the following output:

```
/bin/sh: line 0: cd: /lib/modules/2.6.22.1-41.fc7/build: No such file or directory
Makefile.inc:66: *** /lib/modules/2.6.22.1-41.fc7/build is missing, please set KERNELPATH.  Stop.
```

:oops:

---

### Post by Paerez on 2007-08-01
Oh right sorry. That would explain why my wifi doesn't work!

I have been using ndiswrapper for the wifi.

```
svn checkout http://svn.madwifi.org/trunk madwifi -r2432
cd madwifi/
nice make
sudo make install
sudo modprobe ath_pci

```

---

### Post by Paerez on 2007-08-01
> did the patch apply okay?
Yes

> did make finish successfully?
Yes

> the new modules are in an 'asound' subdirectory, the original ones should've been deleted by 'make install'?
I assume so

> when loading the module, syslog should report that model mbp3 was detected?
I get this in dmesg:
[ 3210.772000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[ 3270.144000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 20
[ 3270.144000] PCI: Setting latency timer of device 0000:00:1b.0 to 64

> what else did syslog say?
If syslog = dmesg see above. I looked in the System Log Viewer and syslog had the same stuff. I don't see the mbp3 you're referring to anywhere.

> what mixer controls did it get you? See attached screenshot.

>  What did you try to get line-out to work?
To get line out to work I swapped to 2ch and 6ch and slid each volume slider up one at a time. I left front and pcm up the whole time.

EDIT: PS: Yes I know my PCM is down. I turned it down because I am at work right now.

---

### Post by pepe# on 2007-08-01
I get this in dmesg:
[ 3210.772000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[ 3270.144000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 20
[ 3270.144000] PCI: Setting latency timer of device 0000:00:1b.0 to 64


did you use ./hgcompile in alsa-driver/ ?
debugging seems to be disabled. the driver should report the detected model or auto-detection. hgcompile calls configure with some parameters, have a look at these.  configure --with-debug=full --with-cards=hda-intel should do it, but check with --help

> See attached screenshot.

please use alsamixer.
mbp3 should provide you with controls for master, pcm,lineIn,LineOut,CD,Mic and some switches.

---

### Post by Paerez on 2007-08-01
I ran:
./hgcompile --with-cards=hda-intel --with-card-options=all

---

### Post by Paerez on 2007-08-01
OK I recompiled with the debug and now I get this:
ALSA /home/nick/src/alsa/alsa-driver/pci/hda/hda_codec.c:1916: hda_codec: model 'w2jc' is selected

Also, when I have pcm and front up, and 6ch set, I get sound out the headphones AND the front speaker. Turning front or pcm up and down turns them both up and down (so muting front mutes the headphones).

It seems like my sound is functional but the "switch off front speaker when headphones are plugged in" part isn't working.

---

### Post by pepe# on 2007-08-01
>  model 'w2jc' is selected
> Also, when I have pcm and front up, and 6ch set, I get sound out the
> headphones AND the front speaker.

But the HP out is very quiet, right? This should be the same as it always was, with w2jc. You seem to have specified this model somewhere, eg in /etc/modules/foo. Remove that. Or try insmod.

If autodetection should for some reason not work, specifying model=mbp3 as parameter for insmod should activate this model independent from your configuration. check with dmesg.

When mbp3 is used, auto-sensing and more should work. All the patch does is adding this new model.

---

### Post by Paerez on 2007-08-01
Good call pepe.

/etc/modprobe.d/options

I had a line that forced the model to be w2jc. All is well now.

---

### Post by scottptsn on 2007-08-02
Having gave up on the graphics thing I have moved onto firefox
I got the two finger tap back fixed and using nspluginwrapper I got flash to work however I can't get realplayer to work because for some reason the auto update doesn't pick the .so file up and I for the life of me can't figure out which one it is to "nsplugwrapper -i file.so" it. Does anyone know the .so file name for the realplayer to link with nsplugwrapper? Sorry for all the questions. I am keeping a file of all the answers I find and when I finally get this thing working I will post a how-to for noobs like me :)

---

### Post by Elv13 on 2007-08-02
Hi, i got my (first) mac today, it is a SR MBP. I tried to install Ubuntu (i hope it will be my primary os) but i am not able to boot from CD. I tried 3 brand of CD-R but it never work, it just dont boot. Do i need to press a key when i boot?

---

### Post by black_raven2525 on 2007-08-02
> **Elv13 said:**
> Hi, i got my (first) mac today, it is a SR MBP. I tried to install Ubuntu (i hope it will be my primary os) but i am not able to boot from CD. I tried 3 brand of CD-R but it never work, it just dont boot. Do i need to press a key when i boot?

yesir, when the screen first lights up, hold the "c" key until you get the menu on the CD.

---

### Post by Elv13 on 2007-08-02
Thanks! I got everyting working inside an hours! It almost took me more time to understand how to boot in ubunu than fixing all bug


Here is a little how to that i think should be quoted in the first post llof this thread. I will update it soon when i will have fixed the touchpad, found how to use the remote and installed the webcam.

**To install ubuntu on your macbookpro santa rosa:**
1- downlaod the alternate cd 32 or 64bit
2- burn it under OSX/Windows/linux as an image
3- downlaod and install bootcamp or rEFI
4- boot on the ubuntu cd by holding the c key during boot
5- install ubuntu

**To use ubuntu:**
1- restart your mac and hold the alt key
2- press escape
3- boot on the failsafe kernel
4- edit the /etc/X11/xorg.conf file (nano /etc/X11/xorg.conf) and change "nv" for "vesa"
5- start X (/etc/init.d/gdm start)
6- download the lastet nvidia driver from the internet (you need to be wired) and patch it using this link [https://cbg.dyndns.org/wiki/ReadingCorner/LinuxOnMacbookPro#graphics](https://cbg.dyndns.org/wiki/ReadingCorner/LinuxOnMacbookPro#graphics)
*dont forget to install build-essential before
7- follow the rest of this link to get things working

**To install pommed (powermanagement and driver):**
1- cd /usr/src/modules
2- grab it svn co svn://svn.debian.org/pommed
3- downlaoad deps sudo apt-get build-dep pommed
4- cd pommed
5- make
6- follow instruction in INSTALL (file) to install it
7- get the init script from a .deb or the web and copy it to /etc/init.d

**To install wireless:**
1- sudo apt-get install build-essential
cd /usr/src/modules/
svn checkout [http://svn.madwifi.org/trunk](http://svn.madwifi.org/trunk) madwifi
cd madwifi
make;make install
modprobe ath_pci


**To install alsa driver (sound):**
1- install deps of alsa (automake, autotools, autoconf ans some other (please provide the list if you do this, i dont remermber it)
cd /usr/src/modules/
rsync -avz --delete rsync://alsa.alsa-project.org/hg/alsa-driver alsa
rsync -avz --delete rsync://alsa.alsa-project.org/hg/alsa-kernel alsa
[download patch_realtek.c.diff] [https://bugtrack.alsa-project.org/alsa-bug/file_download.php?file_id=2097&type=bug](https://bugtrack.alsa-project.org/alsa-bug/file_download.php?file_id=2097&type=bug)
cd alsa/alsa-kernel
patch -p1 < ../../patch_realtek.c.diff
cd ../alsa-driver
./hgcompile
make
make install
/etc/init.d/alsasound stop
lsmod [verify all snd modules are unloaded]
modprobe snd-hda-intel








___________________________


I have this laptop since less than one day and i give my opinion about it:
I used a lot of mac in the past, so i was not lost but this is -my- first mac. It is a really nice laptop. Apple did work on all aspect of this machine to make it nicer and have the "WOW" effect, but there is few things that are not that good. The surface of the touchpad is too abrasive to be usable. My cursor skip over part of the screen because my finger snap on the surface. The keyboard is not designer well, some key like delete are aparently missing and they were keys that i used a lot. The alt/ctrl/super/fn keys are not in an optimal order to work. ALT should be larger than the idontknowwhat key that is close to space. The touchpad is missing the left mouse boutton and the ctrl key is not enough close to the touchpad to replace the lmb. And linux use the middle mouse boutton more than any other OS (for copy/paste) and this is missing too. Synaptic options cant corect all those problem. But i like my mac, i will keep it ;). Dont be scared to buy this laptop, it is one of the best around.

---

### Post by black_raven2525 on 2007-08-03
Wow, Elv13's awesome tutorial above screams to be made into a wiki.  The two I know of are [https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro) and [https://wiki.ubuntu.com/MacBookProFeisty](https://wiki.ubuntu.com/MacBookProFeisty).  The only problem about those is that it gets confusing sorting between steps for the different versions of the MBP.  I propose we start a new wiki page for the MBP 3.1.  I would do it myself but I have no idea how to go about it.

---

### Post by pliz on 2007-08-03
Almost everything works for me on the laptop. The thing that I have not tackled long enough to make it work is suspend. Because of that I turn the laptop on and off quite often. Each time I start it I do not have wireless:

ath_hal module is active, when I rmmod it and then do modprobe ath_pci I get an error about unknown symbols in ath_hal

Another problem is pommed not starting automatically, even though I followed the instructions in INSTALL file.

Does anyone else have similar problems?

---

### Post by pliz on 2007-08-03
I've fixed pommed by editing /etc/init.d/pommed and correcting the path to the program.

---

### Post by trouble1313 on 2007-08-03
Elv13, yes indeed, awesome, I put all of your howto on the first message!

-Trouble

---

### Post by alephsmith on 2007-08-03
Links are truncated/broken in the first post.

---

### Post by martinbures on 2007-08-03
Does piix need to be added to the wiki?

Also, I installed the gutsy test 3 alternate and the piix addition still does not allow me to use the CD drive.   I simply added piix to the end of the /etc/modules file.  I made some other changes and upon reboot, still no CD support.  Did I miss something?

Thanks for the how-to!
martin.

---

### Post by cyberdork33 on 2007-08-03
> **alephsmith said:**
> Links are truncated/broken in the first post.
The links seem to work fine. This forum shortens what you see, but clicking on the link will take to to the correct location.

---

### Post by trouble1313 on 2007-08-03
Hehe, no sorry, I fixed the links. Two of them were broken :)

-Trouble

---

### Post by Elv13 on 2007-08-03
Any one got the touchpad working with synaptic driver? With the configuration included in my xorg.conf, the touchpad dont move... I tried few device but i am not lucky. Can someone with a working touchpad (with the synaptic driver) post his xorg.conf here please or find the error in mine (the server layout section is not the problem, i put those # to use the default config)

EDIT: NVM i found how, i am going to tweak it a little and i will post how.

---

### Post by Dhjiz on 2007-08-03
Hi,

There is a mistake somewhere with pommed, because the init.d/pommed file is looking for pommed in /usr/sbin, and in the INSTALL instructions, it is said that we must copy pommed in /usr/bin, so we must add to the tutorial to copy pommed in /usr/sbin and not /usr/bin as said in the INSTALL file (or modify the init.d/pommed file to search in /usr/bin instead).

---

### Post by Dhjiz on 2007-08-03
> **black_raven2525 said:**
> Wow, Elv13's awesome tutorial above screams to be made into a wiki.  The two I know of are [https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro) and [https://wiki.ubuntu.com/MacBookProFeisty](https://wiki.ubuntu.com/MacBookProFeisty).  The only problem about those is that it gets confusing sorting between steps for the different versions of the MBP.  I propose we start a new wiki page for the MBP 3.1.  I would do it myself but I have no idea how to go about it.

I support this idea. I think something like [https://wiki.ubuntu.com/MacBookPro3,1](https://wiki.ubuntu.com/MacBookPro3,1) or [https://wiki.ubuntu.com/MacBookProFeisty3,1](https://wiki.ubuntu.com/MacBookProFeisty3,1) would be good in order to put all the tips we have found into one place, editable by anyone.

---

### Post by Elv13 on 2007-08-03
```

#! /bin/sh
#
### BEGIN INIT INFO
# Provides:          pommed
# Required-Start:    $syslog $local_fs
# Required-Stop:     $syslog $local_fs
# Should-Start:      
# Should-Stop:       
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Apple laptops hotkeys event handler
# Description:       pommed handles the hotkeys found on the Apple MacBook Pro
#                    and MacBook laptops and adjusts the LCD backlight, sound
#                    volume, keyboard backlight or ejects the CD-ROM drive
#                    accordingly.
### END INIT INFO

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/bin/pommed
NAME=pommed
DESC=pommed

test -x $DAEMON || exit 0

set -e

case "$1" in
  start)
	echo -n "Starting $DESC: "
	start-stop-daemon --start --quiet --pidfile /var/run/$NAME.pid \
		--exec $DAEMON -- $DAEMON_OPTS
	echo "$NAME."
	;;
  stop)
	echo -n "Stopping $DESC: "
	start-stop-daemon --stop --oknodo --quiet --pidfile /var/run/$NAME.pid \
		--exec $DAEMON
	echo "$NAME."
	;;
  force-reload)
	# check wether $DAEMON is running. If so, restart
	start-stop-daemon --stop --test --quiet --pidfile \
		/var/run/$NAME.pid --exec $DAEMON \
	&& $0 restart \
	|| exit 0
	;;
  restart)
    echo -n "Restarting $DESC: "
	start-stop-daemon --stop --quiet --pidfile \
		/var/run/$NAME.pid --exec $DAEMON
	sleep 1
	start-stop-daemon --start --quiet --pidfile \
		/var/run/$NAME.pid --exec $DAEMON -- $DAEMON_OPTS
	echo "$NAME."
	;;
  *)
	N=/etc/init.d/$NAME
	echo "Usage: $N {start|stop|restart|force-reload}" >&2
	exit 1
	;;
esac

exit 0

```

---

### Post by russell.h on 2007-08-03
Hey Trouble, could you update the first post with a current list of broken features? This whole thing is great, I have one of these MBPs and am trying to decide on the best way to divide my hard drive space between Linux, Windows and OS X.

Does anyone happen to know if any other Linux distros are working particularly well with the SR MBPs yet?

---

### Post by Elv13 on 2007-08-03
everything work

ubuntu work well, of course in april this laptop did not exist so many driver need newer version to work, but it is not hard.

---

### Post by pepe# on 2007-08-03
no distribution works particularly well. it really doesn't matter which you choose, you'll have to download the latest drivers/kernel patches anyway.

after you have done that, the basic stuff works. but battery is still at only 2.5 hours max and wakeup from s2ram does not fully work. both could improve with the next release of the nvidia binary drivers but I wouldn't bet on it..

---

### Post by Paerez on 2007-08-03
here's my synaptic options. Pretty close to mac os x movement except the acceleration isn't quite as gradual:

```
Option         "SHMConfig" "on"
    Option         "AccelFactor" "0.08"
        Option  "MinSpeed" "0.2"
        Option  "MaxSpeed" "1.6"
        Option "SendCoreEvents" "true"
        Option "MaxTapTime" "200"
        Option "MaxTapMove" "220"
        Option "MaxDoubleTapTime" "200"
        Option "LockedDrags" "on"
        Option "VertEdgeScroll" "0"
        Option "HorizEdgeScroll" "0"
        Option "VertTwoFingerScroll" "1"
        Option "HorizTwoFingerScroll" "1"
        Option "TapButton1" "1"
        Option "TapButton2" "3"
        Option "TapButton3" "2"

```

---

### Post by Elv13 on 2007-08-03
Update:
 ```

**To install ubuntu on your macbookpro santa rosa:**
1- downlaod the alternate cd 32 or 64bit
2- burn it under OSX/Windows/linux as an image
3- downlaod and install bootcamp or rEFIt
4- boot on the ubuntu cd by holding the c key during boot
5- install ubuntu
Recommended:
return in ox and install rEFIt manualy.

**To use ubuntu:**
1- restart your mac and hold the alt key
2- press escape
3- boot on the failsafe kernel
4- edit the /etc/X11/xorg.conf file (nano /etc/X11/xorg.conf) and change "nv" for "vesa"
5- start X (/etc/init.d/gdm start)
6- download the lastet nvidia driver from the internet (you need to be wired) and patch it using this link https://cbg.dyndns.org/wiki/ReadingCorner/LinuxOnMacbookPro#graphics
*dont forget to install build-essential before
7- follow the rest of this link to get things working

**To install pommed (powermanagement and driver):**
1- cd /usr/src/modules
2- grab it svn co svn://svn.debian.org/pommed
3- downlaoad deps sudo apt-get build-dep pommed
4- cd pommed
5- make
6- follow instruction in INSTALL (file) to install it
7- copy this script to /etc/init.d/pommed
[code]#! /bin/sh 
# 
### BEGIN INIT INFO 
# Provides:          pommed 
# Required-Start:    $syslog $local_fs 
# Required-Stop:     $syslog $local_fs 
# Should-Start:      
# Should-Stop:       
# Default-Start:     2 3 4 5 
# Default-Stop:      0 1 6 
# Short-Description: Apple laptops hotkeys event handler 
# Description:       pommed handles the hotkeys found on the Apple MacBook Pro 
#                    and MacBook laptops and adjusts the LCD backlight, sound 
#                    volume, keyboard backlight or ejects the CD-ROM drive 
#                    accordingly. 
### END INIT INFO 

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin 
DAEMON=/usr/bin/pommed 
NAME=pommed 
DESC=pommed 

test -x $DAEMON || exit 0 

set -e 

case "$1" in 
  start) 
	echo -n "Starting $DESC: " 
	start-stop-daemon --start --quiet --pidfile /var/run/$NAME.pid \ 
		--exec $DAEMON -- $DAEMON_OPTS 
	echo "$NAME." 
	;; 
  stop) 
	echo -n "Stopping $DESC: " 
	start-stop-daemon --stop --oknodo --quiet --pidfile /var/run/$NAME.pid \ 
		--exec $DAEMON 
	echo "$NAME." 
	;; 
  force-reload) 
	# check wether $DAEMON is running. If so, restart 
	start-stop-daemon --stop --test --quiet --pidfile \ 
		/var/run/$NAME.pid --exec $DAEMON \ 
	&& $0 restart \ 
	|| exit 0 
	;; 
  restart) 
    echo -n "Restarting $DESC: " 
	start-stop-daemon --stop --quiet --pidfile \ 
		/var/run/$NAME.pid --exec $DAEMON 
	sleep 1 
	start-stop-daemon --start --quiet --pidfile \ 
		/var/run/$NAME.pid --exec $DAEMON -- $DAEMON_OPTS 
	echo "$NAME." 
	;; 
  *) 
	N=/etc/init.d/$NAME 
	echo "Usage: $N {start|stop|restart|force-reload}" >&2 
	exit 1 
	;; 
esac 

exit 0
```
8- make it executable (sudo chmod 777 /etc/init.d/pommed)
9- enable it (ln -s /etc/init.d/pommed /etc/rc4.d/S10pommed)

**To install wireless:**
1- sudo apt-get install build-essential
cd /usr/src/modules/
svn checkout [http://svn.madwifi.org/trunk](http://svn.madwifi.org/trunk) madwifi
cd madwifi
make;make install
modprobe ath_pci
Then go to network in system;administration
Edit the wireless configuration to use "any" as ESSID and DHCP for getting the IP. If wireless is not in list, reboot.

**To install alsa driver (sound):**
1- install deps of alsa (automake, autotools, autoconf ans some other (please provide the list if you do this, i dont remermber it)
cd /usr/src/modules/
rsync -avz --delete rsync://alsa.alsa-project.org/hg/alsa-driver alsa
rsync -avz --delete rsync://alsa.alsa-project.org/hg/alsa-kernel alsa
[download patch_realtek.c.diff] [https://bugtrack.alsa-project.org/alsa-bug/file_download.php?file_id=2097&type=bug](https://bugtrack.alsa-project.org/alsa-bug/file_download.php?file_id=2097&type=bug)
cd alsa/alsa-kernel
patch -p1 < ../../patch_realtek.c.diff
cd ../alsa-driver
./hgcompile
make
make install
/etc/init.d/alsasound stop
lsmod [verify all snd modules are unloaded]
modprobe snd-hda-intel

**To setup 2 finger scrolling and multifiger tapping:**
1- earase xorg.conf and paste this content:
```
 

Section "ServerLayout" 
    Identifier     "Default Layout" 
    Screen         "Default Screen" 0 0 
    InputDevice    "Generic Keyboard" 
    InputDevice    "Configured Mouse" 
        InputDevice "Synaptics Touchpad" 
EndSection 

Section "Files" 

	# path to defoma fonts 
    FontPath        "/usr/share/fonts/X11/misc" 
    FontPath        "/usr/share/fonts/X11/cyrillic" 
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled" 
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled" 
    FontPath        "/usr/share/fonts/X11/Type1" 
    FontPath        "/usr/share/fonts/X11/100dpi" 
    FontPath        "/usr/share/fonts/X11/75dpi" 
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" 
EndSection 

Section "Module" 
    Load           "i2c" 
    Load           "bitmap" 
    Load           "ddc" 
    Load           "extmod" 
    Load           "freetype" 
    Load           "glx" 
    Load           "int10" 
    Load           "vbe" 
EndSection 

Section "InputDevice" 
    Identifier     "Generic Keyboard" 
    Driver         "kbd" 
    Option         "CoreKeyboard" 
    Option         "XkbRules" "xorg" 
    Option         "XkbModel" "pc105" 
    Option         "XkbLayout" "ca" 
    Option         "XkbOptions" "lv3:ralt_switch" 
EndSection 

Section "InputDevice" 
    Identifier     "Configured Mouse" 
    Driver         "mouse" 
    Option         "CorePointer" 
    Option         "Device" "/dev/input/mouse1" 
    Option         "Protocol" "ImPS/2" 
    Option         "ZAxisMapping" "4 5" 
    Option         "Emulate3Buttons" "true" 
EndSection 

Section "InputDevice" 
      Identifier "Synaptics Touchpad" 
      Driver "synaptics" 
      Option "CorePointer" 
      Option "Device" "/dev/input/mice" 
      Option "Protocol" "auto-dev" 
      Option "LeftEdge" "100" 
      Option "RightEdge" "1100" 
      Option "TopEdge" "50" 
      Option "BottomEdge" "300" 
      Option "FingerLow" "20" 
      Option "FingerHigh" "30" 
      Option "MaxTapMove" "20" 
      Option "MaxTapTime" "100" 
      Option "MaxDoubleTapTime" "180" 
      Option "VertScrollDelta" "20" 
      Option "HorizScrollDelta" "350" 
      Option "VertTwoFingerScroll" "true" 
      Option "HorizTwoFingerScroll" "true" 
      Option "FastTaps" "true" 
      Option "TapButton2" "3" 
      Option "TapButton3" "2" 
      Option "MinSpeed" "0.1" 
      Option "MaxSpeed" "0.7" 
      Option "AccelFactor" "0.1" 
      Option "SHMConfig"  "on" 
EndSection 

Section "Monitor" 
    Identifier     "Écran générique" 
    HorizSync       28.0 - 70.0 
    VertRefresh     43.0 - 60.0 
    Option         "DPMS" 
EndSection 

Section "Device" 
    Identifier     "nVidia Corporation NVIDIA Default Card" 
    Driver         "nvidia" 
EndSection 

Section "Screen" 
    Identifier     "Default Screen" 
    Device         "nVidia Corporation NVIDIA Default Card" 
    Monitor        "Écran générique" 
    DefaultDepth    24 
    SubSection     "Display" 
        Depth       1 
        Modes     "1400x1050" "1280x800" "1024x768" 
    EndSubSection 
    SubSection     "Display" 
        Depth       4 
        Modes      "1400x1050" "1280x800" "1024x768" 
    EndSubSection 
    SubSection     "Display" 
        Depth       8 
        Modes      "1400x1050" "1280x800" "1024x768"
    EndSubSection 
    SubSection     "Display" 
        Depth       15 
        Modes      "1400x1050" "1280x800" "1024x768"
    EndSubSection 
    SubSection     "Display" 
        Depth       16 
        Modes      "1400x1050" "1280x800" "1024x768" 
    EndSubSection 
    SubSection     "Display" 
        Depth       24 
        Modes      "1400x1050" "1280x800" "1024x768" 
    EndSubSection 
EndSection 
``` 

 [/code]

Did someone have a working remote? not me, sudo cat appleIR dont event show text whn i press button.

---

### Post by Dhjiz on 2007-08-04
I have many problems with the Atheros drivers. Once the session is started, it works but not for long. I can work for many hours or just five minute after that, and then it stops working without any error message.

I need to plugin the Ethernet cable to get access to Internet again.

---

### Post by Paerez on 2007-08-04
dhjiz, are you using the current madwifi drivers, or the older svn version mentioned previously in this thread?

If you are using the current one, try this command for installing the drivers:
```
svn checkout http://svn.madwifi.org/trunk madwifi -r2432
cd madwifi/
nice make
sudo make install
sudo modprobe ath_pci
```

---

### Post by Elv13 on 2007-08-04
Dhjiz: read the last update of my tutorial, i fixed the problem

---

### Post by theadman on 2007-08-05
Hi Guys, 

I'm all very new to running Ubuntu on a Macbook Pro and currently have it Boot Camp dual booting OK with a VESA display driver. I would like to get the NVidia driver installed as a next step. So I headed over to [https://cbg.dyndns.org/wiki/ReadingCorner/LinuxOnMacbookPro#graphics](https://cbg.dyndns.org/wiki/ReadingCorner/LinuxOnMacbookPro#graphics) and read it through about 10 times and I still don't understand how do sort it all out.

Do I download the binary file ([http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run)) and then (somehow) run [https://cbg.dyndns.org/store/config/nv_macbook.diff](https://cbg.dyndns.org/store/config/nv_macbook.diff) ??? I really need some help with this.

Can someone please either point me to some info about it or show me some step-by-step code examples.

I really appreciate all the things I've learned on these boards - keep it up guys!

Thanks, 
Adam.

---

### Post by tokyovigilante on 2007-08-05
Anyone tried the new nvidia driver? According to the release notes it supports the 8600m GT.
[http://www.nvnews.net/vbulletin/showthread.php?t=92953](http://www.nvnews.net/vbulletin/showthread.php?t=92953)

---

### Post by pepe# on 2007-08-05
then (somehow) run [https://cbg.dyndns.org/store/config/nv_macbook.diff](https://cbg.dyndns.org/store/config/nv_macbook.diff) ??? I really need some help with this.

as I wrote in the wiki, the patch-file includes a short help how to apply the patch.


> Anyone tried the new nvidia driver? 

It's not new. this is the one we are using all the time..


EDIT:

Did anyone get the infrared control to work?

I have less that 3  hours of battery life, although I deactivated everything, unloaded all modules, got about 7-10 wakeups/sec with powertop. Any ideas here?

---

### Post by Elv13 on 2007-08-05
Like is said on my last post, i am unable to configure the remote. I looked into /dev and found why, when i cat the remote, i get nothing! The  remote just dont work, we need a new driver (or a patch to get the right device in /dev).

About the batery life, on osx it is not htat better, it is not 6 hours like on apple.com, it is about 3 too.

---

### Post by pepe# on 2007-08-06
osx makes at least 4 hours, i think it was even at 5h. just disable bluetooth and wireless.

Activity on a stripped down linux is nowhere near OSX with all its bells and whistles.

does someone know why the ehci controller is there? if I unload ehci_hcd, i can still use my usb mouse in both usb ports. bluetooth works too. expresscard?


BTW: a cat on the /dev/input/event for the IR device gives you some garbage the first time you press a button. who's going to bug the lirc people? :)

---

### Post by trouble1313 on 2007-08-06
Yeah, I have to admit here that the battery life isn't as good as under OSX. HOWEVER, with the current state of drivers, it is still pretty acceptable. I squeeze out a bit more under Vista but not a whole lot. My biggest issue is that the screen is rather flakey about turning off completely. I'll shut the lid and it'll turn off but I'll come back and the screen is back on again and coretemps are in the 60's. No, not terrible but still not great. 
  I tried yanking bluetooth but short of completely disabling it (meaning no easy way to get it back running again without reboot) I don't see a way to do so due to module deps which concerned me because they seemed to be tied to HID and I didn't want to lose keyboard. Yanking sky2 yielded very little, seriously, not even 1 watt from what I could see, so I don't bother anymore. 

My biggest gripe is the touchpad. Well, honestly it just blows.  Drives me crazy. Works fine in Vista and obviously in OSX but I just can't get Synaptics to make me happy. Oh why couldn't they just have split that giant mouse button into two!? I dream of taking out my dremel and sawing it in half as if it would be all that was needed :) 
At the same time, with the amazing work done in just a month, the machine has gone from not really usable under Linux to pretty damn acceptable! I'm pretty stoked at this point and it'll only get better over time.

I'm a long time Unix guy. I own Sparc Stations, HPUX machines, and IBM Power systems.  That's the world I come from...Vista is broken in so many ways that it's pathetic. The MacOS GUI drives me nuts, especially how X is a completely separate deal and windows don't have their own individual controls. So I start twitching if I don't have that happy environment that I so likes! Hell even TWM calms me down. The Apple Fanbois don't get this at all. How DARE someone not use an Apple product?! Maybe my detachment is the reason I want to punch out the various 'hep cats' that work in the apple stores? The great thing about this laptop is that the hardware is truly amazing! This is the first mac that I've bothered with. My wife and kids have macs and they're great for them (under OSX) but hell, this hardware platform is just so sexy and complete that I don't see how aficionados wouldn't want one. I figured that I could hold out for the next release of the Dell XPS1210 but I couldn't wait and I'm glad I didn't. That vidcard in the XPS1330 is pretty weak. 

Ok that's my tirade for the day ;) 

-Trouble

---

### Post by pepe# on 2007-08-06
Backlight and coretemp are fine here. I use conservative and fan1 is running at its lowest setting all the time. It gets kinda hot after a while when I disable the fan via sysfs. But we have a pretty hot summer here in germany and I won't expect much more from a passively cooled 800mhz dual-core.

To disable bluetooth, powertop tells me to

hciconfig hci0 down; rmmod hci_usb

Restoring that shouldn't be a problem. I disabled bluetooth in the default runlevel.

> The great thing about this laptop is that the hardware is truly amazing!

That was my main reason for bying this thing, too. OSX is fun unless you really have to use it. But the hardware can't be compared to any other product, even if you put another 500-1000$/€  into the bucket.

I didn't use the nvidia module yesterday because I was testing with 2.6.23-rc2. There is a patch available in the nv-forums to get the current driver working with this kernel. With nvidia instead of nv, my 15" mbp is at about 3.5 hours. That is at lowest display brightness with not much more than X and internal keyboard.

---

### Post by saserlite on 2007-08-08
Just a quick reminder to everyone....

Remember to report problems in **Launchpad** (the tool Ubuntu use to track bugs).

Ubuntu's Launchpad is here:

[https://launchpad.net/ubuntu/](https://launchpad.net/ubuntu/)

Reporting a bug is a simple matter of clicking on the "Report a bug" button.

---

### Post by chem on 2007-08-09
> **Corvias said:**
> 
I'll even make it easy on you. Below are the links to launchpad of the six bugs I posted. Please add comments and details, so the devs know that there is an interest!

[https://bugs.launchpad.net/ubuntu/+bug/125911](https://bugs.launchpad.net/ubuntu/+bug/125911)
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/125914](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/125914)
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/125915](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/125915)
[https://bugs.launchpad.net/ubuntu/+bug/125916](https://bugs.launchpad.net/ubuntu/+bug/125916)
[https://bugs.launchpad.net/ubuntu/+bug/125918](https://bugs.launchpad.net/ubuntu/+bug/125918)
[https://bugs.launchpad.net/ubuntu/+bug/125919](https://bugs.launchpad.net/ubuntu/+bug/125919)

these refer to the display brightness, the default nv xorg module, the mvidia-glx package, the "crazy colors" bug under feisty, the keyboard light sensors, and the wifi adapter.

Lastly, there's also a bug posted related to the sound problems someone posted recently. It can  be found here:

[https://bugs.launchpad.net/ubuntu/+bug/125332](https://bugs.launchpad.net/ubuntu/+bug/125332)

Make some noise!

To the poster before me... yes, over a dozen pages ago in this thread, a series of bug reports were discussed.  There's also one out there for the Superdrive being nonfunctional.

Gutsy Tribe 4 was just released... hopefully people can update these bugs and keep complaining.  I am not sure how concerned the Ubuntu hierarchy is about having gutsy work on the new MBPs.  Maybe not so much.  Only the wifi was marked as a high priority.

---

### Post by hydraman on 2007-08-11
I must have screwed the pooch trying to install Feisty Fawn on my new MBR 15" and could use some help.

I had XP installed, but can no longer boot to the partition (either thru the rEFIt menu or from the Mac holding down the option key).

After selecting Windows and choosing safe or normal boot and getting the Windows splash screen, it flashes a blue screen with a text message (so fast I can't read it) and then reboots back to rEFIt - whether rebooting in safe or normal mode.

I assumed I made a mistake early on and installed GRUB on the windows partition by mistake, so I've tried fixboot and fixmbr from the repair console on the XP disk, and still get the same results. Is the Windows install FUBAR? MacOSX still boots fine. I finally have the Ubuntu install booting to desktop.

My partitions are:

1. rEFIt
2. MacOSX ("customer")
3. Linux
4. WinXP
5. free space (about 3GB)

I left out the swap space partition recommended under earlier MBP installs - is that possibly the cause?

---

### Post by hydraman on 2007-08-11
> **hydraman said:**
> I must have screwed the pooch trying to install Feisty Fawn on my new MBR 15" and could use some help.

I had XP installed, but can no longer boot to the partition (either thru the rEFIt menu or from the Mac holding down the option key).

After selecting Windows and choosing safe or normal boot and getting the Windows splash screen, it flashes a blue screen with a text message (so fast I can't read it) and then reboots back to rEFIt - whether rebooting in safe or normal mode.

I assumed I made a mistake early on and installed GRUB on the windows partition by mistake, so I've tried fixboot and fixmbr from the repair console on the XP disk, and still get the same results. Is the Windows install FUBAR? MacOSX still boots fine. I finally have the Ubuntu install booting to desktop.

My partitions are:

1. rEFIt
2. MacOSX ("customer")
3. Linux
4. WinXP
5. free space (about 3GB)

I left out the swap space partition recommended under earlier MBP installs - is that possibly the cause?

D'oH!

Figured it out - it was really too simple (needed to edit the boot.ini file to boot from the correct partition).

 Sorry for the clutter.

---

### Post by martinbures on 2007-08-13
Just a note on installing the nVidia patch/driver.  The posts on how to install are not very clear, or maybe my machine was just quirky... BUT...

1.  download the driver and unpack
2.  apply the diff as mentioned
3.  reboot
4.  press esc to get the grub menu - select the failsafe kernel
5.  cd to the installer directory and execute the command 'sudo ./nvidia-installer -aN' as noted in the directions.
It will throw some warning about the wrong runlevel - don't take its advice - it will just kick you to the graphical shell where it wouldn't let me install the driver
6.  allow the installer to reconfigure x

you are done.  enjoy.  now to figure out how to remove the un-paid advertising of the nvidia splash screen on startup...  or how to figure how to get advertising money from nvidia for the ad space... ;)

regards.
martin.

---

### Post by pepe# on 2007-08-13
I didn't go into detail because its different for every distribution/configuration. plus people don't learn anything with step-by-step manuals

> now to figure out how to remove the un-paid advertising of the nvidia splash screen on startup...

look into the README in /usr/share/doc/NV*/

I've set it to wallpaper+debian logo. doesn't make the startup any faster though.


FYI, there is a patch to get the driver working with 2.6.23-rc2(and rc3 probably too) in the nvidia forums. 2.6.23 brings lguest, a very cool virtualization...thing. Anyway, someone over there also made a patch to get the nvidia driver working with xen (and lguest): [http://cyber-labs.org/patches/xen-nvidia/nvidia-binary-driver-100.14.11-1.patch](http://cyber-labs.org/patches/xen-nvidia/nvidia-binary-driver-100.14.11-1.patch)

Works like a charm as long as you don't do obscure stuff like s2ram or play video via xv.

---

### Post by squell on 2007-08-14
Just wondering, 

As MS Windows can be installed on the Macbook Pro with ease (or so I've heard), would it be possible to install Ubuntu using the Wubi installer ([http://wubi-installer.org/](http://wubi-installer.org/)) via the Windows installation?  This would remove the need for a grub boot loader...

---

### Post by cyberdork33 on 2007-08-14
> **squell said:**
> Just wondering, As MS Windows can be installed on the Macbook Pro with ease (or so I've heard), would it be possible to install Ubuntu using the Wubi installer ([http://wubi-installer.org/](http://wubi-installer.org/)) via the Windows installation?  This would remove the need for a grub boot loader...
This actually might just work. I don't know a lot about Wubi, but from what I have read, you should be ok as long as it is only modifying your windows filesystem. I don't know that it will solve the hardware issues though, since it sounds like you would still be running natively.

---

### Post by Elv13 on 2007-08-14
> **pepe# said:**
> osx makes at least 4 hours, i think it was even at 5h. just disable bluetooth and wireless.

Activity on a stripped down linux is nowhere near OSX with all its bells and whistles.

does someone know why the ehci controller is there? if I unload ehci_hcd, i can still use my usb mouse in both usb ports. bluetooth works too. expresscard?


BTW: a cat on the /dev/input/event for the IR device gives you some garbage the first time you press a button. who's going to bug the lirc people? :)

Are you sure of that?
Because me i get nothing, the right device is event5

---

### Post by pepe# on 2007-08-15
> Are you sure of that?
> Because me i get nothing, the right device is event5

The devices file numbers can change. but please investigate with the lirc people and tell us if you find something.

---

### Post by Elv13 on 2007-08-15
On what event do you get the dignal and are you sure it is the remote (not the onboard accelerometer). And the last remote seem to be supported by pommed, not by LIRC sa i think i will continu to investigate on the pommed side. It is probably just a wrong USBid or something like that.

---

### Post by Dhjiz on 2007-08-16
Hi,

There is a problem with the latest posted X.org configuration, the option for the synaptics touchpad must be "AlwaysCore" and not "CorePointer", else it will not work.

And in my opinion the touchpad is really not enough sensitive. I have to force to get it move the cursor.

About the wifi drivers, if I use the commands you said Paerez, I get this message :
> FATAL: Error inserting ath_pci (/lib/modules/2.6.20-16-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
and my problems were with the latest version of the drivers, wich work for about 5 minutes.

I also get some problems with the nvidia drivers, or KDM. KDM doesn't start properly every time, but that's another different problem and I found a workaround starting in recovery mode and launching kdm this way.

---

### Post by black_raven2525 on 2007-08-16
Im getting the same issue with madwifi as Dhjiz.  It started after I installed the Nvidia drivers.  I redownload the source, did a make clean, modprobe ath_pci, the whole thing.  Its still broke.

---

### Post by chem on 2007-08-16
Requesting that the original post be updated with instructions to get the Superdrive to work... I thin k that's a significant piece of hardware that doesn't work out of the box with ubuntu / gutsy.

Good thread.  20 pages, sheesh.  I remember when it was only 3 pages...

---

### Post by Elv13 on 2007-08-16
wireless stopped working for me to after an update (i use the same kernel)

sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          ath0: ERROR while getting interface flags: No such device
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ath0 ; No such device.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
                                                                         [ OK ]

---

### Post by pepe# on 2007-08-16
**Elv13**:
> On what event do you get the dignal

ls /dev/input/by-id/
usb-05ac_1000-event-kbd
usb-Apple_Computer_Apple_Internal_Keyboard_._Trackpad-event-kbd
usb-Apple_Computer_Apple_Internal_Keyboard_._Trackpad-event-mouse
usb-Apple_Computer_Apple_Internal_Keyboard_._Trackpad-mouse
usb-Apple_Computer__Inc._IR_Receiver-event-ir

cat /dev/input/by-id/usb-Apple_Computer__Inc._IR_Receiver-event-ir 

now press a button on your remote. you will get some garbage. once. next time at reboot(or maybe module reloading). :-( 

Anyway, this should be brought to the attention of either the mactel or lirc people. or both. please, someone, investigate.Subscribe to their dev-lists and talk to them. I'm very busy(as can be seen from the reduced number of posts lately ;) )

> And the last remote seem to be supported by pommed, not by LIRC sa i think
> i will continu to investigate on the pommed side

what source suggested to you that the latest santa rosa macbook IR is supported by either pommed or lirc?

pommed does not programm drivers. It is only an application that uses existing drivers for display,sensors, keyboard, so that you can e.g. have keyboard backlight adjusted via ambient light sensors.

lirc brings a macmini driver, but when you load it nothing happens, so it probably does not work for the new IR receiver. The mactel-linux patches include driver too, but they removed it saying 'lirc now supports this', so they probably also never had a driver that works with the santa rosa macbooks.

So there is nothing, currently. Except for this garbage on the event device. You(someone) should try to get lirc/mactel people to investigate this.

> It is probably just a wrong USBid or something like that.

If this were the case, you could just try them all, right?

**chem:**

> instructions to get the Superdrive to work.

it just works for me. Running 2.6.22/23-rc2, you need the intel combined s/p-ata driver.

grep ATA /usr/src/linux/.config|grep -v "not set"
CONFIG_ATA=y
CONFIG_ATA_ACPI=y
CONFIG_SATA_AHCI=y
CONFIG_ATA_PIIX=y

wodim(debians cdrecord) just works, but you can also specify device=/dev/hda or so.

dmesg says:

hda: MATSHITADVD-R UJ-857E, ATAPI CD/DVD-ROM drive
hda: selected mode 0x44
hda: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)


**FYI**:

My patch for sound support got included into the alsa repository. If someone gets capturing to work, please tell me.

Also, here is again the link to my distribution independent wiki page where I track the hardware support in linux:

[https://cbg.dyndns.org/wiki/ReadingCorner/LinuxOnMacbookPro](https://cbg.dyndns.org/wiki/ReadingCorner/LinuxOnMacbookPro)

The linked xorg sample contained the 'AlwaysCore'-entry for over a month now. You also want the GrabEventDevice option so that the touchpad is not used by the generic mouse driver, too. The generic one is only for usb mouse hotplug and such.

Have fun,
/pepe

---

### Post by Elv13 on 2007-08-16
appleir isa link to even5 for me ;) and when i cat it, i get nothing...

I fixed the wireless by removing restricted driver package in synaptic and doing a make clean ; make ; make install. I dont really understand what did append.

I did invertigate on the USBid thing, i confirm it, the driver point to an old revision (8240) and the srMBP have 8242, i will try to see is i can hack the patch to get everything working or i will need to try to write some code (i am too bad normally to fix driver myself)...

EDIT2: Here is the modified appleir patch, i did not tested it because i dont care that much about the remote and it is late where i live. I also attach a newer version of the patch that work with kernel 2.6.22 made by arch linux.  I also edited it to ajust USBid. The path will fail to apply on 2.6.20 kernel. I hope that it will work with the ubuntu kernel. If someone want to test it, please say if it dont work (this is highly possible). It apply like the sound patch but on your kernel source dir (/usr/src/linux-source-* provided by the kernel source package of ubuntu). You will also need to do a make menuconfig/kconfig/gconfig/xconfig of some version of the patch to enable appleir and then make && make modules_install && make install (and edit your grub file).

---

### Post by martinbures on 2007-08-17
With respect to the USB thing, there might be a deeper underlying problem - I don't know.  I have a keyspan USB-to-Serial adapter.  Works great in feisty but doesn't work in gutsy.  It seems to be detected but isn't powered.  

Here is the launchpad bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/132106](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/132106)

---

### Post by chem on 2007-08-17
> **pepe# said:**
> 
> instructions to get the Superdrive to work.

it just works for me. Running 2.6.22/23-rc2, you need the intel combined s/p-ata driver.

grep ATA /usr/src/linux/.config|grep -v "not set"
CONFIG_ATA=y
CONFIG_ATA_ACPI=y
CONFIG_SATA_AHCI=y
CONFIG_ATA_PIIX=y

wodim(debians cdrecord) just works, but you can also specify device=/dev/hda or so.

dmesg says:

hda: MATSHITADVD-R UJ-857E, ATAPI CD/DVD-ROM drive
hda: selected mode 0x44
hda: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)


As you're listing kernel config options, I'm guessing you recompiled the kernel?  Is there a way to get it working without recompiling a kernel using gutsy tribe 4?  Something about piix modules perhaps?  I have not tested anything;  I actually reverted back to OS X because I found the BSD terminal there was quite good; using fink I could get whatever programs and compilers I needed.

---

### Post by pepe# on 2007-08-17
hey chem,

> Something about piix modules perhaps?

stock debian kernel worked when I loaded the piix module.

---

### Post by Elv13 on 2007-08-17
To add the delete key on the key just before the left arrow:
1- sudo nano /etc/X11/xkb/keycodes/xfree86
2- ctrl+w , write 107 and enter
4- change 107 for 108
5- ctrl+w, write 108 and enter (do this again if it show the line you just edited)
6- change 108 for 107
7- ctrl+x to save and exit

To enable level3 key (necessary on international keyboard and usefull anyway):
sudo sed -i~ '/xkb_symbols "ralt_switch" {/a\  include "level3(rwin_switch)"' /etc/X11/xkb/symbols/level3

To apply the change, restart X (ctrl+alt+backspace)

---

### Post by detjoe on 2007-08-17
@chem: Try ide_generic in /etc/modules instead of piix to get the superdrive to work. Found it here [http://ubuntuforums.org/showthread.php?t=515568](http://ubuntuforums.org/showthread.php?t=515568)

---

### Post by Dhjiz on 2007-08-18
I tried sudo modprobe piix and it worked well for me.

---

### Post by Corvias on 2007-08-19
Hi Everyone!

Been gone for awhile (physically and virtually). Wow this thread has grown! And the progress that's been made! I'm trying to get caught up, and I could use some help. I've been trying to apply the diff patch to the nvidia binary drivers, but I haven't had much luck. Here are the steps I've followed:

NOTE: I have done this in recovery mode and regular mode
1. Downloaded the most recent Nvidia binary driver.
2. extracted it in my home folder with -x
3. Downloaded the diff patch to my home folder
4. cd NVIDIA-Linux-x86-100.14.11-pkg1/usr/src
5.  patch -p0 < ../../../nv_macbook.diff
NOTE: After doing this, I got a message saying that nv.c had been patched
6. cd'd up a couple dirs and did ./nvidia-installer -aN
7. Went through the installer with no errors
... And reboot only to be welcomed by an x error:

```
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

I can't seem to find it in my logs, but it also mentioned about the kernel module version not matching the binary portion (or something like that). 

The other thing I noticed is that everytime I try to install the nvidia driver, the wifi card stops working, and I have to "sudo make install" madwifi again.
 
Just for chuckles, here's the diff file I used. Maybe there's something missing?

```
diff -uNr nv.orig/nv.c nv/nv.c
--- nv.orig/nv.c	2007-07-26 08:35:00.000000000 +0200
+++ nv/nv.c	2007-07-26 12:40:11.000000000 +0200
@@ -1555,6 +1555,39 @@
 
     __nv_init_sp = sp;
 
+	{
+    		for (i = 0; i < num_nv_devices; i++) {
+			printk("Macbook Hack\n");
+			struct pci_dev *dev = nv_linux_devices[i].dev;
+			#define NV_WR32(p,i,d)  (__raw_writel((d), (void __iomem *)(p) + (i)))
+			
+			unsigned long mmio_start;
+			__u32 mmio_len;
+
+			mmio_start = pci_resource_start(dev, 0);
+			mmio_len = pci_resource_len(dev, 0);
+			volatile u32 __iomem *REGS;
+
+			REGS = ioremap(mmio_start, mmio_len);
+
+			if(REGS) {
+				NV_WR32(REGS, 0x1708, 0);
+				NV_WR32(REGS, 0x1900, 0);
+				NV_WR32(REGS, 0x1901, 0);
+				NV_WR32(REGS, 0x1902, 0);
+				NV_WR32(REGS, 0x1903, 0);
+				NV_WR32(REGS, 0x1904, 0);
+				NV_WR32(REGS, 0x1905, 0);
+				NV_WR32(REGS, 0x1906, 0);
+				NV_WR32(REGS, 0x1907, 0);
+	
+				iounmap(REGS);
+			} else {
+				printk("Error mapping memory\n");
+			}
+		}
+	}
+
     return 0;
 
 failed:

```

---

### Post by alephsmith on 2007-08-19
I had something similar and needed to explicitly stop the nv and nvidia_new modules from loading.

```
sudo nano /etc/default/linux-restricted-modules-common
```

changing

```
DISABLED_MODULES=""
```
to 
```
DISABLED_MODULES="nv nvidia_new"
```

---

### Post by Corvias on 2007-08-19
WooHoo! That did it! Thank You, I can go to bed now!

---

### Post by 0deuce0 on 2007-08-20
We almost need our own RPM with everything bundled in for the macbook pro SR...

---

### Post by Corvias on 2007-08-20
Good News!

I found some .debs for Pommed 1.8. I can now adjust the screen brightness.

[http://ftp.cica.es/debian/pool/main/p/pommed/](http://ftp.cica.es/debian/pool/main/p/pommed/)

---

### Post by pepe# on 2007-08-21
> I found some .debs for Pommed 1.8. I can now adjust the screen brightness.

as I wrote, the patch that was linked in the corresponding ubuntu bug entry was added to pommed a few weeks ago. You can get it via svn or just use the latest version of pommed. debian unstable already has this included.

the patch uses ACPI to control the display brightness. if someone cares to notify the right kernel devs, it will probably included into the kernel so that we get an interface in /sys/.

---

### Post by cyberdork33 on 2007-08-21
> **pepe# said:**
> > I found some .debs for Pommed 1.8. I can now adjust the screen brightness.

as I wrote, the patch that was linked in the corresponding ubuntu bug entry was added to pommed a few weeks ago. You can get it via svn or just use the latest version of pommed. debian unstable already has this included.

the patch uses ACPI to control the display brightness. if someone cares to notify the right kernel devs, it will probably included into the kernel so that we get an interface in /sys/.
If there is a bug report, then just post the patch to it or the information about the new version, whatever. If not, create a bug report. This will get the best developer attention.

---

### Post by pepe# on 2007-08-21
The information is already there. And it was posted to this forum. There is even a request to sync the debian unstable version to ubuntu, from over a month ago, exactly to adress this issue.

> This will get the best developer attention.

I informed the developer and he fixed it. Next day, it was in debian/unstable.

I repeated the generic info because nobody reads the whole thread anymore. And apparently the thread itself can not be searched, all search results link to the thread itself. And the thread is used by other people than ubuntu.

---

### Post by beelzebob on 2007-08-21
I am having a heck of a time getting pommed to work.  I believe I have followed all the relevant instruction in this thread.  (BTW, the instructions in the first post are incomplete - they don't include steps 8&9 that were given in a later post.)  Now, when I try to use the brightness buttons, I see a little window this what looks like a brightness icon in it, but there is no change to the brightness.  If I type gpomme at a prompt,  I get the following error:

DBus error: The name org.pommed was not provided by any .service files
audio getMute call failed !

---

### Post by virx14 on 2007-08-22
> **beelzebob said:**
> I am having a heck of a time getting pommed to work.  I believe I have followed all the relevant instruction in this thread.  (BTW, the instructions in the first post are incomplete - they don't include steps 8&9 that were given in a later post.)  Now, when I try to use the brightness buttons, I see a little window this what looks like a brightness icon in it, but there is no change to the brightness.  If I type gpomme at a prompt,  I get the following error:

DBus error: The name org.pommed was not provided by any .service files
audio getMute call failed !

DBus error means you did not start pommed. You need to be root to run pommed. Gpomme is run from user account.

I am getting the same audio error and did not figure out how to fix it yet.

---

### Post by virx14 on 2007-08-22
Was anyone at all be able to make pommed work with audio and keyboard brightness? I am using  2.6.22 with all patches from mactel-linux, trunk alsa as of today, but all I can do is to change screen brightness with pommed. 
I am getting the following two warnings when starting pommed:

W: Could not open /sys/class/leds/smc:kbd_backlight/brightness: No such file or directory
W: Audio initialization failed, audio support disabled

---

### Post by pepe# on 2007-08-23
> W: Could not open /sys/class/leds/smc:kbd_backlight/brightness: No such file or directory

Did you  'modprobe applesmc', which is provided by the mactel-linux patches? If so, how about telling us what you did and which files there are..

> W: Audio initialization failed, audio support disabled

How about adjusting the controls in the pommed.conf to actually match your alsa mixer controls?


and btw, gpomme has a much nicer theme than the default gnome-look..

---

### Post by virx14 on 2007-08-23
Thanks pepe#, almost everything works perfectly now. Just need to figure out how to make some kind of suspend work reliably.

---

### Post by misstricky on 2007-08-24
hey there,

i have got just about everything working on my mbp. this thread has been a amazing resource for me...

i cannot seem to get compiz-fusion working... i got it working with the stable stuff, but i could not get emerald to work with it (even after removing whatever beryl stuff was around). so i tried using the unstable stuff from a repo and cannot get compiz-fusion to work at all. 

i was wondering if anyone has got emerald working with compiz-fusion? and for anyone who has compiz-fusion working at all, how did you install it?

here is the verbose error i got when trying to run compiz --replace:

```

liz@ubuntu:~$ compiz --replace -v
Checking for Unsupported sessions: not present. 
Checking for nVidia: present. 
Checking for Xgl: not present. 
Checking for FBConfig: present. 
Checking for texture_from_pixmap: present. 
Checking for copy texture support: present. 
Checking for Intel: not present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for XDamage extension: present. 
Checking for XSync extension: present. 
Detected 1 screen(s)
Checks indicate compiz should work on your system
Found GNOME desktop environment running...
Found running windows manager: metacity
Setting fallback windows manager to metacity 
Loading the ccp settings interface
Starting delayed gtk-window-decorator in the background: sleeping 1.5...
Exporting: __GL_YIELD=NOTHING WINDOW_MANAGER=/usr/bin/compiz 
Executing: /usr/bin/compiz.real --ignore-desktop-hints --replace --sm-disable ccp 
Executing: gtk-window-decorator --replace 

(process:6278): GConf-CRITICAL **: gconf_entry_unref: assertion `REAL_ENTRY (entry)->refcount > 0' failed

```


i've also attached my current xorg.conf  incase that will help.. thanks! :)

---

### Post by btn21 on 2007-08-24
Has anyone tried booting with the "regular" Gutsy "Tribe 5" CD/DVD? or do we still have to use the alternate CD/DVD?

---

### Post by beelzebob on 2007-08-24
> **beelzebob said:**
> I am having a heck of a time getting pommed to work.  I believe I have followed all the relevant instruction in this thread.  (BTW, the instructions in the first post are incomplete - they don't include steps 8&9 that were given in a later post.)  Now, when I try to use the brightness buttons, I see a little window this what looks like a brightness icon in it, but there is no change to the brightness.  If I type gpomme at a prompt,  I get the following error:

DBus error: The name org.pommed was not provided by any .service files
audio getMute call failed !

Can I do it with sudo?  When I type 'sudo pomme' I get the following error:

no such option 'on_batt'

---

### Post by beelzebob on 2007-08-24
> **beelzebob said:**
> Can I do it with sudo?  When I type 'sudo pomme' I get the following error:

no such option 'on_batt'

Okay, I uninstalled pommed and went through the instructions again very carefully.  Now, it almost works.  The remaining issue seems to be that it doesn't remember my settings if I shut down.  Also, it does not work after rebooting unless I go to a prompt and type "sudo pommed".  Is that how it's supposed to work?  If not, what did I miss?

---

### Post by beelzebob on 2007-08-24
Okay, regarding my pommed problems:

THE SCRIPT ON PAGE 18 OF THIS THREAD HAS BUGS!!  

If you just copy it into a text file and try to run it, you'll get syntax errors.  I believe this is due to whitespace characters appearing after the "\" characters.  Get rid of that whitespace, and it runs.

So my question is, how do we get rid of this script and reinstall it?  It seems to have copied itself into a lot of places, particularly files with "K20" in the name.

---

### Post by beelzebob on 2007-08-24
Also, while I'm here.... is there a way to set the gamma in the nvidia control panel at boot/logon?  I have mine set to 0.7 and I think it makes my macbook pro look much nicer, but I have to reset it every time I log in.  It would be nice if it could set itself automatically.

---

### Post by cyberdork33 on 2007-08-25
> **beelzebob said:**
> Also, while I'm here.... is there a way to set the gamma in the nvidia control panel at boot/logon?  I have mine set to 0.7 and I think it makes my macbook pro look much nicer, but I have to reset it every time I log in.  It would be nice if it could set itself automatically.

Have you seen this:
[http://ubuntuforums.org/showthread.php?t=491138](http://ubuntuforums.org/showthread.php?t=491138)

---

### Post by beelzebob on 2007-08-25
> **cyberdork33 said:**
> Have you seen this:
[http://ubuntuforums.org/showthread.php?t=491138](http://ubuntuforums.org/showthread.php?t=491138)

Yeah, it gave everything a sickly yellow tint.  And, it still doesn't solve the problem that you have to redo it every time you log on.

---

### Post by cyberdork33 on 2007-08-25
> **beelzebob said:**
> Yeah, it gave everything a sickly yellow tint.  And, it still doesn't solve the problem that you have to redo it every time you log on.

The community docs have a script to add to your x session to load xcalib everytime. If you have a strange tint, create a different color profile.

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
To calibrate the screen colors (in order to match OS X), you need to install *xcalib*.  This isn't available in the Ubuntu repositories, so you'll have to download it.  Go to [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] http://www.etg.e-technik.uni-erlangen.de/web/doe/xcalib/]("http://www.etg.e-technik.uni-erlangen.de/web/doe/xcalib/") and download the newest Linux binary (save it to the Desktop). To install and configure it, you will need to do a few things in the terminal and mount a Mac OS X partition (to copy your color profile) as follows (substitute your Mac OS partition's partition number for x in /dev/sdax, 2 being the first standard partition): 
```
sudo mv ~/Desktop/xcalib /usr/local/bin/xcalib
sudo chmod 755 /usr/local/bin/xcalib
sudo mount -t hfsplus /dev/sdax /mnt
sudo cp /mnt/Library/ColorSync/Profiles/Displays/* /usr/local/etc
```Then, do an "ls /usr/local/etc" and note the name of the profile (for the next step). Finally, create a new file entitled "51xcalib" in /etc/X11/Xsession.d (sudo nano /etc/X11/Xsession.d/51xcalib) with the following contents:

```
#!/bin/sh
# script to start xcalib when X loads
/usr/local/bin/xcalib "/usr/local/etc/<insert name of profile here>"
```Restart X (Ctrl-Alt-Backspace) and your Mac OS X color profile will be used every time you start up.

---

### Post by beelzebob on 2007-08-25
Cyberdork - thanx... I will try that... all I really need is something to change my monitor's gamma to .7 at boot/logon.  Are color profiles easy to create by hand that will do just that?

ALSO - TO ANYONE HAVING TROUBLE WITH POMMED - I was having a beeyotch of a time getting it to work.  My last stumbling block was that script on page 18 of this thread - it has whitespace characters after the "\" characters, which is a bug.  After taking all those whitespace characters out, my brightness controls work right out of the gate.  Killer.  Now all I need is something to set my gamma at boot.

---

### Post by cyberdork33 on 2007-08-25
> **beelzebob said:**
> Cyberdork - thanx... I will try that... all I really need is something to change my monitor's gamma to .7 at boot/logon.  Are color profiles easy to create by hand that will do just that?
I created one with the calibration tool in OSX. I wouldn't know how to go about it in Ubuntu.

---

### Post by beelzebob on 2007-08-25
> **beelzebob said:**
> Now all I need is something to set my gamma at boot.

For anyone who's curious and wants to do the same thing, just put the following in your .profile:

nvidia-settings -l

Now, your nvidia settings are loading on boot each time.  (The man pages say to put it in your .xinitrc, but that doesn't work for me for some reason.)

---

### Post by Corvias on 2007-08-25
Is anyone else having problems with compiz since tribe 5 was released? I did a fresh install from the tribe 5 cd and installed the nvidia binary drivers with the diff patch, but when I try to turn on desktop effects, I get booted to the logon screen.   Any ideas on how I can get some more detailed info to figure this out?

---

### Post by cyberdork33 on 2007-08-26
> **Corvias said:**
> Is anyone else having problems with compiz since tribe 5 was released? I did a fresh install from the tribe 5 cd and installed the nvidia binary drivers with the diff patch, but when I try to turn on desktop effects, I get booted to the logon screen.   Any ideas on how I can get some more detailed info to figure this out?

I assume Xorg is crashing (then restarting). What is in your /var/log/Xorg.0.log file?

---

### Post by Corvias on 2007-08-27
Here, I think, Is the pertinent excerpt. 

```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 16, (--) framebuffer bpp 16
(==) NVIDIA(0): RGB weight 565
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.
(II) NVIDIA(0): NVIDIA GPU GeForce 8600M GT (G84) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 60.84.49.03.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8600M GT at PCI:1:0:0:
(--) NVIDIA(0):     Apple (DFP-0)
(--) NVIDIA(0): Apple (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Apple (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1440x1440"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
(--) NVIDIA(0): DPI set to (110, 108); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Disabling 32-bit ARGB GLX visuals.
```

---

### Post by Corvias on 2007-08-27
Some progress. I just updated to the latest xorg-server through update manager and reinstalled the nvidia driver, Now when I turn effects on, X doesn't restart... BUT none of the windows have borders.

---

### Post by Bazou on 2007-08-28
Hi everyone,

I just switched to (k)Ubuntu after three years with Gentoo. 

As you can guess I got some problems with this fresh up-to-date install ;) Maybe I forget something new for me with Ubuntu. It's concerning the sound. I Did exactly these steps:

```
rsync -avz --delete rsync://alsa.alsa-project.org/hg/alsa-driver alsa
rsync -avz --delete rsync://alsa.alsa-project.org/hg/alsa-kernel alsa
cd alsa/alsa-driver
./hgcompile --with-cards=hda-intel
make;make install
/etc/init.d/alsasound stop
modprobe snd-hda-intel
```

And every things worked well. But I still don't have anysound.

dmesg contains this last line:
 
[ 2663.627476] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 20
[ 2663.627518] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[ 2663.639937] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...

Is this normal?

I also tried the alsa-utils with aplay. When I play a .wav file I got this output (without sound):

```
./aplay -vv /usr/lib/openoffice/share/gallery/sounds/drama.wav
Lecture en cours WAVE '/usr/lib/openoffice/share/gallery/sounds/drama.wav' : Signed 16 bit Little Endian, Taux 11025 Hz, Mono
Plug PCM: Rate conversion PCM (48000, sformat=S16_LE)
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 1
  rate         : 11025
  exact rate   : 11025 (11025/1)
  msbits       : 16
  buffer_size  : 3763
  period_size  : 235
  period_time  : 21333
  tick_time    : 0
  tstamp_mode  : NONE
  period_step  : 1
  sleep_min    : 0
  avail_min    : 235
  xfer_align   : 235
  start_threshold  : 3760
  stop_threshold   : 3763
  silence_threshold: 0
  silence_size : 0
  boundary     : 1059190337362198528
Slave: Route conversion PCM (sformat=S16_LE)
  Transformation table:
    0 <- 0
    1 <- 0
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 1
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 16
  buffer_size  : 16384
  period_size  : 1024
  period_time  : 21333
  tick_time    : 0
  tstamp_mode  : NONE
  period_step  : 1
  sleep_min    : 0
  avail_min    : 1024
  xfer_align   : 1024
  start_threshold  : 16384
  stop_threshold   : 16384
  silence_threshold: 0
  silence_size : 0
  boundary     : 4611686018427387904
Slave: Soft volume PCM
Control: PCM Playback Volume
min_dB: -51
max_dB: 0
resolution: 256
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 16
  buffer_size  : 16384
  period_size  : 1024
  period_time  : 21333
  tick_time    : 0
  tstamp_mode  : NONE
  period_step  : 1
  sleep_min    : 0
  avail_min    : 1024
  xfer_align   : 1024
  start_threshold  : 16384
  stop_threshold   : 16384
  silence_threshold: 0
  silence_size : 0
  boundary     : 4611686018427387904
Slave: Direct Stream Mixing PCM
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 16
  buffer_size  : 16384
  period_size  : 1024
  period_time  : 21333
  tick_time    : 0
  tstamp_mode  : NONE
  period_step  : 1
  sleep_min    : 0
  avail_min    : 1024
  xfer_align   : 1024
  start_threshold  : 16384
  stop_threshold   : 16384
  silence_threshold: 0
  silence_size : 0
  boundary     : 4611686018427387904
Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 2
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 16
  buffer_size  : 16384
  period_size  : 1024
  period_time  : 21333
  tick_time    : 4000
  tstamp_mode  : NONE
  period_step  : 1
  sleep_min    : 0
  avail_min    : 1024
  xfer_align   : 1024
  start_threshold  : 1
  stop_threshold   : 4611686018427387904
  silence_threshold: 0
  silence_size : 4611686018427387904
  boundary     : 4611686018427387904
############               +                      | 55%%
```

what else must I check?

Cheers,

Gilles

---

### Post by Mister.K on 2007-08-28
What's your Kernel version? I think (I'VE SAY I [COLOR="Red"]THINK[/COLOR]) i've got the same problem with the Festy generic. With the 2.6.22.2 it works perfectly.

Edit : I just read again your post, that can't be the same problem, i wasn't able to compile at all

---

### Post by Bazou on 2007-08-28
Mister K.,

My kernel is Linux 2.6.20-16-generic (Feisty).

I compiled the driver after installing automake, autotools and autoconf. Did you try this?

Did you need to patch with your kernel version?

---

### Post by Bazou on 2007-08-28
I restarted all the steps with the last kernel (2.6.22.5) and the sound still doesn't work :(

---

### Post by Bazou on 2007-08-28
One more thing:

I can't load the driver with the model w2jc option:

```
modprobe snd-hda-intel model=w2jc
```

give the following ouptut in dmesg:

```
[  180.359570] snd: Unknown parameter `model'
[  180.361033] snd_hwdep: Unknown symbol snd_info_register
[  180.361108] snd_hwdep: Unknown symbol snd_info_create_module_entry
[  180.361179] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl_compat
[  180.361250] snd_hwdep: Unknown symbol snd_info_free_entry
[  180.361333] snd_hwdep: Unknown symbol snd_unregister_oss_device
[  180.361421] snd_hwdep: Unknown symbol snd_verbose_printk
[  180.361491] snd_hwdep: Unknown symbol snd_register_oss_device
[  180.361565] snd_hwdep: Unknown symbol snd_ctl_register_ioctl
[  180.361635] snd_hwdep: Unknown symbol snd_card_file_add
[  180.361712] snd_hwdep: Unknown symbol snd_iprintf
[  180.361782] snd_hwdep: Unknown symbol snd_major
[  180.361877] snd_hwdep: Unknown symbol snd_unregister_device
[  180.361954] snd_hwdep: Unknown symbol snd_device_new
[  180.362047] snd_hwdep: Unknown symbol snd_ctl_unregister_ioctl
[  180.362136] snd_hwdep: Unknown symbol snd_lookup_oss_minor_data
[  180.362212] snd_hwdep: Unknown symbol snd_lookup_minor_data
[  180.362282] snd_hwdep: Unknown symbol snd_ctl_register_ioctl_compat
[  180.362365] snd_hwdep: Unknown symbol snd_card_file_remove
[  180.362436] snd_hwdep: Unknown symbol snd_register_device_for_dev
[  180.365841] snd_timer: Unknown symbol snd_info_register
[  180.365915] snd_timer: Unknown symbol snd_info_create_module_entry
[  180.365996] snd_timer: Unknown symbol snd_info_free_entry
[  180.366107] snd_timer: Unknown symbol snd_verbose_printk
[  180.366198] snd_timer: Unknown symbol snd_iprintf
[  180.366302] snd_timer: Unknown symbol snd_ecards_limit
[  180.366383] snd_timer: Unknown symbol snd_oss_info_register
[  180.366453] snd_timer: Unknown symbol snd_unregister_device
[  180.366580] snd_timer: Unknown symbol snd_device_new
[  180.366751] snd_timer: Unknown symbol snd_register_device_for_dev
[  180.403103] snd: Unknown parameter `model'
[  180.404458] snd_timer: Unknown symbol snd_info_register
[  180.404535] snd_timer: Unknown symbol snd_info_create_module_entry
[  180.404627] snd_timer: Unknown symbol snd_info_free_entry
[  180.404739] snd_timer: Unknown symbol snd_verbose_printk
[  180.404829] snd_timer: Unknown symbol snd_iprintf
[  180.404933] snd_timer: Unknown symbol snd_ecards_limit
[  180.405014] snd_timer: Unknown symbol snd_oss_info_register
[  180.405107] snd_timer: Unknown symbol snd_unregister_device
[  180.405235] snd_timer: Unknown symbol snd_device_new
[  180.405406] snd_timer: Unknown symbol snd_register_device_for_dev
[  180.406742] snd_pcm: Unknown symbol snd_info_register
[  180.406816] snd_pcm: Unknown symbol snd_info_create_module_entry
[  180.406887] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl_compat
[  180.407018] snd_pcm: Unknown symbol snd_timer_notify
[  180.407107] snd_pcm: Unknown symbol snd_timer_interrupt
[  180.407177] snd_pcm: Unknown symbol snd_info_free_entry
[  180.407247] snd_pcm: Unknown symbol snd_add_device_sysfs_file
[  180.407337] snd_pcm: Unknown symbol snd_info_get_str
[  180.407582] snd_pcm: Unknown symbol snd_verbose_printk
[  180.407738] snd_pcm: Unknown symbol snd_ctl_register_ioctl
[  180.407807] snd_pcm: Unknown symbol snd_card_file_add
[  180.407895] snd_pcm: Unknown symbol snd_iprintf
[  180.408010] snd_pcm: Unknown symbol snd_major
[  180.408172] snd_pcm: Unknown symbol snd_unregister_device
[  180.408254] snd_pcm: Unknown symbol snd_timer_new
[  180.408324] snd_pcm: Unknown symbol snd_device_new
[  180.408463] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[  180.408601] snd_pcm: Unknown symbol snd_lookup_minor_data
[  180.408672] snd_pcm: Unknown symbol snd_ctl_register_ioctl_compat
[  180.408769] snd_pcm: Unknown symbol snd_info_create_card_entry
[  180.408839] snd_pcm: Unknown symbol snd_power_wait
[  180.408927] snd_pcm: Unknown symbol snd_device_free
[  180.409050] snd_pcm: Unknown symbol snd_card_file_remove
[  180.409120] snd_pcm: Unknown symbol snd_register_device_for_dev
[  180.409294] snd_pcm: Unknown symbol snd_device_register
[  180.409368] snd_pcm: Unknown symbol snd_info_get_line
[  180.412616] snd_hda_intel: Unknown symbol snd_ctl_add
[  180.412712] snd_hda_intel: Unknown symbol snd_pcm_new
[  180.412804] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[  180.412881] snd_hda_intel: Unknown symbol snd_card_register
[  180.412951] snd_hda_intel: Unknown symbol snd_card_free
[  180.413021] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  180.413091] snd_hda_intel: Unknown symbol snd_card_proc_new
[  180.413323] snd_hda_intel: Unknown symbol snd_ctl_find_id
[  180.413416] snd_hda_intel: Unknown symbol snd_verbose_printk
[  180.413804] snd_hda_intel: Unknown symbol snd_ctl_new1
[  180.413940] snd_hda_intel: Unknown symbol snd_component_add
[  180.414029] snd_hda_intel: Unknown symbol snd_card_new
[  180.414098] snd_hda_intel: Unknown symbol snd_iprintf
[  180.414175] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[  180.414244] snd_hda_intel: Unknown symbol snd_ctl_boolean_mono_info
[  180.414338] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[  180.414415] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[  180.414484] snd_hda_intel: Unknown symbol snd_hwdep_new
[  180.414567] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[  180.414655] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[  180.414746] snd_hda_intel: Unknown symbol snd_device_new
[  180.414859] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[  180.414957] snd_hda_intel: Unknown symbol snd_card_disconnect
[  180.415027] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[  180.415207] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
[  180.415371] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[  180.415441] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[  180.415550] snd_hda_intel: Unknown symbol snd_pcm_format_width

```

I know that it should be model=mbp3 but it gives the same error...

---

### Post by salbo on 2007-08-28
I've installed ubuntu on my brand new SR MBP.. I've followed the guide on the front page of this forum.

I've gotten to the point where ubuntu is installed and boots fine, and I've installed the build essentials. From hereon nothing works...

Trying to install the nvidia driver gives me a message that I need to shut down the X server, but for some reason I simply can't...

I can't install wireless or alsa either. The folder /usr/src/modules/ does not exist.

Do you have the solutions to these problems?

Thanks in advance. It is great that you are doing so much work to get Ubuntu on this lovely piece of machinery

---

### Post by black_raven2525 on 2007-08-28
For the Nvidia driver, try booting into single user mode so X just doesn't start at all.  When Grub is loading, hit escape then select the recovery mode option.  As for the modules, you have to create that folder yourself, try this

```
sudo mkdir /usr/src/modules/
```

---

### Post by alephsmith on 2007-08-28
> try booting into single user mode so X just doesn't start at all

Unfortunately the driver install complains about the wrong run level from single user mode. you need to stop your X session. From Gnome do this:

```
sudo /etc/init.d/gdm stop
```

If you use KDE, replace gdm with kdm.

You also don't need to store your source in /usr/src/modules/. They modules can be built from ~/ just as easily.

---

### Post by alephsmith on 2007-08-28
> **Bazou said:**
> I restarted all the steps with the last kernel (2.6.22.5) and the sound still doesn't work :(

At the risk of being condescending: have you checked that output volume in alsa mixer? When I compiled I remember it telling me about the volume being automatically set to mute.

---

### Post by cyberdork33 on 2007-08-28
> **black_raven2525 said:**
> For the Nvidia driver, try booting into single user mode so X just doesn't start at all.  When Grub is loading, hit escape then select the recovery mode option.

Or you could:
```
sudo /etc/init.d/gdm stop
``` to stop the x server, and after installing:
```
sudo /etc/init.d/gdm start
``` to restart things.

NOTE: the 'gdm' would be 'kdm' for kubuntu

EDIT: How did two posts get in ahead of me?

---

### Post by black_raven2525 on 2007-08-28
> **alephsmith said:**
> Unfortunately the driver install complains about the wrong run level from single user mode. you need to stop your X session. 

It gives you the option to process with the install anyway, Ive used this approach twice and its worked for me.  But ya, killing X is probably quicker anyway.

---

### Post by violinmandan on 2007-08-28
I'm trying to install the free nv driver in Kubuntu Gutsy Tribe 5, and it keeps complaining about not finding xorg-server, xproto, or fontsproto. Does anyone know where I can find them?

---

### Post by cyberdork33 on 2007-08-28
> **violinmandan said:**
> I'm trying to install the free nv driver in Kubuntu Gutsy Tribe 5, and it keeps complaining about not finding xorg-server, xproto, or fontsproto. Does anyone know where I can find them?

Ok, I know I sent you over here, but I think I found the package name of a couple:
I think you need x11proto-fonts-dev and maybe x11proto-video-dev

As for the xorg-xserver, i think you just need the dev package (as you should have the actual xorg-xserver package installed by default). So install these, then try compiling again. If you still have an error in the configure, then post back.

```
sudo apt-get install xserver-xorg-dev x11proto-fonts-dev x11proto-video-dev
```

---

### Post by violinmandan on 2007-08-28
> **cyberdork33 said:**
> Ok, I know I sent you over here, but I think I found the package name of a couple:
I think you need x11proto-fonts-dev and maybe x11proto-video-dev

As for the xorg-xserver, i think you just need the dev package (as you should have the actual xorg-xserver package installed by default). So install these, then try compiling again. If you still have an error in the configure, then post back.

```
sudo apt-get install xserver-xorg-dev x11proto-fonts-dev x11proto-video-dev
```

Grrr..... you were right about those packages, but....
Now it wants some more:
```

checking for XORG... configure: error: Package requirements (xorg-server >= 1.2 xproto fontsproto  randrproto renderproto videoproto xextproto) were not met:

No package 'randrproto' found
No package 'renderproto' found
No package 'xextproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Any of those ring a bell?

---

### Post by cyberdork33 on 2007-08-28
> **violinmandan said:**
> Grrr..... you were right about those packages, but....
Now it wants some more:

Unfortunately this is probably going to be a tedious back ad forth thing. You can look in the readme, and make sure that all the dependencies are installed, or you can search for the missing packages every time you try to compile. The -dev packages are those libraries needed to compile against. 

If you do:
```
sudo aptitude search proto
``` you will see that there are several x11 proto packages. You can look for the right one (look for one that is close) and install it then try again. Again, I am not sure that the nv module will even work on your hardware, so this could be all for naught... good luck.

---

### Post by Bazou on 2007-08-29
> **alephsmith said:**
> At the risk of being condescending: have you checked that output volume in alsa mixer? When I compiled I remember it telling me about the volume being automatically set to mute.


Yes of course ;)

All channels are unmuted and the volume is set to the max.

Any other idea?

---

### Post by salbo on 2007-08-29
> **alephsmith said:**
> Unfortunately the driver install complains about the wrong run level from single user mode. you need to stop your X session. From Gnome do this:

```
sudo /etc/init.d/gdm stop
```

If you use KDE, replace gdm with kdm.

You also don't need to store your source in /usr/src/modules/. They modules can be built from ~/ just as easily.

Thanks. I got one step further now.

I get to applying the patch, by following the links. But where does the "nvdriver.conf" file come from?? I suppose I have to download it somewhere.

---

### Post by alephsmith on 2007-08-29
So you are installing the free nv drivers?

If you are you need to get it from git if you want it to work.

AFAIK you only need to apply a patch to the non-free drivers.

---

### Post by Mister.K on 2007-08-29
I've just compiled the 2.6.22.5 kernel on my MBP SR, and my restricted manager ask me... no... show me an error and ask me to install "mactel-linux-patches-2.6.22.5 drivers"... anyone noticed the same thing ?

---

### Post by cyberdork33 on 2007-08-29
> **Mister.K said:**
> I've just compiled the 2.6.22.5 kernel on my MBP SR, and my restricted manager ask me... no... show me an error and ask me to install "mactel-linux-patches-2.6.22.5 drivers"... anyone noticed the same thing ?

It is just how the restricted drivers manager works. it is expects a *drivers package that has the same name as your kernel, which if you are using a custom kernel, will not exist. you can disable the manager, as it will give errors unless you use the normal ubuntu kernels.
In addition, if there were any drivers enabled in the restricted drivers manager, you will likely need to recompile them, linking them to your new kernel.

---

### Post by violinmandan on 2007-08-29
> **cyberdork33 said:**
>  Again, I am not sure that the nv module will even work on your hardware, so this could be all for naught... good luck.

Well, I finally installed them and switched off the vesa driver, and it works!... sort of.
The video displays, but has a frame rate of about 1.5 fps and sometimes stops altogether.
Is there anything that can improve this, or is this always an issue with the free driver?

Also, I'm trying to compile stepmania, but it says it can't find an OpenGL library. Any idea where I could get my hands on that?

---

### Post by salbo on 2007-08-30
> **alephsmith said:**
> So you are installing the free nv drivers?

If you are you need to get it from git if you want it to work.

AFAIK you only need to apply a patch to the non-free drivers.

Thanks again for helping me out.

I've downloaded the newest nvidia driver as it says on the front page of this forum.

Can you please give me precise instructions on what I need to download and how to install it.

I've been using Linux for a few years, but I've never had to deal with problems like these before, so I don't know what to do.

Thanks again.

---

### Post by alephsmith on 2007-08-30
Download the lastet nvidia driver and the patch (to ~/ if it pleases you)

```
sh NVIDIA-Linux-x86-100.14.11-pkg1.run -x
cd NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/
patch -p0 < ../../../nv_macbook.diff
```

stop X

```

cd NVIDIA-Linux-x86-100.14.11-pkg1
./nvidia-installer -aN
```

follow the prompts then restart.

That should be it.

---

### Post by cyberdork33 on 2007-08-30
> **violinmandan said:**
> Well, I finally installed them and switched off the vesa driver, and it works!... sort of.
The video displays, but has a frame rate of about 1.5 fps and sometimes stops altogether.
Is there anything that can improve this, or is this always an issue with the free driver?

Also, I'm trying to compile stepmania, but it says it can't find an OpenGL library. Any idea where I could get my hands on that?

I think it is more of an issue with the very new graphics hardware in the Santa Rosa Macbooks, and still working out bugs. Someone else here may be able to give you more info.

Are you trying to compile for any partitcular reason? why not get a deb package... that should take care of any dependencies automatically... [http://www.getdeb.net/app.php?name=Stepmania](http://www.getdeb.net/app.php?name=Stepmania)

---

### Post by Bazou on 2007-08-30
Hi everyone,

Can someone help me to have sound please?

I follow exactly these steps, all successfully:

```
rsync -avz --delete rsync://alsa.alsa-project.org/hg/alsa-driver alsa
rsync -avz --delete rsync://alsa.alsa-project.org/hg/alsa-kernel alsa
cd alsa/alsa-driver
./hgcompile --with-cards=hda-intel
make;make install
/etc/init.d/alsasound stop
modprobe snd-hda-intel
```

With alsamixer the channels are at max and unmuted. My channels are:
headphone - PCM - Front - Surround - Line - Mic - IEC958 - 3 inputs

I tried the kernels 2.6.20-16-generic and the 2.6.22.5 with mactel patches.

I use alsa version 1.0.14. Is that your version?

With this last kernel my dmesg output is (when I load snd-hda-intel):

```
[ 1944.697245] PM: Adding info for No Bus:timer
[ 1944.724891] PM: Adding info for No Bus:seq
[ 1944.784005] PM: Adding info for No Bus:sequencer
[ 1944.784023] PM: Adding info for No Bus:sequencer2
[ 1944.829638] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 20
[ 1944.830480] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[ 1944.837344] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[ 1944.845170] PM: Adding info for No Bus:pcmC0D2c
[ 1944.845367] PM: Adding info for No Bus:pcmC0D1p
[ 1944.845520] PM: Adding info for No Bus:pcmC0D1c
[ 1944.845675] PM: Adding info for No Bus:adsp
[ 1944.845829] PM: Adding info for No Bus:pcmC0D0p
[ 1944.845980] PM: Adding info for No Bus:pcmC0D0c
[ 1944.846137] PM: Adding info for No Bus:dsp
[ 1944.846277] PM: Adding info for No Bus:audio
[ 1944.846427] PM: Adding info for No Bus:hwC0D0
[ 1944.846573] PM: Adding info for No Bus:controlC0
[ 1944.846740] PM: Adding info for No Bus:mixer
```

I also use KDE, and try "auto detection" and "alsa" as sound system. Something else must be set?


What are the exact step you did? did I forget something?

---

### Post by violinmandan on 2007-08-30
> **cyberdork33 said:**
> I think it is more of an issue with the very new graphics hardware in the Santa Rosa Macbooks, and still working out bugs. Someone else here may be able to give you more info.

Are you trying to compile for any partitcular reason? why not get a deb package... that should take care of any dependencies automatically... [http://www.getdeb.net/app.php?name=Stepmania](http://www.getdeb.net/app.php?name=Stepmania)

I'm trying to compile it because the precompiled versions are only available for the i386. I'm using an i686.
Isn't there some way to get 32-bit binaries to work on a 64-bit system (without installing a 32-bit OS)? I can run a 32-bit windows binary through wine, but it seems a 32-bit Ubuntu binary won't work...

---

### Post by cyberdork33 on 2007-08-30
> **violinmandan said:**
> I'm trying to compile it because the precompiled versions are only available for the i386. I'm using an i686.
Isn't there some way to get 32-bit binaries to work on a 64-bit system (without installing a 32-bit OS)? I can run a 32-bit windows binary through wine, but it seems a 32-bit Ubuntu binary won't work...

i386 vs i686 is not the same as 32bit vs 64bit.
Compiling anything is going to require pretty much the same procedure as previously, look at the error, and try to find the matching dependency. You will likely find many other packages that are 32bit only as 64bit has not taken off on the desktop.

---

### Post by ico on 2007-08-31
Hi all,

I am having issues with WPA wireless on my Santa Rosa MBP (17") running Ubuntu Studio. Tried getting the newest as well as recommended version of madwifi driver. Tried wcid and nm-applet although I do get a list of available networks (wcid works a bit better but has a buggy systray applet). I need the wireless to run WPA/WPA2 enabled. Hence, could someone please post their steps on how they got their ath0 wifi working? Should I also install latest wpasupplicant from CVS as well?

Many thanks!

Ico

---

### Post by redrum on 2007-09-02
Hi Guys, 

Does anyone succeeded in making lm-sensors working with feisty 32-bits ?

---

### Post by pepe# on 2007-09-02
Bazou: You need to make;make install. You can't use snd-hda-intel of alsa version XY with some other kernels alsa subsystem. make install will remove all alsa modules from your *running* kernel and install the compiled ones. Then unload all old modules and modprobe snd_hda_intel.

Oh, and:

> Unknown model for ALC882, trying auto-probe from BIOS.

This means you either have a different sound chip from all other SR MBP users or you're not using the current alsa tree. If you supply the modprobe command with "model=wj2c", old versions of alsa will work partially.
If you have the correct alsa version, snd_hda_intel will auto-detect a mbp model.

---

### Post by l3th0x on 2007-09-02
Hi,

When I try to patch in alsa-kernel, this happens:

Reversed patch detected! Assume -R

Hunk #3 FAILED at 10608 

(all to eight are succeded, except this.). I have not patched it before, so.. why is this happening? is there a manually form to patch it? or a method that I could  unpatch it (I am a newbie..sorry if I said one or too much things that are not correct) .I´m using a 2.6.20-16-generic kernel.

Thank you very much. And thank you to this forum, it´s great!!:KS

Ah, OMT, I have too the "Unknow model for ALC882. Three weeks ago, when I made a clean ubuntu install all worked fine (sound included), but now, with the same (I swear..) clean install, the sound doesn´t work. (I read all the messages in the forum, and tried everything, but have not had results)

Thank you very much again.

---

### Post by redrum on 2007-09-02
I'm not sure you still need to patch alsa kernel. I'm using a non patched alsa kernel, the sound is working just find without a low sound.

---

### Post by pepe# on 2007-09-02
> I read all the messages in the forum, and tried everything, but have not had results

You missed the one where I wrote that the alsa patch is included in the current alsa tree. Current alsa should detect a new model 'mbp' automatically.

---

### Post by l3th0x on 2007-09-02
Hi,
Thank you for the answer.

I read it. But my alsa just not work. I do not why..that is why I am open to all possibilities..:(

Thnk you.

---

### Post by pliz on 2007-09-03
after installing unpatched alsa try the following:

sudo rm /lib/modules/2.6.22-10-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
depmod

then sudo modprobe snd-hda-intel

This works for me. Alsa installs its working driver in a different place where Ubuntu's disfunctional driver is place and the disfunctional driver takes precedence somehow.

Cheers!

---

### Post by l3th0x on 2007-09-03
Hi,

Thank you for your answer, but still not luck..

I have compile my new gutsy kernel with the mactel patches...and still nothing..

but I think that is something about what you said.

When I restart, a message:

cannot locate resource region 5 ... appear after grub.

In the meantime now I am using the /etc/modprobe.d/options:

options snd_hda_intel model=w2jc solution, and now that works...but without the mic, headphones...

my alsa is there due to :

aplay -l
tarjeta 0:Intel [HDA Intel], dispositivo 0: ALC882 Analog [ALC882 Analog]
Subdispositivos: 1/1
Subdispositivos #0:subdevice #0
tarjeta 0:Intel [HDA Intel], dispositivo 1: ALC882 Analog [ALC882 Analog]
Subdispositivos: 1/1
Subdispositivos #0:subdevice #0

And ubuntu is detecting the presence of my soundcard :

lspci -v

00:1b.0 Audio Device: Intel Corporation 82801h (ICH8 Family) HD Audio Controller (rev 3)
Subsystem: Apple Computer Inc. Unknown device 00a0
Flags: bus master, fast devsel, latency 0, IRQ 20
Memory at 9b500000 (64 bit,n-p) size 16
capab. access denied.

so, now..I do not know, 
I am reading google...:(

Thank you very much

---

### Post by Bazou on 2007-09-03
> **pepe# said:**
> Bazou: You need to make;make install. You can't use snd-hda-intel of alsa version XY with some other kernels alsa subsystem. make install will remove all alsa modules from your *running* kernel and install the compiled ones. Then unload all old modules and modprobe snd_hda_intel.

Oh, and:

> Unknown model for ALC882, trying auto-probe from BIOS.

This means you either have a different sound chip from all other SR MBP users or you're not using the current alsa tree. If you supply the modprobe command with "model=wj2c", old versions of alsa will work partially.
If you have the correct alsa version, snd_hda_intel will auto-detect a mbp model.

Hi pepe,

As I wrote, I did make && make install with a synced alsa-tree. 

> after installing unpatched alsa try the following:

sudo rm /lib/modules/2.6.22-10-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
depmod

then sudo modprobe snd-hda-intel

I also tried:
```
rm /usr/src/linux-2.6.22.5/debian/linux-image-2.6.22.5-mactel/lib/modules/2.6.22.5-mactel/kernel/sound/pci/hda/snd-hda-intel.k
```

but nothing. I still have the same dmesg message.

I think that I have a very very low sound, but so low that i'm not event sure of it.

Discouraging...

---

### Post by pepe# on 2007-09-03
l3th0x...please follow this, check if the commands are successful, do everything as root(sudo bash)

boot your favorite kernel.
remove or disable the current alsa configuration in ubuntu, eg your options-entry for modprobe.
pliz said ubuntu may have drivers in strange locations, we find them with:

find /lib/modules/$(uname -r)/  -name snd\*

Delete *all* alsa modules. run depmod -a. try to load alsa, it should fail. eg modprobe snd-hda-intel. Verify via lsmod that no alsa-stuff is loaded. 

If you deleted the alsa source tree, rsync again:
rsync -avz --delete rsync://alsa.alsa-project.org/hg/alsa-driver alsa
rsync -avz --delete rsync://alsa.alsa-project.org/hg/alsa-kernel alsa

cd alsa/alsa-driver
./hgcompile --with-cards=hda-intel
make;make install
depmod -a (just for fun)
modprobe snd_hda_intel

'dmesg' should report  >>hda_codec: model 'mbp3' is selected<<

If it doesn't, use model=mbp3, this overrides auto-detection. If the driver still uses auto-detection or fails, you are still using some old alsa driver instead of the compiled one. Find out why.

You said you compiled the kernel yourself. Verify that alsa is configured as a module and that you are loading the correct kernel.

edit: make sure to use the above rsync URL, not the one mentioned one the alsa website, they are out of sync.
edit2: very low volume is typical for the w2jc model. speakers work and you can use the lineIN as HP-out by switching the 2ch/6ch mixer widget.


advertisement:

My wiki page still has all the latest info on what works and how to do it. No distribution-specific stuff as this would fill a lot of pages. If someone manages to get audio recording or appleIR to work, please tell us. [https://cbg.dyndns.org/wiki/ReadingCorner/LinuxOnMacbookPro](https://cbg.dyndns.org/wiki/ReadingCorner/LinuxOnMacbookPro)

---

### Post by Bazou on 2007-09-03
thanks for your help pepe.

As I got the same error, here are the result of your steps:

```
find /lib/modules/$(uname -r)/ -name snd\*
/lib/modules/2.6.22.5-mactel/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.22.5-mactel/kernel/sound/acore/snd-timer.ko
/lib/modules/2.6.22.5-mactel/kernel/sound/acore/snd-page-alloc.ko
/lib/modules/2.6.22.5-mactel/kernel/sound/acore/oss/snd-mixer-oss.ko
/lib/modules/2.6.22.5-mactel/kernel/sound/acore/oss/snd-pcm-oss.ko
/lib/modules/2.6.22.5-mactel/kernel/sound/acore/snd.ko
/lib/modules/2.6.22.5-mactel/kernel/sound/acore/snd-hwdep.ko
/lib/modules/2.6.22.5-mactel/kernel/sound/acore/seq/snd-seq-midi-event.ko
/lib/modules/2.6.22.5-mactel/kernel/sound/acore/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.22.5-mactel/kernel/sound/acore/seq/snd-seq.ko
/lib/modules/2.6.22.5-mactel/kernel/sound/acore/seq/snd-seq-device.ko
/lib/modules/2.6.22.5-mactel/kernel/sound/acore/snd-pcm.ko
/lib/modules/2.6.22.5-mactel/kernel/sound/acore/snd-rtctimer.ko

root@MACKIE:/usr/src/modules/alsa/alsa-driver# rm /lib/modules/2.6.22.5-mactel/kernel/sound/pci/hda/snd-hda-intel.ko
root@MACKIE:/usr/src/modules/alsa/alsa-driver# rm /lib/modules/2.6.22.5-mactel/kernel/sound/acore/snd-timer.ko

(etc...)
```

```
root@MACKIE:/usr/src/modules/alsa/alsa-driver# find /lib/modules/$(uname -r)/ -name snd\*
```

```
root@MACKIE:/usr/src/modules/alsa/alsa-driver# depmod -a
```

```
root@MACKIE:/usr/src/modules/alsa/alsa-driver# /etc/init.d/alsasound restart
Shutting down sound driver: done
root@MACKIE:/usr/src/modules/alsa/alsa-driver# lsmod
Module                  Size  Used by
af_packet              28044  2
ipv6                  315752  12
hci_usb                21020  6
rfcomm                 46888  6
l2cap                  28672  5 rfcomm
bluetooth              63364  15 hci_usb,rfcomm,l2cap
ppdev                  11400  0
capability              7176  0
commoncap               9600  1 capability
acpi_cpufreq           10760  1
cpufreq_stats           8288  0
cpufreq_userspace       6048  0
cpufreq_ondemand       10896  1
freq_table              6592  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     9736  0
cpufreq_powersave       3200  0
ac                      7304  0
dock                   12392  0
video                  20496  0
button                 10400  0
sbs                    21520  0
container               6528  0
battery                12552  0
nls_iso8859_1           6656  1
nls_cp437               8320  1
vfat                   16384  1
fat                    60208  1 vfat
nls_utf8                3584  1
ntfs                  104288  1
sbp2                   27272  0
parport_pc             42024  0
lp                     15048  0
parport                44300  3 ppdev,parport_pc,lp
snd_page_alloc         13200  0
nvidia               8115256  26
i2c_core               30208  1 nvidia
sky2                   50564  0
shpchp                 38300  0
pci_hotplug            36868  1 shpchp
intel_agp              30496  0
tsdev                  10752  0
evdev                  13184  5
ext3                  146832  1
jbd                    69104  1 ext3
mbcache                11400  1 ext3
sg                     41512  0
sd_mod                 32512  4
ide_cd                 45344  0
cdrom                  41896  1 ide_cd
usbhid                 32576  0
hid                    33536  1 usbhid
ata_piix               18820  3
ata_generic            10116  0
libata                141200  2 ata_piix,ata_generic
scsi_mod              172856  4 sbp2,sg,sd_mod,libata
ohci1394               38984  0
ieee1394              109656  2 sbp2,ohci1394
generic                 7428  0 [permanent]
piix                   12292  0 [permanent]
ehci_hcd               39564  0
uhci_hcd               29600  0
usbcore               160304  5 hci_usb,usbhid,ehci_hcd,uhci_hcd
thermal                16528  0
processor              36232  2 acpi_cpufreq,thermal
fan                     6920  0
root@MACKIE:/usr/src/modules/alsa/alsa-driver# modprobe snd-hda-intel
FATAL: Module snd_hda_intel not found.
```

```
rsync ...
cd alsa/alsa-driver
./hgcompile --with-cards=hda-intel
(etc...)
ALSA modules were successfully compiled.

make
(etc...)
ALSA modules were successfully compiled.

make install
(etc...)
WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

depmod -a
modprobe snd_hda_intel
```

```
dmesg
(etc...)
[ 7702.759141] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
```

Try with model=mbp3

```
modprobe snd_hda_intel model=mbp3
FATAL: Error inserting snd (/lib/modules/2.6.22.5-mactel/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.22.5-mactel/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.22.5-mactel/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.22.5-mactel/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.22.5-mactel/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.22.5-mactel/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22.5-mactel/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```


```
part of dmesg

[ 7846.913605] snd_pcm: Unknown symbol snd_ctl_unregister_ioctl
[ 7846.913734] snd_pcm: Unknown symbol snd_lookup_minor_data
[ 7846.913804] snd_pcm: Unknown symbol snd_ctl_register_ioctl_compat
[ 7846.913901] snd_pcm: Unknown symbol snd_info_create_card_entry
[ 7846.913971] snd_pcm: Unknown symbol snd_power_wait
[ 7846.914064] snd_pcm: Unknown symbol snd_device_free
[ 7846.914188] snd_pcm: Unknown symbol snd_card_file_remove
[ 7846.914258] snd_pcm: Unknown symbol snd_register_device_for_dev
[ 7846.914432] snd_pcm: Unknown symbol snd_device_register
[ 7846.914506] snd_pcm: Unknown symbol snd_info_get_line
[ 7846.919922] snd_hda_intel: Unknown symbol snd_ctl_add
[ 7846.920021] snd_hda_intel: Unknown symbol snd_pcm_new
[ 7846.920113] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[ 7846.920190] snd_hda_intel: Unknown symbol snd_card_register
[ 7846.920260] snd_hda_intel: Unknown symbol snd_card_free
[ 7846.920330] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[ 7846.920401] snd_hda_intel: Unknown symbol snd_card_proc_new
[ 7846.920632] snd_hda_intel: Unknown symbol snd_ctl_find_id
[ 7846.920726] snd_hda_intel: Unknown symbol snd_verbose_printk
[ 7846.920855] snd_hda_intel: Unknown symbol snd_ctl_new1
[ 7846.920990] snd_hda_intel: Unknown symbol snd_component_add
[ 7846.921078] snd_hda_intel: Unknown symbol snd_card_new
```

So, It didn't resolve the problem :(

---

### Post by pepe# on 2007-09-03
You're not using the alsa drivers you installed. Either there are some modules left somewhere or part of alsa is compiled static into the kernel. Everything needs to be a module.

---

### Post by ilmarw on 2007-09-03
I have the exact same issue. Updated the kernel, and now sound doesn't work.

---

### Post by ilmarw on 2007-09-03
Nevermind, did a restart, modprobe now ran fine. Sound OK. Thanks...

---

### Post by l3th0x on 2007-09-03
Jeloou!!

PEPE YOU ARE THE BEST, EVER!! Thank you, thank you very much.:guitar:

and thank you to all this forum, really I have never seen so much support (28 pages!!). You are all incredible!!

Now I am listening portishead, with my headphones :KS, from my very beautiful macbox

I have been "rm -r" the sound/core ones, only, and cannot made it, till now...really, thank you, thank you very much. 

About appleir, in google, I am looking now the magarto page..

(yep, I compiled the alsa as module, I did with a 22.6 kernel, too much reading in google, to made it.), so now :

*appleir
*audio-recording. anyone has used CDDOIT??
*pommed keyboard (do not know why but something I have made wrong, due to I do not have iluminated keyboard :(  
*my cannot locate resource region  pci error message: does not dissapear..
*etc.etc. (I need to read moooree)


Again, arigato gosai mashita!!

---

### Post by Bazou on 2007-09-04
I removed all /sound/core folders and all "find /lib/modules/$(uname -r)/ -name snd\*" files.

My kernel is set with alsa as module.

I don't know why it doesn't work, but I'm now fed up with this, so I leave.

I will maybe try again with the gutsy release.

Anyway, thanks for your help.

bye

---

### Post by Elv13 on 2007-09-04
did you tried my patch for the IR, if nobody test it, it will never work.

---

### Post by DylanRE on 2007-09-04
After installing nvidia drivers, madwifi stopped working. I rebooted and it just won't work. I tried modprobe ath_pci and it failed with this message:

FATAL: Error inserting ath_pci (/lib/modules/2.6.20-16-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

dmesg contains this:

[ 1223.124000] ath_pci: Unknown symbol ieee80211_iterate_nodes
[ 1223.124000] ath_pci: disagrees about version of symbol ieee80211_vap_attach
[ 1223.124000] ath_pci: Unknown symbol ieee80211_vap_attach
[ 1223.124000] ath_pci: disagrees about version of symbol ieee80211_ibss_merge
[ 1223.124000] ath_pci: Unknown symbol ieee80211_ibss_merge
[ 1223.124000] ath_pci: disagrees about version of symbol ieee80211_rate_attach
[ 1223.124000] ath_pci: Unknown symbol ieee80211_rate_attach
[ 1223.124000] ath_pci: disagrees about version of symbol ieee80211_rate_detach
[ 1223.124000] ath_pci: Unknown symbol ieee80211_rate_detach
[ 1223.124000] ath_pci: disagrees about version of symbol ieee80211_send_qosnulldata
[ 1223.124000] ath_pci: Unknown symbol ieee80211_send_qosnulldata
[ 1223.124000] ath_pci: disagrees about version of symbol ieee80211_find_rxnode_debug
[ 1223.124000] ath_pci: Unknown symbol ieee80211_find_rxnode_debug
[ 1223.124000] ath_pci: disagrees about version of symbol ieee80211_create_vap
[ 1223.124000] ath_pci: Unknown symbol ieee80211_create_vap
[ 1223.124000] ath_pci: disagrees about version of symbol ieee80211_input_all
[ 1223.124000] ath_pci: Unknown symbol ieee80211_input_all
[ 1223.124000] ath_pci: disagrees about version of symbol ieee80211_start_running
[ 1223.124000] ath_pci: Unknown symbol ieee80211_start_running
[ 1223.124000] ath_pci: disagrees about version of symbol ieee80211_vap_detach
[ 1223.124000] ath_pci: Unknown symbol ieee80211_vap_detach
[ 1223.124000] ath_pci: disagrees about version of symbol ieee80211_announce
[ 1223.124000] ath_pci: Unknown symbol ieee80211_announce
[ 1223.124000] ath_pci: disagrees about version of symbol ieee80211_chan2ieee
[ 1223.124000] ath_pci: Unknown symbol ieee80211_chan2ieee
[ 1223.124000] ath_pci: disagrees about version of symbol ath_hal_init_channels
[ 1223.124000] ath_pci: Unknown symbol ath_hal_init_channels
[ 1223.124000] ath_pci: disagrees about version of symbol ieee80211_dturbo_switch
[ 1223.124000] ath_pci: Unknown symbol ieee80211_dturbo_switch
[ 1223.124000] ath_pci: disagrees about version of symbol ieee80211_crypto_encap
[ 1223.124000] ath_pci: Unknown symbol ieee80211_crypto_encap
[ 1223.124000] ath_pci: disagrees about version of symbol ieee80211_getrssi
[ 1223.124000] ath_pci: Unknown symbol ieee80211_getrssi
[ 1223.124000] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
[ 1223.124000] ath_pci: Unknown symbol ath_hal_getwirelessmodes


There's a lot more in dmesg, but I'm not pasting it all- you get the point.

PLEASE help.

---

### Post by pepe# on 2007-09-05
> did you tried my patch for the IR, if nobody test it, it will never work.

I tried it and got nothing. Never used IR before so I may have missed a few things. Does it work for you? How did you set everything up? If you can't test it yourself, I'll be happy to help you with that.


DylanRE: Your problem is probably independent from the nvidia stuff. I messed a lot with nvidia and madwifi and they never interacted. It looks more like you are trying to combine old and new modules. Did you do madwifi-unload before loading the new driver?

---

### Post by asoare on 2007-09-05
Hey can someone pls tell me what has currently NOT been fixed with ubuntu under santa rosa MBP ?

---

### Post by DylanRE on 2007-09-05
> **pepe# said:**
> 
DylanRE: Your problem is probably independent from the nvidia stuff. I messed a lot with nvidia and madwifi and they never interacted. It looks more like you are trying to combine old and new modules. Did you do madwifi-unload before loading the new driver?

Well now I can't even get into X (no idea why it stopped working, some error about not having any screens). I'm going to do a complete reinstall of the nvidia and madwifi drivers, and if that doesn't fix it, I'll do a complete reinstall of my system.

---

### Post by DylanRE on 2007-09-05
A reinstall of the driver fixed my video problem, but wifi will not work for me. I tried madwifi-unload, and it unloads ath_hal and wlan, but I still have the same problem when I modprobe ath_pci.

Any ideas?

---

### Post by pepe# on 2007-09-05
> Any ideas?

nothing special. rm -rf your module directory and possible modutil configurations, make;make modules_install, boot new kernel. now try to install nvidia/madwifi from a clean current source tree.. It should just work..


asoare: I don't care about ubuntu, but currently only the IR remote control does not work. Everything else works with a bit tweaking. You have to use a binary nvidia driver and seperate kernel modules for iSight, Sound, Wlan though. If you need paravirtualization, the nvidia module will break s2ram. Battery life is a bit less than with OSX. Did I forget something?

---

### Post by DylanRE on 2007-09-05
pepe, thanks for your help. I now have both the nvidia driver and madwifi installed and running; however, madwifi will not take an IP address. It sees networks but fails to join them. Once again, anyone have any ideas?

---

### Post by pepe# on 2007-09-06
> madwifi will not take an IP address. It sees networks but fails to join them.

what did you try, what did you get? you have to use athX, not wifiX. Also, read the README in the madwifi sources.

---

### Post by trouble1313 on 2007-09-06
Just a heads up regarding the alsa module complaining about symbols after compiling. Do exactly what was recommended. Go find the alsa module in your kernel modules directory and delete it....Then do the make install and depmod and you can modprobe it. Just like what was suggested, the make install seems to put the module in a different spot so the modprobe tries to grab the old one. This occurred after I upgraded to Gutsy. It didn't happen with Feisty.

Regarding Gutsy, I can't really recommend bothering to go to it yet unless there's something you REALLY want that's newer. I've found little power improvement (though I haven't recompiled for the tickless kernel). There's also a 'bug'/'feature' where xserver-xgl gets in the way of the nvidia drivers and the ability to use Compiz. It can be worked around but it was annoying until I figured it out.

I've found little else that's changed though my Firebird fonts suck now. Same old gotchas seem to still apply.

-Trouble

---

### Post by lv1001 on 2007-09-06
This might sound noobish, but just to spare this to others:

Even though I had no automake installed and the ./configure of alsa gave quite some errors,  it ended with "ALSA modules were successfully compiled."

After installing automake, the rest of the alsa-install went just as is should.

Also I have the same thing about madwifi not working after installing/reinstalling/removing/whatever nvidia and even once or twice after trying to install alsa. However, "make install", "modprobe ath_pci" solves this.

LV

---

### Post by DylanRE on 2007-09-06
lv1001, thanks for the insight into madwifi; however, I did get it installed (basically using that same method), it just isn't working properly. Do you have any idea which revision you checked out from svn? I'm beginning to think maybe the revision I have is broken.

EDIT: Grabbed an older rev. and it fixed it. Thank you for your help, everybody (especially pepe)!

---

### Post by brainiac on 2007-09-07
would you mind telling which revision you compiled from? i've got the same issue.

Edit: nevermind... i found another thread [here]("http://ubuntuforums.org/showpost.php?p=2731459&postcount=25")
which tells me to use this revision [here]("http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2372-20070525.tar.gz")

will try and report later

---

### Post by lv1001 on 2007-09-07
I was using madwifi rev 2695 
However, after updating to the newest rev 2704 it still works like charm.

LV

---

### Post by brainiac on 2007-09-07
Are you on feisty or gutsy.... because i think ntwork-manager may be broken... i now get an ip.. but the manager pops up from time to time asking for my password seems like it "forgets" my wpa2 key

---

### Post by cyberdork33 on 2007-09-07
> **brainiac said:**
> Are you on feisty or gutsy.... because i think ntwork-manager may be broken... i now get an ip.. but the manager pops up from time to time asking for my password seems like it "forgets" my wpa2 key
I have noticed it doing that on completely unrelated hardware on gutsy.

---

### Post by beelzebob on 2007-09-07
WARNING - the latest automatic update broke my xserver - now it won't start!  I have no idea which part of the update broke it, but just be warned....

---

### Post by beelzebob on 2007-09-07
Just to follow up my last post.... apparently, you need to rebuild/reinstall the nvidia drivers after installing the latest updates.

---

### Post by DylanRE on 2007-09-07
> **beelzebob said:**
> Just to follow up my last post.... apparently, you need to rebuild/reinstall the nvidia drivers after installing the latest updates.

Sometimes my nvidia driver just stops working and I have to rebuild it. So don't be too surprised if something goes wrong again.

---

### Post by Elv13 on 2007-09-07
if it is a kernel update, update your modules

---

### Post by pepe# on 2007-09-07
Thanks to Stelian Pop, we now have a working IR remote control. His lircd.conf did not work for me so I had to create one with irrecord. If neither one works for you, please submit your lircd.conf.

[https://cbg.dyndns.org/wiki/ReadingCorner/LinuxOnMacbookPro#appleir](https://cbg.dyndns.org/wiki/ReadingCorner/LinuxOnMacbookPro#appleir)

Does someone know a nice remote control frontend like what apple uses to control multiple apps? Currently checking out mms...

---

### Post by trouble1313 on 2007-09-08
Quick question about AppleIR....Can the receiver learn from arbitrary remotes or just the little Apple one that only gives a few functions?

-Trouble

---

### Post by pepe# on 2007-09-08
You should be able to register other remotes, tell me if it works.

stop lircd
irrecord -H macmini -d /dev/usb/hiddev0 myremote
mv myremote /etc/lircd.conf
start lircd

lircd.conf assigns symbols to the signals from the remote. ~/.lircrc assigns symbols to actions in programs.

---

### Post by Elv13 on 2007-09-08
mythTV is the best media frontend i think

---

### Post by [woodstock] on 2007-09-11
Did anyone already started a wiki entry dedicated to the new MBP? This thread has become quite long, and the existing entry at wiki.ubuntu.com refers to this thread regarding the Santa Rosa MBP.

---

### Post by cyberdork33 on 2007-09-11
> **'[woodstock] said:**
> Did anyone already started a wiki entry dedicated to the new MBP? This thread has become quite long, and the existing entry at wiki.ubuntu.com refers to this thread regarding the Santa Rosa MBP.

No, but that is probably an excellent idea at this point. Although, it might be helpful to wait for Gutsy as that release could change a lot.

---

### Post by subferno on 2007-09-11
> **'[woodstock] said:**
> Did anyone already started a wiki entry dedicated to the new MBP? This thread has become quite long, and the existing entry at wiki.ubuntu.com refers to this thread regarding the Santa Rosa MBP.

Yeah, a new wiki page would definitely help. I just got the MacBook Pro and struggling to get Ubuntu to work so far.

---

### Post by alephsmith on 2007-09-12
I'd contribute to that.
What would be the most transparent page name?

MacBookPro Rev 3
MacBookPro Rev C
MacBookPro SantaRosa

---

### Post by martinbures on 2007-09-12
BTW:
Recent updates in gutsy have audio working out-of-the-box.

---

### Post by russell.h on 2007-09-14
A wiki article would be great. I have had my SR MBP since July, but have been waiting for some of the bugs to get worked out (and to get an external drive to free up some space) before putting Ubuntu on it.

Currently this thread is the top hit on Google for "linux on santa rosa macbook pro", and I would be inclined to suggest that "MacBook Pro Santa Rosa" or "Santa Rosa Macbook Pro" would be the best names for the wiki article.

Anyway, I'm sure I'll be in here begging for assistance sometime next week when I give this installation a shot.

---

### Post by alephsmith on 2007-09-14
I have taken it upon myself to start a Wiki page based on this thread: [https://wiki.ubuntu.com/MacBookPro_SantaRosa](https://wiki.ubuntu.com/MacBookPro_SantaRosa)

Forgive my awful Wiki markup. Please feel free to add/remove stuff.

---

### Post by Dhjiz on 2007-09-14
Hello,

First of all, thanks for making that page on the Wiki, it'll be a great help for many people I think.


But I noticed some things that can be modified in my opnion:
[LIST=1]
[*]Wouldn't it be a better idea to do the entire nvidia compilation thing in recovery mode, so that there is no gdm to stop. We could juste give the wget commands to download the rights files, then patch install and reboot to get it working easyily.
[*]I read on the Debian website that the aptitude package manager is more recommended now than apt-get, so could we replace apt-get with aptitude in the commands?
[*]Isn't there a better way to install the pommed and gpomme applications, using the package manager, for example using the gutsy packages ( [http://packages.ubuntu.com/gutsy/utils/pommed](http://packages.ubuntu.com/gutsy/utils/pommed) ), or the debian packages?
[/LIST]

Thanks.
I plan to edit the wiki page, depending of your answers.

---

### Post by alephsmith on 2007-09-14
1. Some people have problems getting an internet connection from a root terminal, including me. At this stage I think getting them into X first is a better option. Also it'll teach them how to get graphics (i.e. vesa) when nvidia breaks again. I also noticed that the installer script complains about the wrong init level in recovery. While it still works, it may confuse people using the wiki.

2. I use apt-get, and I thought it is the Ubuntu way. As far as the wiki I have no strong feelings either way.

3. Do the Debian packages include patches? I don't know. I personally didn't install pommed in that way, I just nabbed the instructions from the OP.

Please also add things to the wiki page. Including:
[LIST]
[*]Super-drive: piix module (feisty) something else for gutsy
[*]I seem to remember black listing some nvidia-modules, any one remember?
[*]I never got iSight going. Anyone have some easy instructions
[*]Mactel patches? should we mention them?
[*]Remote control. I haven't tried this yet.
[/LIST]

PS this was all from memory. I currently don't have Ubuntu on my MacBook Pro, so I must have made some errors in there.

---

### Post by cyberdork33 on 2007-09-15
> **alephsmith said:**
>  I use apt-get, and I thought it is the Ubuntu way. As far as the wiki I have no strong feelings either way.
There are good and bad reasons to use either. apt-get is fine.

---

### Post by .bashrc on 2007-09-15
Hey, while I would love to (and probably plan on) sifting through the last 32 pages of conversation on MBP santa rosa, I just got one and would love to put Ubuntu on it (had it on my MacBook, former Debian PPC user!). What's the current status of the "project," if you will, regarding MBP support? 

Thanks in adv.

---

### Post by Elv13 on 2007-09-16
Screen work 
power management "work", but it can be better (a lot better)
keyboard light work
sensor all work
remote can work (i did not try)
webcam can work too
cpu clock work perfectly
usb/firewire work
3D accel work at 25% of what this card can do, but it is a bug in the driver, we can do nothing about it exept wait and see, but compiz-fusion work at 7-12 fps when moving transparent+reflection+fish cube
wireless work, but i am not able (and i am not alone) to setup WPA
wired network work
cdrom drive work

:

everything work, and will work better in few month, but i deleted OSX and i am fine under linux, so it is not that bad

---

### Post by DeepB on 2007-09-16
> **alephsmith said:**
> I have taken it upon myself to start a Wiki page based on this thread: [https://wiki.ubuntu.com/MacBookPro_SantaRosa](https://wiki.ubuntu.com/MacBookPro_SantaRosa)

Forgive my awful Wiki markup. Please feel free to add/remove stuff.

Check the renamed page
[https://wiki.ubuntu.com/MacBookProSantaRosa](https://wiki.ubuntu.com/MacBookProSantaRosa)

---

### Post by runelord99 on 2007-09-17
Ok I know this is probably a stupid point but I had a look in the readme for the nvidia driver "NVIDIA-Linux-x86_64-100.14.11-pkg2.run" and it says that it supports the 8600 gt in the santa rosa MBP's and that it is for 32bit and 64bit linux. has anyone tried this to see if it works? or is it the same driver that needs to be patched?

---

### Post by alephsmith on 2007-09-17
It supports the GPU. Just not on the Macbook Pro. Current nvidia drivers need to be patched, or you must use on of the two other workarounds (dualhead-reboot or nv bait and switch).

---

### Post by squell on 2007-09-17
Regarding the Wiki page that has been setup ([https://wiki.ubuntu.com/MacBookProSantaRosa](https://wiki.ubuntu.com/MacBookProSantaRosa)), would it make more sense to refer to the Macbook Pro by its revision number and so therefore change the page name?  My reasoning for this is when the next Macbook Pro comes out it will also have a Santa Rosa chipset but the configurations (for graphics, wireless etc) may be different.

---

### Post by pepe# on 2007-09-17
Could you please do wiki-related discussions in $wikipage:talk or so?


> wireless work, but i am not able (and i am not alone) to setup WPA

I've been using WPA2-PSK, i.e. CCMP with PSK. With wpa_supplicant, out of the box.

> power management "work", but it can be better (a lot better)

You get 3 to 4 hours depending on how serious you are with saving power. S2RAM works, s2disk shouldn't be a problem. Alsa does seem to support power management for the chip, but I didn't notice anything. At least one more hour should be possible. My guess is that the nvidia power management doesn't fully work. It's been about the same consumption with the free nv driver when I tested about a month ago.


Did somebody manage to boot linux without bios emulation, i.e. direct efi-boot?
Or am I the only one with serious delays between selecting linux in refit and starting lilo? 
I would really like to reduce the time needed for bootstrapping..

---

### Post by Elv13 on 2007-09-17
i looked at some webpage about that, if we try tu use EFI, we will break nvidia driver (bios required), wireless and sound so it is nto a really good idea...

You are not alone to find the boot slow, it take almost 20 second for me (grub). We can use EFI, i can try with my gentoo (ubuntu is the default, gentoo for multimedia/compiling) when i will have some time, but is not the case right now.

---

### Post by l3th0x on 2007-09-19
Hi,

New  100.14.19 nvidia display driver is out, and it works! (without patch, I mean).

Regards..

---

### Post by Dhjiz on 2007-09-19
I installed the new driver and I confirm there's no need to patch it anymore.

And best of all, the changelog says it support the new Xserver API, so we could hope it to work out-of-the-box in Gutsy, with the new Xorg and Xserver.

Great news.

EDIT: Here is the changelog: [http://www.nvnews.net/vbulletin/showthread.php?t=98635](http://www.nvnews.net/vbulletin/showthread.php?t=98635)

---

### Post by drpynchon on 2007-09-19
I've been following along the progress on this with glee, but I think in all the efforts to spruce things up I've lost track of something. Now that sound, graphics, and wireless are tackled, what exactly are the remaining issues with Ubuntu on the Santa Rosa MBP?

---

### Post by Elv13 on 2007-09-19
> **Dhjiz said:**
> I installed the new driver and I confirm there's no need to patch it anymore.

And best of all, the changelog says it support the new Xserver API, so we could hope it to work out-of-the-box in Gutsy, with the new Xorg and Xserver.

Great news.

EDIT: Here is the changelog: [http://www.nvnews.net/vbulletin/showthread.php?t=98635](http://www.nvnews.net/vbulletin/showthread.php?t=98635)

Gutsy use the same xServer than feisty, xserver 1.4 (X11 7.3) will be avalible only in 8.04. 7.3 had some delay and it came after feature freez.

---

### Post by cyberdork33 on 2007-09-19
> **Elv13 said:**
> Gutsy use the same xServer than feisty, xserver 1.4 (X11 7.3) will be avalible only in 8.04. 7.3 had some delay and it came after feature freez.

doesn't feisty use xserver 1.2?

---

### Post by Elv13 on 2007-09-19
yea, you are right, but gutsy will not use 1.4, both use xorg7.2

---

### Post by Dhjiz on 2007-09-19
No input and output hotplug for Gutsy?

That's completely crap!


That was the best feature of Gutsy. Whatever, what's the URL of the discussion page of the wiki? There's someone who rewrite part of the page to add buggy command and remove useful commands.

---

### Post by psb6m on 2007-09-21
The alsa instructions in the wiki are not working for me. I get down as far as
```
sudo modprobe snd-hda-intel model=mbp3
```
and I get these errors:
```
FATAL: Error inserting snd (/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```
The output from dmesg is extensive; it says among other things "Unknown parameter `model'."

It is not at all clear what (if anything) is being done with the alsa-kernel source that I've downloaded. Can anyone supply more detailed instructions, or some troubleshooting?

Thanks

Peter

---

### Post by Black Mage on 2007-09-21
Is that the full error message?

And did you restart it? I got similiar messages like that and couldn't figure out why nothing was working until I restarted my computer.

---

### Post by pepe# on 2007-09-21
> It is not at all clear what (if anything) is being done with the alsa-kernel source that I've downloaded.

configure in alsa-driver will search and find the alsa-kernel directory if you follow the steps. alsa won't compile without it.

> Can anyone supply more detailed instructions, or some troubleshooting?

The usual error is that people do not unload the old alsa modules. Make sure that your old modules are all deleted. Look for them in /lib/modules/$(uname -r)/kernel/.

'make install' should delete them but it seems ubuntu stores them somewhere else. when you got rid of them, make install again, depmod -a, modprobe snd_hda_intel.

---

### Post by psb6m on 2007-09-23
Just restarting the computer did it. Thanks!

---

### Post by idezmax on 2007-09-23
ok :KS

---

### Post by Dhjiz on 2007-09-24
Does anybody knows if it's possible to boot directly Windows by choosing the Windows icon in rEFIt?

Currently, I installed OS X, rEFIt, Vista and then Ubuntu.
There are three icons in rEFIt: OS X, Ubuntu and Windows.

OS X leads directly to MAC OS X, but Ubuntu or Windows is the same, it leads to GRUB, and in GRUB I can choose between Ubuntu or Vista.

But I would like the Vista icon to launch Windows directly. Do you know if it's possible, and how to do it?

Thanks.

---

### Post by Elv13 on 2007-09-24
rEFI is not a perfect solution yet, theire is no way to really control it.

---

### Post by pepe# on 2007-09-24
> Does anybody knows if it's possible to boot directly Windows by choosing
> the Windows icon in rEFIt?

It should just work. I installed Windows into the last partition, then Linux in between and everything was fine.

Maybe you installed grub to the wrong partition once? You can verify by browsing(man strings) the first bytes of the partition, it will contain strings like GRUB or NTLDR. You could try the recovery mode to recover the windows boot loader, or try fixing the mbr.

I don't think the mbr is of any use, but who knows. rEFIt should survive, just like it survived the original installation.

---

### Post by cyberdork33 on 2007-09-24
> **Dhjiz said:**
> Does anybody knows if it's possible to boot directly Windows by choosing the Windows icon in rEFIt?

Currently, I installed OS X, rEFIt, Vista and then Ubuntu.
There are three icons in rEFIt: OS X, Ubuntu and Windows.

OS X leads directly to MAC OS X, but Ubuntu or Windows is the same, it leads to GRUB, and in GRUB I can choose between Ubuntu or Vista.

But I would like the Vista icon to launch Windows directly. Do you know if it's possible, and how to do it?

Thanks.
Write the MBR code with Vista (see fixmbr), and then install grub to your Ubuntu partition. Right now, grub is in the MBR, and thus, it launches for both OS choices.

---

### Post by Dhjiz on 2007-09-28
Thanks very much for your answers

I didn't know it was possible to install GRUB on a partition and not in MBR.

I'll try what you said.

---

### Post by DeepB on 2007-10-02
hi, any snapshot for my AR5008 MacBook Pro Santa Rosa? ng-r2497 does not work in the long run, disconnect all the time.

---

### Post by chem on 2007-10-03
The sticky-post Apple Intel FAQ really needs a link to three things:

1.  a summary of this thread
2.  the new ubuntu SR MBP wiki page created somewhere in here
3.  pepe's SR MBP wiki page


blah.  This thread is so massive now!  haha.  Anyone tried gutsy-beta with all the latest apple firmware updates?

---

### Post by trouble1313 on 2007-10-05
DeepB, I'm still running Madwifi from 6/13/07.....none of the newer versions seem to work for me. No idea why.


I am running Gusty now and it seems fine in general. Everything seems good out of the box except for the wireless. 

-Trouble

---

### Post by pepe# on 2007-10-05
I've been using madwifi since months now, updated the modules whenever I felt like doing so. Actually pretty often as I played around a lot. Last time was today. Never had the driver NOT working.

Maybe try a make clean before make;make install. Make sure you're running the very kernel that you want to compile the modules for. Also note that 'make modules_install' for a vanilla kernel will delete all modules and install the vanilla ones.

---

### Post by trouble1313 on 2007-10-06
Ok Pepe, you chided me in to fixing things. It seems that for whatever reason, Madwifi 9.3.2 official still does not seem to work on this platform (at least for me). I hadn't gone back and tried a checkout figuring that since there's been 2 official releases since it worked in the repo snapshots that it must have been merged. Seems not to be the case. So I grabbed today's snapshot and viola...it's fine. Go figure.

-Trouble

---

### Post by Dhjiz on 2007-10-06
> **cyberdork33 said:**
> Write the MBR code with Vista (see fixmbr), and then install grub to your Ubuntu partition. Right now, grub is in the MBR, and thus, it launches for both OS choices.

Hi,

I did that and it worked perfectly.
I did sudo grub-install /dev/sda3 to install grub into the partition. Then I rebooted into the DVD of Windows Vista, I chose the REcovery mode and launched the command bootrec.exe /fixmbr to make Vista recover the MBR and remove Grub.

Now each icon leads to its OS.

After these days' updates, the sound stopped working so I reinstalled it following the method in the wiki, but I couldn't control the sound volume with the hotkeys (F3, F4 and F5).

I upgraded the version of pommed following the method in the wiki but I still can't get the hotkeys working for controling the sound.

Does anyone have an idea about this?

Thanks.

---

### Post by lv1001 on 2007-10-06
I did not have any issues with any updates regarding sound. It just works out of the box wih gutsy.
However with any one of the updates the during the last week (don't know which), the keyboard backlight stopped working...
Reinstalling pommed did not do the trick.
Anyone had something similar?

LV

---

### Post by lv1001 on 2007-10-07
I am sitting out in the sun right now without access to my wlan using ubuntu.
I gave it a try and started MacOSX and guess what: Full connection!!! And even seing the neighbours wlan. Why is it that the wlan works that much better with MacOSX?
Don't care that much though, sunny days are rather rare here in northern germany and i can reach the wlan from everywhere inside the house.

BTW: Does anyone know where I can download the tickless kernel-patch for 64-bit? it is not included in gutsy and I did not find it searching the web.

LV

---

### Post by dasein on 2007-10-09
I'm also having problems with the madwifi drivers. They work but not so well after I updated gusty to the latest packages.

1) The madwifi drivers do not have the same signal strength as one would be lead to believe by the OS X indicator. I guess this could be just a difference in reporting the value and the network manager in gusty is just more sensitive. 

2) The madwifi drivers do not allow setting the modulation manually through iwconfig. If you do 'iwlist modulation', it reports that there are no configuratiions available for ath0. Also I know that my wireless router only supports 802.11b and when I am connected it reports 802.11g which I guess is a problem with the development driver.

3) This is the biggest problem. I can only remain connected for a few minutes before I lose my IP address. This occurred after I updated gusty and rebuilt madwifi drivers for the new kernel. Basically network manager continues to report being connected but ifconfig reports no IP address for the wifi0 or ath0 and any attempt to use 'ping' reports 'network unreachable.' I then tried to manually configure the madwifi drivers using 'iwconfig essid blah key blah' which seems to work and then I attempt to renew my IP address from the DHCP server using 'dhclient ath0' which invariably fails. The only way at that point that I've been able to reconnect is to restart my computer which only again allows me to stay connected for a few minutes.

Any suggestions for mainly problem 3 would be greatly appreciated!

---

### Post by Dhjiz on 2007-10-18
So now that Gutsy is out, should I remove all the parts that concerns feisty in the wiki page of the macbookpro santa rosa and just remaine the gutsy-related information ?

---

### Post by alephsmith on 2007-10-19
Most of that page is now unecessary.

From my installations from RC1 only wifi and SuperDrive needed any prodding to work.

Has anyone installed fresh from an 7.10 final image?

---

### Post by epaulin on 2007-10-19
Is there anyone got microphone works? 

I tested on skype and sound recorder, all I got is crazy noise.

---

### Post by dremon on 2007-10-19
SuperDrive worked for me out of the box since Gutsy beta, I didn't do any additional modprobing. The only things I've installed are pommed and wifi. BTW, madwifi has a 1-year old bug (see [here]("http://madwifi.org/ticket/1017")), still unsolved, which perodically hangs the Atheros card with rx overrun error. Might be a hardware issue as well.

Microphone works fine, also in Skype.

You can control the microphone volume with "Digital" slider on the "Recording" tab in the Volume Control applet. Also "Mic Boost" slider can be helpful.

My system: MBP3, Gutsy AMD64.

---

### Post by epaulin on 2007-10-19
dremon:
microphone works after I turn on digital and change Input source back to "Mic", tnx.
I also have SuperDrive works out of box.
About the bug related to madwifi, use can set "iwpriv ath0 bgscan 0" then everything works sweet.

---

### Post by Elv13 on 2007-10-19
New NVIDIA driver, i hope that it will fixe the bug when switching from X11 to console 3 time.

EDIT: NVIDIA... sorry, i have 2 computer and i said the wrong vendor (my other have an ATI)

---

### Post by russell.h on 2007-10-19
AMD driver for what? As far as I know there are no AMD components in an SR MBP.

---

### Post by DrCR on 2007-10-19
> **Dhjiz said:**
> So now that Gutsy is out, should I remove all the parts that concerns feisty in the wiki page of the macbookpro santa rosa and just remaine the gutsy-related information ? 	
Yes, I think we definitely should. At any rate, here's a new thread created for 7.10 Santa Rosa MBP discussion: [Macbook Pro- Santa Rosa - 7.10 Gold](http://ubuntuforums.org/showthread.php?p=3575824). Keeping all the relevant info together for a particular version is a real boon to new users.


My comments:
Just install the x86 version, Desktop LiveCD version to [my MBRed setup](http://www.linuxforums.org/forum/installation/105234-howto-osx-winxp-vista-grub-hiding-linux-one-hard-drive.html).

Right-Click -- I've found a three-finger tap to work for right-clicking. Neither three nor two for scrolling however.

Touchpad -- Highly sensitive such that when the palm of my hand occasinally touches the touchpad while typing the OS registers it as a single-click. (Happend a few times while typing this post).
Laptop Cooks Itself. -- Anyone know a [smcFanControl](http://www.macupdate.com/info.php/id/23049) equivalent for Linux and/or Windows?! Blame rests squarely on Apple's shoulders. Either open up the firmware, or do a proper job (open preferred lol).


DrCR

___________________
[SIZE="2"]MacBook Pro Santa Rosa, 2.2GHz, 250GB Scorpio, Ceramique compound
Pending: Tux Logo mod
OSX, WinXP, Vista (MSDN), Vector 5.8 SOHO, Sidux 2007-03
Pending Fusion "bootcamps" pointing to native OS installs[/SIZE]

---

### Post by pepe# on 2007-10-21
> Right-Click -- I've found a three-finger tap to work for right-clicking. 
> Neither three nor two for scrolling however.

Two-finger-scrolling works nice here, as does edge-scrolling, two/three-finger tapping etc. Corner buttons seem not very reliable.

> when the palm of my hand occasinally touches the touchpad while typing the
> OS registers it as a single-click.

I use syndaemon to deaktivate touchpad taps when the keyboard is in use. It doesn't quite seem to work right know, maybe because of S2RAM...  Don't forget to GrabEventDevice and man synaptics.

> Laptop Cooks Itself

I'm happy with the default setting here. Sometimes I enable the fans because my skin doesn't like warm surface, but in general the laptop is idle and cold. And I mean cold, I warm it up with my palms. You can set a higher minimum fan speed via /sys/class/hwmon/ when you applied the applesmc patches from mactel-linux. I think the applesmc-driver is also in vanilla linux by now.

---

### Post by Corpus_CT on 2007-10-26
> **l3th0x said:**
> Hi,

New  100.14.19 nvidia display driver is out, and it works! (without patch, I mean).

Regards..

What Ubuntu release are you using?

I'm on Gutsy i386, and whenever I install the 100.14.19 nvidea driver, Ubuntu boots in low graphics mode and madwifi is broken. I have to [FONT="Courier New"]madwifi-unload[/FONT], re-build and re-install madwifi and finally re-probe the [FONT="Courier New"]ath_pci[/FONT] mod to get wifi working again.

I've achieved some success using the nvidea-glx-new driver in that I can play Counter-Strike 1.6 in wine, but Source games such as CSS and Team Fortress 2 crash whenever they begin to actually render (ie. once a server has loaded).

---

### Post by holr on 2007-10-31
I have tried compiling the 2.6.23 kernel with mactel patches and can boot into the new kernel fine. However, the latest nvidia driver (100.14.19) installs fine but I keep getting the low-res option when I boot into it. Any ideas? The same happens with the default kernel when I tried compiling the nvidia driver, it works fine with the nvidia-glx-new though, problem is, without the 2.6.23 kernel, my p1i phone doesnt work well so I needed the new kernel with updated patches.

---

### Post by Chrisj303 on 2007-10-31
Sorry if this has been answered before - but I have read through this entire thread and have found it extremely confusing !

I have a new MBP santa rosa. I would like to install gutsy to a partition on it.

All I need to know is this;

Will my graphics card work out-of-the-box with the 64bit Gutsy (final release) ?

And;

Is the edited first post in this thread still relevant? esp. the first 2 points. - can I still not install via a 32 or 64bit Live CD ?


Thanks in advance for any help!

chris

---

### Post by cyberdork33 on 2007-10-31
[https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa)

---

### Post by Chrisj303 on 2007-10-31
Aah, thanks a lot!

---

### Post by lv1001 on 2007-11-05
The latest madwifi svn snapshot (rev. 2826) is broken for me. System freezes on connection.
Does anyone else experience this?
Also, I am effected by [this]("http://madwifi.org/ticket/1017") problem.
Again, am I the only one?

Thanks,
  LV

---

### Post by cyberdork33 on 2007-11-05
> **lv1001 said:**
> The latest madwifi svn snapshot (rev. 2826) is broken for me. System freezes on connection.
Does anyone else experience this?
Also, I am effected by [this]("http://madwifi.org/ticket/1017") problem.
Again, am I the only one?

Thanks,
  LV
The svn versions break every once in awhile. They have before as well. Try an older revision.

In the Santa Rosa wiki page there is a (temp) fix for the bug you linked to.
[https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa)

---

### Post by lv1001 on 2007-11-05
The connection seems to last longer with "iwpriv ath0 bgscan 0" but it still breaks from time to time.
BTW: It says in the wiki-page to put this line _after_ "exit 0". Isn't it useless then?

LV

---

### Post by cyberdork33 on 2007-11-05
> **lv1001 said:**
> The connection seems to last longer with "iwpriv ath0 bgscan 0" but it still breaks from time to time.
BTW: It says in the wiki-page to put this line _after_ "exit 0". Isn't it useless then?

LV
yes. it should go before.

---

### Post by hardawayd on 2007-12-05
I just got my MBP and have tried with no success to install Ubuntu 7.10 using both the live cd-64 and the alternate 7.10 cd-64.  During the installation it keeps indicating corrupt file error messages for some of the files and at the end of the base installation it says it failed.  Have no idea what the problem is.

---

### Post by hardawayd on 2007-12-05
Nevermind. Got it working.  Now have to figure out how to get the bluetooth mouse working.

---

### Post by cyberdork33 on 2007-12-05
> **hardawayd said:**
> I just got my MBP and have tried with no success to install Ubuntu 7.10 using both the live cd-64 and the alternate 7.10 cd-64.  During the installation it keeps indicating corrupt file error messages for some of the files and at the end of the base installation it says it failed.  Have no idea what the problem is.

Please do not post in multiple locations.

> **hardawayd said:**
> Nevermind. Got it working.  Now have to figure out how to get the bluetooth mouse working.

There is a Bluetooth How To in the FAQ.

---

### Post by dremon on 2008-03-21
Might be interesting to other MacBook Pro users.

Because there are no stable drivers for the Atheros AR5418 yet, I've replaced it with Intel 4965AGN which is well-supported and included in the 2.6.24 kernel (Hardy).
The detailed guide for replacing miniPCI-e adapter can be found at [http://www.ifixit.com/Guide/Mac/MacBook-Pro-15-Inch-Core-2-Duo/115](http://www.ifixit.com/Guide/Mac/MacBook-Pro-15-Inch-Core-2-Duo/115)

The whole process was very simple and fast, the new adapter worked immediately out of the box, no problems so far.

The only disadvantage is that there are no drivers for Mac OS X, however I only use it for firmware updates so it was not an issue for me.

When Atheros will release a stable driver for Linux or Madwifi will mature into something usable, I will replace it back perhaps. For now I had too many troubles with it - random disconnects, unstable data stream, etc.

---

### Post by sunbird on 2008-03-27
Hi all,

I've read through this thread several times and still can't seem to figure out how to get madwifi working. I've tried installing using the instructions on the Macbook Pro wiki page, but no go. 

I'd like to try installing the driver from 6/13/07 that some say works, but I'm such a noob that I don't know how... looked on madwifi page and can't find the link. Could someone point me to it? Or provide instructions to make it work?

**FOUND IT:** All snapshots are [here]("http://snapshots.madwifi.org/madwifi-ng/") and the 6/13/07 snapshot is [here.]("http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2438-20070613.tar.gz")

Build 2438 works for me. So glad to be unplugged finally!

---

### Post by pijon on 2008-04-08
I'm having trouble with the restricted nvidia-drivers on my macbookpro (4,1). Some pixels are dead and ubuntu usually crashes within 10-15 minutes. Is there any solution to this problem?

---

### Post by sunbird on 2008-04-08
> **pijon said:**
> I'm having trouble with the restricted nvidia-drivers on my macbookpro (4,1). Some pixels are dead and ubuntu usually crashes within 10-15 minutes. Is there any solution to this problem?

Hi pijon,

you might check out [this thread]("http://ubuntuforums.org/showthread.php?t=717345&highlight=4th") or [this one]("http://ubuntuforums.org/showthread.php?t=720936&highlight=4th") instead... actually, I just looked there and no help on the video driver issue. What card do you have? Mine is a GeForce 8600M GT. This thread is for Macbook Pro 3,1, I'm not sure that the card is the same for v. 4.1 (though it might be). 

For me, I had trouble getting it to work until I used [Envy]("http://www.albertomilone.com/nvidia_scripts1.html"), but that script worked fine and my display is now working perfectly.

---

### Post by pijon on 2008-04-09
Thanks sunbird! Envy fixed the problem with the nvidia-card (8600 GT). :)

---

