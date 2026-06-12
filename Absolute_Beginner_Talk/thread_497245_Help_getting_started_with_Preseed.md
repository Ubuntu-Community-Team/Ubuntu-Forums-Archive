---
title: "Help getting started with Preseed"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by najevi on 2007-07-10
**How do I pass the following boot parameter to the kernel if I am using the ubiquity installer?** 
preseed/file=/media/disk/preseed.cfg

**_BACKGROUND_**
I'm installing from ubuntu-7.04-dvd-i386.iso and have a live boot of ubuntu from that media. 
The answer to my question may be obvious to some but it escapes me!

I quote from  [https://help.ubuntu.com/7.04/installation-guide/hppa/preseed-using.html](https://help.ubuntu.com/7.04/installation-guide/hppa/preseed-using.html)[INDENT]**Loading the preconfiguration file**

                                            If you are using initrd preseeding, you only have to make sure a file named preseed.cfg is included in the root directory of the initrd. The installer will automatically check if this file is present and load it.  
           For the other preseeding methods you need to tell the installer what file to use when you boot it. This is normally done by passing the kernel a boot parameter, either manually at boot time or by editing the bootloader configuration file (e.g. syslinux.cfg) and adding the parameter to the end of the append line(s) for the kernel.  
[/INDENT]I read that how to get the preseed.cfg file included in the initrd is "outside the scope" of that installation guide and I don't trust that my network card will be functioning so I am wanting to try the **file** **method **and **manually **pass the kernel a boot parameter.

I have a preseed.cfg file saved to a floppy and I can see that floppy is mounted at /media/disk so the path to the file is /media/disk/preseed.cfg

Which gives rise to my question:
 **How do I pass the following boot parameter to the kernel if I am using the ubiquity installer?** 
preseed/file=/media/disk/preseed.cfg

$ ubiquity --help 
[FONT=Tahoma]does not reveal anything helpful and there is no man page for ubiquity. 
The [ubiquity README file]("http://codebrowse.launchpad.net/%7Eubuntu-core-dev/ubiquity/trunk/annotate/?file_id=README-20051205083553-550dab3cb68ad622") refers the reader to the "Installation Guide" for this detail ... catch 22 !

[/FONT]Now if you want to really make my day then point me in the direction of a tutorial on how to get the preseed.cfg file into the initrd. Assume that all I know about the initial ramdisk is what google or wikipedia can teach me.

---

### Post by gehel on 2007-08-29
You probably want to read [InstallCDCustomization]("https://help.ubuntu.com/community/InstallCDCustomization#head-7dcb221f59b638ccc230c960b84f7142cb529598"). This will explain how to create a CD with a customized preseed file.

If you want to test your preseed with the standard install CD, you can just pass the option to the kernel :
When the CD boots, press ESC to get a boot prompt, then type "install preseed/file=/media/disk/preseed.cfg".

Note that the preseed will be loaded as soon as the system has access to other media, which mean that you will still have to choose language / keyboard otpions.

---

