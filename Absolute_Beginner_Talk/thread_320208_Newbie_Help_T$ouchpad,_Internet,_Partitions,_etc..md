---
title: "Newbie Help: T$ouchpad, Internet, Partitions, etc."
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by Arithmomaniac on 2006-12-16
I am a brand-new Ubuntu user (6.10 LTS on a Aspire 1640), but have to stick to Windows until I can get the following problems fixed, in order of priority:

1) How do I connect to the internet without having to contact the internet administrator (such as DNS number info)? I know this is possible, since I do it in Damn Small Linux, another platform I am trying to learn. Without this, learning Ubuntu and getting help is too cumbersome.
2) How can I get Ubuntu to mount my other drives? It will only mount the one Ubuntu is on, but I need to access files on my C Partition and want to make my D/hda2 Partition a communal ground for access to files such as schoolwork.
3) How do I get a driver for my Synaptics touchpad that will let me turn off touch-doubleclick?
4) How do I get WinXP to recognize the Partitions I make with Ubuntu
5) Can I get the ext3 filesystem to behave more windows-like, with Windows terms and long, descriptive folder filenames?
6) How do I get 1280x800 support for my monitor?

The forums are just too overwhelming for basic tasks such as these.

Thanks,
Arithmomaniac

---

### Post by seijuro on 2006-12-16
3) you can disable your tap function like this there are some other ways but this method worked for me.

look for this section in your xorg.conf

```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection
```

add that last line "Option..SHMConfig..."

then run

```
synclient RTCornerButton=0 RBCornerButton=0 TapButton1=0 TapButton2=0 TapButton3=0

```

you can add this command to a script to and have it run each time X loads.

personally I just use a script that runs the synclient command when I want the tap to be off rather than X startup so that if I can decide not to turn it off at any point simply by not running the script.

6) about your resolution check to make sure you have the drivers for your video card installed you might need to download the nvidia-glx drivers or the ati drivers. If you need directions on how to get/install the drivers just let us know.

---

### Post by mike3k on 2006-12-17
2) install ntfs-3g, which lets you mount NTFS partitions with read/write access. You might also want to look at [xpresslinux]("http://www.xpresslinux.com/"), which pre-installs ntfs-3g & Wine for better Windows compatibility.

4) you most likely need a third-party application to read ext3 partitions in Windows.

5) ext3 supports long file names. It's a matter of the desktop environment to make it more Windows-like. You might prefer KDE's Konqueror file manager rather than Gnome's Nautilus.

---

### Post by Arithmomaniac on 2006-12-17
3) How do you get xorg.config? How do I add the command to a script?
2) I have a fat32 system, yet I still can't mount the drives.
4) I'm about to try the one at fs-driver.org
6) [This thread]("http://ubuntuforums.org/showthread.php?t=265912") seems inconclusive. I'll post back.

This will still be virtually impossible if I don't have an answer to 1). Please help!

By the way typo in the first post, I have 6.**06** LTS.

Thanks,
Arithmomaniac

---

### Post by seijuro on 2006-12-17
> **Arithmomaniac said:**
> 3) How do you get xorg.config? How do I add the command to a script?

load a console at the prompt type: cd /etc/X11
then either use nano or vim to edit the xorg.conf

sudo nano xorg.conf

or

sudo vi xorg.conf

prolly be a good idea to back up the file before editing:
sudo cp xorg.conf xorg.old

the script I use just make a text file called tap.sh and in the file add the command then set the permissions on the file so that it is executeable you can do this by right clicking the file in the file manager and selecting properties then go to the permissions tab and make the adjustments. Then to run the script yourself just go to whatever directory it's in and type: ./tap.sh

---

### Post by Arithmomaniac on 2006-12-19
1) I have turned on DHCP, but it just does not seem to be working. My Realtek 8139/810x refuses to pick up an Internet connection when plugged into the wall or a D-Link rerouter. Windows and DSL do just fine. 
2) My drives say that they are not removable and that they cannot execute pmount. Am I supposed to access them via filesystem?
3) I'll try it.
4) I use Ext2 IFS, but it asks to format the disk. For one drive, it says that it is not mounted, and that I can look in /etc/fstab for more info. For the other, it says that the drive is locked (perhaps since it is in hibernation)
5) I'll just have to get used to it.
6) I have an Intel 915GM, which the device manager recognizes, but it still will not go to 1280x800 with that driver. Any special code or extra drive I should put in?

Thanks,
Arithmomaniac

---

### Post by Arithmomaniac on 2006-12-20
bump

---

