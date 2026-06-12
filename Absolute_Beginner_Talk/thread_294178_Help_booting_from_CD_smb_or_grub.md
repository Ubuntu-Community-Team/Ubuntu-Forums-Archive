---
title: "Help booting from CD: smb or grub"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by Campitor on 2006-11-06
Hello all:

  I'm trying to install Dapper on a computer, that has Breezy on it.  It is suppoused to be able to boot from CD, but it never does.  I used to have a samartboot cd, which would allow me to boot into a CD, but I lost it.  Here are my questions:

 I found the sbootmgr.dsk file on the internet, but if I burn that one onto a CD, the computer won't boot to it.  Is there any way that I can transform that file into an iso? Or how can I burn it onto a cd and make it bootable? Or does anybody have a sbootmgr.iso anywhere?

Second, I can get to grub very easily.  Is there a way to boot to a CD from grub? I've been reading the grub man  pages for a while, and things are not clear to me at this point.  I know, I can do dist-upgrade to dapper, but I really want to wipe the HD clean, and do a fresh install, plus the internet connection is not too fast.

Thanks in advance for you help

Camp. 

PS>  I don't have a floppy on my box.  Just a DVD.

---

### Post by Ecthelion on 2006-11-06
First of all, to boot from a cd, you have to go to your bios and put your cd-drive as first boot device

You don't have to change anything about your grub ...


> I'm trying to install Dapper on a computer, that has Breezy on it. It is suppoused to be able to boot from CD, but it never does. I used to have a samartboot cd, which would allow me to boot into a CD, but I lost it. Here are my questions:

I found the sbootmgr.dsk file on the internet, but if I burn that one onto a CD, the computer won't boot to it. Is there any way that I can transform that file into an iso? Or how can I burn it onto a cd and make it bootable? Or does anybody have a sbootmgr.iso anywhere?

I don't get this...

Do you mean you want to upgrade to dapper or do you want to make a fresh install

I don't get it about your sbootgr.dsk too...
You can get the only cd you need for dapper [here]("http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download").

---

### Post by Campitor on 2006-11-06
1. I'm sorry I wasn't clear enough.  I have changed the BIOS, to boot from CD first.  It recognizes some CD's, but my bios does not recognize the UBUNTU CD's. It gives a message: Cannot boot from ATAPI CD, try upgrading the BIOS.  I was able to boot with the SmartBoot manager, but I cant find the CD that had it.

2.  I want a fresh install, not an upgrade (i.e. dist-upgrade)

3.  I have an ubuntu CD. What I  want  is to make a bootable CD with SmartBoot manager.  But the only file I have found so far is sbootmgr.dsk, is not recognized by any cd-burning software as an image file. If I just copy it to CD, it is not a bottable CD, and therefore, I cannot use it.

4. That's why I thought, a couple of GRUB commands would allow me to boot into a cd (Ubuntu CD) placed in the tray.  I've seen this question asked before in the fora, but no answer was ever given.

Hope this made my question a bit clearer.

Camp.

---

### Post by Ecthelion on 2006-11-06
Why not upgrading your bios?

It doesn't take 2 minutes and it may be the end of all your problems...

Of course if you have no Windows/DOS, it's sometimes harder to find the correct drivers...

Be carefull not to shutdown your pc while doing it or you might corrupt your bios...

---

### Post by confused57 on 2006-11-06
Here's how to make a SBM boot floppy:
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

---

### Post by louieb on 2006-11-06
You can alway buy a floppie drive or I did some googleing and found this:
[http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB]("http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB")
Let use know how it worked out.
Never mind I just tried it and ... it worked.:o  on one of my old computers. I was getting tired of breaking out the SBM floppie every time I wanted to boot to CD. I go a couple of older computers to try it out on also. Took only a couple of minutes to download and make the changes.

---

### Post by Campitor on 2006-11-07
> **louieb said:**
> You can alway buy a floppie drive or I did some googleing and found this:
[http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB]("http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB")
Let use know how it worked out.
Never mind I just tried it and ... it worked.:o

You are a great googler, I have been looking for this for about two days now. It worked grate. I'll post all that I did, since somethings are not really as stated in the above webpage, and for newbies like me:

1.  downloaded memdisk and sbm.bin

```
wget ftp://ftp.mcc.ac.uk/beta/local/teaching_cluster/disks/memdisk

wget ftp://ftp.mcc.ac.uk/beta/local/teaching_cluster/disks/sbm.bin
```

2. copied both files to: /boot
```
 sudo cp memdisk sbm.bin /boot 
```

3. Edited /boot/grub/menu.lst file with vi and added three lines at the bottom of the file
```
 sudo vi /boot/grub/menu.lst

Add:

title   SBM-Boot a CD
kernel  /boot/memdisk
initrd  /boot/sbm.bin 
```

4. reboot my machine and wait for the grub countdown (if the countdown is too fast, read this: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_the_timeout_seconds_for_GRUB_menu_on_boot-up]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_the_timeout_seconds_for_GRUB_menu_on_boot-up")
  There is a menu entry for SBM, and when choosen, all works great.  Thanks for the help

Camp

---

