---
title: "Problems with re syncing the MBR"
date: 2010-01-11
forum: Apple Hardware Users
---

### Post by jderosa3 on 2010-01-11
I followed these instructions to triple boot my MacBook Pro 5,2:

```
You have already installed Mac OSX and Windows Vista, now to install Ubuntu.

Startup your laptop with Ubuntu Desktop CD inserted into the drive.

In rEFIt menu, choose to boot the Ubuntu CD.

Select English as the language to be used.

Select the 2nd option, the one that says : "Install Ubuntu"

After the loading, on the install screen, select the O.S. Language (English) and hit "Forward" button, then select your country location.

On the Keyboard layout, choose your keyboard language, and on the other window select the variant Macintosh (mine is Portugal - Macintosh), and test the typing if you want.

On the "Prepare Disk Space" menu, select the 1st option: "Guided - Resize SCSI3 (0,1,0), Partition #3 (sda) and use Free Space", and with your mouse select the desired partition size (I set mine to 80% Windows Vista & 20% Ubuntu), and hit "Forward" button.

On "Migrate Documents and Settings" menu, just hit "Forward".

On "Ready to Install" menu, select "Advanced..." and select to install Grub boot loader to the last partition "/dev/sda4" and hit "OK" button, and then hit "Install" button to begin the installation process.

After the installation has finished, hit "Restart Now" button, it will exit the installer and eject your CDROM, then press "Enter" key to restart.

**Use the refit Partitioning Tool to re sync the MBR, then restart again, select the Linux icon on rEFIt to boot into Ubuntu.**
```

When I get to that last step the reFIT partiioning tool says:

Status: GPT partition of type 'Unknown' found, will not touch this disk
[COLOR="Orange"]Error: Not Found returned from gptsync.efi[/COLOR]

Any ideas where I can go from here? Thanks.

---

### Post by linuxopjemac on 2010-01-11
[http://mac.linux.be/content/problems-refit-and-grub-after-installation](http://mac.linux.be/content/problems-refit-and-grub-after-installation)

---

