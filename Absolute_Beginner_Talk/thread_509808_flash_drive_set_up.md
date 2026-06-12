---
title: "flash drive set up"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by mar225 on 2007-07-25
Can someone direct me to setting up a usb flash drive on edgy. I have searched but so far all I get is for booting from flash.

Thanks

---

### Post by overdrank on 2007-07-25
> **mar225 said:**
> Can someone direct me to setting up a usb flash drive on edgy. I have searched but so far all I get is for booting from flash.

Thanks

Hi and maybe this link will help
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by mar225 on 2007-07-25
Thanks but that again is for installation of ubuntu not using a flash drive for storage.

---

### Post by overdrank on 2007-07-25
> **mar225 said:**
> Thanks but that again is for installation of ubuntu not using a flash drive for storage.

Quote from that page
Installing on external or RAID hard disks

If you would like to install Ubuntu on an external hard disk or a RAID array, see the guides below for instructions.

    *

      BootFromFirewireHardDisk - Booting Linux from a Firewire hard disk.
    *

      BootFromUSB - Booting an Ubuntu system on a USB hard disk on computers which cannot boot from USB (using a boot CD)
    *

    [B]  [Ubuntu]LiveUsbPendrivePersistent - Installing Ubuntu or Kubuntu on a USB pendrive with persistent mode
    *[/B]

      Installation/LVMOnRaid - Installing onto a Software RAID Array, with all partitions on RAID and LVM (including root and boot)
    *

      FakeRaidHowto - Installing onto a BIOS RAID array
    *

      How to dual-boot Ubuntu and XP after installing them separately on two HDs - If you really want to keep XP and Ubuntu on separate HDs. ;)

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by mar225 on 2007-07-25
Yooo  Hoooo   Listen up. I don't want to install ubuntu on anything I already have it installed. All I want to do is use the flash disk for transferring files from one machine to another.

---

### Post by MQMike on 2007-07-25
Flash drives (USB Flash Drive, or UFD), already come formatted FAT16 or FAT32.
Just use that.  For data, it's ready to go.

Or, use GParted to format the flash drive any way you wish.
GParted is included with Ubuntu, under System tools somewhere, or simply download and burn your own free iso to bootable CD, insert that CD, re-start your PC, get into GParted, insert the UFD, Refresh devices, and then do your partition editing/formatting.

GParted:   [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

(fwiw, Personal Comment:
U3 is great, but if the UFD comes with it, sometimes I first remove it using U3.com/uninstall; then I partition the UFD using GParted, then I format the partitions, usually as FAT32 for normal data, like documents between XP and Linux.)

---

### Post by mar225 on 2007-07-26
Thanks a million MQMike. Your note was the key. 
I finally formatted as fat32 got rid of U3 and now the chip is recognized and shows up on the desktop.

Next problem...   When I try to access the usb flashdrive in commander it says "mount failed: permission denied". I have gone to permissions for that drive and tried to make changes but they don't stick and commander wont allow it to be accessed.   Where do I go next?   Thanks again.

---

### Post by indytim on 2007-07-26
Try "right clicking" on the usbdisc icon.  From there navigate to permissions and adjust.  Not sure of the conversion to Gnome for this as my primary ops in Kubuntu 6.10.  Should work similar in Gnome-land.

IndyTim

---

### Post by mar225 on 2007-07-26
I did just as you describe but the changes dont save or stick. 

I thought maybe if there was a way to bring up commander with sudo it might over ride the permissions but havent figured that out either.

Thanks for the ideas.

---

### Post by MQMike on 2007-07-26
"I thought maybe if there was a way to bring up commander with sudo it might over ride the permissions but havent figured that out either."

Get a Terminal,
type something like
sudo commander
press Enter, see if commander comes up (which will be as root then)

(This works in Kubuntu.)

---

### Post by avanrens on 2007-08-02
I have a similar problem were my flash drive is read only and I can't change the permission.

---

### Post by indytim on 2007-08-02
Not sure if this will work, but should be painless to try :)

Using whatever your favorite filebrowser is (mine is Krusader):
0.  Insert your usb stick into the usb port
1.  invoke the browser at "sudo" level via the terminal
2.  "right click" on the icon for the usbdisc to bring up the properties
3.  Navigate to the Permissions.
4.  Set your user id as the owner and allow mods for you.  (make sure you cascade down to enclosed folders and files.
5.  Close the terminal
5.  Safely remove (dismount the usb disc).
6.  Re-insert and see if the permissions stick

Report back on whether this was a fix ok?

IndyTim

---

