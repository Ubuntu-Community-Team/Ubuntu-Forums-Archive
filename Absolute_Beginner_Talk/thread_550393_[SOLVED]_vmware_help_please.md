---
title: "[SOLVED] vmware help please"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by fontenot_1031 on 2007-09-13
I am running windows 2000 pro on vmware.  I need to know how to copy files to that virtualized operating system.  Internet doesn't work though.  I've tried creating an .iso of the files I need and then mounting it on start up, but for some reason none of those .iso seem to work.  Any other methods?

---

### Post by bodhi.zazen on 2007-09-13
Did you mount the .iso on the CDROM ?

You could burn the files onto a CD, and then use the physical CD.

---

### Post by kh4nh on 2007-09-13
You can download a Windows version of scp which is pscp from **[here]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html")**, and download/copy from your host OS.

---

### Post by fontenot_1031 on 2007-09-13
Mounting the original CD didn't work :(

---

### Post by mustali on 2007-09-13
Are you using vmware player? In that case, a simple change to the vmware configuration file (.vmx) will allow you to specify the name of the iso image and have it automatically mounted. Add/modify the following lines in the vmx file:

```

ide1:0.present = "TRUE"
ide1:0.fileName = "cd_rom_image.iso"
ide1:0.deviceType = "cdrom-image"
ide1:0.autodetect = "TRUE"


```

Most likely you already have the ide1 parameters in the vmx file, simply substitue the above. Replace cd_rom_image.iso with your iso filename of course.

Boot windows and the iso image should appear as a CD-ROM. If the image is bootable and the BIOS is set to boot from CD-ROM before the hard-disk, the machine will boot from the image.

HTH

---

### Post by fontenot_1031 on 2007-09-13
> **mustali said:**
> Are you using vmware player? In that case, a simple change to the vmware configuration file (.vmx) will allow you to specify the name of the iso image and have it automatically mounted. Add/modify the following lines in the vmx file:

```

ide1:0.present = "TRUE"
ide1:0.fileName = "cd_rom_image.iso"
ide1:0.deviceType = "cdrom-image"
ide1:0.autodetect = "TRUE"


```

Most likely you already have the ide1 parameters in the vmx file, simply substitue the above. Replace cd_rom_image.iso with your iso filename of course.

Boot windows and the iso image should appear as a CD-ROM. If the image is bootable and the BIOS is set to boot from CD-ROM before the hard-disk, the machine will boot from the image.

HTH
Thanx for the help, I've already gotten the .vmx configuration to load fl.iso on boot.  But I've been having problems making the .iso.  I am on vmware player

---

### Post by mustali on 2007-09-14
How did you create the iso file? 

This works for me:
```
mkisofs -o /tmp/cd.iso /tmp/directory/

```

where directory has all the files and subdirectories I want to include in the iso.

---

### Post by fontenot_1031 on 2007-09-16
Thanx for all of your help.  I was able to make an .iso from gnomebaker.

---

