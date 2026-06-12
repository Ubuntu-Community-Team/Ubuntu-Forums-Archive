---
title: "[Solved] iMac5,2 Installation Problems"
date: 2018-09-18
forum: Apple Hardware Users
---

### Post by aweblade4 on 2018-09-18
So I've been following a few guides: 
[https://ubuntuforums.org/showthread.php?t=2287767](https://ubuntuforums.org/showthread.php?t=2287767)
[https://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot/#partitioning](https://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot/#partitioning).

I can't for the life of me get this to work, I'm currently stuck at:
```
grub> linux /boot/vmlinuz&#9001;...tab here!...&#9002;.efi.signed root=UUID=&#9001;the UUID from above&#9002;
```
But, autocomplete isn't doing anything when I hit tab and I have no idea what's supposed to go there, previously I was stuck at:
```
grub> ls -l (hd2,gpt2)
        Partition hd2,gpt2: Filesystem type ext* &#9001;...snip...&#9002; UUID e86c20b9-83e1-447d-a3be-d1ddaad6c4c6 - Partition start at [...]
```
But, as I read some of the reply's I used this instead: ```
cat /etc/fstab
```
I'm not sure what I did wrong to make for autocomplete not to work. I'm not sure what I did wrong and I feel like tried everything at this point. I tried regular Ubuntu, but 1gb of ram made the installer freeze and crash alot. So then I tried regular lubuntu and I got "errno 5" during the installer saying my cd was too fast or something like that even though I was using a usb and if tried installing from the live usb session, I would get "ubi-partman failed with exit code 10" and the installer would completely break in the live session if I tried to continue anyways. I even tried to install windows via boot camp, that didn't work so I tried to force windows on the machine by yanking the hdd out and putting it on another machine to install windows, that didn't work either. So now I don't have a partition of mac os x 10.6.8, but I didn't need it for what I'm gonna be using the machine for anyways. I'm currently using the alternate 64bit lubuntu installer. So far this is the closest I've gotten to a hdd boot on linux.

Notes:
The purpose of this imac is to run a simple .netcore 2.x application.
I bought this imac second hand so I don't have the original snow leapord cd, keyboard, mouse for it and I deleted the original mac os x partition to make room for windows that ended up failing.
[The Screen isn't the best.]("https://i.imgur.com/BavwGKC.jpg")
Thank you for your help.

**SOLVED:** OK, so I got really lucky on one of my install attempts and somehow managed to get grub to install during the install process, where it normally should fail and after that fail crash the installer. But, I'll walk you through what I did so up to that point to somehow get it to work and hopefully be useful to you. Instead of using the official lubuntu mactel Iso (aka the alternate installer) I used [Matt Gadient's modified Iso.]("https://mattgadient.com/2016/07/11/linux-dvd-images-and-how-to-for-32-bit-efi-macs-late-2006-models/") I used [rufus]("https://rufus.akeo.ie/") to burn the iso to my usb and I loaded [jfwells bootia32.efi ]("https://github.com/jfwells/linux-asus-t100ta/blob/master/boot/bootia32.efi")in the /EFI/BOOT folder on the usb after it was finished burning. I also removed my rEFInd usb from earlier, turns out you don't need rEFInd if you can already see the usb in the efi boot menu. I also didn't open the boot menu to select the usb, I just let it run to see what would happen and it loaded into the installer. At first I tried to install it normally without internet, grub failed to install and the installer crashed. After I plugged in the ethernet cable I tried again going for the normal installation, download updates while installing and the extra software and it worked like normal and was bootable. The only thing I had to do is get the wifi drivers installed and I did that with [this video]("https://youtu.be/ukk8tVStOJo"). You can also use [this guide]("https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers") if you don't want or can't watch it.
**TL;DR: **I Used [Mat's ISO]("https://mattgadient.com/2016/07/11/linux-dvd-images-and-how-to-for-32-bit-efi-macs-late-2006-models/") and [this /EFI/BOOT folder on the usb]("https://github.com/jfwells/linux-asus-t100ta/blob/master/boot/bootia32.efi") (so I don't have to use rEFInd) with Ethernet everything worked normally and allowing me to skip the manual boot and installing the mactel repo. 
**Also: **If you are using Winrar, be sure to disable the ISO intergration in  Options > Settings > Intergration and reboot after that. Otherwise  you can't use windows built in iso burner on CDs and DVDs.

---

