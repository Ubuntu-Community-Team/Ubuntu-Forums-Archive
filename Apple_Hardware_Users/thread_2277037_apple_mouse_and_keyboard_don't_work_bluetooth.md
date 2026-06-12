---
title: "apple mouse and keyboard don't work bluetooth"
date: 2015-05-06
forum: Apple Hardware Users
---

### Post by frankyboynl on 2015-05-06
hello, I recently set my Mac to dual boot with os x yosemity/ubuntu 14.04.2. The thing is that I cannot pair the apple mouse and keyboard in Ubuntu. In the bluetooth manager they both flash briefly so that I cannot even select them.



thanks in advance, Frank

---

### Post by este.el.paz on 2015-05-07
> **frankyboynl said:**
> hello, I recently set my Mac to dual boot with os x yosemity/ubuntu 14.04.2. The thing is that I cannot pair the apple mouse and keyboard in Ubuntu. In the bluetooth manager they both flash briefly so that I cannot even select them.



thanks in advance, Frank

@Frank:

Sounds like a driver issue . . . seems like it partially working if you can see the items briefly . . . .  This is beyond my skillset, but you might look at "lsmod" in the Terminal, see what driver shows for bluetooth . . . Or, thinking as I'm typing, check "Additional drivers" tab in Software Update and see if anything shows up for BT.  If you want to confuse the issue a bit with numbers of choices, look at "bluetooth" in synaptic and see if it shows what is installed, and possibly recent upgrades . . . .

e..

---

### Post by William_H._Jones_I on 2015-05-14
frankyboynl,

I was trying to do the same thing, but the instructions I have found thus far have not yielded a positive result.  Can you post what you did to enable the Yosemite-Ubuntu dual-boot please?  I would be eternally grateful.

---

### Post by frankyboynl on 2015-05-15
first in os x you need to install the refit bootmanager. then you go in launchpad to the disk manager, and shrink the mac partition. Then you make sure you have an ubuntu cd-dvd-usb. then you reboot into ubuntu, and when you are in the partitioning section you choose the empty space that is now available, format it to ext4 and use as bootpoint /.  That should do the trick. My problem was that when booting into ubuntu, it didn't recognize my bluetooth keyboard and mouse, so during the installation I had to hook up usb ones.


grtz, Frank

---

### Post by William_H._Jones_I on 2015-05-16
frankyboynl,

I tried the rEFInd tool, but that made my Mac act really unstable, especially when in Mac OS X and waking from sleep.  My problem, albeit with Xubuntu, was not having the right video drivers.  I could boot of the boot thumb drive, but got a couple of error messages indicating no video drivers, then the screen went blank.  I couldn't see anything.  This also happened with a boot DVD using rEFInd.  I could boot directly off the DVD and set everything up, but once again, I didn't have any video.  Also, when booting directly off the DVD, I was asked to create not only the / partition, but also a swap partition and the reserved BIOS Boot partition.  I take it that the swap partition is created automatically, and the reserved BIOS Boot partition ignored entirely, when using rEFInd, but I'm not sure, as I have yet to be able to use boot media with rEFInd.

BTW, I'm using an early 2011 17" MacBook Pro (MacBookPro8,3) running Mac OS X 10.10.3.  I have a resident Intel HD Graphics 300 graphics card with an AMD Radeon HD 6750M discrete graphics card.  I really like Mac OS X, but this is an extra laptop, so I could also run Linux natively.  I'm not sure if reverting back to Mac OS X in the future is possible, although technically I don't see why I couldn't just load Mac OS X from my boot thumb drive.  

Is it possible to load Ubuntu/Xubuntu by first wiping out the hard drive?  I have yet to see anything on that.  Of course, what happens if I still don't have the correct video drivers?  I couldn't even use tithe old school way, with text only input.

EDIT: I have yet another issue with my MBP.  I checked the S.M.A.R.T. status yesterday and it was still Verified.  Today, however, it says Failing.  I have noticed extremely strange happenings over the past several days, but as long as the system didn't indicate any hardware errors, I thought everything was cool.  I guess I'll just have to get another hard drive, oh and a Torx screwdriver as well (thank you Apple for using Torx screws).  Not that this has anything at all to do with the graphics issues, but maybe after a hard drive install everything will work.

---

### Post by Pein1911 on 2015-11-30
hi, i just installed Ubuntu 15.10 on my laptop (Lenovo Y500), i have a wireless apple keyboard, but i cant make it pair with ubuntu, Bluetooth in Ubuntu can detect my keyboard easily, but after i press next to connect to keyboard, it just show loading text, without asking for Pair Keyword, and then connect failed !! Then i try boot to Windows to Pair it, it worked fine, then i unpair and try again in Ubuntu but  no change, anyone can help me thanks !

---

### Post by Wobbo on 2016-02-10
I have exactly the same problem. I have posted some information about my experience. I haven't found a way to solve this problem but maybe this extra information could help. askubuntu: mac keyboard wireless problem [http://askubuntu.com/questions/729550/mac-bluetooth-wireless-keyboard-and-keypad](http://askubuntu.com/questions/729550/mac-bluetooth-wireless-keyboard-and-keypad)

---

### Post by este.el.paz on 2016-02-10
@et al:

This **could*** be a bug related behavior . . . on recent installs of U-MATE 16.04 and testing liveDVD I get a "blueman applet" error . . . that relates to "bluetooth" . . . but, since I don't use BT I haven't messed with it.  But, checking launchpad for similar bug reports might bring some response or solutions . . . .

e....

---

### Post by calvinabice10 on 2016-02-12
This trick works especially on the original Bluetooth Wireless keyboards, mice and trackpads. New keyboards and trackpads were released in late 2015 which do not have removable batteries. This may not work for those devices. 


Switch off the keyboard by holding down the power button for at least 3 seconds
Click the Bluetooth icon in the menu bar
Click on &#8220;Set Up Bluetooth Device&#8221; or &#8220;Open Bluetooth Preferences&#8221;
Turn on the keyboard by holding down the power button, BUT DO NOT LET GO OF THE POWER BUTTON. It must be kept held down through the entire process.
The Setup Assistant will find the keyboard, so click the name of the keyboard, and then click on &#8220;Continue&#8221;. Make sure you are still holding the power button down.
You will be prompted for the Pairing Code. You can now release the power button, type the pairing code on the keyboard and then press return. There will be a slight delay whilst the pairing completes (a few seconds)
The keyboard will now be Paired.

---

