---
title: "Mavericks upgrade broke rEFIt/GRUB"
date: 2014-08-11
forum: Apple Hardware Users
---

### Post by __PG__ on 2014-08-11
I have a MacBookPro 5,3 runnning Ubuntu 12.04.5 LTS.  I upgraded to OS X Mavericks a few days ago.

The OS X upgrade worked fine, and there were no visible changes to the rEFIT menu. However attempting to boot Ubuntu fails and I end up at the GRUB command line.
I upgraded to rEFInd and that menu boots correctly, however it produces the same problem, i.e. I end up at the GRUB command line.

I can boot into Ubuntu with the following commands from GRUB:
root=(hd0,3)
linux /boot/vmlinux-3.2.0-67-generic root=/dev/sda4 ro
initrd /boot/initrd.img-3.2.0-67-generic
boot

Evidently the problem is that rEFIT and rEFInd lost the correct settings. 

I presume that the problem will be fixed by creating a suitable entry in refind.conf. Do any Mac users have sample entries for booting Ubuntu from a MacBook partition? 

My grub version is GNU GRUB 0.97

Curious to see what other users are doing. Perhaps an upgrade to GRUB 2 or the use of newer EFI methods with rEFInd?

Thanks in advance.

---

### Post by MikeBraxner on 2014-08-11
I experienced similar problems in the past, usually after Apple-Store "assistance/help", and OS X upgrades. In those cases, it turned out to be EFI screw ups, namely multiple, conflicting BootManager entries ... Apple just doesn't believe in sharing their toys, now do they. Once these EFI hick-ups had been straightened out, i.e. had been removed, a simple re-install of rEFInd got everything working peachy again. 

So, at your own risk, here is a GNU/Linux command line road-map (adjust as needed) to removing all superfluous bootmanager entries, and re-install rEFInd. 

1) mount the ESP (adjust sdaX to your installation) 
***sudo mount /dev/sdaX /boot/efi***


2) get a list of all known bootmanager entries
***sudo efibootmgr***


3) Using the reported *BootXXXX* id's, remove **ALL** entries **EXCEPT** rEFInd's (probably *Boot0000*) one at a time, e.g. ...
***sudo efibootmgr -b 0081 -B***


4) when only rEFInd's entry is left, i.e. all others are gone, including any 'un-named' ones, re-install rEFInd *AGAIN*, using the install script ...
***sudo ./install.sh***


5.) if ...
***sudo efibootmgr***


... reports a BootOrder that does not *at least begin* with rEFInd's *BootXXXX*, you can reset the boot order to only utilise rEFInd via ...
***sudo efibootmgr -o XXXX***


This always worked for me without a glitch, but as I said, use at your own risk ... and make dammed sure you have some bootable USB sticks/restore partition with Linux/OS X at hand ... just in case ;-)

---

### Post by __PG__ on 2014-08-20
Well for whatever reason, when I set my rEFIt system up all those years ago, all the rEFIt (and rEFInd) files are on the OS-X partition.
When I installed rEFINd it was from within OS-X.

Thus, in /boot in Ubuntu, there is no efi directory, only a grub directory.

rEFIt/rEFINd are installed on my Mac drive (which is labelled Macstuff can can be seen from Ubuntu)
 
/media/Macstuff/efi$ ls -lttotal 36
drwxrwxr-x 1 root 80     8 Aug  8 21:13 refit
drwxr-xr-x 1 root 80     8 Aug  6 22:04 refind
drwxrwxr-x 1 root 80    23 Aug  6 16:35 tools
-rw-rw-r-- 1 root 80 26301 Mar 24  2009 rEFIt License.rtf
-rw-rw-r-- 1 root 80  4437 Mar 24  2009 rEFIt ReadMe.rtf

With that in mind, would you recommend following your procedure from within OS-X?  Or will your method not work for my setup?

Honestly it's been so long since I set up the system that I'm not as familiar with the ins and outs of dual-booting as I once was

---

### Post by MikeBraxner on 2014-08-20
First, the files you're referring to are the rEFIt/rEFInd distribution files, ***not*** the installed bootmanager. For some general EFI background info, have a look at [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)  and [http://www.rodsbooks.com/refind/installing.html](http://www.rodsbooks.com/refind/installing.html), as well as some basics on the efibootmgr (e.g. [http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr) or [https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)).

Second, if you review [http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html), in particular the section on *"Fixing the Installation" - step 10*, you'll see that installing rEFInd does'nt create a /boot/efi directory, but instead installs the required files to the ESP, which should be *mounted* in, say, /boot/efi such that *efivars* can properly find them (see above).

Third, please don't expect me to provide OS/X answers, which I don't have, to questions *specifically* posed in a **Linux forum**. efibootmgr does the job in a **Linux** environment, (and I think I remember warnings that trying to use efibootmgr on OS/X will brick the system), so boot into Ubuntu, or boot a 'try ubuntu' version and use that one, or find an OS/X application that *"can create and destroy boot entries, change the boot order, change the next running boot option, and more"*.

The basic principles outlined previously hold true, but if you decide to utilize OS/X, then you'll have to find a viable cli/gui application for the job.

---

