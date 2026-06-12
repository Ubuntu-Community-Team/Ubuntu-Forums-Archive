---
title: "[SOLVED] Menu.Lst missing"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by Roger Gundberg on 2008-01-15
When installing Ubuntu nearly 90% is indicated by the progress bar, a pop-up/over says Executing grub install (HD0) failed. This is a fatal error. consequently the Menu.lst was not written. I tried Super GRUB Disk but it relies on Menu.lst as well, and it's not there. I ran this script and the end product indicated no such directory/file.

sudo fdisk -l

ls /media/disk/boot

ls /media/disk/boot/grub

cat /media/disk/boot/grub/menu.lst


I have loaded and erased Ubuntu four times. What causes this?

---

### Post by bumanie on 2008-01-15
Have you checked the md5 checksum of the download and verified disc burn errors are not present? Also, what are you system specifications?

---

### Post by stchman on 2008-01-15
> **Roger Gundberg said:**
> When installing Ubuntu nearly 90% is indicated by the progress bar, a pop-up/over says Executing grub install (HD0) failed. This is a fatal error. consequently the Menu.lst was not written. I tried Super GRUB Disk but it relies on Menu.lst as well, and it's not there. I ran this script and the end product indicated no such directory/file.

sudo fdisk -l

ls /media/disk/boot

ls /media/disk/boot/grub

cat /media/disk/boot/grub/menu.lst


I have loaded and erased Ubuntu four times. What causes this?

You may have a corrupt install disc.  I recommend that you burn the disc at no greater than 8x.  Also check the MD5 sum.  

Here are the MD5 sum values for all Ubuntu Gutsy versions.

```

ebf7ad055bc39634065daa10de980d7e *ubuntu-7.10-alternate-amd64.iso
9a4ae3cfd68911a861d094ec834c9b48 *ubuntu-7.10-alternate-i386.iso
61c87943a92bc7bf519da4e2555d6e86 *ubuntu-7.10-desktop-amd64.iso
d2334dbba7313e9abc8c7c072d2af09c *ubuntu-7.10-desktop-i386.iso
43ff753b260729b12c7d21d3a6db8c73 *ubuntu-7.10-server-amd64.iso
7d88cd87df509a740d9f47b9bbf1375e *ubuntu-7.10-server-i386.iso
5308a79f5e652edba5be84644ee14b09 *ubuntu-7.10-server-sparc.iso
```

If you are using Windows you will need to get an MD5 checksum program.

---

### Post by rfruth on 2008-01-15
tried the alternate CD ? You can choose LILO or GRUB

---

### Post by dstew on 2008-01-15
I have heard of this problem before. I suspect there are some machines in which the BIOS is set up to protect the MBR somehow. What is your hardware?

---

### Post by adrian15 on 2008-01-16
> **Roger Gundberg said:**
> I tried Super GRUB Disk but it relies on Menu.lst as well, and it's not there. 

Linux -> Boot Linux Directly

option does not rely on menu.lst although most of the times cannot find the kernel and initrd and it fails to boot, but it's worth a try.

adrian15

---

### Post by Roger Gundberg on 2008-01-20
I believe this was a misunderstanding on my part inasmuch as the manual partitioning of a drive. The partition needed a mount point '/' and to format as ext3. Then informed me that a  swap file  would be a good Idea. I went back only to  discover  that of the  many configurations  none  indicated  'SWP'  for  swap file or any other configuration that made sense. I skipped the swap file, and proceeded with the installation. If I may digress, the manual setup process should not be 'so manual'. All OS's need a placement to start, this is common sense. If Ubuntu needs a swap file then the software should make a determination and  an effective  solution  be applied. As it turned out the program  installed  quite well  once the  'copy to entire disk, option was chosen (it did not take the whole disk, but only half of a  40Gb  drive). At any rate ,I have installed  and upgraded Ubuntu, and am happy once more. Thank you for your help and attention.

---

### Post by bobpaul on 2008-01-21
> **Roger Gundberg said:**
>  I skipped the swap file, and proceeded with the installation. If I may digress, the manual setup process should not be 'so manual'.

I have to disagree. Manual NEEDS to be absolutely manual. There are many times I've reinstalled, or installed along side other *nix systems and wanted the installer to use particular partitions or even share them between systems. Using manual I can be sure that works correctly. If the installer made any choices by itself at all during manual, I would probably be forced to clean up a large mess afterwards.

You know, like if I were trying to do anything fancy during a Windows installation. :-x

What you want, and what might not be a bad idea, is an option to have a Guided/Manual hybrid. Perhaps something that starts with a guided partition scheme, but then allows the user to view the scheme proposed and manually make changes or just accept it. That wouldn't be so bad...

---

