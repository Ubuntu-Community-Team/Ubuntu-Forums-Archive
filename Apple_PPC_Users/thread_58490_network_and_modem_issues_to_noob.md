---
title: "network and modem issues to noob"
date: 2005-08-20
forum: Apple PPC Users
---

### Post by ubuntubrian on 2005-08-20
I installed hoary onto my Tibook after repartitioning with iPartition (luckily no problems and all my data safe and sound!). During the install I responded to the network setups using defaults. In the early stages the installer detected Airport but I don't know about my modem. The upshot is that now ubuntu does not find my modem port, and I have no idea which port it is, nor my Airport and DHCP. I presume I can configure these in Hoary but have no idea of how to do so. Can anyone provide idiot proof help? Much appreciated!

---

### Post by ubuntubrian on 2005-08-20
Additionally to my last post: when I run the Ubuntu Device database collection, I get past Audio Test, Video Test and mouse Test but the next, Network Test just sites there, not frozen but does nothing at all. Should I reinstall Hoary and enter info (of which I am ignorant) concerning the questiona about network, airport and DHCP?

---

### Post by pierba on 2005-08-20
Look here: [http://forums.gentoo.org/viewtopic-t-365647.html](http://forums.gentoo.org/viewtopic-t-365647.html)

Pietro

---

### Post by ubuntubrian on 2005-08-20
Thanks Pierba but I don't think it applies as I do not have airport extreme on my almost 3 year old TiBook. Essentially what I need to know is how to configure my network settings in ubuntu after it has been installed. Some install tutorials mention that "if you don't have a DHCP server or ethernet network you'll be given the chance to set up a PPP account"-this during installation of Hoary. I don't recall any questions regarding PPP. On OS X I set up my network settings after the OS installed. Can I do this with Ubuntu or do I need to reinstall it and try to set up my PPP settings during installation?

---

### Post by ubuntubrian on 2005-08-20
After much checking on the net I think that my modem is not recognized period. It's a HCF USB modem model 'microdash'. I get an error when I 'sudo pon' after running the pppconfig utility: unrecognized option '/dev/modem'
I checked out Linmodem support but that is all windows as far as I can tell. I wish one of those people who wrote to this forum things like, "I install Hoary onto my TiBook G4 and everything worked immediately and I'm posting this from Firefox right now!!" would reply and let me know what modem they had.
Helppppp!

---

### Post by Hairy_Palms on 2005-08-20
i personally dont like mac OS (9 or X) and i think mac hardwares ugly as hell but i wont hold that against you ;) try the drivers from the website below youll want the debian package and follow the instructions not the autoinstall.run tell us how you get on :)
[http://www.linuxant.com/drivers/hcf/index.php?PHPSESSID=c71df39058823d950ddfe7b512b6c27b](http://www.linuxant.com/drivers/hcf/index.php?PHPSESSID=c71df39058823d950ddfe7b512b6c27b)

---

### Post by ubuntubrian on 2005-08-21
Thanks, even though you must use wintel boxes, but I forgive you! The only Debian version of the driver is listed as for x86 architecture but I'll give it a go. There is another for ppc architecture which I'll download too. As these are drivers for linux maybe the ppc version is correct?

---

### Post by ubuntubrian on 2005-08-22
To update: I downloaded both the .deb file and the ppc file. The .deb file would not install as the architecture was wrong, x386. I tried to install the ppc version as described in the instructions. I get an error when I try 'make install', 'NO RULE TO MAKE TARGET `inf/HCFCTY.mst', needed by `inf/hcbusb.cty'
I have absolutely no idea what this means at all or how to proceed. Any help?

---

### Post by Ptero-4 on 2005-08-22
[QUOTE=ubuntubrian]To update: I downloaded both the .deb file and the ppc file. The .deb file would not install as the architecture was wrong, x386. I tried to install the ppc version as described in the instructions. I get an error when I try 'make install', 'NO RULE TO MAKE TARGET `inf/HCFCTY.mst', needed by `inf/hcbusb.cty'
I have absolutely no idea what this means at all or how to proceed. Any help?[/QUOTE]
 The ppc version is a source code and you need to compile it. Do you have the dev packages (they're on the CD)? and have you typed ./configure in the directory containing the drivers? If so did it show errors? If not did you typed make afterwards? did it stopped with errors?

P.d: I asked all of that b/c one of the most common issues new users have when installing drivers, especially winmodem drivers, is that they come as uncompiled source code and when the user tries to compile the drivers the user often overlooks the output of the steps he followed and if there were errors in one step those errors are not obvious but break bad in the last step and when that happens it tends to be very difficult to track where the problems began.

---

### Post by ubuntubrian on 2005-08-22
I got the install instructions off of the conexant site and ran 'make install', which ultimately worked. I then ran 'hcfusbconfigure' and discovered that I needed to install the kernel headers as described, so I did. That install went fine. I ran the config command again and this time Ubuntu completely froze after I got an error message that "no hcfusbmodem device found". I restart and I get a lockup again right after the boot starts and lines regarding the "hcfusbmodem". Here's as far as the boot gets just before a line loading the gnome-manager. Here is the reference:
/usb/lib/hcfusbmodem/modules/osusb.c:UsbControlCompletionRoutine:error:URB status -110, req=5, index=0, value=0".
I tried the rescue mode off the install cd but got lost when asked which disk to install to. I am not trying to reinstall-yet.
Of course I can't do anything in Ubuntu as it won't boot.

---

### Post by ubuntubrian on 2005-08-23
After many emails to linuxant support it turns out that they are aware of serious issues, like system freezes, connected with the installation of their HCFUSB modem driver for PPC. After much checking it seems that this was an issue with Warty Warthog also so it has been unresolved for about a year. I voiced my discontent but they say they have no idea when they will resolve the issue. I will uninstall the driver and if anyone can help me with how to do that , I'd appreciate. Assuming that I can boot into Ubuntu (about 1 out of 5 trys results in booting up).

---

### Post by ubuntubrian on 2005-08-24
And to add to the complexity of installing headers, etc., I get a:
"WARNING: missing file /usr/src/linux/include/linux/autoconf.h
The cause of this is usually a missing or unconfigured
kernel source tree (and sometimes an incorrect directory or symbolic link).

First, ensure that the proper kernel source and compiler packages
from your distribution vendor and/or the community are installed.

The Linux kernel can then be reconfigured by running "make menuconfig"
under the kernel source directory (usually /usr/src/linux).

Verify that the proper options for your system are selected.

Then compile and install your new kernel (for more information about
this procedure, see the README file under the kernel source directory),
reboot the system using the new kernel, and re-run "hsfconfig".
dpkg: error processing hsfmodem (--install):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
hsfmodem"
can anyone tell me why the Ubuntu install would not create these files? It seems as if users are having a myriad of problems surrounding this issue and that it requires downloading and compiling and installing new kernels and patches. This is nuts and really makes me appreciate OS X. I want to support Linux and Open source but for god's sake scotty!

---

### Post by ubuntubrian on 2005-08-29
I thought that I should close out this thread with the info that:
the conexant modem driver for ppc is not source code and does not need, nor can it be, compiled. It is a straight install. The bad news is that conexant knows that this driver can freeze entire systems if instaqlled and they have no work around or idea of when or how to fix it. Now that's service! Glad I didn't buy the license first!

---

