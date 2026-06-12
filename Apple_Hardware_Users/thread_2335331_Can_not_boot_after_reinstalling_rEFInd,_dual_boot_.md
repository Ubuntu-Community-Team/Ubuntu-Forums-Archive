---
title: "Can not boot after reinstalling rEFInd, dual boot OS X El Capitan"
date: 2016-08-27
forum: Apple Hardware Users
---

### Post by davidbogner on 2016-08-27
Hi,

I have following system: 
Mac Mini late 2014, 
Dual boot Mac OS X El Capitan
Ubuntu 16.04.1 with BTRFS (upgraded from 14.04)
HardDrive: SSD

Partitions:
```

     Device         Start       End   Sectors   Size Type

     /dev/sda1         40    409639    409600   200M EFI System
     /dev/sda2     409640 487528671 487119032 232.3G Apple HFS/HFS+
     /dev/sda3  487528672 488798207   1269536 619.9M Apple boot
     /dev/sda4  488798208 961146879 472348672 225.2G Linux filesystem
     /dev/sda5  961146880 976771071  15624192   7.5G Linux swap

```

 After I reinstalled rEFInd in Ubuntu via the .deb install package, I could not boot anymore. Only holding the "ALT" key brings up the Mac boot manager letting me boot into Mac OS X. I reinstalled then rEFInd in Mac OS X following the SIP guidelines (using terminal in recovery mode according to [http://www.rodsbooks.com/refind/sip.html](http://www.rodsbooks.com/refind/sip.html) ). No success.

I then created a bootable Ubuntu USB stick, booted with stick and ran boot-repair: no success. Here is the result of BootInfo summary created by boot-repair:

[http://paste2.org/ex0HHwaM](http://paste2.org/ex0HHwaM)

I did read, that rEFInd is not really necessary to boot on EFI system. So I assume a solution would be be to have a working GRUB installed on /dev/sda in order to dual boot. I thought boot-repair would do that, but I can not even configure it (in the advanced options the GRUB location tab, etc. are greyed out).

Any help is very appreciated.

---

### Post by mook765 on 2016-08-27
You booted Boot-Repair in CSM-mode (legacy-mode).
This is not really helpful, your operating-systems are installed in UEFI-mode.
Please run Boot-Repair again, but make sure to boot in UEFI-mode, then post the new URL of the Boot-Repair-summary.
Then we can see more...

---

### Post by howefield on 2016-08-28
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by davidbogner on 2016-08-28
Thank you for that. That was an important hint. I now tried for 5 hours to boot in EFI mode, without success but the last try did the job finally. All the USB-devices (I used SD-cards within a card reader, maybe that was a problem too) with a gpt partition table were not recognised. But then I inserted the old sd-card (from which I booted in legacy-mode) after starting into the boot manager and suddenly there appeared the option "EFI boot" in the boot manager. That was pure luck. I could have tried forever creating differenct boot media.

So the actual report from the boot-repair is this:
[http://paste2.org/9fY9sh5x](http://paste2.org/9fY9sh5x)

Next step would be running boot-repair again (still can not configure any MBR options in advanced mode, but maybe that is not necessary)?

Thank you for your advice.

---

### Post by davidbogner on 2016-08-28
So I ran boot-repair. This is the output:

[http://paste2.org/nMKF8G70](http://paste2.org/nMKF8G70)

I will now try a restart......

---

### Post by davidbogner on 2016-08-28
OK. I am now preparing some coffee for the next hours of troubleshooting. Boot repair resultat in following:

-> Booting now directly into Mac OS X

But I can now boot into EFI-boot medium with the following trick:

-> Hold option key on boot
-> Wait for boot manager to be shown
-> Remove and insert my sd-cards into my card reader again
-> EFI boot shows

What is next: As I do use  Ubuntu 95%, I want to have a genuine dual boot again. Apparently there are some "new" approaches how to dual boot without refind. But first step would be to be able to boot into my Ubuntu installation. Maybe I will try to modify grub.cfg on my usb-boot device. or install ubuntu on another device and then hopefully have the option to boot Ubuntu from my Mac hard drive too.

Any better idea is always appreciated.

---

### Post by oldfred on 2016-08-28
You show rEFInd installed.
Not sure that Boot-Repair fixes that.

       [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

### Post by davidbogner on 2016-08-28
> **oldfred said:**
> You show rEFInd installed.



Yes I installed refind on Ubuntu, but I deleted the files mentioned in [http://www.rodsbooks.com/refind/installing.html](http://www.rodsbooks.com/refind/installing.html) for uninstalling refind on linux:

/boot/refind_linux.conf, 
 /etc/refind.d

I also installed refind on Mac. But right now, after running boot-repair, it seems to be disabled and I am booting straight into Mac OS X when I turn on the computer.

My next goal is to be able to boot into Ubuntu again. The final goal remains to have a working dual boot system again....

Any idea if [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd) will help for being able to boot again into my Ubuntu installation?

---

### Post by davidbogner on 2016-08-28
I will try that, now:

[https://wiki.ubuntuusers.de/GRUB_2/Reparatur/](https://wiki.ubuntuusers.de/GRUB_2/Reparatur/)

---

### Post by davidbogner on 2016-08-28
YESSSS. Now my system boots directly into Ubuntu. In order to to boot Mac OS X again, I have to press the option key until the Mac boot manager appears. So maybe in some near future I will also have GRUB to show me the boot options again in order to be able to boot into Mac OS X from GRUB too from time to time.

---

