---
title: "Installing (K)ubuntu the hard way? (No CD)"
date: 2006-12-13
forum: Apple PPC Users
---

### Post by picoday on 2006-12-13
Question: (short version)

How do I install Kubuntu onto an old Mac Powerbook (Pizmo) which has no CD-Rom drive (it is broken)? I think it ought to be possible to do that via the Firewire (mounting Pizmo as target to another Mac. (I've previously succesfully installed OS X on it this way).

Another complication I need to work around is... I don't yet have a running Kubuntu (this is my very first try with anything Linux).

(Long version... my story of failure :)

I've been trying this for over a day now with little success. 

I'm completely new to Linux but have some (little) experience with using Unix (does Mac OS X count? :) and completely new to linux.

I tried:

First to just boot from the standar "Edgy 6.10 ppc desktop" CD on another mac I have. No luck to boot on my Powerbook G4 17 inch from year 2000 (not sure why) but booted nicely on my newer Powerbook G4 12 inch (which has no DVD/RW but just a CD R/W, not sure if that might be why it works). Anyway, I used the newer PB and mounted the "target" Pizmo as an external Firewire drive (hold down T key while booting). Then I proceeded to install from the one mac onto the target's drive. Seemed to work fine mostly, until the installer crashed (guess it got confused by installing onto /dev/sda). I tried booting it anyway, but... no luck.

Then I tried various ways to boot directly from the harddrive of the Pizmo. I followed the instructions from here

[https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/boot-drive-files.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/boot-drive-files.html)

I also read much of the other stuff in an and around there in the same guide. 

My first stumbling block... it says I need an HFS filesystem, but doesn't say how to make that? DiskUtility doesn't give it as an option. Some digging around I managed to create two HFS partitions on the drive and format them, by using hfs-utils from the other computer booted from the live-CD. For some reason the disks never seem to ever get bigger than 2Gb (limitation of HFS?). 

I installed all those files as said and booted as explained and... yes it does work. But the installer always gets stuck when its "scanning for .iso images" which it fails to find. The HD-install docs don't mention iso images. The USB stick method seems to use the same installer files and there it does mention .ISO images. 

It is rather vague on where to find images and where/how to place them on the drive though. The section on "where to find images" points to a place where there is exactly one image called "mini.iso" in net-boot. Moreover, I suspect that the files have to be renamed to "mini.ISO" for the scan to find em. Initially it didn't until I tried that. But even so, to no avail, it boots but then when those images are found it complains that it can't read from the cdrom? The installer doesn't proceed from there anymore. I also tried placing the original "live CD" .ISO image on there with pretty much the same end result.

Then... I tried to just copy the whole live-CD image onto the hard drive partition (from OS X, using "ditto") making the HD-paritition contain exactly the same as the live-CD, hoping to be able to just boot from that as if it were a live CD and proceed to install into the remaining partition. But again... no luck. I got my hopes up it starts into the graphical splash screen. But soon thereafter it is making "try-and-fail" repetitive style HD noise and sits there for a while and then dumps me into a rudimentary bash environment with no instructions on what I'm supposed to do there whatsoever.

I've no clue what to try anymore... HEEELLP! :)

---

### Post by picoday on 2006-12-14
Yes! I got it running. I'm posting this message from Ubuntu!

I hadn't tried "netboot" before. The docs for netbooting seemed to imply I needed first to set up a local server somehow to serve a CD image to the comp being installed.

However... this is misinformation, using the http method it connects to a ubuntu mirror on the internet and loads all required stuff from there.

Also, as it turns out it works fine on a HFS+ volume, the comment about HFS+ not working is another piece of misinformation in the docs (probably these docs are *really* old?). I clued into this when looking into debian instead of Ubuntu, and found some detailed instructions on how to do it, which explictly explain to install files for HD booting onto HFS+ volume.

Another nice surprise is that the netboot method works great and even works over the wireless, it detected the wireless fine and configured automatically using my wireless router's DHCP server.

If anyone cares and runs into similar problems. Here's what I did.

1) Boot target computer holding down T key.
2) plugin via a firewire into another mac running OS X
3) open disk utility and initialize HD of target to a "Apple Extended" (HFS+) non journaled **no OS 9 drivers**
4) download all the files in the netboot directory [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-powerpc/current//images/powerpc/netboot/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-powerpc/current//images/powerpc/netboot/))
5) places these files in the root directory of your target machine
6) reboot target machine as follows (see also [https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/ch05s01.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/ch05s01.html) )
 
6.1) reboot holding down command-option-o-f
6.2) when open firmware prompt appears type

```

boot hd:x,yaboot

```

x was 3 for me, but it may depend on the layout of the partitions. It should be the number of the partition where you installed the files before.

A method of trial and error worked for me (first try 1, then 2 etc.)

Note that when I first tried with OS 9 drivers installed it didn't work for me at this point.

6.3) when yaboot prompt appears, simply press enter

=> booting starts. You will be thrown into a text-based installer which worked very well for me. 

It asked me some questions about keyboard etc. and offered the option to chose between wireless and cable ethernet. I used wireless and it configured itself fine via DHCP from my wireless router.

It asked me a couple more questions which were easy to answer and eventually... well I'm posting this from within Ubuntu!

(And I'd like a pat on the back now :)

Also, these docs are really not very good... Should I' offer to try and add some info about the netboot process and fix some misinformation I uncovered in it. Would that be a good thing? How would I go about doing that?

---

