---
title: "GRUB never installing"
date: 2014-08-25
forum: Any Other OS
---

### Post by medwatt on 2014-08-25
Hello,
I'm always wanting to learn Linux and almost always I'm out of luck because something happens that makes me give up. Then after a while I get drawn again into Linux. So what's my problem? Everything installs well except that after the installation GRUB doesn't show up and I end up booting into Win 7. I have tried Ubuntu, Mint, Deepin and never had any luck because GRUB never shows up. The mysterious part is that when I tried installing Ubuntu on a friend's computer, the installer detected Win7 and so before the installation I was asked whether to install Ubuntu alongside Win7, whereas in mine, the installer did not detect that.
I have a lenovo v570 laptop with 750GB HDD partition like this:
100GB - Win 7 - NTFS
250GB - Storage drive 1 - NTFS
220GB - Storage drive 2 - NTFS
8GB - SWAP
Rest - Linux root - EXT4
The first three partitions were done during Win 7 setup. It was during the time I was installing Linux that I created the two additional partitions.

I have no idea why GRUB doesn't boot during startup. I tried using BOOT-REPAIR as recommended in this site and there was an error: **paste.ubuntu.com/8142133. **So, please help me figure out why this is happening with all distros, not just with one. My computer is not UEFI capable so I don't think the problem lies there.
Thanks
Your assistance is greatly appreciated.
[ATTACH=CONFIG]255825[/ATTACH][ATTACH=CONFIG]255824[/ATTACH]

---

### Post by oldfred on 2014-08-25
Moved to other OS, since not Ubuntu.

Not sure if your install if not working because you booted Boot-Repair in UEFI mode? 
Line 522 says you booted in UEFI mode, but it is trying to reinstall in BIOS mode.
But one of the standard grub scripts is missing, so it will not run update.
Lines 819 show missing file, lines before that try the efi install, but fail which they should.

Your installs are in BIOS mode, so be sure to always boot in BIOS mode.

---

### Post by medwatt on 2014-08-25
I've tried the same process in Ubuntu, then Mint and lastly in Deepin. I wanted to install Ubuntu. I had this error so I tried other distros to see if the problem persists. It does.
I've already said that my computer doesn't support UEFI mode. One other problem which I always seem to face is that whenever the computer switches on and I but into the Linux installer I never see the menu which shows the available options. I usually just press ENTER because I know that the first option will always boot into Live mode or install mode.
Please help.

---

### Post by oldfred on 2014-08-25
Please do not post screen shots in line. 
Use advanced editor and paper clip icon to attach screen shots.
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

Boot script said you booted in UEFI mode?

What computer? What model & video chip/card?

From BIOS what boot options do you have?
If it is UEFI you should have two options to boot flash drive from UEFI/BIOS menu, one UEFI and one not UEFI and the not UEFI often is just the name/label of the flash drive.
Or can you use one time boot key often f12 but varies.

---

### Post by medwatt on 2014-08-25
My Laptop is Lenovo V570. I've said it many times. It doesn't support UEFI. For one I only have a BIOS menu. Also I've checked other owners of Lenovo v570. They said they too though they had UEFI but later realized that's not the case.

---

### Post by oldfred on 2014-08-25
Do you get grub menu at all?
Lenovo's do have limited BIOS which can make for issues.

If you are getting grub menu, it may be a video issue. It does look like your specs include dual Intel/nVidia video and how you have to add boot options varies depending on which video mode you boot with. Some let you set it in BIOS others just auto switch.
If booting with nVidia, you need nomodeset, but if Intel then other settings are required and nomodeset usually does not work.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

