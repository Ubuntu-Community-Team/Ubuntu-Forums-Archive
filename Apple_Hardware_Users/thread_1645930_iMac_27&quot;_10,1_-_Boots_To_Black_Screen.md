---
title: "iMac 27&quot; 10,1 - Boots To Black Screen"
date: 2010-12-15
forum: Apple Hardware Users
---

### Post by Voelkl on 2010-12-15
Hey All =)

Just installing for the first time, i have a Ubuntu friend over helping me. When attempting to boot to the CD for installation we get a flashing "_" in the top left hand corner of the screen, and after a few seconds the screen goes black and remains that way.

Any ideas?

Cheers
Voelkl

---

### Post by arabis on 2010-12-15
Before install, did you prepare your hard drive with Bootcamp and rEFIt?
Installing Ubuntu on a Mac is a little tricky. Make sure you read and understand this page:
[https://help.ubuntu.com/community/Intel_iMac]("https://help.ubuntu.com/community/Intel_iMac")

For cd, you can use this one:
[http://cdimage.ubuntu.com/ports/releases/10.10/release/ubuntu-10.10-desktop-amd64+mac.iso]("http://cdimage.ubuntu.com/ports/releases/10.10/release/ubuntu-10.10-desktop-amd64+mac.iso")

Don't forget to install grub on your "/" linux partition, not on your mbr.

---

### Post by Voelkl on 2010-12-16
> Before install, did you prepare your hard drive with Bootcamp and rEFIt?
Installing Ubuntu on a Mac is a little tricky. Make sure you read and understand this page:
[https://help.ubuntu.com/community/Intel_iMac]("https://help.ubuntu.com/community/Intel_iMac")

I've partitioned the HDD and installed rEFIt, i have burned the iso to a disc and when i boot to it, I get a screen with the funny logo and what looks like a keyboard, then it just goes black. The optical drive makes noise for about 5mins then nothing. I left it for an hour just incase it was loading.

I've reinstalled my Mac and then redone the partition maps and rEFIt. Also tried burning the disc at slower speeds and booted to a USB drive and same issue.

I'm lost.

Thanks for you help mate.

---

### Post by arabis on 2010-12-16
Did you try the iso I have suggest to you?
If it doesn't work, use this one below, it worked for me but you will have to use text base installer:
[http://cdimage.ubuntu.com/ports/releases/10.10/release/ubuntu-10.10-alternate-amd64+mac.iso]("http://cdimage.ubuntu.com/ports/releases/10.10/release/ubuntu-10.10-alternate-amd64+mac.iso")

---

### Post by silentbot on 2010-12-22
Hi Voelkl,

I had the exact same issue you have right now and it took a while to figure out how to get the install running. Thanks to the help I got from a Linux savvy friend of mine I got my system installed.

First off, you will need to download the Alternative install iso that allows you to install text based. You can chose the version you want to use here: [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

If I have understood it correctly, the main reason for this is due to the fact that there is a setting enabling the mini-port to be used during install. You could obviously just plug an external monitor to your mini port on the mac and run the normal install or make life easier and download one of the alternative installs. I have an iMac 27" i5 and downloaded the amd64bit alternative install. 

Now, what you need to do is the following:


[LIST=1]
[*]Download image as stated above.
[*]Since you have already installed reFit you can just go ahead and insert the disc with the alternative install and reboot the machine. Make sure to be holding down the "c" key on the keyboard to boot from the Disc.
[*]Install Ubuntu. The alternative install method takes a lot longer than the usual Ubuntu install so keep that in mind. It may take you up to an hour to complete everything. Make sure you select the right partition during install so you don't accidentally overwrite your OSX install.
[*]Once the installer is finished and you get a first reboot you will get to the refit menu. Select to boot from Ubuntu. **Note:** Do NOT let Ubuntu load on its own as you will get the same result, a black screen. Make sure you select the safemode option and press the "e" key. You will be shown a screen with the string information relating to this particular boot option. Locate the line that starts with "Linux" and make sure you add to the end of that line "radeon.modeset=0 nomodeset" and then press Ctrl+X. This will give you the chance to load Ubuntu in a low graphic mode and give you the opportunity to install the ATI drivers.
[*]Once you log into your Ubuntu install go to System ->Administration and install the proprietary drivers.
[/LIST]

That's it, once you've done that reboot and you are good to go. You should not have any more problems with blank or black screens.

Good Luck,

SilentBot

---

