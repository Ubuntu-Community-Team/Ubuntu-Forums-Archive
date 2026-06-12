---
title: "difficult question: booting ubuntu off ipod (with xgl?)"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by Mogen317 on 2006-03-31
I'm pretty new to linux and brand new to ubuntu.  Here is what i would love to be able to do but i'm not sure its possible.  Please point me in the right direction.

I have a 30gb ipod (video).  It's a FAT32 format.  I would like to run an operating system off my ipod.  I am also smitten with the recent XGL live cd that was released and have heard that XGL also works with Ubuntu.  I also like the fact that ubuntu is regularly updated and seems pretty easy to use.  

So... I would like to boot a XGL version of ubuntu off my ipod.

Here's what seems dificult.  

1. i know ubuntu is meant to be installed permentally on one computer.  Does ubuntu have all the hardware detect functions that a live cd type distro thats meant to be moved from computer to computer does?  Maybe it would be easier to somehow copy the image of a live cd to the ipod.

2. i've read reports of other people trying to boot linux off ipods that the tiny 1.8" hard drive is not meant to be accessed continually and can get very hot potentually damaging your ipod.  I know that other distros such as Damn Small Linux have features like a frugal install for a CF flash card meant to limit the amount of read's and write's.  Does ubuntu have anything like this?

3. Even though 30 gigs is a pretty big space i want to save as much room for music as possible.  other distros have an option to download/install only the programs you want.  does ubunto have any thing like this?

4. finally, an ipod really isn't a traditional hard drive, it has its own processor and such.  Do i have to worry at all that by installing a bootable os that the ipod might get confused and try to run ubuntu instead of the ipod firmware!!


Thank you so much if you can help me out.  i realize i'm asking alot, so who knows, maybe ubuntu isn't right for me?

---

### Post by stuporglue on 2006-03-31
> 1. i know ubuntu is meant to be installed permentally on one computer. Does ubuntu have all the hardware detect functions that a live cd type distro thats meant to be moved from computer to computer does? Maybe it would be easier to somehow copy the image of a live cd to the ipod.


Most stuff should just work, but you'd probably have to reconfigure video each time if you wanted anything with 3d acceleration. You could just download the ISO and put it on your iPod, but then you couldn't boot other computers from it. You could use Qemu though.

> 2. i've read reports of other people trying to boot linux off ipods that the tiny 1.8" hard drive is not meant to be accessed continually and can get very hot potentually damaging your ipod. I know that other distros such as Damn Small Linux have features like a frugal install for a CF flash card meant to limit the amount of read's and write's. Does ubuntu have anything like this?


It's more of the long-term wear and tear. Ubuntu doesn't have the frugal type install, that I know of. Putting your swap partition on the iPod would be pretty brutal for it...

> 
3. Even though 30 gigs is a pretty big space i want to save as much room for music as possible. other distros have an option to download/install only the programs you want. does ubunto have any thing like this?

This is where you're going to start running into problems. I think that the iPod  won't like it if you mess with it's partitions, but to get a propper Linux install, you'd need at least two new partitions (swap and root). Ubuntu isn't going to go onto a FAT32 partition easily, if at all. 


> 4. finally, an ipod really isn't a traditional hard drive, it has its own processor and such. Do i have to worry at all that by installing a bootable os that the ipod might get confused and try to run ubuntu instead of the ipod firmware!!

This isn't a problem. They're different places and different architectures. The iPod looks for it's boot loader in a specific place. 


My analysis:

Installing Ubuntu or annother Linux on your iPod at the same time as having it work as an iPod would be very difficult. If you're up to it, that's cool and good luck. :-) 

The next best option would be to keep a copy of Qemu for Windows/Linux on your iPod, and an image of a Linux system (like DSL does, or others at the FreeOSZoo). The downside is that Qemu uses SDL for the graphics, and I'm nearly 100% that you couldn't get XGL working inside it. 

What you're asking for is pretty tough, so you're probably going to have to make some decisions:
     Install to iPod     vs    No install to iPod
1) no iPod functionality vs. iPod functionality
2) XGL                  vs.    No XGL
3) Boot from iPod     vs. No Boot from iPod
4) More wear on iPod  vs. Normal disk wear on iPod


Good luck!

---

### Post by BlaineM on 2006-04-05
I know this is not what you are looking for, but I thought it was cool anyway.  [http://ipodlinux.org/Main_Page](http://ipodlinux.org/Main_Page)

---

### Post by matt_risi on 2006-10-11
Fact of the matter is HOW FRIGGIN SWEET would it be to have a running Ubuntu distro off an iPod?! Power to you for even fathoming this.

---

