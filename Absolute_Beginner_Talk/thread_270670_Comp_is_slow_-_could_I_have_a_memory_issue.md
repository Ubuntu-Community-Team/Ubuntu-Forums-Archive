---
title: "Comp is slow - could I have a memory issue?"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2006-10-03
How do I check my RAM and make sure it's working properly. TIA.

P.S. - I had been investigating whether my graphics card was the issue, but everyone seems to have lost interest in that line. I'd still appreciate help checking that if anyone has input. Thanks again.

---

### Post by bulldog on 2006-10-03
You can run memtest in GRUB.

Try glxgears in your terminal and look at the output to see if your graphics card have the proper fps.

Here is some extra info what could be of use.

[http://ubuntuforums.org/showthread.php?t=140989](http://ubuntuforums.org/showthread.php?t=140989)

---

### Post by ricardisimo on 2006-10-03
Is it safe to assume that 120-ish FPS is not optimal?

---

### Post by bulldog on 2006-10-03
Yep that's safe.

---

### Post by ricardisimo on 2006-10-03
> **bulldog said:**
> Yep that's safe.

OK, where to begin...? Should I run memtest from startup? Please remember I'm a noobster and I don't even know what GRUB is or how to get there. Is there a certain syntax for using memtest?
I glanced over the thread link you sent, and as I recall I don't have Nvidia drivers. There's certainly no modprobe or Nvidia folder in etc. I believe the driver is called vesa. Any hints? Thanks again.

---

### Post by bulldog on 2006-10-03
What kind of graphics card do you have?

Memtest is an option in your bootmenu.

---

### Post by PriceChild on 2006-10-03
When you start your system, the grub menu loads.

You will get several options of which kernel to boot, different versions shown by numbers, and also recovery versions.

At the bottom will be "memtest86+" or something like that. Just press down on the keyboard to highlight it then press enter.

---

### Post by ricardisimo on 2006-10-03
from terminal:
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741 /760/761 PCI/AGP VGA Display Adapter

---

### Post by bulldog on 2006-10-03
That's nice to know,but I'm curious what it is,a nVidia or ATI based chipset.

Don't know if there's a SIS graphic's driver,I have never heard of it,but could be ofcourse.

Don't you have a manual or something like that?
It should be in there.

I'm off for the next 17 hours,maybe someone else can help you in the mean time,or you have to wait till tomorrow.

It gives you the time to figure out what's in the box :D

---

### Post by ricardisimo on 2006-10-03
Quick reminder... what would I (normally) press on startup to get bootup options? Is it f8?

---

### Post by bulldog on 2006-10-03
> **ricardisimo said:**
> Quick reminder... what would I (normally) press on startup to get bootup options? Is it f8?

If you set your computer on it's going to display your hardware and stuff.
If everything is right you get a menu where you can choose which kernel you want to boot,or you see hit ESC to see more options.

Then you see GRUB and one of the options you have is to run memtest to check your memory.

But that's not your problem I think,you need to figure out if you have an ATI or nVidia graphic's and install the driver for it.

---

### Post by confused57 on 2006-10-03
I have integrated Sis video graphics controller, Ubuntu automatically assigned the "vesa" driver, which had some video display problems...changed the driver to "sis" and the video graphics displayed much better.

You can change it by:
```
 gksudo gedit /etc/X11/xorg.conf
```

change "vesa" to "sis"

or you can:
```
sudo dpkg-reconfigure xserver-xorg
```
Just select "no" at the first screen to autodetect, then you're probably safe to select the default values for everything else, except for your video driver or possibly your desired screen resolutions.

Before you change anything, you might want to back up your xorg:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

### Post by ricardisimo on 2006-10-03
> **bulldog said:**
> That's nice to know,but I'm curious what it is,a nVidia or ATI based chipset.

Don't know if there's a SIS graphic's driver,I have never heard of it,but could be ofcourse.

Don't you have a manual or something like that?
It should be in there.

I'm off for the next 17 hours,maybe someone else can help you in the mean time,or you have to wait till tomorrow.

It gives you the time to figure out what's in the box :D
You're asking the $20,000 question. I keep hoping that someone would tell me how to get chipset info, and instead I keep getting other very interesting and very useful, but somewhat off-target suggestions. So, how do I get my chipset info for my graphics card. Like I said above, supposedly the current driver is one called "vesa" (based on running ```
sudo dpkg-reconfigure xserver-xorg
``` in the terminal. The most info I can get on the type of card is "generic". Thanks.

---

### Post by ricardisimo on 2006-10-03
> **confused57 said:**
> I have integrated Sis video graphics controller, Ubuntu automatically assigned the "vesa" driver, which had some video display problems...changed the driver to "sis" and the video graphics displayed much better.

You can change it by:
```
 gksudo gedit /etc/X11/xorg.conf
```

change "vesa" to "sis"

OK... this is kind of weird. I changed the driver to "sis" and two things happened: 
[LIST=1]
[*]My display is much smoother and more well-behaved (my screens actually scroll rather than jump)
[*]My fps is one-third what it was before! It's at about 40 frames/second now.
[/LIST]
This can't be right, or can it?
Can anyone tell me a foolproof method of determining my chipset and the appropriate driver? Thanks again everyone.

---

### Post by zekopeko on 2006-10-03
the only method i can think right now is to watch your computer screen when it starts.

i have a **ASUS a7nx8** motherboard so that is what appears at the left upper corner just when i start the computer.

---

### Post by ricardisimo on 2006-10-04
> **ricardisimo said:**
> OK... this is kind of weird. I changed the driver to "sis" and two things happened: 
[LIST=1]
[*]My display is much smoother and more well-behaved (my screens actually scroll rather than jump)
[*]My fps is one-third what it was before! It's at about 40 frames/second now.
[/LIST]
This can't be right, or can it?
Can anyone tell me a foolproof method of determining my chipset and the appropriate driver? Thanks again everyone.

I tried ***sudo lshw*** and got this:
```
*-display
                description: VGA compatible controller
                product: 661/741/760/761 PCI/AGP VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga cap_list
                resources: iomemory:d0000000-d7ffffff iomemory:dfee0000-dfefffff ioport:dc00-dc7f irq:11
```

Is this at all helpful for determining my chipset and the appropriate driver? TIA.

---

