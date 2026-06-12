---
title: "Linux Hangs on Boot from rEFIt"
date: 2009-02-23
forum: Apple Hardware Users
---

### Post by brentgrunenberg on 2009-02-23
Hi All, 

If you can please help me I've tried twice now to install the lastest release of Ubuntu (8.10) on my Macbook Pro. I used Bootcamp to create a partition. I then installed refit and it starts fine as my computer boots. Then within the LinuxLive cd boot I used the Partition manager to delete the partition I created in Bootcamp, and when installing I selected Install on the largest continuous free space. The Linux and Swap paritions are installed fine. In the last panel, I selected under the advanced options to install the linux boot from Sda03. This is all in the directions for installing on a Mac. 

After the installation and reboot without the live CD, I ran the partition manager in refit and it appeared to work fine. When I select the option to boot to Linux from HD the Linux logo appears against a White background (as the Apple does when booting OS X)... but thats all, nothing happens past this point. 

Whats happening here? Why wont Linux boot?

Thanks in advance for your advise. I tried posting this in the Absoulte New Beginers section of the forum and got no responses, though I figure this is where I should have posted to begin with ;). 

Cheers, 

BG

---

### Post by darksidedude on 2009-02-23
ok well, you should install grub to the "MBR" when installing ubuntu, since OS X uses EFI there will be no issue installing grub to the fake "MBR"

then just sync the MBR to the GPT in REFIT. and you should be alright.

I've had to do this several times with my macbook.

---

### Post by brentgrunenberg on 2009-02-23
Thanks for the responce man. By mgr I assume you mean master boot record.. And whbe you say that do you mean hda0.. Or where is tried to install the first time? Because I assigned it to my Linux partision.. 

And 2., if it's already installed there, how do I change where grub is installed? And how do I delete the install from hda03? 

Thanks much for your help!!

Cheers, 
BY

---

### Post by darksidedude on 2009-02-23
yea master boot record. it is the place ubuntu defaults to install grub. I would just so everything is set up just wipe old ubuntu out and reinstall make sure you format the / partition swap doesn't matter

---

### Post by cyberdork33 on 2009-02-23
> **brentgrunenberg said:**
> After the installation and reboot without the live CD, I ran the partition manager in refit and it appeared to work fine. When I select the option to boot to Linux from HD the Linux logo appears against a White background (as the Apple does when booting OS X)... but thats all, nothing happens past this point. 

You're OK. This is addressed in the AppleIntelInstallation page:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Fix%20the%20Partition%20Tables](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Fix%20the%20Partition%20Tables)

Basically, you just need to shutdown and startup again (not reboot), and it should work.

> **darksidedude said:**
> ok well, you should install grub to the "MBR" when installing ubuntu, since OS X uses EFI there will be no issue installing grub to the fake "MBR"while it IS possible to install to the MBR, we generally recommend installing to the Linux root partition (as he has done). This is because, unlike a PC, a Mac has loader that you have to use before getting to GRUB, and since the MBR is the only location windows can use for it's bootloader, we avoid interfering with anything in the MBR. 

For a plain, dual-boot setup though, you can install to the MBR and it will work the same, though since he has already installed to the partition, installing to the MBR also, will now create a second icon in rEFIt for Linux.

then just sync the MBR to the GPT in REFIT. and you should be alright.

I've had to do this several times with my macbook.[/quote]

---

