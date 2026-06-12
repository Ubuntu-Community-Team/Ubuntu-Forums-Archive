---
title: "Ubuntu on iMac &lt;USB&gt;"
date: 2012-08-31
forum: Apple Hardware Users
---

### Post by LunaMacNoob on 2012-08-31
I want to install Ubuntu Desktop 12.0.4 on a dead iMac. The iMac has no OS installed into it. The only access I have is through an uncompatible OS X Snow Leopard DVD. This gives me access to Disk Utility and terminal (although the terminal will not recognise the sudo command).

I would like create a USB installer (not cd at all costs, as I have no access to CDS at this time). By installer, i want it to install onto my internal HD off my USB.

I do not have access to another apple computer. I do have access to a machine running Windows 7 

Help would be mega appreciated

---

### Post by Lars Noodén on 2012-08-31
Which kind of iMac?  Does it have an Intel processor or a PPC?  That will determine which image you download and put on your USB stick.

---

### Post by LunaMacNoob on 2012-08-31
> **Lars Noodén said:**
> Which kind of iMac?  Does it have an Intel processor or a PPC?  That will determine which image you download and put on your USB stick.


[http://www.everymac.com/systems/apple/imac/specs/imac-core-2-duo-2.0-20-inch-aluminum-specs.html](http://www.everymac.com/systems/apple/imac/specs/imac-core-2-duo-2.0-20-inch-aluminum-specs.html)
Intel

---

### Post by Lars Noodén on 2012-08-31
Ok.  You can use the AMD64 or AMD64+mac images.  

Here are some instructions for making a bootable USB stick using Ubuntu, OS X or other.  I hope they work for you, I've had mixed results myself lately:

[https://help.ubuntu.com/community/Installation/FromImgFiles/](https://help.ubuntu.com/community/Installation/FromImgFiles/)

---

### Post by LunaMacNoob on 2012-08-31
> **Lars Noodén said:**
> Ok.  You can use the AMD64 or AMD64+mac images.  

Here are some instructions for making a bootable USB stick using Ubuntu, OS X or other.  I hope they work for you, I've had mixed results myself lately:

[https://help.ubuntu.com/community/Installation/FromImgFiles/](https://help.ubuntu.com/community/Installation/FromImgFiles/)

I can't use the Mac tutorial ecause terminal doesn't recognise the sudo command
If I follow windows instructions, will it boot on iMac

---

### Post by Lars Noodén on 2012-08-31
> **LunaMacNoob said:**
> I can't use the Mac tutorial ecause terminal doesn't recognise the sudo command
If I follow windows instructions, will it boot on iMac

What about a plain [font=Courier New]su -[/font] instead?  And then working without sudo.  It's been a while so I cannot remember what the terminal is like on the installer DVD.

---

### Post by LunaMacNoob on 2012-08-31
> **Lars Noodén said:**
> What about a plain [font=Courier New]su -[/font] instead?  And then working without sudo.  It's been a while so I cannot remember what the terminal is like on the installer DVD.

So I type in  su-*dd*if=/path/to/downloaded.img*of=/dev/rdiskN*bs=1m

---

### Post by Lars Noodén on 2012-08-31
I'm looking at the Terminal utility in a Snow Leopard installation DVD and it looks like you can bypass the sudo / su stuff and just work directly with dd.  

There are a limited number of shell utilities provided so you may have to use the graphical Disk Utility program to figure out which device your USB stick is using.

---

### Post by LunaMacNoob on 2012-08-31
> **Lars Noodén said:**
> I'm looking at the Terminal utility in a Snow Leopard installation DVD and it looks like you can bypass the sudo / su stuff and just work directly with dd.  

There are a limited number of shell utilities provided so you may have to use the graphical Disk Utility program to figure out which device your USB stick is using.

Could you explain these steps in detail please?

I'm a mac noob:/

---

### Post by Lars Noodén on 2012-08-31
It would take a while and not a small amount of effort to write up and there are already many other guides to creating bootable USB sticks for Ubuntu installation.  Can you winnow through some of the available guides until you find one that works for your situation?

---

### Post by LunaMacNoob on 2012-08-31
> **Lars Noodén said:**
> It would take a while and not a small amount of effort to write up and there are already many other guides to creating bootable USB sticks for Ubuntu installation.  Can you winnow through some of the available guides until you find one that works for your situation?

None of these work without sudo or some mac program. I've searched for hours

---

### Post by Lars Noodén on 2012-08-31
I've looked further at using the Snow Leopard install DVD and run into a dead end: how will you get the disc image?  No web browser on the DVD, not even curl or wget.  So you will need another machine.

What systems do you have available?  Apparently no OS X but maybe you have an Ubuntu machine or something else?

---

### Post by LunaMacNoob on 2012-08-31
> **Lars Noodén said:**
> I've looked further at using the Snow Leopard install DVD and run into a dead end: how will you get the disc image?  No web browser on the DVD, not even curl or wget.  So you will need another machine.

What systems do you have available?  Apparently no OS X but maybe you have an Ubuntu machine or something else?

i have a windows 7 laptop that i can get the image off. I can put that on one usb and burn it to another usb

---

### Post by Lars Noodén on 2012-08-31
Then that's what we're stuck with.  I don't use Windows so I wouldn't know if the old guide still works for Vista7.  But there are quite a few:

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
[https://help.ubuntu.com/community/Installation/FromUSBStick#From_Windows](https://help.ubuntu.com/community/Installation/FromUSBStick#From_Windows)

I hope these help.  The basic steps ought to be the same.

---

### Post by LunaMacNoob on 2012-08-31
> **Lars Noodén said:**
> Then that's what we're stuck with.  I don't use Windows so I wouldn't know if the old guide still works for Vista7.  But there are quite a few:

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
[https://help.ubuntu.com/community/Installation/FromUSBStick#From_Windows](https://help.ubuntu.com/community/Installation/FromUSBStick#From_Windows)

I hope these help.  The basic steps ought to be the same.

i followed the steps, success!
tried alt-booting on imac
woulnt pick usb up as bootable
picked up in disk utility but on information, botable: no

help?

---

### Post by Lars Noodén on 2012-08-31
What about using the open firmware.  When the iMac is powered on, press cmd-opt-O-F (all four at the same time) until you get a prompt.  Cmd is the 'historical marker' symbol.  Then at the prompt try the following.

```

boot usb1/disk@1:2,\\yaboot

```

If usb1 does not work, try usb0.  That's my last guess.

---

### Post by LunaMacNoob on 2012-08-31
> **Lars Noodén said:**
> What about using the open firmware.  When the iMac is powered on, press cmd-opt-O-F (all four at the same time) until you get a prompt.  Cmd is the 'historical marker' symbol.  Then at the prompt try the following.

```

boot usb1/disk@1:2,\\yaboot

```

If usb1 does not work, try usb0.  That's my last guess.

nothing happens when i hold down the keys

---

### Post by Lars Noodén on 2012-08-31
It only works when the machine is just starting to boot just as it is turned on.  It may take a few tries to get into Open Firmware.

---

### Post by LunaMacNoob on 2012-08-31
> **Lars Noodén said:**
> It only works when the machine is just starting to boot just as it is turned on.  It may take a few tries to get into Open Firmware.

doesnt boot into open firmware

final question, if i burn the iso for ubuntu mac onto a cd using a windows disk burner, will it boot on my iMac

---

### Post by Lars Noodén on 2012-08-31
(Booting to Open Firmware has been tricky for me, but with persistence I have been able to get it to boot.)

Windows claims to do lots of standard things but then when push comes to shove actually implements variations that are subtly incompatible or broken.  Hence the infamous "embrace, extend, extinguish" strategy.  There's no telling how they handle CDs/DVDs unless you actually try it and see for your self whether it works or not.  I do hope it works for you.

Note, many of the Ubuntu images are now oversized and no longer fit on a CD or CD-RW.  In those cases, you'll have to use a DVD (or a reusable DVD-RW) or else turn to smaller distros like Lubuntu and load the rest from the network.

---

