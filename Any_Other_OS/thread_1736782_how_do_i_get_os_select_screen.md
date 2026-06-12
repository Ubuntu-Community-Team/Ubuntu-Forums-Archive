---
title: "how do i get os select screen??"
date: 2011-04-22
forum: Any Other OS
---

### Post by cbennett a7xftw on 2011-04-22
well i partitiond a drive so i have 250 gbs for windows 7 and 250 gbs on ubuntu 10.10, but i cant boot from ubuntu.  it automatucally goes to windows, if i insert the gparted live disk i can select which partition to boot from but how do i get the screen that asks me which one i want to boot from?

---

### Post by oracle2b on 2011-04-22
Go to: Partition -> Manage flags

If you want to reinstall grub than here's the [guide]("https://help.ubuntu.com/community/GrubHowto#Backup, Repairing and Reinstalling GRUB").

---

### Post by oldfred on 2011-04-22
Boot flag is used by windows (and lilo) but not by grub or grub2. Some BIOS will not let you boot unless you have a boot flag on a primary partition.

Link by oracle2b is to old grub. Unless you upgraded you probably have grub2 which is different on how to reinstall the boot loader to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

If you need detailed help post this:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

