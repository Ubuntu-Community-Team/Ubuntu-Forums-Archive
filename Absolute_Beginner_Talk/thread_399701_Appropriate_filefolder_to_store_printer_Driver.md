---
title: "Appropriate file/folder to store printer Driver"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Parasitesss on 2007-04-02
Getting ready to install the Hp printer driver, It prompts me to choose a folder to store the printer driver in, I want to be organized, is there a specific file or directory appropriate for me to store this new driver in?

would it be any of these, perphaps?
[PHP]
/bin 	Essential user command binaries (for use by all users)
/boot 	Static files of the boot loader, only used at system startup
/dev 	Device files, links to your hardware devices like /dev/sound, /dev/input/js0 (joystick)
/etc 	Host-specific system configuration
/home 	User home directories. This is where you save your personal files
/lib 	Essential shared libraries and kernel modules
/mnt 	Mount point for a temporarily mounted filesystem like /mnt/cdrom
/opt 	Add-on application software packages
/usr 	/usr is the second major section of the filesystem. /usr is shareable, read-only data. That means that /usr should be shareable between various FHS-compliant hosts and must not be written to. Any information that is host-specific or varies with time is stored elsewhere.
/var 	/var contains variable data files. This includes spool directories and files, administrative and logging data, and transient and temporary files.
/proc 	System information stored in memory mirrored as files.[/PHP]

---

### Post by theninthdimension on 2007-04-06
Parasitesss,

     I have no idea if this helps you or not, but mine is in my /home folder. I think that is where the hplip install directions suggested ([http://hplip.sourceforge.net/install/install/index.html)](http://hplip.sourceforge.net/install/install/index.html)). I don't know if this has any effect on other users or not since I'm the only person who uses my computer.

Jeff.

---

