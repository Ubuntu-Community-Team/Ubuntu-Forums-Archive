---
title: "Ubuntu Dual Boot Manager"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by divisortheory on 2007-06-02
I had ubuntu installed and then installed Windows on a different partition.  Windows removed the ubuntu boot manager, so now I want to get ubuntu to rescan all my drives and partitions and rebuild the boot manager.  How do I do this?  At the moment I can't even figure out how to get back into my old ubuntu installation at all.  I booted from the CD, is there a way to do it from there?

---

### Post by mikewhatever on 2007-06-02
You can reinstall the boot loader (Grub) using this guide 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub#head-09167948173503db5923da717a106f0c3aac1cd2](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub#head-09167948173503db5923da717a106f0c3aac1cd2)

---

### Post by divisortheory on 2007-06-02
I tried this but maybe I'm doing something wrong.  When I open up the grub shell from the terminal, I do as instructed by typing:

find /boot/grub/stage1

However, the response I get is:

Error 15: File not found

---

### Post by ugm6hr on 2007-06-02
I think you need to try the "Using the Desktop/LiveCD and Overwriting the Windows bootloader" section.

(Otherwise you can keep the Windows bootloader and use Grub4DOS).

---

### Post by divisortheory on 2007-06-02
Ok, I went through those steps and everything worked.  Except the part where it actually did anything.  The output from the commands seemed to indicate everything was successful, but when I rebooted, it just went straight back into Windows, no boot loader at all.

---

### Post by ugm6hr on 2007-06-02
> **divisortheory said:**
> Ok, I went through those steps and everything worked.  Except the part where it actually did anything.  The output from the commands seemed to indicate everything was successful, but when I rebooted, it just went straight back into Windows, no boot loader at all.

Hmmm... not sure what happened.  I've never had to reinstall GRUB myself.  I have used the Windows bootloader to access GRUB though.  There might be enough info/links in this thread to help you use Grub4DOS:
[http://ubuntuforums.org/showthread.php?t=457015&highlight=grub4dos](http://ubuntuforums.org/showthread.php?t=457015&highlight=grub4dos)

**I've cut and paste the bits you need:**

Download Grub4dos: [http://sourceforge.net/project/showfiles.php?group_id=104188](http://sourceforge.net/project/showfiles.php?group_id=104188) (you only need the *grldr* file in the .zip file)

Add (and save) the following line at the end of C:\boot.ini (this file is hidden) as an Administrator Windows user:

   C:\grldr="Ubuntu"

Then copy *grldr* to C:\, and create the GRUB4DOS configuration file at C:\menu.lst (which you can just copy from your original menu.lst (/boot/grub/menu.lst) to C:\ from within Windows if you install [http://www.fs-driver.org/](http://www.fs-driver.org/))

Next time you start windows, there is a new option "Ubuntu" which can be used to start GRUB for DOS. This should then give a second prompt for Ubuntu.  If this works, re-edit C:\menu.lst and change the time setting to 0 to make it default to full Ubuntu.

---

