---
title: "multiple hard drive troubles"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Kaja_Rang on 2007-07-22
Hello Ubuntu Forums.

I just replaced XP on my computer with Feisty Fawn. It's an older dual processor P3 with two SCSI HD's: an 18GB and an 80GB. When i installed Ubuntu, I formatted the 18GB which had XP, leaving the data on the other HD (named GAMEZ)  intact. The installation went smoothly and I am enjoying the wonderful eye candy of Compiz.

My problem is this:
I can read the files on GAMEZ, but I am unable to delete data on it. When I attempt to delete a file, I am confronted with the following error message: " *path of the file* " cannot be delete because it is on a read only disk.

When i view the properties of the drive, all options for folder access are grayed out.


If there is a way to somehow change the permissions on the drive I would love to hear about it. If not, I would like to recieve advice on how best to format the drive in question

Thank you for your time.

---

### Post by ddrichardson on 2007-07-22
The drive is probably NTFS formatted, have a look for ntfs-3g which will allow you to read/write an NTFS volume.

---

### Post by Kaja_Rang on 2007-07-22
I found ntfs-3g in the add/remove applications list and attempted to download it.

I recieved an error with the following details:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/f/fuse/fuse-utils_2.6.3-1ubuntu2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/f/fuse/fuse-utils_2.6.3-1ubuntu2_i386.deb)
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/n/ntfs-3g/libntfs-3g0_1.328-1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/n/ntfs-3g/libntfs-3g0_1.328-1_i386.deb)
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/n/ntfs-3g/ntfs-3g_1.328-1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/n/ntfs-3g/ntfs-3g_1.328-1_i386.deb)
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/n/ntfs-config/ntfs-config_0.5.5-0ubuntu1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/n/ntfs-config/ntfs-config_0.5.5-0ubuntu1_i386.deb)
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)

---

