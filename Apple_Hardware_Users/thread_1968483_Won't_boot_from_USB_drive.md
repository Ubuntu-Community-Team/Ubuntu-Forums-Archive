---
title: "Won't boot from USB drive"
date: 2012-04-29
forum: Apple Hardware Users
---

### Post by dreamkatcha on 2012-04-29
Hi,

I've just downloaded and installed version 12.04 beta 2 to a USB drive using the instructions on the Ubuntu home page. Everything seemed to go well with no error messages, but when I reboot I'm unable to select the USB thumb drive as a bootable device - only my OS X installation is available.

If I insert the thumb drive while I'm in OS X I get the error message "the disk you inserted is not readable by this computer. Initialise, ignore or reject?" and I'm unable to mount the converted image file as Finder tells me there are "no mountable file systems".

I'd just burn the image to a CD instead, but my CD writer is knackered - a problem affecting lots of users of older Mac Minis that Apple refuse to acknowledge even exists. I think Snow Leopard broke something because it was after I upgraded to this when the problems arose.

Any ideas would be much appreciated please.

---

### Post by subehsharma on 2012-05-01
I have been there where you're right now and spent many sleepless nights trying to work it out. FInally i was able to do it by following this link. 

[http://www.b3ns.com/threads/ubuntu-1...ile-system.29/](http://www.b3ns.com/threads/ubuntu-1...ile-system.29/)

The trick is that unlike installation in a windows machine, in mac you'd need Ubuntu on USB stick as well on a CD. So, you'l boot into cd and from there all the files will automatically be taken from your USB.

---

### Post by dreamkatcha on 2012-05-01
Thanks for the reply. I get the impression it *would* be easier to create a boot CD, but I don't trust my CD writer not to corrupt half a dozen discs before creating a working one. The only workaround I've found is to burn everything at the minimum speed, though even then the results are hit and miss.

Maybe I'll give it a go on someone else's Windows machine. Just a bit miffed to have to jump through all these hoops before I've even got off the starting blocks.

---

### Post by falconbeak on 2012-05-03
[http://penguintosh.com]("http://penguintosh.com")
Worked for me.

---

### Post by dreamkatcha on 2012-05-03
Hmm, interesting, thanks. I managed to use it to create an Ubuntu USB drive that's recognised in OS X, but still won't boot. 

Apple in their wisdom made their new aluminium keyboards incompatible with the EFI of older Macs (*their own hardware!*) so to select an alternative boot source on startup I have to hold down the remote's play button and navigate using the wheel.

Using rEFIt, the option to boot into Ubuntu appeared to be available but I couldn't select it. Without rEFIt, the only option I had was to boot into OS X.

If I was into conspiracy theories... :-k

---

### Post by Dave75 on 2012-05-06
I've been successful in installing 12.04 on a USB flash key and booting from it on a Mac.

I've used the PLOP Boot Manager; you don't have to install anything on your Mac, just burn on a CD the file "plpbt.iso" you can find in the PLOP Boot Manager zip file (just google it), then start your Mac pressing ALT as usual for boot option and select CD, then after booting from CD (so the PLOP file burned on it) you'll see a graphical window list where you can chose to boot from HD, or USB and other choise; just select USB having your USB flash key with Ubuntu installed on it already insterted in your MAC. 

Actually I'm writing from 12.04 installed on USB flash key booted on my MacBook Pro 5.1

Davide

---

