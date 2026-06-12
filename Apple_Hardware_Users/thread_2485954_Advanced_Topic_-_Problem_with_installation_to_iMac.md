---
title: "Advanced Topic? - Problem with installation to iMac 14.3 (10 year old)"
date: 2023-04-15
forum: Apple Hardware Users
---

### Post by sm2art on 2023-04-15
I have some experiences in the past of running ubuntu on PCs, but never on a Mac before. I recently was given an old iMac, with 16GB ram and 1.2Tb Fushion Harddrive,  Apple no longer provides OS support for this model since the end of last year. 
I am doing a few things including running the newest version of OS using Opencore Legacy Patcher, that part is good, but with some programs crashing. I am experimenting of running ubuntu on it.

I partitioned the HD, such as Mac OS is in its own partition, and I also created four 16GB mini-partitions, so that I could boot Install Mac OS Big Sur, Install Mac OS Monterey, and Install Mac OS Ventura, and finally I used the following command to write the ubuntu.dmg onto the 4th mini-partitions:
sudo dd if=ubuntu.dmg -of=/dev/diskN bs=1ms status=progress (diskN is obtained by using diskutil list)

I also reserved a few other partitions: One Partition with exFat, which could hold Data for both Mac and Linux, and another partition 150GB initially formatted inside Mac (using HD Utility) as exFat, which I intend to install Ubuntu.

So I rebooted the Mac while holding down the Opt-key on the Mac, sure enough, all the mini-partitions showing up on the boot menu, especially the ubuntu boot is showing up as ESP, so I clicked on it, it flashed a message: unknown filesystem, but apparently that's a benign message, then it presents me with a booting menu, first line:  try or install ubuntu..., and I chose the first option.A few minutes later, I was presented with an Install Welcome Screen, which give me two options:
1. Try Ubuntu, 2. Install Ubuntu

I chose 1 to try, it also presented me with Install on the lower right hand side corner on the desktop. 
It specifically says: You can try ubuntu without making any changes to your computer, **directly from this CD**. 

I bold-faced the **Directly from this CD** part, I wrote the disc image directly to a mini-partition on the internal hd, but I think it's treating it as a virtual CD ROM drive. So I started the installation process, I chose the 150 GB partition that I reserved while in MAC, and formatted ext4 journal filesystem, and mounting to /, and chose to install the boot loader to the same 150 GB partition,  everything seems okay to this point, when click to proceed, it gave me an error message that it cannot unmount the CD ROM drive, I am assuming it's the virtual CD ROM drive, as this Mac does not have a CD ROM drive. 

I am wondering what's the best strategy of overcoming this? Can I remove the virtual CD ROM, ie, is there an installation media I can use without the need of emulating the virtual CD ROM?

**Just a quick update**: I started the Install Ubuntu directly without choosing the Try Ubuntu option, when the same error message occurs, I click the try to close the CD ROM option, it's proceeding with the installation now. 
                                 [B]But now it stuck at Detecting filesystem.  - anyone has any idea on how to deal with this? (I think this is related to cannot eject virtual cd rom).

Further update: So looks like one cannot directly using an internal partition as an installation media, I was trying to avoid using a USB drive, as it's slow. So I resorted to create a USB installation media, and install from there, and used the mini-partition as a swap partition, so it works perfect.  I do have a question though, why it's necessary to eject the virtual cd rom, why would it cause installation to fail?

Another observation: If you want to try without installing, you can comfortably use a mini-partition like I did, it's relatively fast, I tried in-vain to turn on persistent storage option, so the wifi-setting and program update would stick, but I did not want to continue. I may try a persistent storage friendly distribution. Now I managed to install one distribution, there is nothing to stop me from install another.

[/B]
Thanks all in advance.

---

### Post by sm2art on 2023-04-15
Another quick observation: if I just run live CD option, I could not get WIFI, even though lshw -C network does detect it, but I cannot install the wifi driver, in the installation, there is an option to install 3rd party drivers to enable wifi. So if you are interested in trying live cd without installation, go to the installation part, and select the install 3rd party driver, and click okay, wait until it finishes the installation of ubuntu drivers, then click all the way back to try the live cd, this time, you can try the live cd with wifi on. I do believe it would be nice to try the live cd without going through this route, but it works this way.

---

### Post by jeremy31 on 2023-04-15
Moved to Apple Hardware

---

