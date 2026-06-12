---
title: "Lenovo B570E2, boot from UEFI"
date: 2013-01-20
forum: Any Other OS
---

### Post by The_Aegidius on 2013-01-20
Hello  :)

Few days ago I bought a new Lenovo B570E2, with no OS, and I want to install Arch Linux on it. I saw some partitions on the hd and I deleted them. At this step, the Arch Linux live cd didn't start anymore but just show my [theese]("https://www.dropbox.com/s/j3j9t7jlnk6f562/Foto%2018-01-13%2022%2048%2046.jpg") options and then a black screen.
 
I did know about UEFI so I thought that was the problem: it was missing the UEFI partition, so Arch live could not start. So I installed Ubuntu to make it create the UEFI partition. Then I erase the Ubuntu partition to install Arch on it. At this step I reboot the computer and all I see is [this](https://www.dropbox.com/s/cqbxfup0bb2w3xw/Foto%2020-01-13%2010%2045%2055.jpg) error message:
 
> 
error: file '/boot/grub/x86_64-efi/normal.mod' not found.

 
Now I can't reach the BIOS options or the boot menu.
 
Did I brake up my new computer?

---

### Post by mips on 2013-01-20
> **The_Aegidius said:**
> 
Did I brake up my new computer?

I doubt it.

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

---

### Post by iponeverything on 2013-01-20
Really no big deal.

You just managed to create some extra work for yourself..

---

### Post by The_Aegidius on 2013-01-20
I'm really so frustrated about it :(

---

### Post by iponeverything on 2013-01-20
An easy way out would be download and install 12.10 -- 
it has smarter UEFI code. Getting in to the BIOS is tricky -- I ran into the same issue with my X230..

It'll at least get your system up.

---

### Post by The_Aegidius on 2013-01-20
I cannot lunch nothing! I cannot run boot from any device! I just get the grub rescue and I don't know what to do.

I feel so bad ;(

---

### Post by mips on 2013-01-20
Oh I think Manjaro linux which is based on Arch also has support for UEFI in it's installer. just double check if you are interested.

---

### Post by The_Aegidius on 2013-01-20
I cannot boot nothing!!!

I just see the grub rescue shell and nothing else.

---

### Post by mips on 2013-01-20
[http://forums.lenovo.com/t5/IdeaPad-S-series-Netbooks/How-to-enter-BIOS-setup-in-IdeaPad-S10-s-boot-boost-mode/td-p/61246/page/2](http://forums.lenovo.com/t5/IdeaPad-S-series-Netbooks/How-to-enter-BIOS-setup-in-IdeaPad-S10-s-boot-boost-mode/td-p/61246/page/2)

> Hi,
 
1. remove your hdd
 
. boot your ideapad (without any device attached to it nor ethernet)
 
it will show up broadcoms NIC trying to boot remotely and fail...
 
3. restart your ideapad -> TADA the prompt is back again.
 
get a fresh BIOS update from here:
 
[http://www-307.ibm.com/pc/support/site.wss/MIGR-72939.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-72939.html)
 
best regards
 
KJ

> thanks for the suggestion of removing the harddrive.. it wasnt too hard to get out of the netbook ..after booting it didn't appear to be booting off any other devices (blank screen) but after shutting down a few times and pressing keys on boot it tried to boot off the lan device multiple times until reboot..... after trying to boot off the lan device I shut it down and upon restart the options (f2 for bios, f12 for boot menu) appear.... SUCCESS thanks erik for the suggestion...I didnt try it earlier since it didnt make sense that the menu would showup on the next reboot...maybe this is a failsafe lenovo has after adding options that disable access to bios =X (shame on lenovo) SOLVED

Different model but worth a try.

---

### Post by oldfred on 2013-01-20
Some have reported that the fast boot setting by passes the UEFI/BIOS boot keys and then you only can get into UEFI menu from Windows. Or you then have to do major work arounds to try to get back into system.

Samsung know issue, not sure about others:
       [https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)
Booting the Ubuntu installer in UEFI mode from a USB disk on certain Samsung laptops (530U3C, NP700Z5C) may trigger a firmware bug that renders the machine unbootable. Users are advised to use caution when installing on Samsung laptops and ensure that they are configured for legacy BIOS mode, not UEFI mode. (1040557) 

            UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop - fix released
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)

Before secure boot users installed Ubuntu without too many issues.
       
 How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
    
        The State Of Linux Distributions Handling Secure Boot
[http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI](http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI)

---

### Post by iponeverything on 2013-01-20
below link looks like the issue you are having.

[http://askubuntu.com/questions/213871/grub-rescue-prevents-live-cd-usb-or-boot-menu](http://askubuntu.com/questions/213871/grub-rescue-prevents-live-cd-usb-or-boot-menu)

---

