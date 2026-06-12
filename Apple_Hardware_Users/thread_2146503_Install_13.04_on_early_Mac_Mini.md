---
title: "Install 13.04 on early Mac Mini"
date: 2013-05-18
forum: Apple Hardware Users
---

### Post by jamesisin on 2013-05-18
I can't get the installation media to appear.

The Mini is an early Intel model, I'm guessing maybe 2008 or 2009, DVI port and no mini-dispaly on the rear.

I have tried using 12.04, 12.10, and 13.04 and several iterations (32/64; Intel/AMD; Mac optimized) both as a USB (thanks ImageWriter) and CD/DVD (13 no longer fits on a CD).  I can't get anything to appear in the EFI boot menu (I get only the usual Mac HDD and Recovery HD choices).

Advice?

---

### Post by jamesisin on 2013-05-19
Anybody?

---

### Post by jamesisin on 2013-05-19
I have installed rEFIt and also made attempts using an external DVD drive (in case the Combo Drive was bad which it's not).  Still the same: I get no option in EFI or in rEFIt for the installation media.

---

### Post by jamesisin on 2013-05-21
So I tried wiping the HDD and reinstalling Lion just in case.  Then I discovered that both the Mac and Windows didn't like the USB drive I had created using 12.04.  So I hopped onto my 10.04 machine and created another 13.04 USB installer.  That one didn't get a format request from either.  Nonetheless, I still am unable to get the Mac to recognize any installation media (for Ubuntu) that I give it.  (It recognized the Lion USB installer just fine.)

---

### Post by bastones on 2013-05-24
When I had first tried installing Ubuntu via a DVD disc it would display a blinking cursor when I pressed C at start up in order to boot into the Ubuntu DVD disc. The way I went around this is by pressing the Alt key at start up and instead choosing the "EFI" disc option. From here a GRUB menu appeared and I chose "Try Ubuntu" which booted me into the Ubuntu desktop on the LiveCD and I installed Ubuntu from there. Just a wild guess but may be something you may also want to try.

I'd recommend you first install [rEFInd]("http://www.rodsbooks.com/refind/") (an active [fork]("http://refit.sourceforge.net/#news") of rEFIt) so you can easily boot between Ubuntu and Mac OS X when you start up your Mac mini. Before installing Ubuntu I created a partition in Mac OS X using Disk Utility as MS-DOS. When installing Ubuntu, using the partitioner within the installation wizard, I deleted the MS-DOS partition I had created and with that newly-available free space I created one primary and logical partition - for the Ubuntu installation and swap (virtual memory), respectively.

---

### Post by GhettoMrBob on 2013-05-25
Just to simplify the process and avoid having to delete that MS-DOS partition as bastones said, you can instead either shrink your OS X partition via disk utility or add a partition and delete it within disk utility. This way once you're in the live installer you can select the use available free space option.

Also, the USB Ubuntu installer is only recognized from the rEFIt menu from my experience.

Another thing to consider: make the USB installer via terminal in OS X. Open up terminal while your USB is mounted. Type "diskutil list" and it should show you all the mounted partitions. Next type "diskutil unmountDisk /path/to/usb". Then to write the Ubuntu image to the USB type "sudo dd if=/path/to/.iso of=/path/to/usb bs=4m".
[B]
Things to note:[/B]
Instead of having to type the path to the Ubuntu image, you can drag the image into the terminal window and it will autofill, helping to avoid a mistake.
While doing the actual dd'ing of the image, if you use place an "r" in front of the usb path (ex: /dev/**r**disk1) the dd will be quicker.
I've never once had an issue with this method and then finding the USB installer within the rEFIt menu.

---

### Post by jamesisin on 2013-07-13
Ok, using rEFInd I am able to get to what I believe is my Ubuntu 13.04 amd64 + Mac installation USB stick.  However, selecting that penguin leads not to a boot environment and the installer.  Instead it leads to an error of some kind:

[IMG]http://soundunreason.com/slopbucket/img_4394_800.jpg[/IMG]

---

