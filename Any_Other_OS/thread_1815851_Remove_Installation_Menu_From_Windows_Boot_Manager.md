---
title: "Remove Installation Menu From Windows Boot Manager"
date: 2011-08-01
forum: Any Other OS
---

### Post by mardangga on 2011-08-01
Hii....

I've finished the installation of Debian Squeeze using Installer loader from Windows. But the Installer menu is still appear on Windows Boot Manager.
I've try to uninstall the "Installer Loader" from Windows and I got an error message about BCDEDIT (if I'm not wrong), during uninstallation process.
I ignore it,  and continue the uninstallation process until complete. But, After I reboot my computer, the Installer menu is still appear on Windows Boot Manager.
Can anyone help me to fix this problem??
Oh, I almost forgot, I'm using Windows Vista Business SP2.

Thank You 4 the attention 'n sorry about my poor English :)

---

### Post by garvinrick4 on 2011-08-01
Do not mess with Windows boot loader BCD and if you have you might have to reinstall it.
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
Did you install grub2 when you installed Debian? If not then use the Debian live Cd (install cd) and install grub to sda: I am using sda5 as linux install (USE YOUR OWN) "sudo fdisk -l" (lower case L) without quotes in terminal will give you your linux install number:
```
sudo mount /dev/sda5 /mnt
``````
sudo grub-install --root-directory=/mnt /dev/sda
```Now reboot into debian:

#I believe debian grub2 comes without os-prober to add other installs to boot menu and in your config file: While in debian run this in a terminal just in case I remember right.
```
sudo apt-get install os-prober
```Should be able to boot into both now as a grub menu entry:
If not run this below and post back here with Results:
```
#Download this Script to DESKTOP:
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
#Open a Terminal and use these four commands one at a time. (copy and paste them is easiest)
cd Desktop
unzip boot_info_script060.zip
chmod +x boot_info_script.sh
sudo ./boot_info_script.sh
#There will now be a file called RESULTS  on Desktop copy and paste to this Thread:
Use code tags and will be easier to read: 
(Highlight all text after pasting and click on # sign in upper right of message box)

1. You are changing directory's to Desktop
2. You are unzipping 
3. You are making spript executable
4. You are executing the Script
5. Done Results on Desktop 


```

---

