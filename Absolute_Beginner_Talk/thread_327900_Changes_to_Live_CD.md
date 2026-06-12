---
title: "Changes to Live CD"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by michaeljustman on 2006-12-29
Right now I'm making changes to my ubuntu livecd with hopes of installing some modules (newest fglrx w/ support for my video card, etc) adding the firmware for my wireless card, and installing some extra software.

When I chroot into the filesystem that I've extracted from the CD and make changes, will these changes be installed when I use the CD to install ubuntu to my machine or will they just be on the livecd?

---

### Post by Shay Stephens on 2006-12-30
I don't know the answer to that.  But as is, any changes I make to the existing live cd have never transfered over to the hard drive install.  So my guess is the chances are slim.  But who knows, you may discover something cool :-)

---

### Post by michaeljustman on 2006-12-30
I'm using this tutorial: [http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm]("http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm")

I'm not talking about making changes whilst running the LiveCD, but am extracting its contents onto my harddisk and uncompressing the linux image and using chroot, to execute commands such as apt-get, etc, to install things. Then I'm going to recompress it and make a new LiveCD.

I'ven't found any solid info on whether the changes to the LiveCD will also be the same that is installed when you use it to install to your harddisk.

Maybe I'm not making any sense. Thanks anyway.

---

### Post by maniac_X on 2006-12-30
> **michaeljustman said:**
> 
Maybe I'm not making any sense. Thanks anyway.

Making perfect sense to me. In a nutshell, you are trying to slipstream in your own preferences to create a personal Live CD, correct?
.

---

### Post by michaeljustman on 2006-12-30
@maniac_X: Exactly

Anyway... Does anybody know the best way to do this? I thought the tutorial was fine until it started telling me that I didn't have enough space when I tried to install more packages. Space shouldn't matter too much because I can always put it on a DVD.

I know that there is a tool to do this (can't remember the name), but I uninstalled it because it kept on making like 4MB iso images.

Anybody have a better tutorial or know of something to make my life easier doing this?

---

### Post by 3rdalbum on 2006-12-30
Reconstructor, or UCK (Ubuntu Customisation Kit), will help you make changes to the Live CD. Yes, the changes you make to the decompressed SquashFS image will be installed to the hard disk when you Ubiquity.

---

