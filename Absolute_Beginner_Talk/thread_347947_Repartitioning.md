---
title: "Repartitioning"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Mets on 2007-01-28
hey guys,

I'm interested in installing Ubuntu in a dual-boot configuration with Windows XP.  I already have XP installed, and my hard drive only has one partition, in the NTFS format, which is entirely taken up with my C drive.  My hard drive here on my laptop isn't huge, so that's why I did this.  Hosing my computer is not an option, which makes the install a little bit harder, and so I have a few questions.

1. Does the Ubuntu installer have a way to safely repartition existing drives?  If not, does anyone know a good, free/open source program that will do the job?

2. Do I need to make a swap partition?  I'd rather not waste the space, and I have 1gig of ram.  I don't think I'll be doing anything too intensive on linux, outside of running MATLAB or something.

3. Can I read and write to my C-drive from Ubuntu?

4. How much space does an install take up and how much space does Ubuntu need?  I have maybe 5 gigs free space now, and I could probably get a few more if needed.  I'm really just looking at trying Ubuntu out, and if I love linux I'll totally reformat later.  So I guess I'm looking for a functional install so I can start using linux and try to get used to the whole dual-boot process, but also have something more permanent  than a live CD.

Thanks a lot!

---

### Post by housam on 2007-01-28
Gparted is the right tool you need it to do the partitioning . you can either downloaded or use the one on the live CD.
You need a swap partition of 1Gb .
You can mount the xp partition after installation and then read and write to the xp files.
5Gb is fare enough for ubuntu.
Boot from the live CD and try ubuntu first it is fully functionally.

---

### Post by SuperTeece on 2007-01-28
I've setup three dual-boot machines with XP/Dapper. Everytime I just let the CD do it for me. The only advice I can give you is to run Disk Cleanup and Defrag in XP before starting the proccess.

---

### Post by matt91 on 2007-01-28
mounting ntfs here > [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

---

### Post by Mets on 2007-01-28
Thanks a lot guys, I guess I'll give it a shot!

Is the 1gb swap drive necessary with dual-boot.  It seems kind of wasteful...

---

### Post by Mets on 2007-02-04
Well, I did it!  Installed and working well, only a few minor issue to iron out.  GParted rocks!  Thanks a lot for your help

---

