---
title: "UEFI and Vaio laptop"
date: 2012-09-03
forum: Any Other OS
---

### Post by UltimateCat on 2012-09-03
Hi:;)
I would like to put Fedora on my new laptop but after reading about this UEFI I'm having a difficult time trying to understand what I need to do.

This new Sony Vaio that I purchased is a SVE1500 Enhanced E series with a 3rd generation i5 processor and is a dual core. It has a 1 GB AMD Radeon graphics card and 500GB HDD and 6 GB of RAM.  It also has this Unified Extensible Firmware Interace system partition all of it's own.

I did some reading because I knew nothing about this UEFI.
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Multiboot_on_BIOS](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Multiboot_on_BIOS)

After some reading and note taking I realized that I might (if I understood the reading) have to configure the Grub somehow. And read that the Linux bootloader should also be installed in UEFI-GPT mode if booting from the same disk.  I really do not understand what to do with this UEFI and Grub.

I learned that for Linux to acces UEFI runtime services the UEFI firmware processor architecture and the Linux Kernel must match. It's independent of the bootloader used.

I'm doing mybest reading and trying to learn what to do in order to install Fedora on my new laptop.  It is clear to me however; that if I fail to do this configuring ( don't know at this point) and fail to make this UEFI and the Kernel work together correctly it will cause Kernel panic.

I'm open to suggestions as this seems somewhat complicated and I don't want to wreck my new laptop.  What do you make of all of this and if it were you; how would you proceed?

How do I know if I have this match?

---

### Post by sandyd on 2012-09-03
[s]Just turn off UEFI.

As part of microsoft's requirements, there MUST be a way to turn off UEFI on x86 pcs.

However, it was indicated in Windows 8, not 7 ([http://download.microsoft.com/download/A/D/F/ADF5BEDE-C0FB-4CC0-A3E1-B38093F50BA1/windows8-hardware-cert-requirements-system.pdf](http://download.microsoft.com/download/A/D/F/ADF5BEDE-C0FB-4CC0-A3E1-B38093F50BA1/windows8-hardware-cert-requirements-system.pdf)), so I don't know of the requirements apply or not.[/s]
Read that fast, then went back again.

Do you mean a EFI partition, not UEFI partition?

---

### Post by YannBuntu on 2012-09-04
Hello
Please indicate your Boot-Info URL. [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by UltimateCat on 2012-09-05
> **sandyd said:**
> [s]Just turn off UEFI.

As part of microsoft's requirements, there MUST be a way to turn off UEFI on x86 pcs.

However, it was indicated in Windows 8, not 7 ([http://download.microsoft.com/download/A/D/F/ADF5BEDE-C0FB-4CC0-A3E1-B38093F50BA1/windows8-hardware-cert-requirements-system.pdf](http://download.microsoft.com/download/A/D/F/ADF5BEDE-C0FB-4CC0-A3E1-B38093F50BA1/windows8-hardware-cert-requirements-system.pdf)), so I don't know of the requirements apply or not.[/s]
Read that fast, then went back again.

Do you mean a EFI partition, not UEFI partition?

Yes, I mean UEFI System Partition.

How exactly do I work with this UEFI in order to install Fedora?
Do I have to make some adjustments in the BIOS?

---

### Post by UltimateCat on 2012-09-05
> **YannBuntu said:**
> Hello
Please indicate your Boot-Info URL. [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Sorry, I don't have this live cd. Do I need it?

The Vaio is brand new-

---

### Post by oldfred on 2012-09-05
As the instructions on Boot-Repair say. You can download it into a LiveCD or download it as a full bootable repairCD.

If you have Windows in UEFI/gpt mode all other installs need to be UEFI also. But if Windows isBIOS/MBR then all other installs need to be BIOS.

If drive is partitioned with gpt not MBR(msdos) and first partition is efi, then you are in the UEFI mode.

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)
Recompiling GRUB not required with newest versions of grub.
Creating efi partition & folders in advance works.Must be 64bit version to have UEFI 

Good technical references:
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

---

### Post by UltimateCat on 2012-09-08
Oldfred:

I will read the documentation again; Thank You

It is a little confusing as I have not done this before and I am trying to wrap my head around this process/procedure to be able to install Fedora.

If the recovery disc's from Sony fail to arrive shortly; I will be returning the Vaio for a full refund.  During the Recovery Media Process; a Sony rep and I discovered that the Recovery Partition is corrupt-

It's amazing that these recovery disc's are on back-order.

Thanks again;)

---

### Post by UltimateCat on 2012-09-10
I found good information pertaining to this UEFI at the Linux Foundation's website. They made a PDF addressing this UEFI ordeal-

"Extract the OS venders key exchange key and install it to the data base. This tool would be activated by the UEFI System as soon as it saw UN-autherised media inserted so the platform owner could decide whether they wished to accept the key for OS install and boot"

[http://www.linuxfoundation.org/publications/making-uefi-secure-boot-work-with-open-platforms](http://www.linuxfoundation.org/publications/making-uefi-secure-boot-work-with-open-platforms)

This information in the PDF is in reference to the UEFI secure boot and how it can be implemented.  

Even with help and instructions this is hard to grasp-
It is my hope that I will eventually understand this and the other links you posted so that I can install Fedora.

---

### Post by exploder on 2012-09-10
UltimateCat, I am glad that you posted this question! Many of us are going to be asking the same thing in the near future and to be completely honest I do not have a very good understanding of UEFI either. This is something that everyone will have to deal with sooner or later.

I saw in the OpenSuse release notes they might have a solution for this in place but I do not know weather it is included in the DVD or Live CD version of the release. I also read an article posing the same question about OpenSuse. I just thought I would bring this up just in case it might help you out.

Please let us know how this turns out because this is indeed a very interesting question and I would like to know how to resolve this myself.

---

### Post by YannBuntu on 2012-09-10
**@UltimateCat and exploder:** please do not mistake, UEFI is not the same thing as "Windows8 Secure Boot".

UEFI is a kind of new BIOS which became widely spread in ~2011, and Ubuntu has no major problem with it. See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

On the other hand, "Windows8 Secure Boot" may be a major problem, but we do not have enough information yet as it will be shipped with Windows8.

---

### Post by oldfred on 2012-09-10
It was my understanding that the secure boot switch was only used with the official release of Windows 8. Current systems normally do not have that turned on. So is your system using the "secure" boot feature? If so it is the first one we have seen. Many users have installed dual boot with UEFI, but they have been Windows 7 and Ubuntu.

---

### Post by exploder on 2012-09-10
YannBuntu, thanks for clarifying that for me. What you said makes sense and now I understand. Thanks!

---

### Post by UltimateCat on 2012-09-14
> **exploder said:**
> UltimateCat, I am glad that you posted this question! Many of us are going to be asking the same thing in the near future and to be completely honest I do not have a very good understanding of UEFI either. This is something that everyone will have to deal with sooner or later.

I saw in the OpenSuse release notes they might have a solution for this in place but I do not know weather it is included in the DVD or Live CD version of the release. I also read an article posing the same question about OpenSuse. I just thought I would bring this up just in case it might help you out.

Please let us know how this turns out because this is indeed a very interesting question and I would like to know how to resolve this myself.

I have lots of information about this UEFI System Partition and in fact a good article that the Linux Foundation made a PDF of it-
I'll make another post to share. I've been studying this for about 2 weeks-

---

### Post by UltimateCat on 2012-09-14
The information that I have studied has come from multipule sites; however this PDF that I mentioned above is very good documentation from The Linux Foundation.
http:[www.linuxfoundation.org/publications/making-uefi-secure-boot-work-with-open-platforms](www.linuxfoundation.org/publications/making-uefi-secure-boot-work-with-open-platforms)

I learned that for Linux to access UEFI Runtime Services, the UEFI Firmware processor architecture and the Linux Kernel processor architecture must match.
<#otherwise it causes kernel panic>

One of the key things concerning this UEFI is to extract the OS venders key exchange key and install it to the data base.  This tool would be activated by the UEFI System as soon as it saw un-authorised media inserted so the platform owner could decide whether they wished to accept the key for OS install and boot-

A gentleman at the Linux Foundation on the advisory board is working with Linux Developers to do all that he can and they are working on it-

[http://www.zdnet.com/blog/open-source/linus-torvalds-on-windows-8-uefi-and-fedora/11187](http://www.zdnet.com/blog/open-source/linus-torvalds-on-windows-8-uefi-and-fedora/11187)

[http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement](http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement)

Unfortunately i had to return my Vaio because the Recovery Partition was corrupt.  I'm expecting a replacement within the week.

BTW the newer Sony Vaio's have the UEFI System Partition and based on my research I highly suspect (don't have complete confirmation) that all the new laptops:
Lenovo, HP, Samsung, Toshibia....etc. will as well.

It is my sincere hope to find a way to install Fedora and get around this UEFI System Partitioning design-
[http://docs.fedoraproject.org/en-US/Fedora/17/html/Installation_Guide/s2-grub-whatis-booting-uefi.html](http://docs.fedoraproject.org/en-US/Fedora/17/html/Installation_Guide/s2-grub-whatis-booting-uefi.html)

The name of one of the company's or corporations that are mass producing the UEFI System is called Insyde-
[http://www.insydesw.com/](http://www.insydesw.com/)

All this reading, learning and researching has been interesting to say the least-

Cheers:popcorn:
Ultimatecat

---

### Post by UltimateCat on 2012-09-24
I posted the information in the thread above for folks to learn from.

Closing the thread-

---

