---
title: "More of a hardware question than a Linux question."
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by moebob24 on 2008-01-17
What are these? I am pretty sure they are for a monitor but what kind of monitor fits on those plugs?????

I know what the pink one is, I just don't know what the other 2 are.

Also...is there a Linux version of Irfanview or something that can view and resize images on the fly. I had to open up gimp and do it that way. Even using gimps resize was harder than Irfanview.

[IMG]http://i100.photobucket.com/albums/m15/shadowahcker/CIMG0326.jpg[/IMG]

---

### Post by zxscooby on 2008-01-17
[http://en.wikipedia.org/wiki/Com_port](http://en.wikipedia.org/wiki/Com_port)

---

### Post by moebob24 on 2008-01-17
I guess I have an old mother board. I was given this computer as a gift and I put Ubuntu on it as well as a few other upgrades. 


I need to get a new video card that supports dual monitors. 

Any help with the image question or should I make a new post?

---

### Post by kostkon on 2008-01-17
> **moebob24 said:**
> Also...is there a Linux version of Irfanview or something that can view and resize images on the fly. I had to open up gimp and do it that way. Even using gimps resize was harder than Irfanview.

I recommend you to use *gThumb*.

---

### Post by Thanoulis on 2008-01-17
The blue one of the top is the serial RJ-xxx (cannot remember now) port. There you can connect some "Special" devices (they told you so). The other one is the serial port to connect the old CRT monitors, i guess.

---

### Post by Paulmd on 2008-01-17
> **moebob24 said:**
> What are these? I am pretty sure they are for a monitor but what kind of monitor fits on those plugs?????

I know what the pink one is, I just don't know what the other 2 are.

Also...is there a Linux version of Irfanview or something that can view and resize images on the fly. I had to open up gimp and do it that way. Even using gimps resize was harder than Irfanview.

[IMG]http://i100.photobucket.com/albums/m15/shadowahcker/CIMG0326.jpg[/IMG]

You have 2 com ports (serial ports), and a parallel port. What screwed up one the poster who said one of them was for a crt monitor is that your backplate is mislabeled. The VGA port, which is for monitors is NOT on that picture.

Com ports are legacy, at one time they were a way to connect a mouse or an external  modem. Other uses included digital cameras and label printers. 

Parallel ports are also legacy, the 2 most common uses were printers and scanners. Sometimes they were used to make direct pc-to-pc connections for data transfer. 

Parallel and serial ports disappeared from most laptops years ago, but are still included on most desktops. But that is changing.

Eventually serial mice were replaced with ps2 mice, which were in turn replaced with usb. Modems moved to internal cards, and to usb. Pretty much everything else moved to usb as well.

I can think of at least 5 different standards that were used for connecting up mice at one time or another. Usb simplifies things, a lot.

---

### Post by Paulmd on 2008-01-17
> **Thanoulis said:**
> The blue one of the top is the serial RJ-xxx (cannot remember now) port. There you can connect some "Special" devices (they told you so). The other one is the serial port to connect the old CRT monitors, i guess.

Some correction is in order. The rj- number us wrong, it's used for telephone, and ethernet style jacks. You may be thinking of rs-232, which is a standard serial port.

Also, the 2 serial ports are the same. You were mislead by a backplate. The monitor connection is 15 pins and female. Both connections here are 9 pins and male.

---

### Post by Paulmd on 2008-01-17
> **moebob24 said:**
> I guess I have an old mother board. I was given this computer as a gift and I put Ubuntu on it as well as a few other upgrades. 


I need to get a new video card that supports dual monitors. 

Any help with the image question or should I make a new post?

What are the specs on your current board?

All I can tell from the image is that it was rebuilt after 1999. (the color coding standard of the ports is called pc-99) 

I know it was REbuilt, or pieced together from parts because the backplate labeling does not match the motherboard ports, though it is close enough. The backplate was printed for a motherboard with integrated graphics, and you have a separate video card.

MOST likely, that means you have an AGP card. 

Given the expected age of the machine, I wouldn't go overboard, perhaps a geforce fx 5200 or 5500.

---

### Post by moebob24 on 2008-01-17
> **Paulmd said:**
> What are the specs on your current board?

All I can tell from the image is that it was rebuilt after 1999. (the color coding standard of the ports is called pc-99) 

I know it was REbuilt, or pieced together from parts because the backplate labeling does not match the motherboard ports, though it is close enough. The backplate was printed for a motherboard with integrated graphics, and you have a separate video card.

MOST likely, that means you have an AGP card. 

Given the expected age of the machine, I wouldn't go overboard, perhaps a geforce fx 5200 or 5500.

It is a KT333 Dragon Lite

It supports 184 pin DDR RAM
Im not sure of the socket for the CPU tho..
My CPU is an AMD Athlon XP +1500
on boot it says it clocks to 1300MHz
I think i should build a new PC, i got this as a gift from a friend because he didn't have use for it and i put ubuntu on it. 

It has been a good PC except for the speed. I upgraded the RAM which helped a lot but I know I would need a new CPU to see real results. And in that case I might as well get a new mobo and CPU with that.

---

### Post by Paulmd on 2008-01-17
> **moebob24 said:**
> It is a KT333 Dragon Lite

It supports 184 pin DDR RAM
Im not sure of the socket for the CPU tho..
My CPU is an AMD Athlon XP +1500
on boot it says it clocks to 1300MHz
I think i should build a new PC, i got this as a gift from a friend because he didn't have use for it and i put ubuntu on it. 

It has been a good PC except for the speed. I upgraded the RAM which helped a lot but I know I would need a new CPU to see real results. And in that case I might as well get a new mobo and CPU with that.

I can tell you it is a Socket A (alias Socket 462). It can support a faster cpu, up to an athlon 2100+. It does have agp, and a new enough version of agp to support your basic off the shelf dual-head card.

This is the manual.

[http://www.soyo.com/uploads/downloads//manuals/k7/mk7vxbl12.pdf](http://www.soyo.com/uploads/downloads//manuals/k7/mk7vxbl12.pdf)


As for prices... check out ebay, that processor is no longer being made, but you can still turn up new ones, and working used ones.

---

### Post by moebob24 on 2008-01-17
> **Paulmd said:**
> I can tell you it is a Socket A (alias Socket 462). It can support a faster cpu, up to an athlon 2100+. It does have agp, and a new enough version of agp to support your basic off the shelf dual-head card.

This is the manual.

[http://www.soyo.com/uploads/downloads//manuals/k7/mk7vxbl12.pdf](http://www.soyo.com/uploads/downloads//manuals/k7/mk7vxbl12.pdf)


As for prices... check out ebay, that processor is no longer being made, but you can still turn up new ones, and working used ones.

I don't think it is worth upgrading the CPU...might as well get a new mobo and upgrade to a newer socket for better CPUs...the new Phenom look pretty sweet...uses the AM2 socket which is on many mobos so my selection is vast. LOL anyone want to buy a 1GB stick of 184 pin RAM?

---

### Post by hsweet on 2008-01-19
If you don't mind writing text commands, you can use imagemagic to resize 1 or 1000 images automatically, for starters.
Here are a few links

[http://www-128.ibm.com/developerworks/library/l-graf/?ca=dnt-428](http://www-128.ibm.com/developerworks/library/l-graf/?ca=dnt-428)
 [http://www.imagemagick.org/Usage/](http://www.imagemagick.org/Usage/)
[http://www.imagemagick.org/script/index.php](http://www.imagemagick.org/script/index.php)
[http://www.imagemagick.org/Usage/basics/#mogrify](http://www.imagemagick.org/Usage/basics/#mogrify)

The command mogrify will do the resizing

---

