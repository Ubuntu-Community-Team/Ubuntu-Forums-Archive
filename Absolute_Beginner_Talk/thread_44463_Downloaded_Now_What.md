---
title: "Downloaded: Now What?"
date: 2005-06-26
forum: Absolute Beginner Talk
---

### Post by Valet on 2005-06-26
It seems like everytime I try to burn the downloaded Install CD, and I bring it up to my freshly home built PC, the CD drive won't detect the CD.  I ahve no floppy drive.

Do you have to modify the CD Image to be Bootable before you burn?  If so I would appreciate it if someone told me how.

---

### Post by Kvark on 2005-06-26
Here is a few ideas.

Make sure your computer does boot from CDs. Try with another CD that you know is bootable. You may have to change bios settings.

Make an MD5 checksum of the ISO file and compare to the checksums on the download site to make sure your download wasn't corrupted.

Make sure you burned the image in the correct way (no compression, directCD formatting or other stuff, just burn from image) and without modifying it in any way.

---

### Post by Valet on 2005-06-26
I know for a fact that my CD-ROM supports bootable disks due to recently trying to install Mandriva, then having it just die halfway through the installation.

And does decompressing or "extracting" the file count as modifying?  Cause that just might be the problem...   ](*,)

---

### Post by Xian on 2005-06-26
[QUOTE=Valet]Do you have to modify the CD Image to be Bootable before you burn?  If so I would appreciate it if someone told me how.[/QUOTE]
No, if you've correctly burned the ISO then it should boot as long as you have your BIOS properly configured. Read the section [Boot Device Selection](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch03s06.html#boot-dev-select) within the install manual for further instructions.

---

### Post by Valet on 2005-06-26
Ok, I'm burning the image now.

---

### Post by Kvark on 2005-06-26
[QUOTE=Valet]And does decompressing or "extracting" the file count as modifying?  Cause that just might be the problem...   ](*,)[/QUOTE]

Yeah, that would be the problem, after you burn it from image and browse around on the CD all the files will be there. There is no need to extract it before burning.

---

### Post by paul_earl on 2005-06-26
I downloaded and burnt a CD (on windoze).  It won't boot!  If I display the directory 
 it shows one file: ubuntu-5.04-install-i386.iso

If I display the directory from a 4.10 CD, it has 8 folders and a couple of text files in
the root directory.  

Doesn't there have to be some program that unpacks the .iso file before burning the CD?

---

### Post by Kyral on 2005-06-26
[QUOTE=paul_earl]I downloaded and burnt a CD (on windoze).  It won't boot!  If I display the directory 
 it shows one file: ubuntu-5.04-install-i386.iso

If I display the directory from a 4.10 CD, it has 8 folders and a couple of text files in
the root directory.  

Doesn't there have to be some program that unpacks the .iso file before burning the CD?[/QUOTE]
 You cannot burn the ISO directly. Fire up your burning proggy and find the "Burn Disc Image" or similar option. Use THAT to burn the ISO :D

---

### Post by poofyhairguy on 2005-06-26
Dear poster....you want this page;

[https://wiki.ubuntu.com/BurningIsoHowto?highlight=%28iso%29](https://wiki.ubuntu.com/BurningIsoHowto?highlight=%28iso%29)

---

