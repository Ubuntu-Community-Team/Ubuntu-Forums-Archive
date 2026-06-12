---
title: "Install from ISO to clean system"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by jmooney80 on 2005-11-30
I have been around and have worked on PC's for many years but newbe to Linux world.  I have downloaded an ISO file from Ubuntu and burnt it to CD as directed.  It will not boot in new system.  I have tried using the "make CD Bootable option" when I burn the CD.  I know the system will need to see a operating system to boot from on the disk but all it has is the ISO image.  I dawnloaded and installed isobuster and was able to view the files but am still unsure how to proceed to make a bootable CD install image.  Any direction would be appreciated.
-Joe

---

### Post by ed_d on 2005-11-30
Do you double check your cd when done? I will burn an ISO, then mount it back and make sure that I do not have an ISO coaster, but can see the list of files on it. If I see files other than ISO, I will reboot and make sure that my cd is in the list of bootable options. Smoetimes you may have to make the bootlist cd then floppy then disk, as the cd may take more time to read.

---

### Post by ranf on 2005-11-30
[QUOTE=jmooney80]I have been around and have worked on PC's for many years but newbe to Linux world.  I have downloaded an ISO file from Ubuntu and burnt it to CD as directed.  It will not boot in new system.  I have tried using the "make CD Bootable option" when I burn the CD.  I know the system will need to see a operating system to boot from on the disk but all it has is the ISO image.  I dawnloaded and installed isobuster and was able to view the files but am still unsure how to proceed to make a bootable CD install image.  Any direction would be appreciated.
-Joe[/QUOTE]
[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

---

### Post by Qrk on 2005-11-30
Is your BIOS set to allow a boot to CD? If you burned it right, this is probably your problem.

Getting into your BIOS depends on what computer you have. Most use either Esc, del or F12. It should flash on the screen when you first turn on your computer. (saying something like, press del to enter setup)

Once there, change the boot order so that the computer looks to boot from a CD first, then the hard drive.

---

### Post by jmooney80 on 2005-11-30
Thanks Ed, ranf and Qrk,
I used the [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto) URL and things are proceeding.  I was able to burn a CD that did boot and is now in the process of loading.  I am a Cisco tech and comfortable with command line but have virtually no Unix\Linux experiance.  Trying to remidy that issue as best I can.  If there is anything I can do for you let me know by email [email]jmooney80@hotmail.com[/email].   Yall take care and thanks again.
-Joe

---

