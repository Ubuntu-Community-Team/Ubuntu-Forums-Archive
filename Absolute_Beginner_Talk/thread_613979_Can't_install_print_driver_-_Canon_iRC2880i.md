---
title: "Can't install print driver - Canon iRC2880i"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Muad Dib on 2007-11-15
Hi,
This is a toughy.  At our office we have a Canon iR C2880i multifunction printer/scanner/fax device.  I have checked the sites recommended in other threads for linux based drivers and come up empty handed.  A few of them have offered alternatives that count all documents as color documents.  I am an independent sales rep and pay for all of my printouts and copies out of pocket.  I can't afford to be charged for color on everything I print.

The driver disk has an ndis file for linux, but I am too much of a noob to be able to work with the terminal commands.  They all come back as file not found or some other error.  To make matters worse, the printer is a network printer and my connection is wireless.  Fortunately that has not proven to be too much of an issue just yet.

[B]The bottom line is this: I need a techie type who can walk me through the steps to install the driver in extremely dumbed down baby steps.[B]

I will be extremely grateful for any help you can offer.  I need the functions on this printer to work and I don't want to have to resort to falling back on Windows.  Please help.

Many thanks

---

### Post by bumanie on 2007-11-17
Sorry, I can't help with the steps you require. But what I can tell you is that canon are not supporters of open source. I have read something to the effect, that hell will freeze over before canon would think about releasing linux drivers. Not sure if that is still their current philosophy, but it apparently was not so long ago.
you could try this site [http://cweb.canon.jp/drv-upd/bj/other.html](http://cweb.canon.jp/drv-upd/bj/other.html). It is Japanese, but if you can find your printer number, the binary that the computer understands should be the same.

---

### Post by Muad Dib on 2007-11-23
Thanks for the reply, but my model doesn't show up there.  If anyone has a way around this, I'd be grateful.

---

### Post by primski on 2007-12-03
Hello,

it is indeed true canon has poor support for linux drivers, however there are some workarounds for some of the features of the mentioned printer model.

For basic printing use this driver 'Generic PCL 5c Printer Foomatic/hpijs', you can select color profiles, black & white, full color, etc. etc. so that should get you going for a start.

However, scanner and fax features are a bit harder to install on Linux. We are using them successfully from windows computers, but are still investigating how to make them work on Linux too. Will report if have any succes..

Try the mentioned driver and we'll go on from there.

---

### Post by vk5la on 2008-02-22
Hi all,
Canon have released linux drivers for their imageRUNNER Series machines a while back now and include
both postscript and a linux port of their UFRII (Ultra Fast Rendering) Printer description language.

Virtually all of the blackand white and colour machines are fully supported with these drivers.
For instance, for the iR2880 they are available to download as an RPM or DEB package from:

[http://www.canon.com.au/products/multifunctionals/multifunctional_digital_devices/irc2880_drivers.aspx](http://www.canon.com.au/products/multifunctionals/multifunctional_digital_devices/irc2880_drivers.aspx)

Scroll down to the bottom and you'll see them there...
I hope this helps you.
I have tried to install them on Ubuntu but they have a dependency problem that I haven't manage to solve yet.
I have successfully used these drivers with imageRUNNERs and Suse enterprise  linux 10.

Cheers
Andy

---

### Post by hubie on 2008-05-09
I'll have to check out the debian UFRII drivers. 

I originally set up my Canon IR 2800 and CIR 3220 devices by downloading the PPD files for them (it has been a while, so I don't know if I got them by downloading the Mac or Windows PPD files, but they are posted on the download section for the printers with all the other drivers), then I installed them in CUPS.  I cannot recall if you can install printers with PPD files via the CUPS administration page, but I know you can do it through the command line.  Once the PPD files are installed, you can set up all the printing options (duplex, extra trays, etc.) via the administration page as usual.

My memory on this is a little foggy, but if anyone wants to know how I did it, I can figure it out and let you know.

---

