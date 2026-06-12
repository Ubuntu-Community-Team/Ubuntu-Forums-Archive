---
title: "Installing Ubuntu onto a Hitachi 4gb microdrive"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by father of 2 sons on 2007-03-18
I am planning to build a low power machine for my garage.  It will be mostly used for internet and music/video via a network drive in the house.  My plan includes installing Ubuntu onto a 4gb Hitachi microdrive via an IDE adapter from Addonics.  Since the adapter and the drive support ultra DMA 33 mode-2, I don't forsee a problem.  Also, since the microdrive is an actual hardrive, I should have no need for an embedded or read only enviroment, Since I will not have the read/write limits of a solid state CF card.

  
  I really didn't have a need for a low power machine, but after looking at prices,  I thought it would be a cool project.  Here are the components:

 PC CHIPS V21G V1.0C VIA C7 VIA CN700 Flex ATX Motherboard/CPU Set
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813185094](http://www.newegg.com/Product/Product.aspx?Item=N82E16813185094)

 CORSAIR ValueSelect 512MB
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820145530](http://www.newegg.com/Product/Product.aspx?Item=N82E16820145530)

 ENCORE ENRXWI-SG 108Mbps Wireless Access Point
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833180049](http://www.newegg.com/Product/Product.aspx?Item=N82E16833180049)

Addonics IDE to CF adapter with 3.5" bay mount
[http://www.addonics.com/products/flash_memory_reader/adidecf.asp](http://www.addonics.com/products/flash_memory_reader/adidecf.asp)

Anyone see a problem with this setup?  I am new to linux so i am just guessing on how the ubuntu installer will react to the microdrive setup.

---

### Post by h0ax on 2007-03-18
Wow - I like the concept,

Personally I have never tried anything like this, but it looks like you've thought it out and based on your logic and my own thoughts - I think it will work.
Linux is so portable that it can be installed on mostly anything

Let us (or me :P) know how it goes!

---

### Post by father of 2 sons on 2007-03-18
I will Post my results when the components arrive later this week.  If Ubuntu works, I plan to pick up 1 or 2 more microdrives (depending on price, maybe Ebay) for other linux distros or maybe a slimmed down version of XP.

I know their are cheaper ways to multi boot, but it just sounds cool to plug in a new microdrive and have a new os enviroment.

---

### Post by PhillyB on 2007-03-18
That is very cool, I definitely want to hear about that.

---

### Post by father of 2 sons on 2007-03-25
The box works great.  Ubuntu installed with no issues, but drive access is slower since it is only a micro drive.  The temperature inside the box is 22c and the CPU is at 24c with no case fans, almost silent.  Overall, a success.

I would like to add that Ubuntu was a fine choice for my first attempt at Linux.  I had some trouble installing the driver for the Via cn700 video, but once I did some research and learned how to utilize scripts, it was pretty easy.  The package manager is great and so is the update notification(s) for whatever packages I have installed.  

Kudos to the Ubuntu team!

---

