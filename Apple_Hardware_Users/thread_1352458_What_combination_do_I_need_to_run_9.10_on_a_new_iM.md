---
title: "What combination do I need to run 9.10 on a new iMac"
date: 2009-12-11
forum: Apple Hardware Users
---

### Post by jamesey on 2009-12-11
I have an Intel Apple iMac March 09-version 9,1, not to be confused with karmic 9.10 I would like to dual boot with macOS just so I can do firmware updates, but it's not mandatory. I don't mind my only boot option being Ubuntu. 

I previously installed 9.04 using rEFIt and the instructions here for dual booting MacOS and Ubuntu. [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation) . That worked perfectly fine. 

I was doing a fresh install with Karmic 9.10 and am have difficulty getting Ubuntu to boot.

First I tried reinstalling macOSX (completely wiping the HD), then rEFIt, then making a partion, and doing a grub install to /dev/sda3. When I tried booting into the Legacy OS (rEFIt doesnt recognize the grub partition) I just see the word GRUB and nothing happens. I even tried fixing the partitions through the rEFIt manager, but that didnt work either. 

Second, I tried reinstalling macOSX (completely wiping the HD, making a partition, and then I skipped installing rEFIt after reading that it's not necessary for GRUB 2. I installed Ubnuntu and set Grub install to /dev/sda3. I still don't get a boot into Ubuntu. 

I guess what I need is a clear process for installing Karmic with grub 2 onto an iMac. Assume I start with only MacOSX. do I need rEFIt? when do I make a partition? Which partion do I install Grub2 to? Is there anything else to do?

---

### Post by neoxro on 2009-12-12
What I had to do on a macbook with rEFIT was to use grub-efi to boot.  Follow Step 18 in this thread [http://ubuntuforums.org/showthread.php?t=1327758](http://ubuntuforums.org/showthread.php?t=1327758)

---

