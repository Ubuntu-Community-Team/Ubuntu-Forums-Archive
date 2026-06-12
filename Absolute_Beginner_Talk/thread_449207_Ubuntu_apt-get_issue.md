---
title: "Ubuntu apt-get issue"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by haw730 on 2007-05-20
Ok, Im running Feisty 7.04 and I am trying to get this ndiswrapper up and running. I know what I need to do but when I try the apt-get install build-essential linux-headers-$(uname -r) from the cd everything appears ok and then I get this error 
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/pool/main/g/gcc-4.1/g++-4.1_4.1.2-0ubuntu4_i386.deb  MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/pool/main/g/gcc-defaults/g++_4.1.2-1ubuntu1_i386.deb  MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/pool/main/d/dpkg/dpkg-dev_1.13.24ubuntu6_all.deb  MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/pool/main/b/build-essential/build-essential_11.3_i386.deb  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
That is the only issue I am having. I get the same error when i go through synaptec manager. Does this mean there is something wrong with the burn or the image file i downloaded. Any help would be greatly appreciated.
Thanks (I hate bein a noob)

---

### Post by Outrunner on 2007-05-20
md5sum mismatch means that, yes, there's probably something wrong with the .iso you downloaded. You might want to download another .iso(check this out aswell [https://help.ubuntu.com/community/UbuntuHashes?highlight=%28hash%29](https://help.ubuntu.com/community/UbuntuHashes?highlight=%28hash%29)) and burn a fresh disk.

---

### Post by haw730 on 2007-05-20
will I have to reinstall ubuntu? if so will I mess up any partitioning?

---

### Post by haw730 on 2007-05-20
Ok I am trying to move step by step but i always seem to hit a snag. now it is giving me this error. I have made a new cd from a new iso file and this is the error i get when trying to run the apt-get install commmand:

> Err cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418) feisty/main build-essential 11.3
  Unable to unmount the CD-ROM in /cdrom/, it may still be in use.
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/pool/main/l/linux-source-2.6.20/linux-libc-dev_2.6.20-15.27_i386.deb  Unable to unmount the CD-ROM in /cdrom/, it may still be in use.
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/pool/main/g/glibc/libc6-dev_2.5-0ubuntu14_i386.deb  Unable to unmount the CD-ROM in /cdrom/, it may still be in use.
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.2-0ubuntu4_i386.deb  Unable to unmount the CD-ROM in /cdrom/, it may still be in use.
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/pool/main/g/gcc-4.1/g++-4.1_4.1.2-0ubuntu4_i386.deb  Unable to unmount the CD-ROM in /cdrom/, it may still be in use.
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/pool/main/g/gcc-defaults/g++_4.1.2-1ubuntu1_i386.deb  Unable to unmount the CD-ROM in /cdrom/, it may still be in use.
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/pool/main/d/dpkg/dpkg-dev_1.13.24ubuntu6_all.deb  Unable to unmount the CD-ROM in /cdrom/, it may still be in use.
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/pool/main/b/build-essential/build-essential_11.3_i386.deb  Unable to unmount the CD-ROM in /cdrom/, it may still be in use.
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

lol. all i want to do is get some internet access.

---

### Post by useResa on 2007-05-23
In your sources.list the cdrom is still mentioned as a source for packages.
You can resolve this in the following way:
Open a terminal (Applications --> Accessories --> Terminal)
Issue the command ```
gksudo gedit /etc/apt/sources.list
```
This will open the sources.list file in an editor.
You will have line (IIRC it is the second line) starting with "deb cdrom".
Place a # in front of it to comment it out and save the file and close the editor.
Next issue the command ```
sudo apt-get update
```

I hope this will solve it for you.

---

