---
title: "original iMac - won't boot from cd"
date: 2005-08-20
forum: Apple PPC Users
---

### Post by jpscag on 2005-08-20
I have tried both the live cd and the install cd, but I can't get either to boot on my iMac. It has a 233 Mhz PowerPC 750 (G3) processor with 64 MB of RAM. It is running Mac OS 9.2.2 and all the hardware and ports are working fine.  I have tried holding down "c" upon startup, but this does not work.  Also, it will not allow me to select the cd as the startup disk in the control panel. Does anyone know how I can get this to work?

---

### Post by DJ_Max on 2005-08-20
There are tons of threads on this, a quick search should reveal the answer.

1.) Make sure you have a valid ISO image
2.) Make sure you burned the ISO image correctly.
3.) Try holding down option.
4.) Try to boot it from firmware.

---

### Post by jpscag on 2005-08-20
[QUOTE=DJ_Max]There are tons of threads on this, a quick search should reveal the answer.

1.) Make sure you have a valid ISO image
2.) Make sure you burned the ISO image correctly.
3.) Try holding down option.
4.) Try to boot it from firmware.[/QUOTE]


Thank You.  I tried those steps and still nothing.  I know the cds are good because they both worked on my G4 iBook.  Anymore ideas?

---

### Post by ninotob on 2005-08-20
[QUOTE=jpscag]I have tried both the live cd and the install cd, but I can't get either to boot on my iMac. It has a 233 Mhz PowerPC 750 (G3) processor with 64 MB of RAM. It is running Mac OS 9.2.2 and all the hardware and ports are working fine.  I have tried holding down "c" upon startup, but this does not work.  Also, it will not allow me to select the cd as the startup disk in the control panel. Does anyone know how I can get this to work?[/QUOTE]

(edit:  did you burn the ISOs as bootable discs or as data discs?  If you put one in an operating system, do you see a single ISO, or do you see a largish directory tree and many files?  If the former, you burned the discs improperly)

Although it shouldn't affect your ability to boot a cd, I suspect the memory is too low to run a desktop environment.  You may be limited to a text based system, though I wouldn't bet any money on my suspicion.

Let's just pretend that the cd-rom is broken in some way -- perhaps it is fine and perhaps it isn't, but it is odd that you can't boot from it.  I don't really want to take the time to edit the following netinstall description that I originally posted in Apple's forums, but I'll repost it here in case it proves helpful to anyone.  In summary, it describes how to perform a netinstall on a G3 ibook with a dead cdrom and no firewire.  I started first with Woody but eventually used ubuntu -- once I got it figured out, it worked flawlessly. 

------the rest is copied from my prior offsite post---------

Here's an update for posterity or anyone else who may have a single USB ibook (no firewire) with a dead CDrom and a hosed filesystem on the HD. Yes, it will boot from an external source ... unfortunately, it is a little bit of an effort. This worked for me:

Systems: dead ibook, router which assigns IPs by DHCP, SuSE 9.1 box running an NFS server, bootp, and tftp. I set these up in Yast with the default settings (makes a tftp directory: /tftpboot) and pointed the NFS server to that dir.

I placed a debian woody linux distribution there, I have the link at home sadly but I'll append it later. I put all the files in the /tftpboot directory as I had some problems when they were kept in subdirs. It's all of ten or 12 small files so it wasn't a big deal to me to figure out why.

With the iBook connected to my router, I turned it on holding down "command-option-o-f" thus entering open firmware. At the prompt, you need to tell the iBook where to boot from -- I couldn't boot from either the CD or the HD. I fooled around with usb setting for some hours but gave up eventually. So planning to boot over the network, type:

boot enet:XXX.XXX.XXX.XXX,yaboot

the XXX.... part is the IP on your LAN of the computer hosting the boot files. In this case, "yaboot" is debian's booter -- if you boot a different OS, you would need to replace "yaboot" with the name of the file that starts the boot process. Also note, you can get to other directories on your linux server but when typing on the mac from open firmware, use backslash. So, if you have your boot file in some other directory, when typing out your command in open firmware, you would replace "yaboot" with "\path\filename_to_execute". You don't have to type the name of the tftp directory -- that is root from the perpective of the iBook.

Yaboot transfers and runs. I had problems with the default install, but typing "install-safe" at the yaboot prompt worked and got a minimal (text only) system going. I then went through the Debian Woody http install procedure (hello 1990s -- I forgot just how bad linux installation used to be) and began setting up a real system.

So anyway, netbooting debian will work on an ancient crippled mac. Sadly, I encountered a DMA error in my post installation attempt to get KDE up and running. Then the HD stopped spinning and now the system is hosed again -- just get a kernal panic on rebooting. Tonight I'll reinstall as above, but this time check YES when asked if I want to check the HD for bad blocks during formatting. I'll keep my fingers crossed but I suspect the HD controller may be defective.

(NOTE: wasn't the controller -- it was the HD -- I had to replace it with a new one. Also, as noted in the link below, I eventually used the Ubuntu distribution which although Debian based, is much nicer than Debian Woody.)

-----

Here's a link to the files I used to netboot:

[http://archive.ubuntu.com/ubuntu/dists/hoary/main/installer-powerpc/current//images/powerpc/netboot/](http://archive.ubuntu.com/ubuntu/dists/hoary/main/installer-powerpc/current//images/powerpc/netboot/)

-------

---

### Post by Kalif on 2006-07-25
From the posts above a belief that improperly burnt CD:s is the main cause of failing installations on G3 imac:s.
As far as my tests, factory Dapper CD:s are working as bad as any home made CD:s. The CD:s are ofcourse fully readable with all files that you could expect in the places where they possibly should go. Still the imac hangs before any message or image has been shown on the screen.
The same behaviour as with my previous excursions with home burnt media. ](*,) 

From perusing both ubuntuforums and the web it seems like there actually _IS_ a problem regarding booting a recent ubuntu/xubuntu/kubuntu CD on old G3 imac:s.

I got myself an original rev-a G3 233Mhz imac last winter. My objective was twofold, having a cut down surf terminal for looking up phone numbers and other "light weight" items quickly, and having a relatively cool (thermaly) machine for serving DHCP, DNS, SMTP etc during the summer.

Having bad luck installing from my home burnt CD:s (Hoary at that time) made me revert to using a factory made Warty CD which did get me through the installation process as far as to the first boot from the hard disc; which failed. Then I figured that the drive did not properly work with modern home burnt CD:s, a common problem with older CD-readers. Hence I figured I could wait until the upcoming Dapper release, and a couple of factory produced CD:s.

Then even if Warty was not working fully up to the task of installing the Ubuntu system on my G3, it _DID_ at least _BOOT_ from the CD. Hoary did not and Dapper still does not.

Yes, I have tried booting using both "C" and power commands in the open firmware. BTW Can any sane person explain why a company taking so much pride in user friendliness still produces systems without proper documentation of their boot-loader? Neither proper on-line help, nor anything in the manual included with the system. Any no name far east PC motherboard manufacturer would be ashamed not to document their BIOS:es.

Since there are heaploads of cute looking G3:s out there to be recycled, some clever person must have found a way of getting around to installing UBUNTU on such a system. At least since they are supposed to be supported.

Is reverting to Debian and "upgrading" to Ubuntu from there a proper (and cumbersome) way of dealing with this problem?

Cheers,
k.

---

