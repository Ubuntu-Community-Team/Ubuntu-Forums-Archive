---
title: "Need Open Firmware command line to EXT HD and other help"
date: 2009-05-04
forum: Apple Hardware Users
---

### Post by harmonz on 2009-05-04
I need help booting into Ubuntu which is on an ext HD. A Lacie 160gb (Porsche-Firewire bought about 2 years ago.) I am using a Powerbook G4 1.5 GHz running Boot Rom v. 4.9.ofo & 10.4.11.

I can get to Open Firmware 3, and write 0 > boot cd:,\install\yaboot
to do a live cd with 7.04 which shows me a Ubuntu 7.04 system on the LaCie Partition disk1s11.
Swap is on disk1s9 and bootstrap was supposed to be on disk1s10 but failed to write (probably due to wrong formatting)

What is the OpenFirmware line to boot from the ext HD instead of the CD? (specifically-!: I'm not even at a novice level at command lines).

Disk Utility shows:
	Name : 	disk1s11
	Type : 	Volume

	Disk Identifier : 	disk1s11
	Mount Point : 	Not mounted
	Connection Bus : 	FireWire
	Partition Type : 	Apple_UNIX_SVR2
	Device Tree : 	fw/node@d04b620307ce85/sbp-2@c000/@0:11
	Writable : 	Yes
	Capacity : 	11.3 GB (12,166,000,128 Bytes)
 
How else can I boot from the Ubuntu system?
From within OSX for example?
How can I fix the bootstrap partition. Format it from OSX (unless I do get to the Ext HD and then perhaps format from there, or go back to the Live CD boot.) 
What is an advised size for the bootstrap partition? 
What size is best for the swap disk?

Formatting was tricky from the Live CD, but evidently safe. Once formatted, how do I get the bootstrap files installed? (assuming that will make bootup to Ubuntu more straight forward - otherwise - how else?)

Can you steer me to a URL that will advise me on a way to access content on the disk1s11 from within OSX 10.4.11?

Can I do this from Terminal and if so, what command line (specifically-! given less than novice status.)

Would anyone who understands my issues, send me an email that you might be a reluctant or willing mentor?
Email access available by clicking my ubuntuforum user name to the left. Send me your Skype name if that is possible?

-

PS I have a Live CD of 9.04 PPC not yet tested.
I hope to redo this whole exercise from it.

I will need to know how to get Ubuntu to recognize Airport Express at 10.0.1.2
with WEP. (one machine has an airport card.)

The other machine (ThinkPad) does not so I'll need to install support for a USB adaptor Netgear WG111 v3. (ie. a unix driver or help configuring or writing some sort of wrap around.?.!) - Unless 9.04 is already able to use these. (probably run Xubuntu from there.)

Is Netgear Unix friendly? or is Linksys or Belkin or Trendnet better? Or is another better?
My deadline to return the Netgear to Staples is today. The have the Linksys

Thanks,
Marc

---

### Post by tiresia on 2009-05-04
In Open Firmware every device has its own specifical path. Since the OF path is quite long there is for common used devices an 'alias' name - so that you can memorize and type it easier. To know an alias for a device type in Open Fimrware 'printalias'
For a Device connected to your computer via Firewire the alias should be 'fw' (check it with printalias). Therefore if you want to boot from an Ubuntu installer placed on the FW-Disk type```
boot fw:,\install\yaboot
```

But if want to boot from an external HD (connected via FW or USB), you need to 'install' the LiveCD the right way. Here is a link with some info
[https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld](https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld) (see the section Booting from USB memory stick')

From your post I don't understand if you want to install Ubuntu on the external HD, or if you want to boot the Installer from the external HD in order to install Ubuntu on the *internal* HD

---

### Post by harmonz on 2009-05-04
Thank you for the line "printalias" I'll try this.
I have jaunty on an ext. HD. At the time of this question, I could not get 7.04 which was on that ext HD to bootup. I thus only sought to boot up from the ext HD. 

I have no interest in doing anything to the Internal HD.

I have Kubuntu on a USB and have hoped to boot from it. All of this is an exercise in the possibilities. The only need to, is a need to know. 

I;ll review the link provided for the memory stick and hopefully get that to work.

Now onto other basics like getting the airport network working, as well as the bluetooth keyboard. 2 hours and counting and no luck. (I'll post that separately.)

thanks

---

### Post by stream303 on 2009-05-05
As for booting Ubuntu on an external firewire disk, perhaps the easiest thing to do is just hold down the alt / option key on startup and you should be presented with the icons for the disk you want to boot from.

I haven't booted 9.04 from an external drive, but in the past, even though one could install painlessly onto an external firewire drive, when rebooting, it usually required manually going back in and editing /etc/yaboot.conf and possibly /etc/fstab UUID's to what they should be.

Pxwpxw was a great help, and from what I hear, yaboot has become a lot smarter - but don't be surprised if after a successfull install the firewire seems cranky. :)

It can be done - the last time I did this on a small G-tech 80gb drive was back during Feisty and Gutsy days - so perhaps things are a bit easier today.

(I actually just got tired of all that and put OSX on the firewire, and Ubuntu dedicated to the internal. )

With 9.04, usb wireless support is much improved due to much of the kernel's atheros-chipset support - so I happily run Belkin F5D5070 and Netgear WG111v2 usb wireless stick on my G5.  And of course the Airport-extreme works as long as you download and install the b43 firmware cutter - but it's nice to know you can use many more usb sticks these days - no problem with wpa2 and Jaunty's Network Manager either.

---

