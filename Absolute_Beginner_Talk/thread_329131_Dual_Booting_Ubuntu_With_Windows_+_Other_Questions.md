---
title: "Dual Booting Ubuntu With Windows + Other Questions"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by alcedo on 2007-01-01
Hi all, i have a few questions to ask:

1.) Firstly i noticed that many people have problems installing Windows only AFTER they installed Ubuntu. Seems like Grub is conflicting with the windows boot manager or something... 

So im wondering that isn't it better for someone to install Windows First, and thereafter install Ubuntu ?

2.) Also What exactly is MBR ? Whats the difference btw MBR and GRUB ? from what i "know" both seems to allow users to choose which OS they want to boot . Also, how do u completely wipe off your entire MBR data ? 

3.) I have noticed that my Ubuntu Live CD works only on my Old computer system, not my new one. Could this be due to the fact that my old computer system has a FAT32 file system, while my new system is made up entirely off the NTFS system, thus preventing the Live CD from booting up ?

Thanks :)

---

### Post by meng on 2007-01-01
1. Windows overwrites the master boot record and assumes it is the only OS you want to load.
2. MBR = master boot record, which is that area of the hard disk where the computer first looks at boot time. GRUB is a bootloader, which is a program (I suppose) which actually does the booting. By default, GRUB is installed to the MBR. There is a Windows bootloader which again by default gets installed to the MBR. The difference is that GRUB allows you a choice in what gets booted (whereas Windows bootloader does not).
3. No. I assume there is some other incompatibility which is preventing the LiveCD from working with your other system. This does not automatically mean that Ubuntu cannot be installed on that system, but it may require some fiddling. The install itself would probably require the Alternate CD rather than the Live CD. You could try the Live CD in safe graphics mode, and there are other boot options which could be tried (e.g. noacpi)

---

### Post by hoges on 2007-01-01
I had the same thing as point 3. Basically a lot of later graphics drivers don't work in ubuntu, so it requires some messing around in console to get xserver (the gui) to load.

---

### Post by ieee488 on 2007-01-01
3.)  I have Windows 2000 installed on my old PC. The hard drive is NTFS, but I was able to install Ubuntu 6.06 with no problems, so I agree that it is something else that causing problems for you.

---

### Post by walkerl on 2007-01-01
You need to check your BIOS setting and make sure that your computer is set to boot from the CD first, it not, the computer will not start the live CD.

---

### Post by alcedo on 2007-01-03
Thanks for all the information,

Yeah i checked already. its does boots from the CD with no problems. Looks like i have to try the alternate cd than =X

---

### Post by raul_ on 2007-01-03
You mentioned that it was an old computer...does it have at least 256MB RAM?

---

### Post by Sef on 2007-01-03
There are some options on the Live CD for booting problems.   I believe you push F6 to get them.  

What is your graphics card?

> You mentioned that it was an old computer...does it have at least 256MB RAM?

It works on his old computer, not his new one.

---

### Post by raul_ on 2007-01-03
> **Sef said:**
> It works on his old computer, not his new one.

My bad. I think it's pretty safe to install from the Alternate Install Cd. Even if the Live CD doesn't boot, that doesn't mean that the whole system won't. I can't seem to load my Edgy Live CD (it gives me some "huh?'s" and i tried all the options i found..some people say to wait but i'll just load dapper's Live CD

---

