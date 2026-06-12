---
title: "Installing Ubuntu 6.10 on iBook G3 600 Mhz"
date: 2007-08-29
forum: Apple PPC Users
---

### Post by Pierre Valtorta on 2007-08-29
Hello,

   I'm trying to install Ubuntu 6.10 on my iBook G3 600 Mhz with Mac OS 10.1.5. I downloaded this version from a mirror site. When I try to boot the CD, by pressing the letter "c" as the computer is starting, my computer does not boot Ubuntu Installer, instead it starts Mac OS X. From Mac OS X, I decided to investigate the Ubuntu CD I had burned. This is the file I have on the CD:

    ubuntu-6.10-desktop-powerpc.iso

** Note that the file image is a blank page with top left corner folded and containing a Disk image.

I double clicked on the file and then Disk Copy opened and the following message appeared:

   Mounting ubuntu-6.10-desktop-powerpc.iso

  Then a folder called

   Ubuntu_PowerPC_edgy 

appeared on my desktop, it has the following folders:

   - casper
   - dists
   - etc
   - install
   - pics
   - pool
   - ppc
   - preseed
 
and the following files

   - cdromupgrade
   - md5sum.txt
   - README.diskdefines

Then I burned a new CD containing this folder Ubuntu_PowerPC_edgy and
I tried to boot the Installer using it, and the same result happened.

   Then I tried booting the Installer from a Hard Disk partition, that is I copied the files:

   - initrd.gz
   - vmlinux
   - yaboot
   - yaboot.conf

to the 2nd partition. I then restarted my computer and held the following keys:
 
   option + command + o + f

which brought me to a OpenFirmWare session. At the prompt, I typed

   0 > boot hd:2,yaboot

and  OpenFirmWare printed a message stating that it did not recognize the partition number. 

   I have two questions:

   1) What am I doing wrong ?
   2) How do you obtain information about a partition number of a partition ?

Thank you

---

### Post by BryannMelvin on 2007-08-29
It sound as if you or someone burned your cd as a data cd and not an iso image.

I have never used either a windows or mac OS computer to burn an iso ( I migrated from OS/2 to Linux and Solaris) but the Ubuntu support and wiki pages have specific instructions on how to burn and Ubuntu ISO cd from these operating systems.

I DO advise using the Alternate cd not the live CD to install Ubuntu on your ibook. I had problems with the edgy live cd on my ibook 500 g3 and None with the alternate

---

### Post by pxwpxw on 2007-08-30
> **Pierre Valtorta said:**
> Hello,

   I'm trying to install Ubuntu 6.10 on my iBook G3 600 Mhz with Mac OS 10.1.5. I downloaded this version from a mirror site. 
   I have two questions:

   1) What am I doing wrong ?
   2) How do you obtain information about a partition number of a partition ?

Thank you


1. As BryannMelvin suggests, you are burning the iso as a file.
and the Alternate Install is also a good idea.

2.   Your open firmware boot command should still boot yaboot, if you have the right partition and the files are in the Macos partition root, not the desktop or a folder, but will then fail when looking for the CD.

3. You can get partition numnbers from macosx: terminal , if your macosx version has these commands.
```

diskutil list
###( the disk0s* numbers, not the list item numbers).
sudo pdisk -l

```

4. You can in fact run an Alternate install ISO (not burned) from your macosx partition, just using a different set of vmlinux and initrd, yaboot and yaboot.conf from hd-media images
See the Install Guide for Alternate Install.

5. Or you can burn the iso correctly (so it writes the files you listed, not just the iso image file). Macosx diskutility if you have a mac with a burner, or Nero Burning Rom I have used on a PC for burning a Mac ppc iso.

6. Use ubuntu704, no reason I know of to use 610.

---

### Post by senuxis on 2007-08-30
you need to burn the iso with disk utility. to do that right click on the iso and choose to open it with disk utility, you should then see the iso listed in the left side of the window, select your iso file name and then click on the yellow burn icon, pop in your cd, and then click on burn.

---

### Post by curly_nostrill on 2007-08-31
I'm not sure about 10.1.5 but in 10.3.9 I used in a terminal```
hdiutil burn <ubuntudisk.iso>
``` where ubuntu disk is the exact name of your .iso image.  Terminal is in the Utilities folder inside the Applications folder... on 10.3.9 anyway.

Super easy and makes a perfect disk every time... as long as your cd writer is ok.

---

