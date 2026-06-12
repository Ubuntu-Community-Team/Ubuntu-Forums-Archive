---
title: "Problem Installing"
date: 2016-12-31
forum: Apple Hardware Users
---

### Post by squeak24 on 2016-12-31
Hey

How is everyone this wonderful day?

I am having issues installing Ubuntu Studio onto my old MacBook (mid-2010 model).

It has 250GB HD with 4GB of RAM, but whenever I try and install Ubuntu Studio I get the following error:

> 
execution grub-install /dev/sda/ failed

Any ideas how to resolve this issue?

---

### Post by howefield on 2016-12-31
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by squeak24 on 2016-12-31
I think I sussed it. I reformatted the disk and changed the mount point to

```
/
```

I will check it out later when I get back home later

Well, the results are in, the mount mount didn't work. When I did the install this time it didn't kick it out when it got to the grub part. I am at a loss, any suggestions will be greatly received!

Happy New Year!!!

OK, I am still having issues with this.

I have done the Boot-Info thing, you can see the details here [http://paste2.org/vZasEmVs](http://paste2.org/vZasEmVs)

Any help is greatly received.

I am getting there slowly, I found this little trick to bypass the grub install:

> ubiquity -b

And [this]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd") very useful page on how to install grub.

But when I get to the installing bit for grub, I get the following errors:

```

root@ubuntu-studio:/# apt install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  grub-common grub-pc-bin libc-dev-bin libc6 libc6-dbg libc6-dev libc6-i386
Suggested packages:
  grub-legacy-doc mdadm multiboot-doc grub-emu xorriso glibc-doc
The following packages will be REMOVED:
  grub-gfxpayload-lists grub-pc grub2-common
The following NEW packages will be installed:
  grub libc6-i386
The following packages will be upgraded:
  grub-common grub-pc-bin libc-dev-bin libc6 libc6-dbg libc6-dev
6 upgraded, 2 newly installed, 3 to remove and 259 not upgraded.
Need to get 13.5 MB of archives.
After this operation, 9,489 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc6-dev amd64 2.23-0ubuntu5
  Temporary failure resolving 'au.archive.ubuntu.com'
Err:2 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc-dev-bin amd64 2.23-0ubuntu5
  Temporary failure resolving 'au.archive.ubuntu.com'
Err:3 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc6-dbg amd64 2.23-0ubuntu5
  Temporary failure resolving 'au.archive.ubuntu.com'
Err:4 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc6 amd64 2.23-0ubuntu5
  Temporary failure resolving 'au.archive.ubuntu.com'
Err:5 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc6-i386 amd64 2.23-0ubuntu5
  Temporary failure resolving 'au.archive.ubuntu.com'
Err:6 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 grub-pc-bin amd64 2.02~beta2-36ubuntu3.2
  Temporary failure resolving 'au.archive.ubuntu.com'
Err:7 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 grub-common amd64 2.02~beta2-36ubuntu3.2
  Temporary failure resolving 'au.archive.ubuntu.com'
Err:8 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main amd64 grub amd64 0.97-29ubuntu68
  Temporary failure resolving 'au.archive.ubuntu.com'
E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.23-0ubuntu5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.23-0ubuntu5_amd64.deb)  Temporary failure resolving 'au.archive.ubuntu.com'

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc-dev-bin_2.23-0ubuntu5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc-dev-bin_2.23-0ubuntu5_amd64.deb)  Temporary failure resolving 'au.archive.ubuntu.com'

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dbg_2.23-0ubuntu5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dbg_2.23-0ubuntu5_amd64.deb)  Temporary failure resolving 'au.archive.ubuntu.com'

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.23-0ubuntu5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.23-0ubuntu5_amd64.deb)  Temporary failure resolving 'au.archive.ubuntu.com'

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i386_2.23-0ubuntu5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i386_2.23-0ubuntu5_amd64.deb)  Temporary failure resolving 'au.archive.ubuntu.com'

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc-bin_2.02~beta2-36ubuntu3.2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc-bin_2.02~beta2-36ubuntu3.2_amd64.deb)  Temporary failure resolving 'au.archive.ubuntu.com'

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_2.02~beta2-36ubuntu3.2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_2.02~beta2-36ubuntu3.2_amd64.deb)  Temporary failure resolving 'au.archive.ubuntu.com'

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/grub/grub_0.97-29ubuntu68_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/grub/grub_0.97-29ubuntu68_amd64.deb)  Temporary failure resolving 'au.archive.ubuntu.com'

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@ubuntu-studio:/# grub install /dev/sda
The program 'grub' is currently not installed. You can install it by typing:
apt install grub
root@ubuntu-studio:/# apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  grub-common grub-pc-bin libc-dev-bin libc6 libc6-dbg libc6-dev libc6-i386
Suggested packages:
  grub-legacy-doc mdadm multiboot-doc grub-emu xorriso glibc-doc
The following packages will be REMOVED:
  grub-gfxpayload-lists grub-pc grub2-common
The following NEW packages will be installed:
  grub libc6-i386
The following packages will be upgraded:
  grub-common grub-pc-bin libc-dev-bin libc6 libc6-dbg libc6-dev
6 upgraded, 2 newly installed, 3 to remove and 259 not upgraded.
Need to get 13.5 MB of archives.
After this operation, 9,489 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc6-dev amd64 2.23-0ubuntu5
  Temporary failure resolving 'au.archive.ubuntu.com'
Err:2 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc-dev-bin amd64 2.23-0ubuntu5
  Temporary failure resolving 'au.archive.ubuntu.com'
Err:3 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc6-dbg amd64 2.23-0ubuntu5
  Temporary failure resolving 'au.archive.ubuntu.com'
Err:4 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc6 amd64 2.23-0ubuntu5
  Temporary failure resolving 'au.archive.ubuntu.com'
Err:5 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc6-i386 amd64 2.23-0ubuntu5
  Temporary failure resolving 'au.archive.ubuntu.com'
Err:6 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 grub-pc-bin amd64 2.02~beta2-36ubuntu3.2
  Temporary failure resolving 'au.archive.ubuntu.com'
Err:7 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 grub-common amd64 2.02~beta2-36ubuntu3.2
  Temporary failure resolving 'au.archive.ubuntu.com'
Err:8 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main amd64 grub amd64 0.97-29ubuntu68
  Temporary failure resolving 'au.archive.ubuntu.com'
E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.23-0ubuntu5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.23-0ubuntu5_amd64.deb)  Temporary failure resolving 'au.archive.ubuntu.com'

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc-dev-bin_2.23-0ubuntu5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc-dev-bin_2.23-0ubuntu5_amd64.deb)  Temporary failure resolving 'au.archive.ubuntu.com'

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dbg_2.23-0ubuntu5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dbg_2.23-0ubuntu5_amd64.deb)  Temporary failure resolving 'au.archive.ubuntu.com'

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.23-0ubuntu5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.23-0ubuntu5_amd64.deb)  Temporary failure resolving 'au.archive.ubuntu.com'

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i386_2.23-0ubuntu5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i386_2.23-0ubuntu5_amd64.deb)  Temporary failure resolving 'au.archive.ubuntu.com'

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc-bin_2.02~beta2-36ubuntu3.2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc-bin_2.02~beta2-36ubuntu3.2_amd64.deb)  Temporary failure resolving 'au.archive.ubuntu.com'

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_2.02~beta2-36ubuntu3.2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_2.02~beta2-36ubuntu3.2_amd64.deb)  Temporary failure resolving 'au.archive.ubuntu.com'

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/grub/grub_0.97-29ubuntu68_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/grub/grub_0.97-29ubuntu68_amd64.deb)  Temporary failure resolving 'au.archive.ubuntu.com'

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@ubuntu-studio:/# apt install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  grub-common grub-pc-bin libc-dev-bin libc6 libc6-dbg libc6-dev libc6-i386
Suggested packages:
  grub-legacy-doc mdadm multiboot-doc grub-emu xorriso glibc-doc
The following packages will be REMOVED:
  grub-gfxpayload-lists grub-pc grub2-common
The following NEW packages will be installed:
  grub libc6-i386
The following packages will be upgraded:
  grub-common grub-pc-bin libc-dev-bin libc6 libc6-dbg libc6-dev
6 upgraded, 2 newly installed, 3 to remove and 259 not upgraded.
Need to get 13.5 MB of archives.
After this operation, 9,489 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc6-dev amd64 2.23-0ubuntu5
  Temporary failure resolving 'au.archive.ubuntu.com'
Err:2 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc-dev-bin amd64 2.23-0ubuntu5
  Temporary failure resolving 'au.archive.ubuntu.com'
Err:3 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc6-dbg amd64 2.23-0ubuntu5
  Temporary failure resolving 'au.archive.ubuntu.com'
Err:4 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc6 amd64 2.23-0ubuntu5
  Temporary failure resolving 'au.archive.ubuntu.com'
Err:5 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc6-i386 amd64 2.23-0ubuntu5
  Temporary failure resolving 'au.archive.ubuntu.com'
Err:6 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 grub-pc-bin amd64 2.02~beta2-36ubuntu3.2
  Temporary failure resolving 'au.archive.ubuntu.com'
Err:7 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 grub-common amd64 2.02~beta2-36ubuntu3.2
  Temporary failure resolving 'au.archive.ubuntu.com'
Err:8 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main amd64 grub amd64 0.97-29ubuntu68
  Temporary failure resolving 'au.archive.ubuntu.com'
E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.23-0ubuntu5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.23-0ubuntu5_amd64.deb)  Temporary failure resolving 'au.archive.ubuntu.com'

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc-dev-bin_2.23-0ubuntu5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc-dev-bin_2.23-0ubuntu5_amd64.deb)  Temporary failure resolving 'au.archive.ubuntu.com'

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dbg_2.23-0ubuntu5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dbg_2.23-0ubuntu5_amd64.deb)  Temporary failure resolving 'au.archive.ubuntu.com'

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.23-0ubuntu5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.23-0ubuntu5_amd64.deb)  Temporary failure resolving 'au.archive.ubuntu.com'

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i386_2.23-0ubuntu5_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i386_2.23-0ubuntu5_amd64.deb)  Temporary failure resolving 'au.archive.ubuntu.com'

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc-bin_2.02~beta2-36ubuntu3.2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc-bin_2.02~beta2-36ubuntu3.2_amd64.deb)  Temporary failure resolving 'au.archive.ubuntu.com'

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_2.02~beta2-36ubuntu3.2_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_2.02~beta2-36ubuntu3.2_amd64.deb)  Temporary failure resolving 'au.archive.ubuntu.com'

E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/grub/grub_0.97-29ubuntu68_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/grub/grub_0.97-29ubuntu68_amd64.deb)  Temporary failure resolving 'au.archive.ubuntu.com'

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@ubuntu-studio:/# apt-get update
Err:1 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial InRelease
  Temporary failure resolving 'au.archive.ubuntu.com'
Err:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
  Temporary failure resolving 'security.ubuntu.com'
Err:3 [http://au.archive.ubutu.com/ubuntu](http://au.archive.ubutu.com/ubuntu) xenial-updates InRelease
  Temporary failure resolving 'au.archive.ubuntu.com'
Err:4 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-backports InRelease
  Temporary failure resolving 'au.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://au.archive.ubuntu.com/ubuntu/dists/xenial/InRelease)  Temporary failure resolving 'au.archive.ubuntu.com'
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease](http://au.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease)  Temporary failure resolving 'au.archive.ubuntu.com'
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease](http://au.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease)  Temporary failure resolving 'au.archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease](http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease)  Temporary failure resolving 'security.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.
root@ubuntu-studio:/# grub-install /dev/sda
Installing for i386-pc platform.
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.
root@ubuntu-studio:/# 
```

Anyone have any ideas on what I am doing wrong?

---

### Post by g33zr on 2017-01-02
Have you searched these forums or elsewhere about installing *any* Linux distro onto a Mac? Are you dual-booting or wiping the drive and installing just Ubuntu Studio? You need to create a separate efi/boot partition if you expect to boot. Again, please search through this forum, there's plenty of useful info.

---

### Post by squeak24 on 2017-01-03
> **g33zr said:**
> Have you searched these forums or elsewhere about installing *any* Linux distro onto a Mac? Are you dual-booting or wiping the drive and installing just Ubuntu Studio? You need to create a separate efi/boot partition if you expect to boot. Again, please search through this forum, there's plenty of useful info.

I have searched extensively, both on these forums and using Google. I have noticed others have had the same issues, but nothing what has been suggested so far has worked for me.

I have been able to install it, bypassing the GRUB install, but I just can't seem to install the GRUB as detailed in my last post.

---

### Post by g33zr on 2017-01-03
I don't understand why you are installing GRUB this way. Again, are you dual-booting or installing just Ubuntu? Meanwhile, what does your partition table look like?

---

### Post by squeak24 on 2017-01-03
> **g33zr said:**
> I don't understand why you are installing GRUB this way. Again, are you dual-booting or installing just Ubuntu? Meanwhile, what does your partition table look like?

I am not dual booting.

As stated in previous posts, I have tried a straight install, but it fails to install teh GRUB, the installation fails.

After a Google Search I found a way of bypassing the GRUB installation, then manually installing the GRUB after Ubuntu is installed. But everything I have found has failed.

Looking at [http://paste2.org/vZasEmVs](http://paste2.org/vZasEmVs) the Partitions at that time were set as:
```

da1: __________________________________________________________________________  
	    File system:       vfat

 	    Boot sector type:  FAT32
 	    Boot sector info:  No errors found in the Boot Parameter Block.
 	    Operating System:  
 	    Boot files:        /EFI/ubuntu/MokManager.efi /EFI/ubuntu/fwupx64.efi 
 	                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/shimx64.efi
  
	sda2: __________________________________________________________________________
  
	    File system:       ext4
 	    Boot sector type:  -
 	    Boot sector info: 
 	    Operating System:  Ubuntu 16.04.1 LTS
 	    Boot files:        /etc/fstab
  
	sda3: __________________________________________________________________________
  
	    File system:       swap
 	    Boot sector type:  -
 	    Boot sector info: 
```

I followed the instructions I found here [http://www.macworld.co.uk/how-to/mac/how-install-linux-on-mac-3637265/](http://www.macworld.co.uk/how-to/mac/how-install-linux-on-mac-3637265/)

---

### Post by g33zr on 2017-01-03
I think you've over-complicated your install. I recommend you try again from scratch and pay special attention to partitioning, which should be done manually in your case. For example:

sda

Ext 4 /boot/efi 500 mb
Ext 4 /              30 gb
swap                   4 gb
Ext 4 /home    your choice

This setup should boot without messing around with GRUB. I've dual-booted and installed various Linux distros many times on my Macs when I had Macs and never had to manually configure GRUB. In sum, let the install program do its thing.

---

### Post by squeak24 on 2017-01-04
I have tried again, and got the same error. I formatted the entire drive and repartitioned.

---

### Post by g33zr on 2017-01-04
^Strange. Have you been able to install and boot any other Linux distro on your MacBook? If not try, for example, Mint or Bodhi.

---

### Post by squeak24 on 2017-01-04
I have just tried to install Mint, that came up with the same error, but instead of just crashing the install it came up with an option to have the boot loader on a different device.

So, I am wondering if it will be worth rEFInd, the try again.

I have Mint on a DVD (I am running that one a different machine so I know that works), and Ubuntu Studio is on a USB Stick

---

### Post by g33zr on 2017-01-04
rEFInd would make sense if you were dual booting, but if you've wiped the MacBook and are installing only Linux, you shouldn't need it. Unfortunately, I can't look over your shoulder when you set up your boot partition, but let's think this through: ext 4, /boot/efi, esp flag. Is that what you have? If you don't add the esp flag, it won't boot.

---

### Post by squeak24 on 2017-01-05
I have tried again this morning, came up with the same issue.

I have attached a screenshot as to how I have set the partitions up.
 
I am thinking about sticking Mint and Ubuntu Studio onto the machine, but obviously, I need to get it working first.

---

### Post by g33zr on 2017-01-05
Here's how I set up my Ubuntu 16.10 partition table (leaving out /home) on my iMac:

/dev/sda1   Fat32    EFI System Partition   /boot/efi   boot/esp
/dev/sda2   Ext4                                      /
/dev/sda3   swap

I think this is how your boot partition should be configured. Also, shouldn't you have 4GB for swap?

---

### Post by squeak24 on 2017-01-05
Thanks for the tip, I will give it another go tomorrow. I am starting to wonder if it's worth it.

---

### Post by squeak24 on 2017-01-07
[FONT=arial]so, I tried again yesterday, and still get the same issue. I did find this [https://help.ubuntu.com/community/MacPro](https://help.ubuntu.com/community/MacPro).

But most of the commands, especially after you get into root, it states I can't update as the file system is read only.

I did manage to edit 
[/FONT][FONT=arial]/etc/default/grub

But had to use sudo rather than root. But then when I tried to update the grub it failed.[/FONT]
I also tried this, but again, no avail.

[http://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot/](http://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot/)

---

### Post by g33zr on 2017-01-07
I'm baffled that you're unable to boot Ubuntu or another Linux distro. I ran several different distros on my old MacBook, sometimes dual-booting two at a time. As a last resort, you might want to give rEFInd a try after all. Frankly, I'm out of ideas. Perhaps someone else can step in and help you. Good luck.

---

### Post by squeak24 on 2017-01-07
I am stuck, I have no idea what the problem is.

I will ask one of my colleagues next week who is a bit of Ninja with Ubuntu to see what he can figure out.

I have submitted the bug here [https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1654757](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1654757)

---

