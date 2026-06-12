---
title: "A *working* tutorial for triple booting Unibody Macbook Pro's with Bootcamp and rEFIt"
date: 2008-11-19
forum: Apple Hardware Users
---

### Post by elfprince13 on 2008-11-19
So, I just ordered a new Macbook Pro (320GB HD, 2.53GHz CPU, 512MB 9600m GT, 4GB of DDR3), googled around a bit and followed the tutorials on the Ubuntu wiki for triple booting with Bootcamp and rEFIt. First, I used Bootcamp to create a 200GB partition for Leopard and a 120GB partition for Vista. I rebooted onto the Vista installation DVD (Ultimate, x64), and formated the 120GB partition to NTFS, installation run smoothly. After my first boot into Vista I installed the bootcamp drivers, followed by all the updates. this went flawlessly as well.....one quirk with the bootcamp drivers is that regardless of your touchpad settings, right clicking requires a three-finger click. After that I used Vista to set the drive label for the windows partition to "Skaro HD" (my Macintosh HD is "Dagobah HD" and my external is "TARDIS," complete with matching icons). At that point I rebooted into Leopard and downloaded the amd64 version of 8.10, burned the .iso to a blank CD with Leopard's Disk Utility, and booted off the Ubuntu CD. Next, I selected "Safe Graphics Mode" from the Modes menu (F4 if i remember correctly), and started it in LiveCD mode. the wireless worked flawlessly, and the resolution was correct so I ran the installer, selected the US Macintosh keyboard layout, and clicked through the settings I wanted until I reached the partitioning tool. here I selected that I wanted to do it manually. I sized the Vista partition down by 20GB, and created an ext2 partition for Ibex. I clicked next and confirmed that I **did not** want to create a swap partition. from the last step confirming my settings I clicked "Advanced" and told it to install grub to my Ubuntu partition (sda4). I let the installation run. at this point I booted back into Leopard and installed rEFIt. after you run the installer, ignore what they say about the blesser working automatically, open a terminal and
```
cd /efi/refit
./enable.sh
```

restart and the rEFIt menu should appear. trying to start Vista or Ubuntu at this point leads to a black screen with a blinking white cursor, so I ran the partition sync tool, powered down, and started it back up. at this point Vista would not boot, giving the error that everyone seems to be getting, about winload not being found, or corrupted, so I checked the Ubuntu would boot (it did), and then restarted onto the Vista installation C=DVD, after selecting I wanted to repair I found that the Recovery Environment didn't pick up my Vista installation, even though everything else on my computer could see it, and the automatic repair told me that the disk was corrupted. chkdsk told me this was a lie, so I used
bootrec ([http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)) from the command prompt and ran ```
bootrec /scanos
``` which did see my installation on C:, where it was supposed to be. I ran ```
bootrec /fixmbr
``` since I a had read that the winload error was related to Ubuntu overwriting the MBR, and restarted, but I still couldn't boot Vista. I booted once more onto the Vista install disc, hoping that bootrec /rebuildbcd would fix things and this time the Recovery Environment immediately recognized my installation and said that for some reason the partition it was on wasn't listed, and that its size was set to 0. I choose to automatically repair this, restarted to rEFIt, powered off completely, and then booted into Vista. at this point, both Vista and Ubuntu wanted to check their disks for errors. all that remains is to install ext2 drivers on OS X and Vista, MacDrive on Vista, and possibly disable journaling on my Leopard partition so that Ubuntu can write to it too. I also need to remove the Vista entry from GRUB since I only need GRUB for booting Ubuntu, and install a few more drivers. and create a swap file for Ubuntu.

---

