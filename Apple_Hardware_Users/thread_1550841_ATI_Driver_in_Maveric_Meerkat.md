---
title: "ATI Driver in Maveric Meerkat?"
date: 2010-08-11
forum: Apple Hardware Users
---

### Post by chillyperson23 on 2010-08-11
I have an iMac 27 inch from late 2009 

I've been trying to get the ATI driver to work in 10.10 When i go to hardware drivers, it says "checking for availible drivers" then it has the ATI driver shown, but when i click download, it stops and a box shows up that says "SystemError: installArchives() failed" 


Then i downloaded the driver from ATI's site. i set it as executable, and ran it, and it didnt work. So i ran it again and chose the option, "Generate distribution specific driver package" and it says "errors were found" and tells me where the log is. 

This is the log when choosing Ubuntu maveric


Package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 385: dpkg-buildpackage: not found
./packages/Ubuntu/ati-packager.sh: 385: dpkg-buildpackage: not found
[Error] Generate Package - error generating package : Ubuntu/maverick


This is the original log when just installing normally. during installation it seems to hang at "Postprocessing kernel module


Errors during DKMS module removal
Errors during DKMS module removal

Creating symlink /var/lib/dkms/fglrx/8.753/source ->
                 /usr/src/fglrx-8.753

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
cd /var/lib/dkms/fglrx/8.753/build; sh make.sh --nohints --uname_r=2.6.35-14-generic --norootcheck.....
cleaning build area....

DKMS: build Completed.

fglrx.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.35-14-generic/updates/dkms/

depmod....

DKMS: install Completed.
[Message] Kernel Module : update-initramfs for current kernel version.
[Message] Kernel Module : update-initramfs for latest kernel version.








Has anyone had this problem and fixed it?

---

### Post by chillyperson23 on 2010-08-11
Needless to say it doesnt work. Black screen on boot unless i change "quiet=splash" to "nomodeset" in grub

---

### Post by meborc on 2010-09-03
ATI HD 4850 works ok with 10.10 beta, but the ATI proprietary driver fails to install :(

---

### Post by altonbr on 2010-09-04
Did you get the proprietary ati driver to install in Maverick? It doesn't show up in jockey for me.

I don't think it's recommended to install straight from the ATI/AMD website: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)

---

### Post by P4man on 2010-09-05
Similar problem here. Just installed 10.10 beta, jockey isnt even offering drivers for my ATI 4870. I downloaded the drivers from ati site, but they wont install. I tried generating the packages for maverick, but those packages refuse to install as well. 

So Im stuck with the OSS driver (which is not really an option for me because they still lack powermanagement features and make my machine way too noisy).

---

### Post by splater on 2010-09-09
Same thing here with my ATI HD 4300 ...

---

### Post by akshar_patel_47 on 2010-09-10
I'm having the same problem... the additional drivers utility is not finding my ATI proprietary drivers..

---

### Post by OldGaf on 2010-09-12
> **akshar_patel_47 said:**
> I'm having the same problem... the additional drivers utility is not finding my ATI proprietary drivers..

same here....

Kinfocenter see's the card correctly:
Mobility Radeon HD 4200

jockey isn't even offering drivers.

I am doing this on my new Aspire One 721-3574.
The driver worked on 10.04.1 but the network cards were not working.
Trying 10.10 and network cards work but not the video drivers.

All work on openSUSE 11.3

---

### Post by altonbr on 2010-09-12
Everyone, it has something to do with xorg-server being at 1.9 and the proprietary drivers haven't caught up yet. Better stick with either open source drivers or Ubuntu 10.04 Lucid Lynx if 3D support is important to you.

---

### Post by P4man on 2010-09-13
> Everyone, it has something to do with xorg-server being at 1.9 and the proprietary drivers haven't caught up yet. 

You are probably right. However,ATI's release note state the drivers work with:

> XOrg 6.8, 6.9, 7.0, 7.1, 7.2, 7.3, 7.4 or 7.5 

Just curious, how does that relate to the versioning you see elsewhere, like xorg 1.8,  1.9 ?

Also, I saw this article on phoronix:

> 
Upgrading to 1.9 from 1.8 breaks both the graphics and input drivers ABI, which will require all of Ubuntu's X.Org drivers to be rebuilt as they will not otherwise function when the xorg-server 1.9 push occurs. NVIDIA's binary driver is compatible with X.Org Server 1.9 and ATI's Catalyst driver that is usually months behind in supporting X.Org Server updates should actually work with the 1.9 release at this point. 
[http://www.phoronix.com/scan.php?page=news_item&px=ODQ4Ng](http://www.phoronix.com/scan.php?page=news_item&px=ODQ4Ng)

I guess they got it wrong. While the installer clearly has provisions to build for maverick, it just doesnt work at this point. Oh well. Its ATI, so what else is new..

---

### Post by altonbr on 2010-09-13
For Ubuntu 10.10 Maverick Meerkat, X.Org is 7.5 while X.Org Server is 1.9. As you said, the new version breaks ABI from 1.8 to 1.9 and ATI simply hasn't caught up.

See the table on Wikipedia that I take care of: [https://secure.wikimedia.org/wikipedia/en/wiki/Ubuntu_releases#Version_history_of_common_programs](https://secure.wikimedia.org/wikipedia/en/wiki/Ubuntu_releases#Version_history_of_common_programs)

---

### Post by lucianct on 2010-09-13
I have the same card as OldGaf (mobility radeon hd4200). I tried to use the drivers provided by ati (apparently they were recently updated to support maverick too) but that didn't work out very well. I managed to install fglrx but it crashes on startup. Any ideas?

---

### Post by kimsmarkin on 2010-09-14
Window Management: Unminimizing, Maximalise, thorough investigation, resizing windows and window switching (Alt + Tab) is substantially the picture freezes for about 1 second. Your mileage may vary.

---

### Post by P4man on 2010-09-14
> **lucianct said:**
> I have the same card as OldGaf (mobility radeon hd4200). I tried to use the drivers provided by ati (apparently they were recently updated to support maverick too) but that didn't work out very well. I managed to install fglrx but it crashes on startup. Any ideas?

Yeah, wait for a driver that works and stick with the open driver for now (or 10.04)

---

### Post by workage on 2010-09-17
*EDIT: Just realized this is topic is for Apple users, disregard at your discretion.*

Same issue here, I even added the x-org experimental ppa and used their FGLRX package, I just get a console... so I ran aticonfig --initial. No change at reboot, so uninstalled fglrx and deleted xorg.conf, it didn't make a backup so I let it re-create. Back in business but wish I could use the latest video driver.  Haven't attempted sudo sh ./atiinstaller yet however.

---

### Post by niM_xaM on 2010-10-12
Hi Guys,

I've been having problems since I upgraded to 10.10 from 10.04. I have ATI HD 3XXX card and in Meerkat, I would suddenly get a distorted display followed by total system freeze. This can strike at any time and during seemingly any kind of activity .. browsing / playing media / working on office / even when typing commands at the terminal .. Its just like the infamous "Blue Screen of Death" in that other OS..

Everything was fine in 10.04 though..

So I purged fglrx and restarted X .. 
and proceeded to downloading latest driver from AMD version 10.9 but when I run it, I get the following error message: 

```

root@Dave-HOME:/home/david# ./ati-driver-installer-10-9-x86.x86_64.run
Created directory fglrx-install.eRItKv
Verifying archive integrity... All good.
Uncompressing ATI Catalyst(TM) Proprietary Driver-8.771.............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 ATI Technologies Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.35-22-generic-pae:; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.eRItKv

```Does anyone have any idea what went wrong? or how to fix it?

I know that there may be a possibility that the ATI prop driver hasnt caught up yet but I'm pretty sure I've read in more than one place that this version of driver (v10.9) supports Meerkat ... 

Anyone having the same problem? All help is much appreciated.

niM_xaM

---

### Post by Ozzmoziz on 2010-10-17
Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.35-22-generic:; make sure that the version is being
correctly set by --iscurrentdistro




Same problem - ATI Radeon HD 3600 Series

---

### Post by P4man on 2010-10-17
The ones on AMD site havent been packaged for maverick. You can create your own packages from that installer, but its a pointless exercise since the one proposed by jockey ("additional drivers") is the same 10.9 version . which btw, works fine now on my 4870. 10.10 should be out any moment now. Catayst 10.10 that is. Judging by the name that will have to work great on maverick ;)

---

