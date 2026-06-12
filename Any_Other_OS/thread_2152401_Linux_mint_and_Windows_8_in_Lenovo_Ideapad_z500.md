---
title: "Linux mint and Windows 8 in Lenovo Ideapad z500"
date: 2013-06-07
forum: Any Other OS
---

### Post by mshariful on 2013-06-07
Dear All,
I installed Linux mint in my Lenova  Ideapad z500 (windows 8 preinstalled without any dvd). Linux mint asked me to create a partition
on the hard drive where windows 8 is also installed. I did. Linux mint
worked fine but I could not boot my Windows 8!

Then I used few boot utilities and I was successful to
start Windows 8. While I was in windows I deleted the linux mint partition. But now
when I try to boot windows 8, the boot process begins and I get an error message that something went wrong
and the boot process must restart...and the loop repeats again and again!

Lenovo has a one key recovery...I tried it but it does not work! :( 

I used Ubuntu live CD and made a picture (attached) of my different partitions of my hard drive. I marked
the two partitions in red which were together before installing linux mint. 

My questions is can I merge this two partitions? Will it solve the problem?
I will appreciate any suggestions very much.
Thanks
Shariful

---

### Post by Rebelli0us on 2013-06-07
You accidentally screwed something up. Can you use Windows Recovery to reinstall W8 the way it was?

If so, then use Windows disk manager to "shrink" the largest partition to make room for Linux. 
Then install Linux in manual mode and tell it to install in the newly created space.

---

### Post by mshariful on 2013-06-07
Hi,
Thanks for your reply. I tried one key recovery in Lenova but it does not work! 
My Lenova was shipped without a dvd. So, I do not know how I can use disk manager.
Can I get it somewhere online?

---

### Post by monkeybrain2012 on 2013-06-07
When you installed Mint you installed  the bootloader, now after you deleted mint you deleted it as well hence your machine not bootable. To fix the mbr you need a Windows 8 dvd.
[http://www.redmondpie.com/how-to-fix-windows-8-mbr-master-boot-record/](http://www.redmondpie.com/how-to-fix-windows-8-mbr-master-boot-record/)

I tried to search "windows 8 fix mbr without install disc" nothing came up maybe you can do a search again or ask Mircrosoft.

Edit: easy way, just get rid of Windows and install Mint. :)

---

### Post by oldfred on 2013-06-07
If Windows was pre-installed it boots with UEFI. Was Mint installed in UEFI or BIOS boot mode. Partitions should not have been combined? Windows has its partitions with NTFS and Mint would have its partition in ext4 format.

Are you booting in UEFI mode?

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by mshariful on 2013-06-08
Thanks oldfriend for your reply. I will try your suggestions. 
Have a nice weekend!
-Sharif

---

### Post by simadi on 2013-06-26
hi! does z500 work fine with ubuntu?

---

### Post by oldfred on 2013-06-26
Other models work.

 Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
See post #29 on removing Battery to get it to reset &  boot Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)
Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)
 lenovo u310  - install to SSD
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)
> Discovered that on my Lenovo, if I press F12 repeatedly on startup, it takes me into a Boot Order menu. If I select Windows there, it boots into Windows. I also found that to get into BIOS at startup on my Lenovo tower, you press F1 rather than the F2 I'm used to on other computers.

---

