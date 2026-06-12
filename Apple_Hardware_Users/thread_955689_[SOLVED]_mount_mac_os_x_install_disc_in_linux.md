---
title: "[SOLVED] mount mac os x install disc in linux"
date: 2008-10-22
forum: Apple Hardware Users
---

### Post by jeffhollon on 2008-10-22
can someone tell me how to mount a mac os x install disc in ubuntu?  I am trying just to make an iso of the disc so i can use it with vmware or virtualbox.  i have installed hfsutils and run sudo hmount /dev/scd0 /media/cdrom0  and get this error.  hmount: /dev/scd0: not a Macintosh HFS volume (Invalid argument)

I have no idea where to go from here.  

I am kind of new so need some step-by-step instructions on how to make these isos from the install discs.  File manager in ubuntu shows the title of the install discs correctly, but will not mount no matter what i do.

thanks,

Jeff

---

### Post by mfox on 2008-10-22
You do the installation within VMware or VirtualBox.  In both of these, you start by making a new virtual drive and you follow the steps until you're asked for the installation CD/DVD.  I believe that you need to use a physical drive to install within Linux, but I may be wrong.  If you do, you'll first have to burn your iso to disk.

---

### Post by cyberdork33 on 2008-10-22
> **mfox said:**
> You do the installation within VMware or VirtualBox.  In both of these, you start by making a new virtual drive and you follow the steps until you're asked for the installation CD/DVD.  I believe that you need to use a physical drive to install within Linux, but I may be wrong.  If you do, you'll first have to burn your iso to disk.
Yep, you can use the physical media.

---

### Post by jeffhollon on 2008-10-22
well, i tried that it it says no bootable media in drive.  I want to make the isos so i need to mount it in linux to do that.   i use virtualbox in a linux host and don't want to install on my laptop, just make the isos so that vmware on a different machine will load.  the other machine doesn't seem to like the actual cd, but will install from an older version that is iso format.

---

### Post by tiresia on 2008-10-22
> **jeffhollon said:**
> can someone tell me how to mount a mac os x install disc in ubuntu?  I am trying just to make an iso of the disc so i can use it with vmware or virtualbox.  i have installed hfsutils and run sudo hmount /dev/scd0 /media/cdrom0  and get this error.  hmount: /dev/scd0: not a Macintosh HFS volume (Invalid argument)


You do not need 'hmount'. 
If you Optical Drive is '/dev/hda' type
```
sudo mount -t hfsplus /dev/hda /media/cdrom
```

---

### Post by jeffhollon on 2008-10-22
Now, that is what i needed.  mounted up now.  perfect thanks a ton

---

### Post by tiresia on 2008-10-22
Can you please mark the thread as solved?

---

### Post by jeffhollon on 2008-10-22
new problem,.  i used the sudo command above and got it mounted but when i try to create an iso it just dies out.  so, i thought, see if you can copy the files and i get an error on say the 'library' file that i don't have permissions to copy this file.  I am at a loss at this point.

so close, yet so far

---

### Post by tiresia on 2008-10-22
How are you trying to make an .iso file? Are you working as root?

---

### Post by jeffhollon on 2008-10-22
i'm an idiot, got so excited it mounted forgot to run brasero as root to make the iso.  making iso now, no errors for now.  when it completes error free, i will mark the thread as solved.  thanks again for the help

---

### Post by jeffhollon on 2008-10-22
!!!

---

### Post by Gwyneth Llewelyn on 2012-05-15
Sorry to bump this thread. Using the instructions provided under Ubuntu 12.04 LTS, I get the following errors when mounting the Mac OS X install disk for Snow Leopard:


# sudo mount -t hfsplus /dev/cdrom /cdrom
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg | tail gives me:

[382843.817892] hfs: unable to find HFS+ superblock
[382851.522141] hfs: can't find a HFS filesystem on dev sr0.
[382864.374908] hfs: unable to find HFS+ superblock
[382870.247657] ISO 9660 Extensions: Microsoft Joliet Level 1
[382870.248071] ISO 9660 Extensions: IEEE_P1282
[383006.369544] hfs: unable to find HFS+ superblock
[398360.434317] hfs: unable to find HFS+ superblock

Mounting the same disk under ISO 9660 works flawlessly, but I get only the partition that is usually reserved for a Windows BootCamp install.

My reasoning is that the Mac OS X Install Disk is a hybrid DVD-ROM which requires some special extra setup for Ubuntu to recognise it as such — Macs are able to do that natively, but Ubuntu might require something else, perhaps using a different block device?

Any clue to what I should be doing?

---

