---
title: "Video_driver_configuration"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by jamil_1 on 2007-06-08
I Have a quite old graphics card by trident. I want to ask that whether I should configure the driver                 specially or rely on what feisty has done for me. I am also having problems regarding playing video file and some times video is choppy or some what odd.
here is what lspci shows

01:0a.0 VGA compatible controller: Trident Microsystems TGUI 9660/938x/968x (rev d3) (prog-if 00 [VGA])
        Flags: medium devsel, IRQ 11
        Memory at ff400000 (32-bit, non-prefetchable) [size=4M]
        Memory at ff8f0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at f6900000 [disabled] [size=64K]

---

### Post by starcraft.man on 2007-06-08
WOW! That is an old card. The easiest solution is for me to tell you to go out and get _any_ recent Nvidia card you can. I don't know why Video is choppy, the card not powerful enough to handle it maybe? I'd really get a new one if I were you...

If your interested in keeping it, I found this[ post the only other Trident ]("http://ubuntuforums.org/showthread.php?t=176502&highlight=trident+9660")on the board I think.. I don't think its particularly relevant to you though so skip to next link. [This one ]("http://ubuntuforums.org/showthread.php?t=83973")will tell you how to manually configure the screen and resolution and such. I doubt it will fix the choppy video, thats just the card/lack of right driver.

Thats it, all the best.

---

### Post by veerakumar on 2007-06-08
Try vga or vesa and then check trident
Xorg & Xfree86 has drivers for trident.
Or use linux kernel framebuffer driver for trident if it exists.
:o

---

### Post by jamil_1 on 2007-06-08
I wish I could say you are not ridiculing me. You are so easily saying that  i should buy a new graphics card. well man I am living in that part of world where computer and internet itself  are luxury then how could I imagine so easily  to buy a new graphics card. If you can't tell me the solution then please do not ridicule me.
(this refers to

 > WOW! That is an old card. The easiest solution is for me to tell you to go out and get any recent Nvidia card you can. I don't know why Video is choppy, the card not powerful enough to handle it maybe? I'd really get a new one if I were you...

If your interested in keeping it, I found this post the only other Trident on the board I think.. I don't think its particularly relevant to you though so skip to next link. This one will tell you how to manually configure the screen and resolution and such. I doubt it will fix the choppy video, thats just the card/lack of right driver.

Thats it, all the best.reply )

---

### Post by starcraft.man on 2007-06-08
> **jamil_1 said:**
> I wish I could say you are not ridiculing me. You are so easily saying that  i should buy a new graphics card. well man I am living in that part of world where computer and internet itself  are luxury then how could I imagine so easily  to buy a new graphics card. If you can't tell me the solution then please do not ridicule me.

Not trying to make fun of you, thats just a card I haven't seen in a long while. Follow the second link I gave and you can manually reconfigure the xorg. Also consider like veera pointed out the different drivers, one might work better. You prolly won't find much support here for that card, most users I know are nvida intel or ati... wasn't trying to be mean.

---

### Post by RTrev on 2007-06-08
> **jamil_1 said:**
> I Have a quite old graphics card by trident. I want to ask that whether I should configure the driver                 specially or rely on what feisty has done for me. I am also having problems regarding playing video file and some times video is choppy or some what odd.


One thing you might want to check is that the DVD player you're using to play those videos has DMA enabled.  I had choppy playback once, and that turned out to cure it.

HTH,
Bob

---

### Post by jamil_1 on 2007-06-08
Please tell me how can I check whether DMA is enabled or not ? iF NOT THEN HOW CAN I ENABLE IT

---

### Post by RTrev on 2007-06-08
> **jamil_1 said:**
> Please tell me how can I check whether DMA is enabled or not ? iF NOT THEN HOW CAN I ENABLE IT

Well, I checked mine like this:

```

sudo hdparm /dev/cdrom

/dev/cdrom:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

```

I don't know what that last error line is all about.

There is also an option in my BIOS which enables DMA for IDE devices.

This isn't the same machine I was on when I had the problem, and someone who knew what they were doing fixed it for me, so I'm not sure what they did.  But *if* this is your problem, I think you can either set it in the BIOS or use hdparm to set it.  Do a:

```
man hdparm
``` to find out what option you need to use with your device.

---

### Post by jamil_1 on 2007-06-08
well my out put is like this

[B]jamil@jamil-desktop:~$ sudo hdparm /dev/cdrom

/dev/cdrom:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
[/B]

I am simply clueless

---

### Post by RTrev on 2007-06-08
> **jamil_1 said:**
> well my out put is like this

[B]jamil@jamil-desktop:~$ sudo hdparm /dev/cdrom

/dev/cdrom:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
[/B]

I am simply clueless

Yeah, me too.  Unless you can find a way to set it in your BIOS.  Sorry, it was a long shot but I'd hoped it would help.

Don't give up.. somebody will wander by who has an answer for you.

---

