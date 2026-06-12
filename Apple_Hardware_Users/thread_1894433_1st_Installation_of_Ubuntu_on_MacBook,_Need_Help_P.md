---
title: "1st Installation of Ubuntu on MacBook, Need Help Please !"
date: 2011-12-12
forum: Apple Hardware Users
---

### Post by xptional on 2011-12-12
Hi :)
I have MacBook 2.16GHz Processor, 500GB Hard Drive, 1GB RAM. 
I want to install Ubuntu beside Snow Leopard 10.6. Please Help me in this regard because it will be my 1st installation on MacBook and I am afraid if some hazard :) happen - - - ...., 

Could I installed it where the Snow Leopard is already there, I mean in the same partition ?
Should I need to do partition my internal hard drive for Ubuntu ? 
How much should I allocate for Ubuntu ? 
Could I do with Ubuntu CD, or with Snow Leopard Disk utility ? 
And in which format, the partition should be ? 

Should I install Ubuntu before or after Installation of Snow Leopard ? 

I thank you in advance for your cooperation for your help . :)

---

### Post by Testingte on 2011-12-12
You may want to try Dual-Booting (Ubuntu gives you the option for such things ;P)

Install Snow first, then give it... maybe half of your hard drive space for Ubuntu. Depends on how often you'll use it.

As far as sharing your files across the two, Ubuntu makes it easy with the ability to mount your other half of the hard drive for customization :D

Since you are used to a mac, I'd recommend looking at this post, just for simplicity's sake: [http://www.webupd8.org/2011/12/how-to-enable-mac-os-x-like-natural.html#more](http://www.webupd8.org/2011/12/how-to-enable-mac-os-x-like-natural.html#more)

If you want a guide, I'm making one on my YouTube channel ;)  (not to self advertise rofl.)

If you want to see that and/or suggest anything for that, it's over here: [http://www.youtube.com/watch?v=pJVqN5aaH_w&feature=g-upl](http://www.youtube.com/watch?v=pJVqN5aaH_w&feature=g-upl)

Hope this helped you out! :D

---

### Post by breimer273 on 2011-12-13
Also, I use rEFIt which you can install from OSX. Its just a new boot loader that will make it easy for you to choose whether you want to start OSX or Ubuntu. You don't need it I just like it. You can get it here: [http://refit.sourceforge.net/](http://refit.sourceforge.net/)

Other than that, I am not sure of anyway to completely overwrite the OSX partition because of the EFI, I am sure there is a way to do it I just don't know it. So I would start with the dual boot situation and then later go solo if that's what you want.

---

### Post by xptional on 2011-12-13
Thanks for your suggestions :) I will see the links and will watch the video, Then I will update to you :)

Just one more, : if I install Ubuntu and OS X with only one partition, later on if Ubuntu craches, or I want to upgrade, Then OS X will have no effect of these changes .. ? 

If I make two partitions, in one I install OS X and then in 2nd I install Ubuntu .. later if ubuntu has some problem, or i want to upgrage with new installation,  and same for OS X, ..  If i reinstall OS X, then I have to reinstall Ubuntu as well or not ??  and vice versa , 

I will be grateful to you for your help .. thanks !

---

### Post by Testingte on 2011-12-13
I'm not entirely sure it's possible to do them both under one partition, you'll have to split your hard drive into two to dual-boot.

As far as Ubuntu having a problem.. that doesn't really happen ;P.

But when you want to upgrade Ubuntu, just type in the command "update-manager -d" (without quotes of course ;P) either in the terminal or after hitting Alt+F2

That will then tell your update manager to upgrade to the latest Ubuntu distro!

But for Mac... I'm not sure because I've never used it.

But if it works the same as Windows then... yes, it will want to install in your whole system, then you can tell Ubuntu to make its own partition again.

---

### Post by xptional on 2011-12-13
Thank you so much Testingte, 
I saw your videos, these are about customizing somethings in Ubuntu. But I need some help regarding installation, .. when I will come to customize something, it will be pleasure to get help from your videos. 
Anyhow, For Now

I have decided to do TWO Partitions, one for OS X and other for Linux Ubuntu. 

On DELL in office, I installed 10.04 LTS ( Long Term Support ) version. And I don't have any problem. I prefered it because it seems more stable. 
Should I prefer this 10.04 LTS, or it won't be a problem, If go to latest versions, ... ??

Thanks for reply :)

---

### Post by Testingte on 2011-12-13
It is always wise to go for the Long Term Stable release mate ;) Excellent choice!

There are several tutorials on how to install and configure good ol' 10.04 (I've actually only been a Linux user since 10.04 xD)

Next Long Term stable release is already in the making! And it will be supported for a full 5 years rather than the current 3!

I have been making videos on customization for every frustrated user trying to figure out everything new ;P lol.

Dual booting is also wise as well when first starting out Linux!

(Not quite sure if the Mac scrolling app I linked you to will work in there though..)

---

### Post by oldfred on 2011-12-13
I do not know Macs but this has some info. Ubuntu's efi boot is still a work in progress as it has some bugs including reformating & deleting the efi partition.

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)
grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB (200MiB or more recommended). Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)
[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)

---

### Post by xptional on 2011-12-24
I am again here for your help please :)

I have read about how to install, and I came to the point that EFI is necessary to install Ubuntu on MacBook. 

Should I install EFI on my Snow Leopard first ? 
There is also rEFIt, I am confused, should I install EFI or rEFIt ? 
What about GRUB ? should I install GRUB on snow leopard before Ubuntu10.04 LTS ? 

I explain you, that i have tested my Ubuntu 10.04 LTS by live CD on my MacBook with SnowLeopard, and it works fine. Mouse, keyboard etc and also Wireless ... 
On my MacBook, I have two parition, I installed SnowLeopard on one parition, and second parition I made it as MS-DOS(FAT).  On startup, pressing ALT/OPT Key on macbook, it show two disk anyhow.. 

My live CD Ubuntu 10.04 LTS distribution is 32-bit :)

MacBook 2.16 GHz
RAM      1 GB
HDD     300 GB Snwo Leopard     ,  200 GB MS-DOS (FAT) , I want to install ubuntu in 200 GB . 

Thanks for your help

Editted:---------

I came across a link about installation, he did ISO-2 USB EFI booter, .. but I have a CD for ubuntu installation, then what should I do for that, thanks for your help [http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/]("http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/")


I found  that Apple already use EFI as described, 

""  Apple uses EFI for its line of Intel-based Macs. Mac OS X v10.4 Tiger for Intel and Mac OS X v10.5 Leopard implement EFI v1.10 in 32-bit mode, even on 64-bit CPUs (newer Macs have 64-bit EFI).[26] ""
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface")

---

### Post by oldfred on 2011-12-24
I do not know enough about Macs to really help. I am sure someone here in the Apple sub forum can help.

---

### Post by Apewall on 2011-12-25
> **xptional said:**
> I am again here for your help please :)

I have read about how to install, and I came to the point that EFI is necessary to install Ubuntu on MacBook. 

Should I install EFI on my Snow Leopard first ? 
There is also rEFIt, I am confused, should I install EFI or rEFIt ? 
What about GRUB ? should I install GRUB on snow leopard before Ubuntu10.04 LTS ? 

I explain you, that i have tested my Ubuntu 10.04 LTS by live CD on my MacBook with SnowLeopard, and it works fine. Mouse, keyboard etc and also Wireless ... 
On my MacBook, I have two parition, I installed SnowLeopard on one parition, and second parition I made it as MS-DOS(FAT).  On startup, pressing ALT/OPT Key on macbook, it show two disk anyhow.. 

My live CD Ubuntu 10.04 LTS distribution is 32-bit :)

MacBook 2.16 GHz
RAM      1 GB
HDD     300 GB Snwo Leopard     ,  200 GB MS-DOS (FAT) , I want to install ubuntu in 200 GB . 

Thanks for your help

Editted:---------

I came across a link about installation, he did ISO-2 USB EFI booter, .. but I have a CD for ubuntu installation, then what should I do for that, thanks for your help [http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/]("http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/")


I found  that Apple already use EFI as described, 

""  Apple uses EFI for its line of Intel-based Macs. Mac OS X v10.4 Tiger for Intel and Mac OS X v10.5 Leopard implement EFI v1.10 in 32-bit mode, even on 64-bit CPUs (newer Macs have 64-bit EFI).[26] ""
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface")

rEFIT is the easiest solution to what you want to do.

---

### Post by xptional on 2012-01-02
Any help please .? 

Should I need to install first rEFIt or not ?? 

I want to install Ubuntu on my machine snow leopard ....

---

### Post by Wolfador on 2012-01-02
> **xptional said:**
> Any help please .? 

Should I need to install first rEFIt or not ?? 

I want to install Ubuntu on my machine snow leopard ....

I installed rEFIt first, then used Disk Utility to shrink my current install and left the new area empty. Then I used a usb drive to boot the Ubuntu install and selected use free space.

---

### Post by breimer273 on 2012-01-02
> **Wolfador said:**
> I installed rEFIt first, then used Disk Utility to shrink my current install and left the new area empty. Then I used a usb drive to boot the Ubuntu install and selected use free space.

This is the same thing that I did too. No problems. To me it seems impossible to have two bootable OSes on the same partition. I feel like this would confuse the EFI. I allocated half of my drive to Ubuntu and the other half to OSX. You could allocate more or less depending on what kind of setup you want. Whether you want a swap partition and/or a partition to share files across both OSes. All of that info should be in the installation guide(s). I would install rEFIt first, I think.

---

### Post by Wolfador on 2012-01-02
I setup my MBA 64gb with 50 to OS-X and 14 to Ubuntu. 3 of that 14 being a swap. Still have about 5gb left with everything I need loaded up.

---

