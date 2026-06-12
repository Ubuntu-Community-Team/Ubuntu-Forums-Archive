---
title: "Help Please: GRUB2: Choose next OS to boot from Ubuntu or from WinXP"
date: 2012-08-20
forum: Any Other OS
---

### Post by silentquasar on 2012-08-20
[These instructions]("http://www.adaptivecomputing.com/resources/docs/adaptivehpc/appendixA_automate_dualboot.php") explain how, with GRUB v1, to make it possible to choose which OS will boot next, either from Windows or Linux, by redirecting GRUB to look for a menu.lst file on a separate FAT32 partition. Either Ubuntu or Windows can then modify that menu.lst file to determine the next OS that will boot.

Does anyone know how this could be done in GRUB2? I'm thinking something could be put in the 40_custom or 41_custom file in /etc/grub.d/, but I'm not sure what.

---

### Post by OM55 on 2012-08-20
Hello silentquasar,

Grub2 does not have a "menu.lst" text file option and its structure is quite different.
However, there is a simple graphical tool that will allow you to do the same things with ease, with no need to learn the complexities of Grub2.

To install 'grub-customizer' just type in terminal the following commands:

```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer

```You will need to accept (by "Yes") to allow adding this PPA to your repository list and also the installation of grub-customizer, but it works very well.

Hope that helps!

---

### Post by oldfred on 2012-08-21
Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

I boot several ISO directly. drs305 posted this tip to use a config file:

```

menuentry 'Live ISOs' {
configfile (hd2,4)/iso/livecdimage.cfg
} 

```

and my livecdimage.cfg is just more typical grub2 menu entries in a text file in my sdb4 partition or (hd2.4)

I think my old os/2 had a dd type script that in Windows wrote the os/2 boot to the MBR and in os/2 wrote the Windows boot loader to the MBR.

You can also leave a Windows like boot loader (Lilo) that chainloads to the PBR - partition boot sector and use commands to move boot flag from Windows to Ubuntu. You do have to install grub2's boot loader to the PBR which is not normally suggested. Lilo works better than the Windows boot loader as it will work with a boot flag on a logical partition where Windows only can boot primary partitions.

You can leave the Windows boot loader in the MBR, and use a USB flash drive with a grub2' boot loader and when flash is inserted boot that, otherwise it defaults to the Windows.

---

### Post by silentquasar on 2012-08-21
I'll have to try some of what you're suggesting. My bigger issue is that I'd like to alternate Windows/Linux on every reboot, or be able to decide which system I boot to via script. This will be a remotely deployed system.

---

