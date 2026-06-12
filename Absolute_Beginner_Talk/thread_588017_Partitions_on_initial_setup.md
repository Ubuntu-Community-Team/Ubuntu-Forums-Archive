---
title: "Partitions on initial setup"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by aicoma on 2007-10-23
HI  folks,
first post after first installation of Ubuntu 7

I have followed all the instructions and installed Ubuntu from a CD on my windows XP intel machine  i created. All went fine except when i chose to create a partition size for what i thought was going to be for the Ubuntu filesystem, it appear to have done the opposite. 

The result is i know have 50GB allocated to windows XP (NTFS) and 180GB to Ubuntu (EXT3). Is it easy to re-jig these sizes without losing my XP data using the Gparted application....? 

I also appear to have about 3.3gb FAT32 partition /dev/sda2 and im not sure what this is for.
Any guidelines much appreaciated

:confused:

---

### Post by LaRoza on 2007-10-23
> **aicoma said:**
> HI  folks,
first post after first installation of Ubuntu 7

I have followed all the instructions and installed Ubuntu from a CD on my windows XP intel machine  i created. All went fine except when i chose to create a partition size for what i thought was going to be for the Ubuntu filesystem, it appear to have done the opposite. 

The result is i know have 50GB allocated to windows XP (NTFS) and 180GB to Ubuntu (EXT3). Is it easy to re-jig these sizes without losing my XP data using the Gparted application....? 

I also appear to have about 3.3gb FAT32 partition /dev/sda2 and im not sure what this is for.
Any guidelines much appreaciated


If you haven't tweaked Ubuntu yet, wipe it with Gparted (delete that partition and any other partition created that you are not using).

Then, increase XP's partition to a size you want Make a new partition of a size you want, format as EXT3, then make a swap partition, 512 MB if you don't hibernate, more if you do.

Then reinstall Ubuntu to those partitions.

I would suggest keeping the small Windows partition, and shrinking the Ubuntu partition, then creating a larger partition you can use for sharing data.

---

### Post by aicoma on 2007-10-23
there was i thinking i could do a quick resize in Gparted !
oh well, ill look into what you suggested, how do i increase my windows partition once ive deleted the Ubuntu one ?

thanks again

---

### Post by steve.horsley on 2007-10-23
Sounds like you have 50G too much allocated to XP, to me. Still, its your 'puter.

I'm not sure that gparted will resize NTFS. I suggest you use gparted (from the installer CD) to remove the Ubuntu partition, then run the installer again and have another fiddle with that re-sizing slider. 

Be aware that removing the Ubuntu partition will break the bootloader and you will not be able to boot windows until you replace the bootloader from either the windows installer CD or by perfrming another Ubuntu install.

---

### Post by aicoma on 2007-10-23
thanks ill give that a try steve,

regards

Marc

---

