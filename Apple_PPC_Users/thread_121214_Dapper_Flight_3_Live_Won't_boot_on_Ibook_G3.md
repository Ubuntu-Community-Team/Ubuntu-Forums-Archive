---
title: "Dapper Flight 3 Live Won't boot on Ibook G3"
date: 2006-01-24
forum: Apple PPC Users
---

### Post by Double Roller on 2006-01-24
Albeit I'm a bit of a newbie, I've been running Breezy on a clamshell ibook G3 1st revision (one usb, no firewire ) for awhile now. It is quick and very stable. I'm curious about the dapper build, especially X11 R7 since my graphics card should work with the next release, and as of yet, I've got meager 2d and no 3d and I'd prefer not to rebuild the entire drm because, yep, I'm a newbie. 

When attempting the Live CD Boot, yaboot sends me into Open Firmware and after giving "mac-boot" a try as led by the prompt, the following error message appears

Can't allocate initial device tree chunk

Default Catch! codmethod <draw-rectangle> not found ; ihandle=ff9cd580 phandle=ff893b60

I'm only running breezy on this machine. I'd be very interested in any suggestions anyone might have. (I've reburned the cd 6 times to double check)

---

### Post by cvmostert on 2006-02-14
I also have problems booting dapper on a dell 510m inspiron.... all the others boot well... 

will try on my other machine... 
ciao

---

### Post by ssam on 2006-02-14
if you have got the bandwidth you could download and try a daily
[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/) (they are dated YYYYMMDD).

you should probably file some bugs at [http://launchpad.net/malone](http://launchpad.net/malone)

---

### Post by Double Roller on 2006-02-22
[QUOTE=ssam]if you have got the bandwidth you could download and try a daily
[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/) (they are dated YYYYMMDD).

you should probably file some bugs at [http://launchpad.net/malone](http://launchpad.net/malone)[/QUOTE]


I appreciate the reply. I'm having the same problem now with Dapper Flight 4. As I said earlier, I'm running breezy on my clamshell ibook g3 300 now. It is super stable and I've had almost no problems. 

Dapper Flight 4 comes up with a slightly different error. but regardless, booting any and all of the kernel images on the ppc live cd break out from the boot process and send me to an Open Firmware prompt, at which point I've tried everything I can think of. Typing the suggested mac-boot prompt results in a DEFAULT CATCH!... telling open firmware where to find yaboot on the cd directly with "boot cd:,\install\yaboot" results in a CLAIM denied message. 

If you have any suggestions, or anyone out there has some knowledge of yaboot, or happens to have an ibook working with the Dapper drake live cd, I'd be very interested.

---

### Post by Double Roller on 2006-02-25
I filed a bug just a few days ago, who knows, maybe Ibook hackers around the world will unite, or I'll just have to accept that my little-engine-that-could- machine is obsolete at last.

---

### Post by rayhaque on 2006-04-27
I am getting this same error trying to boot my iBook Original with Dapper Drake 6.

Error reads as: Can't allocate initial device tree chunk

All I want to do is watch an mp4 video that I downloaded.  But it seems I need a new gstreamer (and new everything else to go with it).

I hope someone fixes this.  I would hate to think that the future powerpc releases won't work on my hardware.

---

### Post by markuspm on 2006-04-28
I see the identical problem on my clamshell ibook G3 1st revision (one usb, no firewire) .

When attempting to boot the Live CD Ubuntu 6.06 (built on 20060331), yaboot sends me into Open Firmware and an error message appears:

yaboot:
----------

boot: live
Please wait, loading kernel...
Elf32 kernel loaded...
Loading ramdisk...

Open Firmware:
---------------------

Can't allocate initial device-tree chunk
Apple Powerbook2,1 1.3f1 BootROM built on 10/28/99 at 18:10:16
Welcome to Open Firmware
 ok
0 >

---

### Post by rayhaque on 2006-04-29
I'm wondering if resetting the firmware would help (Apple+Option+P+R while booting).  But I know that would break yaboot, and I would have a useless system if Dapper still didn't boot up for installing.

Anyone have any ideas on this?

Developers: Is there something we can do to provide you some feedback?  What changed between Breezy and Dapper that might be causing this?

---

### Post by markuspm on 2006-04-30
> I'm wondering if resetting the firmware would help (Apple+Option+P+R while booting).

I don't think so. I can boot Breezy 5.10 still fine with my existing Open Firmware settings.
If you want to try anyway you could write down some of the settings first.
(Boot into Open Firmware holding Apple+Option+O+F while booting.)
On the prompt enter 'printenv' to show he current config.
Enter 'shut-down' to exit.
To repair any settings use e.g. 'setenv boot-command mac-boot'
My guess for now is that it might be a problem with the larger initrd in 6.06 than in 5.10?

---

### Post by mungewell on 2006-05-01
[QUOTE=markuspm]> 
My guess for now is that it might be a problem with the larger initrd in 6.06 than in 5.10?[/QUOTE]


Hi,
I'm seeing the same message running Xubuntu 6.06beta2 on an iMac 266/160MByte RAM. It's not the initrd....

Swaping the kernel image (/install/powerpc/vmlinux) with that from 5.10 progressess the boot a bit further showing the Xubuntu splashscreen - until it errors when it can't find the module tree (for 2.6.12-9) which is understandable.

I guess that there's a kernel issue on these older machines.
Simon.

---

### Post by MrMosier on 2006-05-03
I am seeing the same message as I try to boot from the Xubuntu Dapper Beta2 text installer cd and live cd on my G3 iMac (333mhz/64mb RAM). I have Xubuntu Breezy installed on it right now, so I am going to try removing all entries in /etc/at/sources.list, apt-cdrom add, and then apt-get dist-upgrade to see if I can at least get Dapper going. Has anyone submitted this bug, because I did not see it on the [http://launchpad.net/malone](http://launchpad.net/malone) site at all (the bug referring to the kernel problem seems to only effect 700-1000 mhz machines).

***UPDATE*** After installing the "server" version of Breezy, then using the text mode install of Xubuntu Dapper (Beta 2), Xubuntu is up and running fine on that 333mhz 64mb RAM iMac. Could the problem be just with the cd (I have restarted several times with no errors at all with the updated kernel)?

---

### Post by zjwagner on 2006-05-28
I am having this problem as well, on a G3 iMac, using an ISO that I downloaded today.  Im getting the same error:
 ```
Can't allocate inital device-tree chunk

Apple iMac Open Firmware 3.0.f2 built on 04/23/99 at 14:31:03
etc etc...

ok
0> 
```

the 0> allows me to type stuff, so maybe there is something at this promt I can type?  Any help would be appriciated.

---

### Post by nicolas314 on 2006-05-29
For what it's worth: Dapper does not boot on iMac G4 either.
(G4 800 MHz with 768M RAM)
Installation in graphics mode failed completely, I had to install
with Breezy then dist-upgrade and reboot to get through. I had
a fully working machine then... until next reboot where everything hangs
miserably after "initializing kernel". Fails pretty early, even the keyboard
does not respond.

I guess the PPC stuff is not yet up to par as far as testing is concerned...

---

### Post by fra.sa on 2006-05-31
hi all
same problem here tryng to upgrade xubuntu breezy to dapper on an imac g3 233 96mb ram.

Solved this way:
Before I ran the dist-upgrade I installed the official linux 2.6 powermac build from the ppckernel.org web site as an alternative kernel to boot from.
After the dist-upgrade finished I rebooted with the above mentioned kernel and the machine started.
Some functionalities were missing (because of the standard kernel) and so I recompiled a 2.6.16.18 vanilla kernel with the config from the dapper shipped kernel(2.6.15-23) and things went a bit better.
Still some tweaking to do but the most functionalities are there .

Things broken: ( but the system is usable)

pbbuttonsd doesn't start (/dev/pmu doesn' t exist)
device mapper problems (reported in kernel log)

(maybe the kernel need some patches that the ubuntu developers applied to the 2.6.15 one)

Hope helped someone.
francesco

 p.s. sorry my english

---

### Post by fra.sa on 2006-06-01
just tried my new compiled kernel (2.6.15 from dapper repositories) on my imac g3 233 with a hack suggested here :

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508")

now the system starts flawlessly!
bye
francesco

---

### Post by nkbj on 2006-06-01
Francesco: Was it the one-line code patch that did the trick?

---

### Post by fra.sa on 2006-06-01
yes, applied manually to the source!

---

### Post by maxillo on 2006-07-02
Any progress on this bug being fixed in the current kernel?

I installed Ubuntu 5.10 on a Imac G3 333Mhz, but would prefer Xubuntu.  I'm not quite sure how to apply the fix manually during a kernel compile.

cheers

Mike

---

### Post by nkbj on 2006-07-02
The fix is in the current Dapper kernel (2.6.15-25). It is not on the the released CDROM images.

---

### Post by phibxr on 2006-07-04
Wow, that sounds great! Time to return to Ubuntu from Gentoo/OS X land I suppose. :)

Edit: Back from installation and upgrading, and -- believe it or not -- it j u s t  w o r k s!

No bootsplash, which made me fear the worst when I recieved no information after the "Loading ramdisk..."-message, but what a shock it was when the GDM screen loaded up after a few moments. Yay!

(iMac/iLamp G4 700mhz)

---

### Post by maxillo on 2006-07-08
Great,

Now can you give me some pointers as to how I can slip the new kernal into an install CD, or perhaps upgrade my BB 5.10 Imac to the DD 6.06 with the new kernel?

cheers

---

### Post by AlphaMack on 2006-07-09
I would like to know this as well.  Are there plans to respin the ISOs from the May 31st build?

---

### Post by phibxr on 2006-07-16
I'd love to be able to install Dapper on my own and other G4 computers as well, without having to install Breezy first and then upgrade.

I know Ubuntu is supposed to be cleanly upgraded to the next release, but I'm still not too comfortable with upgrading and prefer having a clean install that I know will work no matter what further changes in the repositories are made.

---

### Post by RavenOfOdin on 2006-07-19
I have the same problem when trying to reinstall 6.06 on a hopelessly corrupted G3.

Sad, that Canonical or Ubuntu didn't see fit to include a low-resource text mode installer in the Live CD - since of course they wanted to combine the two.

---

### Post by conner_bw on 2006-07-25
I'm also having this " Can't allocate initial device-tree chunk" problem with the current Xubuntu and Ubuntu Server versions 6.06 [described here](http://www.ubuntuforums.org/showthread.php?t=221582), anyone know how to fix this without already having Ubuntu installed on the target machine?

---

### Post by ubuntu27 on 2006-07-25
> **RavenOfOdin said:**
> I have the same problem when trying to reinstall 6.06 on a hopelessly corrupted G3.

Sad, that Canonical or Ubuntu didn't see fit to include a low-resource text mode installer in the Live CD - since of course they wanted to combine the two.

Yes they have text mode.

Canonical/Ubuntu has decided to create TWO Disk. One which is called Desktop CD (Previously Live CD) and Alternate CD (Install CD).

What you want is the Alternate CD which install in text mode.

[http://www.ubuntu.com/download](http://www.ubuntu.com/download)



**Desktop CD**

The desktop CD allows you to try Ubuntu without changing your computer at all, and at your option to install it permanently later. You will need at least 192MB of RAM to install from this CD.

See the [release notes]("http://wiki.ubuntu.com/DapperReleaseNotes/UbiquityKnownIssues") for known issues installing from this CD. This image is not suitable for upgrading from previous releases; see the [upgrade instructions]("http://wiki.ubuntu.com/DapperUpgrades") for that.


**Alternate install CD**

The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * creating pre-configured OEM systems;
    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installing GRUB to a location other than the Master Boot Record;
    * installs on systems with less than about 192MB of RAM.

---

