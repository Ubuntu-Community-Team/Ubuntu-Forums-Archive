---
title: "Ubuntu 16.04 64-bit Live don't see SSD for installation"
date: 2016-09-06
forum: Apple Hardware Users
---

### Post by peppedimi on 2016-09-06
I have a Macbook Pro 2.2 with one HDD and one SSD; on the SSD I have installed Ubuntu 14.04 32-bit; the HDD is only for data (no Mac Os X). In the SSD I have some free space, because I'd like to install an Ubuntu 16.04 64-bit, near the Ubuntu 14.04 32-bit. But when I boot the ISO from the HDD (with Grub2), Ubuntu don't see the SSD but only the HDD... so it's impossible install in the SSD. If I boot from the HDD an Ubuntu 14.04 32-bit ISO Live, instead, Ubuntu see also the SSD. Where is the problem? Thanks a lot for the help.
In attachments are the images of HDD ad SSD from GParted:

[ATTACH=CONFIG]271005[/ATTACH]

[ATTACH=CONFIG]271006[/ATTACH]

Where is the problem? Thanks a lot for the help.

---

### Post by QIII on 2016-09-06
Moved to Apple Hardware Users.

You may be encountering some Apple-specific issue, so you might get better answers here.

---

### Post by peppedimi on 2016-09-07
Ok, thank you!

Could the problem be the absence of a EFI partition at the beginning of the SSD?
The partition table is GPT.

Here the output of "sudo parted -l":

```

***@***:~$ sudo parted -l[sudo] password for ***: 
Modello: ATA Samsung SSD 850 (scsi)
Disco /dev/sda: 120GB
Dimensione del settore (logica/fisica): 512B/512B
Tabella delle partizioni: gpt


Numero  Inizio  Fine    Dimensione  File system  Nome  Flag
 1      1049kB  60,0GB  60,0GB      ext4
 2      120GB   120GB   1049kB                         bios_grub




Modello: ATA FUJITSU MHW2120B (scsi)
Disco /dev/sdb: 120GB
Dimensione del settore (logica/fisica): 512B/512B
Tabella delle partizioni: gpt


Numero  Inizio  Fine    Dimensione  File system     Nome  Flag
 1      1049kB  2097kB  1049kB                            bios_grub
 2      2097kB  118GB   118GB       ext4            Dati
 3      118GB   120GB   2130MB      linux-swap(v1)



```

---

### Post by Bucky Ball on 2016-09-07
Welcome. As you are wanting to install somewhere specific, and NOT on sda, then you are going to need to set up partitions manually. Regardless of what your issue now it, when you get to the partitioning section of the install, you need to choose 'Something Else' and select the SSD from there. Is it there?

From what you're saying I'm presuming you have Ubuntu installed using EFI on sda. If that install is using EFI, you need to boot the install media in EFI. You'll probably see two entries for the install media, one with (UEFI) next to it, one without. Obviously, choose the (EFI) option.

The install *may* automatically take care of the EFI stuff for you (as you booted in EFI and the install should be wise to that and may look for an existing EFI partition or create another one on sdb if it needs to), but never tried this so hopefully someone who has can jump in. Not sure if you need to create a second EFI partition on sdb or the details for that install will be written into the existing EFI partition on sda 'automagically'. :-k

---

### Post by oldfred on 2016-09-07
I also do not know Mac. They seem to  have many different versions and each version has specific requirements.

But most comments before by those who know Mac seem to suggest gpt with UEFI as Mac is normally UEFI. And they usually suggest dual booting as some Mac utilities are required and need to be run occasionally, which you cannot do from Linux.

 [http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios](http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios) 


 EFI partitions: Also some info on efi partition on a Mac.
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)
With 15.10, similar wiht 16.04
The amd64 (Intel x86 64bit) images specifically targeted at Apple hardware (amd64+mac) are no longer produced. 
[http://mattjanik.ca/blog/2015/10/01/refind-on-el-capitan/](http://mattjanik.ca/blog/2015/10/01/refind-on-el-capitan/)
[http://ubuntuforums.org/showthread.php?t=2297148](http://ubuntuforums.org/showthread.php?t=2297148)

---

### Post by peppedimi on 2016-09-09
Thank you Bucky Ball and Oldfred,

but I already tried to install choosing "something else" and the installation software detects only the hdd; here one image:

[IMG]https://dl.dropboxusercontent.com/u/1784644/Installazione%20something%20else.png[/IMG]

If I boot Plop Live, instead, detects both the hdd and ssd... it's a mistery...

When I boot the Live version for install there isn't no choise for using Uefi or not Uefi.

---

### Post by oldfred on 2016-09-09
With PC, the UEFI offers two boot options for Ubuntu live flash drive. One is UEFI:name and other just name (BIOS) where name if label or brand of flash drive. Not sure with Mac.
Are you sure you have 64 bit version? The 32 bit version does not have UEFI boot option.

Have you tried using gparted on live installer to see if it shows SSD?

---

### Post by peppedimi on 2016-09-12
When I boot the Live Ubuntu 16.04 64-bit (*-amd64.iso) there isn't a boot option.. the OS loads automatically.
The GParted on live installer doesn't shows the SSD.
The same with the Live Kubuntu; here the output of rescan-scsi-bus.sh

```

kubuntu@kubuntu:~$ sudo rescan-scsi-bus.sh
Scanning SCSI subsystem for new devices                                                       
Scanning host 0 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs                               
Scanning host 1 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs                               
Scanning host 2 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs                                     
 Scanning for device 2 0 1 0 ...                                                                    
OLD: Host: scsi2 Channel: 00 Id: 01 Lun: 00                                                         
      Vendor: ATA      Model: FUJITSU MHW2120B Rev: 0013                                            
      Type:   Direct-Access                    ANSI SCSI revision: 05                               
Scanning host 3 for  SCSI target IDs  0 1 2 3 4 5 6 7, all LUNs                                           
0 new or changed device(s) found.                                                                         
0 remapped or resized device(s) found.                                                                    
0 device(s) removed.                                                                                      
kubuntu@kubuntu:~$

```

---

### Post by peppedimi on 2016-09-13
So, is there no hope? Install a version of Ubuntu near to another already installed and running is really so difficult?
(For years I used linux and I "demonstrated" that you can do it also in a law firm, but in this case I have to admit that is not easily to love...).

---

### Post by oldfred on 2016-09-13
I do not have a Mac, but some threads that may possibly help, or they may be too old.

 [http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios](http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios) 
   Mac with NVMe
[http://ubuntuforums.org/showthread.php?t=2274095](http://ubuntuforums.org/showthread.php?t=2274095)
EFI partitions: Also some info on efi partition on a Mac.
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)
With 15.10
The amd64 (Intel x86 64bit) images specifically targeted at Apple hardware (amd64+mac) are no longer produced. 
[http://mattjanik.ca/blog/2015/10/01/refind-on-el-capitan/](http://mattjanik.ca/blog/2015/10/01/refind-on-el-capitan/)
[http://ubuntuforums.org/showthread.php?t=2297148](http://ubuntuforums.org/showthread.php?t=2297148)

---

