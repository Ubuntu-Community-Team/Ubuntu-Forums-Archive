---
title: "IBM ThinkPad X40 install hangs"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Hookheathen on 2007-05-16
Hello,
I am experiencing problems when attempting to load Feisty F onto my Thinkpad X40 - each attempt the partitioning window hangs. I have seen other possible solutions like running fdisk and removing the partitions before installing Ubuntu, but what then? Apart from removing the IBM programs would this action dispense with Win XP altogether? This is not what I wish to do and wonder if by removing these partitions I could still dual boot into Win - in case of extreme need!

Any guidance gratefully appreciated.

HH

---

### Post by terdon on 2007-05-16
First of all, are you sure it hangs? It took ages when I installed edgy but did actually work in the end (i did not partition for feisty).

Another thing you can try is the alternate cd with the text installer.

Finally, if you remove the partitions then yes, you will lose windows altogether.

---

### Post by girishv on 2007-05-16
Hi,

One easy way is to create free space on the hard disk within windows. Open the disk manager (under my computer-> manage computer etc) and then resize the drive where you want to install ubuntu (usually your d-drive or c-drive). And then in the initial boot of ubuntu with the live CD select the second option
use safe graphics mode

Girish

---

### Post by Hookheathen on 2007-05-16
Thanks for the suggestion. Regret not much success. In XP Computer Management - Disk Management it shows IBM Preload with 51.59 GB NTFS and another named IBM Service with 4.29 GB FAT32, but I am unable to find a way to resize the IBM Preload partition. Any suggestions?

---

### Post by oilchangeguy on 2007-05-16
this is an older machine. and depending on the specs, you might do better using version 6.06.

---

### Post by Hookheathen on 2007-05-16
Spec is; Pentium 1.2Ghz, 1024 MB, 40gig. 12.1" TFT. So not that old, in fact younger than my Fujitsu Amilo which loaded up Ubuntu without a murmur.

---

### Post by nickpaton on 2007-05-16
Try the old Dapper trick which I've seen a few people using successfully on Feisty -

At the initial choices screen, press F6 other Options where you will see a command line.

Type 

```
noapic nolapic
``` 

at the end and hit enter.

Other than that installing with alternative using text mode as already suggested.  It seems that quite a few PC's require this for Feisty for some reason.

HTH

---

### Post by Hookheathen on 2007-05-17
Thanks for the advice. 
After 20+tries and a few self-induced diagnostic pages of interrogating the hard drive, feisty  loaded up all by itself and I used the guided partitioning of the hard drive. So I now have feisty working...... well partially. 

The more disturbing thing is I am unable to switch on the wireless. There is no apparent external mechanical switch as on other laptops and when the IBM stuff was working OK I could turn on the wifi via a screen application. Is there a way to turn on this piece of hardware in Ubuntu? The installation process has seemingly eaten the IBM (windows) partitions and I am unable to boot into XP and turn on the wifi that way. I am stuck. Please assist.

---

### Post by terdon on 2007-05-17
You could try using wlanassistant (install from synaptic), that should let you switch on the wireless.

---

### Post by nickpaton on 2007-05-17
To work out what wireless chipset you are using please could you post the result of:

```
lspci -v | less
```

It is a very long output, so possibly you may want to only post the results of the networking and ethernet sections.

If in doubt post the whole lot and we can find the relevant section.

From there we can find the best way to install and set up the correct driver.

---

### Post by nickpaton on 2007-05-17
> **Hookheathen said:**
>  The installation process has seemingly eaten the IBM (windows) partitions and I am unable to boot into XP and turn on the wifi that way. I am stuck. Please assist.

To see if your windows partition still exists please can you post the output of

```
sudo fdisk -l
```

I must admit that if you have tried to install Feisty 20 or so times, then I would be tempted to completely wipe the whole of the HDD and to first reinstall XP followed by Feisty using the method you've found actually works.

It does seem that whatever you have done to install Feisty has damaged the bootloader and is preventing you from carrying out a dual install.

BTW what type of Feisty installer CD are you using?  Is it the alternative one?

EDIT: Have a look at [this]("http://ubuntuforums.org/showthread.php?t=441248") recent post about repairing the Windows MBR and Ubuntu grub - could solve your dual boot problem without needing to reinstall everything.

---

### Post by Hookheathen on 2007-05-24
> **nickpaton said:**
> To work out what wireless chipset you are using please could you post the result of:

```
lspci -v | less
```

It is a very long output, so possibly you may want to only post the results of the networking and ethernet sections.

If in doubt post the whole lot and we can find the relevant section.

From there we can find the best way to install and set up the correct driver.

Sorry for the delay in replying. The dual boot failed and XP was damaged preventing me to WiFi the internet, my only access at this time. So I had to reformat the HD and restore to IBM factory settings - a ruddy chore especially going through WIN registration.

Rather than risking a repeat of this process and losing WiFi access, I have not yet installed Ubuntu but can advise the 11b/g wireless LAN mini PCI adapter is manufactured by Atheros Communications. Does this help in identifying the appropriate driver?

---

