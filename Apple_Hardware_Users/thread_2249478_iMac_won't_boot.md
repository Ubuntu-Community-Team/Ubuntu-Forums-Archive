---
title: "iMac won't boot"
date: 2014-10-22
forum: Apple Hardware Users
---

### Post by Ed_Reed on 2014-10-22
I can't get this iMac to boot to the live CD.  It is a iMac 4.1, 2 Ghz Intel Core Duo, with ATI Radeon X1600 video .  I tried the 32 bit, the 64 bit, and the 64 bit-AMD for MAcs.  Can anyone point me to the proper ISO image, none of these will boot. This is a fairly old iMac, probably around 2006-07 era.  
Thanks.

---

### Post by este.el.paz on 2014-10-25
> **Ed_Reed said:**
> I can't get this iMac to boot to the live CD.  It is a iMac 4.1, 2 Ghz Intel Core Duo, with ATI Radeon X1600 video .  I tried the 32 bit, the 64 bit, and the 64 bit-AMD for MAcs.  Can anyone point me to the proper ISO image, none of these will boot. This is a fairly old iMac, probably around 2006-07 era.  
Thanks.

You should be able to boot any of them . . . not necessarily only the "+mac" version, assuming that the iMac is 64 bit . . . so . . . question, did you check the md5sum number of the iso?  And, are you trying to boot USB or DVD?  How are you selecting the boot disk?  "c" key? or "option"??

Can you boot anything else like the OSX install disk?

e.e.p.

---

### Post by PartisanEntity on 2014-10-27
What happens when you try to boot from the live CD?

And what OS do you currently have installed on your iMac?

---

### Post by Ed_Reed on 2014-10-27
When I try to boot from the DVD, holding down the "c" key it spins a bit, but eventually goes into the Mac OSX (The version installed is 10.4) . After the Mac OSX boots, it says the disk is not readable. 

I've not tried to boot from a USB, nor have I tried the OSX disk .  



> **PartisanEntity said:**
> What happens when you try to boot from the live CD?

And what OS do you currently have installed on your iMac?

---

### Post by entangled on 2014-10-28
I have an iMac (21.5", 11,2, mid-2010) and it will not boot ubuntu from CD, DVD or USB stick (following ubuntu wiki). 
I use rEFInd, and each time the device is detected but it tells me there is no bootable media. 
ubuntu media (DVD or USB) is rejected in Finder as unreadable).
I have found that only the following live disks work and allow booting: 
Archboot, (media accepted in Finder, contains EFI folder, boots into text-based Arch for net install)
Fedora 19 (and probably 20, I don't have media any more)
Clonezilla (media accepted in Finder, contains EFI folder, boots into ubuntu saucy)
All other distributions fail with 'no bootable image'.

Many iMacs seem to be OK but your iMac may be the same as mine.
My theory is that the iMac is detecting only media with EFI folder, configured for EFI boot. By mounting the ubuntu iso in linux (running in a virtualbox image) I can see there is no EFI folder in the ubuntu iso.
The media that will not boot actually needs MBR, and that won't work on these iMacs.
Incidentally, I download from cdimage.ubuntu.com and it shows the iso, together with a list file and a manifest file. The list file shows /EFI/BOOT/ is on the disk. The manifest file does not show EFI anywhere. The actual file seems not to contain EFI either (but I'm downloading the vervet file now to check). It seems as if the /EFI/BOOT/ folder is intended to be on the image but it is not.

---

### Post by entangled on 2014-10-28
Have now tested vervet (kubuntu) live booting my iMac. It works.
The image contains the /EFI folder and I get proper booting into grub from the USB.
Someone must have corrected the problem in the most recent builds. 
If I can get sleep and resume to work I might switch to linux permanently (Yosemite is OK, looks a bit better than Mavericks but functionally the same).

---

### Post by Ed_Reed on 2014-10-29
Thank you for your help.  I'll try some of these other distro's to see if I can get it to work. 
 
For the vervet, did you use the AMD 64 or the Intel image?



> **entangled said:**
> Have now tested vervet (kubuntu) live booting my iMac. It works.
The image contains the /EFI folder and I get proper booting into grub from the USB.
Someone must have corrected the problem in the most recent builds. 
If I can get sleep and resume to work I might switch to linux permanently (Yosemite is OK, looks a bit better than Mavericks but functionally the same).

---

### Post by entangled on 2014-10-29
I used the AMD64 image, [http://cdimage.ubuntu.com/kubuntu/daily-live/current/vivid-desktop-amd64.iso](http://cdimage.ubuntu.com/kubuntu/daily-live/current/vivid-desktop-amd64.iso) written to USB as an iso (no need to convert) using the command:
sudo dd if=/Downloads/vivid-desktop-amd64.iso of=/dev/disk1 bs=1m
NB You need to know the identity of the disk for your outfile; mine was /dev/disk1, but yours could be different.

If you use rEFInd it might not detect the USB on first reboot, but just use Esc key (use wired keyboard and mouse; bluetooth will lose contact when ubuntu boots) to make rEFInd reload and it should detect several boot prospects.  I chose the first one to the right of OSX.

kubuntu behaved quite well booting from a USB stick, but I haven't gone as far as installing it.
Good luck.

---

