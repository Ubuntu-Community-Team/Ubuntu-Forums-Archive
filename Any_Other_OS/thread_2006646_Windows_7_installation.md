---
title: "Windows 7 installation"
date: 2012-06-19
forum: Any Other OS
---

### Post by *^kyfds( on 2012-06-19
It's been a while since i've tinkered with boot loaders, so i'm afraid i've gone a bit rusty when it comes to editing with them.

I'm trying to install windows 7 from a USB (using a guide located [here]("http://www.maximumpc.com/article/howtos/how_to_install_windows_7_beta_a_usb_key")) t. I've sucessfully prepped the USB, and all I now need to do is actually install it.

i'm running:

dell optiplex 170L
unknown processor 
running ubuntu 12.04 (used to run windows 7 until i messed up bootloader)
512 mb of ram
unknown graphics chip or motherboard.

If i want to install windows 7, do i need to create a new partition before the installation?

and will i have to edit the bootloader in order to construct a dual boot of both windows and Ubuntu? how do i do this?

All help will be very much appreciated,

~thehumorouscheese

---

### Post by wilee-nilee on 2012-06-19
> **Thehumorouscheese said:**
> It's been a while since i've tinkered with boot loaders, so i'm afraid i've gone a bit rusty when it comes to editing with them.

I'm trying to install windows 7 from a USB (using a guide located [here]("http://www.maximumpc.com/article/howtos/how_to_install_windows_7_beta_a_usb_key")) t. I've sucessfully prepped the USB, and all I now need to do is actually install it.

i'm running:

dell optiplex 170L
unknown processor 
running ubuntu 12.04 (used to run windows 7 until i messed up bootloader)
512 mb of ram
unknown graphics chip or motherboard.

If i want to install windows 7, do i need to create a new partition before the installation?

and will i have to edit the bootloader in order to construct a dual boot of both windows and Ubuntu? how do i do this?

All help will be very much appreciated,

~thehumorouscheese

In the best circumstances you want the W7 to be the first partition on the HD.

Are you trying to repair a W7 or actually install.

Post a a screenshot of gparted from Ubuntu looking at the HD.

Post using the paper clip in the reply panel with the screenshot.

512 ram is barely enough to run both of those OS as well.

Why did you not use the usb tool by microsoft.
[https://wudt.codeplex.com/](https://wudt.codeplex.com/)

---

### Post by *^kyfds( on 2012-06-19
When i had windows 7 installed previously, it ran without a problem.

I save quite a large amount of ram because the video output is not compatible with windows aero.

i'm working on that screenshot

---

### Post by *^kyfds( on 2012-06-19
here's the screenshot.

---

### Post by wilee-nilee on 2012-06-19
So I notice a couple of things, first Ubuntu has very little in it, can this just be reinstalled after saving whatever is in there?

W7 if allowed will install a boot partition and a main partition.

So if you can, to make this easiest, wipe the Ubuntu, let the W7 install, resize it with its disk manager, leaving a unallocated for ubuntu.

Then install the ubuntu.

There is custom partitioning making possibilities here, there always is, personally I would suggest practising that on a usb thumb before trying with an actual install using 2 OS.

Basically overall you want W7 as the first partition for easy access for repair...etc with the W7 on  the usb.

---

### Post by *^kyfds( on 2012-06-19
i suppose that is an option.

i think i might have a spare hard drive that's much larger and much newer than the one i'm currently using.

would it be worth backing my stuff up, replacing the HDD and installing ubuntu through wubi?

---

### Post by wilee-nilee on 2012-06-19
> **Thehumorouscheese said:**
> i suppose that is an option.

i think i might have a spare hard drive that's much larger and much newer than the one i'm currently using.

would it be worth backing my stuff up, replacing the HDD and installing ubuntu through wubi?

I would not suggest wubi, it is just a file in windows and subject to its failure. 

You could shrink and clone the ubuntu, but the partition number will be different on the install, if you use clonezilla, you will have to renumber the clone partition.

If you have a second HD and can run both, you could install the windows to it and copy the ubuntu to it afterwards.

I suspect you have a older setup which will be a master and slave set up the slave cannot be booted from generally, and you want the grub to be the bootloader generally unless you use esaybcd.

---

### Post by *^kyfds( on 2012-06-19
Is there a software i can use to completely erase the contents of hard disk that i can run from USB stick?

---

### Post by wilee-nilee on 2012-06-19
> **Thehumorouscheese said:**
> Is there a software i can use to completely erase the contents of hard disk that i can run from USB stick?

The windows install disc will do it or gparted from a ubuntu live cd.

Honestly there are a lot of ways to do this and numerous bootable cd's to do it with.

You can use darik's nuke and boot if you really need to.
[http://www.dban.org/](http://www.dban.org/)

---

### Post by *^kyfds( on 2012-06-19
thanks for your help.

i've bought myself a bit of time because i downloaded the wrong iso.

time to backup!

---

### Post by wilee-nilee on 2012-06-19
> **Thehumorouscheese said:**
> thanks for your help.

i've bought myself a bit of time because i downloaded the wrong iso.

time to backup!

Since there was never an answer to the windows usb tool I would just say if your W7 is not a MS certified install don't use it.

---

