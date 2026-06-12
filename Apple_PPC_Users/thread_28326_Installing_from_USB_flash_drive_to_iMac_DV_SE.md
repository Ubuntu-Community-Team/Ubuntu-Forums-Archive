---
title: "Installing from USB flash drive to iMac DV SE"
date: 2005-04-19
forum: Apple PPC Users
---

### Post by kozimodo on 2005-04-19
Is it possible to install Ubuntu from a USB stick?  The reason I ask is that the DVD drive is defunct and I'd rather not spend the money to repair it.

---

### Post by spaceballl on 2005-04-19
No not with a mac. I can't figure out for the life of me Apple doesn't support it. I really wanted to use 2/3 of my iPod shuffle for an ubuntu install and the rest for music, but that won't work. The best your'e going to do is that you CAN find Firewire flash drives on the internet, and apparently those work. They're more expensive than USB ones though. I've never tried, but I'd like to some time.

_Kevin

---

### Post by zoexii on 2007-01-04
Apple DOES support it on some models...  Though I've never personally seen it done.  I am trying to install on a Pismo with a broken DVD drive, but cannot get any help.  Just now someone has sent me to this thread to prove that it CANNOT BE DONE!  A quick google search of "Pismo usb boot" suggests that (given the correct firmware) it is possible.

---

### Post by didg on 2007-01-04
An iMac DV should be ok, at least I'm able to run the LiveCD (feisty) from an USB stick, but there's two issues:
1) cd: alias is used in ofboot so it can't boot from the graphic bootloader (option key), need to make  a new iso.
2) missing /dev/fb0 so you get a black screen on an iMac. need to switch console and reconfigure X.

You must copy the CD image with dd not cp (from OSX or linux)

After that:
go to  OF console.

find the name of the usb stick. (cf. bug #35731) should be something like
usb1/disk@0 or usb0/disk@0
type
boot usb1/disk@0:,\install\yaboot


Or look at the manual ([https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/](https://help.ubuntu.com/6.10/ubuntu/installation-guide/powerpc/)) there're other options for booting the alternate CD.

For double checking you can download pppccd rescue disk from [http://ppcrcd.pld-linux.org/](http://ppcrcd.pld-linux.org/), this one should boot from the Mac menu (option key).

Notes: 
for me me plugging the stick in the keyboard is unreliable.
with USB 1, it's a bit slow.

---

### Post by gurnemanz on 2007-01-06
How about this? Won't work for the iMac, but might work for a Pismo or later. It's kludgy, but so what?

You'd need a Firewire PowerBook in target mode, along with a CompactFlash card adapter carrying a 1 GB (or better) compact flash card in the PCcard slot.

Download the desired iso; copy to the compact flash card inside the card slot on the Powerbook; select the flash card as the boot drive in Set Startup; hope the frelling thing will boot; install to the HD of the PowerBook.

Anyone know why this WON'T work? I used to boot my PB180, 5300 and 1400 from the CF card all the time.

:-k

---

