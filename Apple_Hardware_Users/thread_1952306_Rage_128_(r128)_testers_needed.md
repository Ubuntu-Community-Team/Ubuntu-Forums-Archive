---
title: "Rage 128 (r128) testers needed"
date: 2012-04-04
forum: Apple Hardware Users
---

### Post by tormod on 2012-04-04
Hi, I am looking for someone with an r128 graphic card who would be willing to test the patch I posted in [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=622606#15]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=622606#15")

The patch should prevent the driver from crashing when run without an xorg.conf, although it won't come up with the optimal resolution or anything.

On the longer term I would like to help getting more of these old Macs work out-of-the-box but I would need access to the hardware (I have a PowerBook G4 with Radeon R100-family card myself) or people willing to test and report. For now there are so many workarounds and tricks it is insane.

How to apply a patch:
```
sudo apt-get build-dep xserver-xorg-video-r128
apt-get source xserver-xorg-video-r128
cd xserver-xorg-video-r128-*
patch -p1 < $HOME/Downloads/patch-to-be-tested.patch
# please make sure the patch command did not fail before continuing
debuild -b -us -uc
cd ..
sudo dpkg -i xserver-xorg-video-r128_*.deb
```
You will then have to restart X (log out and in again) or, depending on login manager etc, you may have to switch to a text console and run e.g. "sudo restart lightdm".
Make sure you test this without any xorg.conf file!
In your report please attach Xorg.0.log files from both with and without the patch.

---

### Post by linuxopjemac on 2012-04-04
Thanks for this. I added a link to this post in the MintPPC forums as well.

---

### Post by theos911 on 2012-04-04
Should I try this on my Powermac G3 Blue & White or my Powerbook G3 Wallstreet? (Both have a r128, but I am limited on time and want to use whichever would be more helpful to you.)

IIRC, both of these machines needed:
```
Option "NoAccel" "true"
```in their conf file or they would fail to start x.

---

### Post by tormod on 2012-04-04
> **theos911 said:**
> Should I try this on my Powermac G3 Blue & White or my Powerbook G3 Wallstreet? (Both have a r128, but I am limited on time and want to use whichever would be more helpful to you.)

IIRC, both of these machines needed:
```
Option "NoAccel" "true"
```in their conf file or they would fail to start x.

OK, in that case the "accel" bug will most likely mask the bug I wanted to fix, and an xorg.conf and tweaking will be needed anyway. So let's leave it for now so we don't waste our time, but thanks a lot anyway for offering to test. Is this on Ubuntu 12.04 and is there a bug report for it?

linuxopjemac, thanks for posting this to the MintPPC forum. Seeing that MintPPC is closer to Debian, it makes more sense as well since I am not even sure the SIGBUS bug is seen on Ubuntu. But now you reported there that you don't need any xorg.conf? Can you please post your Xorg.0.log (in either forum)?

---

### Post by rsavage on 2012-04-04
In Ubuntu/Lubuntu 12.04 you don't have 3d hardware acceleration anymore (it will be the same in MintPPC 11).  The code has been removed from Mesa for a lot of old cards.  

So in the past using DRI caused lockups with the r128 and AIGLX, and this is one of the reasons why people had to edit xorg.conf files.  In new versions you shouldn't have this problem.

I think I am correct in saying the Sigbus error was caused when people used the option UseFBDev false?  This is not the default value for PowerPC.  The default is UseFBDev true.

People used UseFBDev false when the correct framebuffer was not loaded.  From what I gather, sometimes the openfirmware framebuffer does not like to release control.  In debian you should be able to get the correct framebuffer loaded from the kernel command line (yaboot prompt).  In Ubuntu 11.04> it is a little more complicated, but explained in the FAQ.

---

### Post by linuxopjemac on 2012-04-04
ok, PowerBook G3 Pismo with MintPPC 11 / Debian Wheezy without xorg.conf:

3.2.0-2-powerpc

processor	: 0
cpu		: 740/750
temperature 	: 19-22 C (uncalibrated)
clock		: 400.000000MHz
revision	: 131.0 (pvr 0008 8300)
bogomips	: 49.93
timebase	: 24966218
platform	: PowerMac
model		: PowerBook3,1
machine		: PowerBook3,1
motherboard	: PowerBook3,1 MacRISC2 MacRISC Power Macintosh
detected as	: 70 (PowerBook Pismo)
pmac flags	: 0000001f
L2 cache	: 1024K unified
pmac-generation	: NewWorld
Memory		: 768 MB

0000:00:10.0 VGA compatible controller [0300]: ATI Technologies Inc Rage Mobility M3 AGP 2x [1002:4c46] (rev 02) (prog-if 00 [VGA controller])
	Subsystem: ATI Technologies Inc Rage Mobility M3 AGP 2x [1002:4c46]

---

### Post by tormod on 2012-04-04
rsavage, you're absolutely correct. The SIGBUS bug was only with UseFBDev false, and it is true by default for powerpc. So if there is no reason to use UseFBDev false, my patch has not much practical implications. So much for a bug fix trying to find a bug :) I'll go chasing some other bugs instead!

---

### Post by rsavage on 2012-04-05
Hi Tormod, I didn't mean for you to abandon your patch!  Not owning an r128 card I don't know the full story behind setting UseFBDev false.  It maybe useful for some people.

I don't know if we'll ever see framebuffers built again into Ubuntu kernels.  If not, the default UseFBDev true is always going to be a problem for people.

I think people should fallback to a low graphics setup, but for some reason this doesn't work for imac G3 users?  Maybe the necessary screen settings are outside the default ranges?  If you could investigate that then you'll make some lubuntu users happy!

---

### Post by tormod on 2012-04-06
Sure, I think the patch makes sense, it just seems not so critical for users at the moment so I can't justify people spending precious time on it. But if someone could test it (with Option "UseFBDev" "false" in their xorg.conf) I would appreciate it.

If there are some updated r128 bug reports with details and logs I can take a look.

I know there is the issue that the driver can not read out sync frequencies from the built-in panels, and thus defaults to low resolution unless the user specifies ranges in xorg.conf. At some point in time, the xserver got more careful with the default ranges, so this fallback resolution became more limited. I don't know if there is any way to get the correct parameters from the card or BIOS/openfirmware. The MacOS drivers can have hardcoded values depending on detection of laptop model for what I know.

Anyway, wrong default resolution is a minor issue compared to those where X does not come up at all so that the live CD is not usable. So if people experience this on 12.04 please file bug reports.

---

### Post by str8bs on 2012-07-11
Hi, don't know if this helpful as this is built in CRT model with HorizSync/VertRefresh required in xorg.conf. Lubuntu 3.2.0-23 with aty128fb added to /etc/modules and /etc/initramfs-tools/modules booting with ```
video=offb:off
```iMac G3 600Mhz Rage128 TR Ultra AGP 16M

Like an idiot, I forgot to save log before patch, but have included one from 3.2.0-25 without patch. I can re-test on either kernel if it helps.

FWIW, Options "UseFbdev" and "NoINT10" do not seem to effect this machine. Rather than "NoAccel", I have to either disable DRI or ForcePCIMode and acceleration (with old Mesa 7.11) works fine.

If you have any suggestions on getting these to work in AGP mode, I would greatly appreciate it. [http://ubuntuforums.org/showthread.php?t=2013307http://](http://ubuntuforums.org/showthread.php?t=2013307http://)

---

### Post by tormod on 2012-07-11
str8bs, thanks for the testing! There is just one combination missing, the unpatched driver with xorg.conf like WithXorgConfMonitorAndScreenFBdevFalse. If that combination fails, but it works with the patch, then we know the patch makes it *somewhat* better.

To reinstall the original driver, just run:
```
sudo apt-get install xserver-xorg-video-r128/precise
```

---

### Post by andersond on 2012-07-11
Well I have r128 on a PowerMac G4(desktop)and  got lots of trouble trying to install ubuntu since it uses new drivers and xorg.conf.

Until 5.04 it was OK

Between 7.x and 12.04 I could not run nothing. And tried lots of workarounds, between offb:off, setting up xorg.conf to useFBdev=false and/or NoInt10=true - dont remeber everything I tried - but I tried EVERYTHING ! - Just 5% of the woarkarounfs "worked", because opened the X, but very slow and freezing a lot, until system die.

After 12.10 Quantal it installed and ran ok, by default. It´s still very very slow, but I´m not sure if the reason is still the framebuffer issue or low performance MAC versus heavy OS - anyway now I am trying to install lubuntu on it and having other kind of problem during installation (I guess there´s nothing to do with the r128 video card this time, but who knows) - I posted a topic here: [http://ubuntuforums.org/showthread.php?t=2022972](http://ubuntuforums.org/showthread.php?t=2022972)

Once it´s intalled and running I will be glad to help with further and deeper testes within my box, in order to take advantage of 3d accel and everything .

Regards, Anderson

---

### Post by str8bs on 2012-07-11
tormod: Thanks for your efforts to make these R128 cards continue working for a living.
I redid the test in a more verbose way. The only time X failed to start was unpatched with UseFBDev False. Let me know if I missed something again.

Also, any use repeating test on another iMac g3 333 with Rage 128 Pro 6M ?

---

