---
title: "What a nightmare install"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by max renn on 2008-02-08
All I can figure is that gparted wrote to win partition instead of MBR, and that Grub doesn't play well with my BIOS?

History:

Three drives in computer: hda, sda, sdb.  WinServer2k3 on sda1.  Booting from sda in BIOS.

use gparted on ubuntu live to resize NTFS down to provide room for ubuntu.

windows on sda1, / on sda2, /home on sda3

reboot into external USB ubuntu 7.10 dvd and run text based setup.

partition drive not making / bootable and install grub which detects win2k3 partition.

reboot to cannot load a system error (forget actual error, but implies no bootable drives in system)

Load up live cd and find all partitions installed and accessible.

konsole and sudo grub, find (hd1,1) and fix  (why not hd0,1?)

reboot and have grub menu, but cannot load linux kernel and boot loader missing from winders.

remove hda from computer, reboot, grub menu missing

download SuperGrub three times, burn, boot, grub prompt, but looking for supergrub menu.  figured out supergrub must boot from *ide* cdrom drive, not usb.

supergrub fixes grub and puts it on (hd2,2), huh?!?  but i've only got two drives in there.

reboot and grub menu back, but still won't find linux partition.

remove sda2, run supergrub, fixes (hd0,1), reboot into linux and it works!

Try windows and bootloader missing.  screw it.  wipe out linux partitions. reboot to 'A Disk Read Error Occured. Press CTRL ALT DEL to restart'.

run win2k3 setup and recovery and access drive just fine.  do fixboot - nope, do fixmbr - nope

do chkdsk /r and now boot up to blank screen with assorted, variably colored ascii characters.

pull this drive out (computer now has ZERO drives) and pop in other computer (non-boot).  Can access win partition very well thanks.

Remove all partitions.  Good bye Windows, Welcome to gparted, grub, ubuntu!

---

### Post by nikoPSK on 2008-02-09
please try testdisk to see if it can recover your partition.

---

### Post by azimuth on 2008-02-09
Grub and Gparted/Linux see and number drives differently. 

Grub                       Linux
(hd0)                         hda
(hd1)                         sda (identified a  serial drive)
(hd2)                        sdb

Partitions are also counted differently
(hd1,0)                       sda1    Windows
(hd1,1)                       sda2     /
(hd1,2)                       sda3     /home

The grub command "setup (hd1)" would have put grub into the MBR of drive sda, where your bios should have found it booting to that drive.

If you ain't confused yet, that makes one of us.

---

### Post by max renn on 2008-02-09
> **nikoPSK said:**
> please try testdisk to see if it can recover your partition.

I already tossed the windows partition.  It wasn't that big a deal, although it would have been nice to keep.  But thanks for the idea. :)


> **azimuth said:**
> Grub and Gparted/Linux see and number drives differently. 

When your bios was set to boot from sda , the grub command "setup (hd1)" would have put grub into the MBR of drive sda.

If you ain't confused yet, that makes one of us.

LOL, yeah I'm confused, but I do understand the logistics of the situation.  I reinstalled again with all drives in the box and the same thing happened.  Boot with no grub/linux until I remove the other drives and fix grub.  So it must be loading grub onto a different HD during the install process.  

So i'm up to my 10th or so install.  Lately trying to get my two networks to work properly.  Install demands to put my internal giganic on eth0 and my Internet nic on eth1.  Then, of course, the metric is lower for the eth0 gateway (what linux forces on me), so I cannot ping outside to Internet.  So even deleting the route still magically appears after some time and network stops working.  But if I install with only one nic (so that means removing three pieces of hardware) then the gw metric seems to remain stable.

Starting to sound like an install of 95/98, removing all of this hardware... (welcome to the past :)

But now I am stuck at getting my NTFS partitions loaded (the drives I stick back in after install). 

**hal-storage-fixed-mount-all-option refused uid 1000 **

So I try to install ntfs-config in adept and I get the error that it cannot perform that function completely.  I used apt and it loaded a bunch of other (prerequisites?), but it did install, only it doesn't seem to work.  Nothing happens when I click start menu link (ntfs configuration tool) and I still get hal error in Konqeror.  Same with knetworkmanager, processes show it running, but nothing on the desktop.

This is all really disheartening.  From what I read on the web, ubuntu is pushing peeps to switch from windows, but I don't have the time (or the will) to go through all of this mysterious crap.  I fully believed I could be up and running within 24 hrs and I am nowhere near even recognizing my partitions yet.  I spent two weeks lurking, planning, running live cd (which works fine) and I'm now into my tenth install.  I'll give it another 48 hours, but I have people relying on this computer being fully functional on Monday.

---

### Post by nikoPSK on 2008-02-09
No problem, just to let you know, it might be a bit frustrating to you if this is your only PC and you have full time linux on it. I have 5 other PC's, two are vintage macs, another one is a lappy and two older desktops.

Just letting you know,
nikoPSK

---

### Post by azimuth on 2008-02-09
Just a random thought. If you have a Windows server that needs 24/7 access, you do not want a dual boot setup on it. You can not run both OS concurently. It's an either or situaltion. The only way around this is to run one of them in a virtual machine (VM Ware or Virtual Box) inside the other operating system.

---

### Post by nikoPSK on 2008-02-09
> **azimuth said:**
> Just a random thought. If you have a Windows server that needs 24/7 access, you do not want a dual boot setup on it. You can not run both OS concurently. It an either or situaltion. The only way around this is to run one of them in a virtual machine (VM Ware or Virtual Box) inside the other operating system.

thats a good solution. :) Or, if you have an old pc, cram in a larger hardrive and do that?

---

### Post by azimuth on 2008-02-09
> **nikoPSK said:**
> thats a good solution. :) Or, if you have an old pc, cram in a larger hardrive and do that?

That is the ultimate solution, if you have the hardware (old pc) to do it. It is amazing how usable Linux (any distro) will make a machine that can no long handle the latest and greatest from Redmond. I have a Pentium 200Mhz that runs quite nicely on Puppy Linux and Xubuntu. This poor old computer would barely run on win 98.

---

### Post by nikoPSK on 2008-02-09
> **azimuth said:**
> That is the ultimate solution, if you have the hardware (old pc) to do it. It is amazing how usable Linux (any distro) will make a machine that can no long handle the latest and greatest from Redmond. I have a Pentium 200Mhz that runs quite nicely on Puppy Linux and Xubuntu. This poor old computer would barely run on win 98.

puppy saved my first pc I ever got. :D

---

### Post by max renn on 2008-02-09
> **nikoPSK said:**
> No problem, just to let you know, it might be a bit frustrating to you if this is your only PC and you have full time linux on it. I have 5 other PC's, two are vintage macs, another one is a lappy and two older desktops.

Just letting you know,
nikoPSK

I do have several other PCs.  My idea is to gradually convert back to Linux.  I have an old box with a linux bridging firewall, and I used Slackware for a couple of years back in the day.

> **azimuth said:**
> Just a random thought. If you have a Windows server that needs 24/7 access, you do not want a dual boot setup on it. You can not run both OS concurently. It an either or situaltion. The only way around this is to run one of them in a virtual machine (VM Ware or Virtual Box) inside the other operating system.

Actually, I am trying to replace this win server with linux.  I was going to keep the win partition just to keep myself familiar/troubleshoot with it.

---

### Post by jvc26 on 2008-02-09
I havent used [Xen]("http://www.cl.cam.ac.uk/research/srg/netos/xen/") recently, but Xen would enable you to have both on the server at the same time in virtual machines, without having one virtual inside the other - especially useful as your linux server will not have a GUI. It may well be something looking into, especially as you appear pretty competent with server environments.

Il

---

### Post by max renn on 2008-02-09
So I don't know what's up with the ntfs-config ubuntu package, but it fails to install again.  I got the dev's package from: [http://flomertens.free.fr/ntfs-config/](http://flomertens.free.fr/ntfs-config/)  for ubuntu Fiesty and it installed, no error.  But it still wouldn't open on desktop.

Aaaaaaaaaaaaaaaaaaaahhhhhhhhhhhhhhhhhhhhhhh, Evidently, we are supposed to run ntfs-config with sudo from terminal. Who would've figured?  

```
sudo ntfs-config
```

A config window pops up and click-click and now I can see my ntfs partitions fine.

hal-storage-fixed-mount refused uid 1000 error is FIXED

---

### Post by max renn on 2008-02-09
> **Illuvator said:**
> I havent used [Xen]("http://www.cl.cam.ac.uk/research/srg/netos/xen/") recently, but Xen would enable you to have both on the server at the same time in virtual machines, without having one virtual inside the other - especially useful as your linux server will not have a GUI. It may well be something looking into, especially as you appear pretty competent with server environments.

Il

Ummmmm, yep, I saw a youtube where someone had xen installed with Mac and linux, it was very interesting.

---

### Post by nikoPSK on 2008-02-10
> **max renn said:**
> Ummmmm, yep, I saw a youtube where someone had xen installed with Mac and linux, it was very interesting.

could you link please? I can;t seem to find it.

---

