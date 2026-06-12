---
title: "Can't find a fix for my screwed console"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by Ryuki_NdranC on 2008-04-19
Ok. i tryed the solution you gave me and it still doesnt work, i made a fresh install of gusty and now i can properly say when it gets screwed.

1. Fresh install of Gusty... (problem: the gusty usplash takes to long to load and when changing to console with "ctrl + alt + f(1-6)") i got a console with the wrong screen resolution, all lettes are way to big and fall out the screen)

FIX: I did "sudo nano /boot/grub/menu.lst (and deleted "ro quiet usplash" from my main boot)

2. Installed ndiswrapper and bcm4318 driver (all works fine now)

3. Installed ATI eXpress 200M driver with the "restricted driver manager" and rebooted. (problem: well the usplash screen isnt active so it boots really fast, thats not the problem, but when i try to "ctrl + alt + f(1-6)" the screen now gets all screwed with colors and patters with no console shown what so ever, same thing happens when the systems is shutting down. when i go and check the /boot/grub/menu.lst it doesn't has the ro quiet usplash line, so i dont know how to fix this problem)

Any ideas? It bugging me bad this problem, if you know anything, help plz

Thanks in advance.

---

### Post by mgmiller on 2008-04-19
You cold try changing the vga attributes in menu.lst.

I know these instructions are for resolution during graphical boot, but they also change the attributes when you change to a console.

How to change the resolution during the graphical boot:

You need to edit /boot/grub/menu.lst and add vga=771 or 788 or 792 
to the end of the line for the kernel you are booting.

First make a backup of the old one:

```
sudo cp /boot/grub/menu.lst menu.lst.backup
```

Then edit the file:
```

sudo gedit /boot/grub/menu.lst
```

Once you have the vga= number you like, add it to the automagic line options 
in the additional options area so it carries through to kernel updates. 
This is in /boot/grub/menu.lst as shown below, where I have selected vga=786,
which will set the boot screen to 640x480 24 bit color:

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=786

Finally, to append the change to all kernel lines, run the following: 
 
```
 sudo update-grub 
```

To know which vga= number to use, consult this handy chart:

640x480 800x600 1024x768 1280x1024
......768...........771.............773...........775.................256 colors
......784...........787.............790...........793.................(8 bit)
......785...........788.............791...........794.................(16 bit)
......786...........789.............792...........795.................(24 bit)

---

### Post by Ryuki_NdranC on 2008-04-19
I did that, besides not showing the splash screen, but just a black screen, when i try to change console mode its just shows a black screen. I'm so pissed with Gutsy I'm seriously considering to install Hardy :(

Any other ideas? Thx anyway.

---

### Post by mgmiller on 2008-04-19
Since hardy is only 4-5 days away, it's not too bad a stretch to wait, or you could try live CD of the release candidate.  It that fixes it, then you know you're good to go.  You could do the upgrade now and it will change itself to the final release when the time comes.

---

### Post by Ryuki_NdranC on 2008-04-19
> **mgmiller said:**
> Since hardy is only 4-5 days away, it's not too bad a stretch to wait, or you could try live CD of the release candidate.  It that fixes it, then you know you're good to go.  You could do the upgrade now and it will change itself to the final release when the time comes.

Alrdy installed Hardy ;) so far so good, but i haven't installed the fglrx driver for ati yet, i will post my results for the sake of knowledge :)

---

### Post by Ryuki_NdranC on 2008-04-19
OK definitively its the fglrx installed by the hardware drivers that screws my console, with the vesa ones, everything is fine :(:( i sooo sad, hardy installed my BCM4318 in no time with b43-fwcutter and start working right away and with no apparent slowdowns in performance.

:(:(

Can't believe isnt a fix anywhere :(, i guess i have to bit my hand and get on with my life :(

well thx anyway for your answer, good luck

---

### Post by Ryuki_NdranC on 2008-04-20
I tryed with envyNG and after i install the driver (8-3) it doesn't fix so far only with the vesa drivers i can swich to my console TTY without any screwed colors. :(

---

### Post by propwashz on 2008-04-22
use the commands and chart in the post above to add _defoptions vga=###_ (where the ### corresponds to your normal screen resolution and color depth) while editing your /boot/grub/menu.lst

make sure there is no # in front of the entry you add/change

my console was doing the same thing as yours--but that fixed it

---

### Post by Ryuki_NdranC on 2008-04-22
> **propwashz said:**
> use the commands and chart in the post above to add _defoptions vga=###_ (where the ### corresponds to your normal screen resolution and color depth) while editing your /boot/grub/menu.lst

make sure there is no # in front of the entry you add/change

my console was doing the same thing as yours--but that fixed it

... OK im gonna try. Put what screen resolution i should use if my laptop is widescreen (1280x800)??? 1024x754 maybe? i have a problem with the GDM login screen that each custom login screen i download looks aweful when my widescreen monitor force it to fit :(

Im gonna try this tonight and post inmediate results.

Thx for your imput, i REALLY apreciated :)

---

### Post by mgmiller on 2008-04-22
> make sure there is no # in front of the entry you add/change

Actually, in this instance, you do need a single # at the start of the line.  A double ## means comment, a single # means execute.  

This is the only place I know of where this is the case.  I don't know why, but there you go.

---

### Post by Ryuki_NdranC on 2008-04-22
Ok i fix it... kind of :)

Here's what i did.

```
sudo apt-get install hwinfo
```

then

```
sudo hwinfo --framebuffer
```

this show me

```

  02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.447]
  Unique ID: rdCR.mrzO17IxmKC
  Hardware Class: framebuffer
  Model: "ATI RADEON XPRESS 200M Series MS48"
  Vendor: "ATI Technologies Inc."
  Device: "MS48"
  SubVendor: "ATI RADEON XPRESS 200M Series"
  SubDevice: 
  Revision: "01.00"
  Memory Size: 256 MB
  Memory Range: 0xc0000000-0xcfffffff (rw)
  Mode 0x0382: 320x200 (+320), 8 bits
  Mode 0x030d: 320x200 (+640), 15 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+960), 24 bits
  Mode 0x0320: 320x200 (+1280), 24 bits
  Mode 0x0392: 320x240 (+320), 8 bits
  Mode 0x0393: 320x240 (+640), 15 bits
  Mode 0x0394: 320x240 (+640), 16 bits
  Mode 0x0395: 320x240 (+960), 24 bits
  Mode 0x0396: 320x240 (+1280), 24 bits
  Mode 0x03a2: 400x300 (+400), 8 bits
  Mode 0x03a3: 400x300 (+800), 15 bits
  Mode 0x03a4: 400x300 (+800), 16 bits
  Mode 0x03a5: 400x300 (+1200), 24 bits
  Mode 0x03a6: 400x300 (+1600), 24 bits
  Mode 0x03b2: 512x384 (+512), 8 bits
  Mode 0x03b3: 512x384 (+1024), 15 bits
  Mode 0x03b4: 512x384 (+1024), 16 bits
  Mode 0x03b5: 512x384 (+1536), 24 bits
  Mode 0x03b6: 512x384 (+2048), 24 bits
  Mode 0x03c2: 640x350 (+640), 8 bits
  Mode 0x03c3: 640x350 (+1280), 15 bits
  Mode 0x03c4: 640x350 (+1280), 16 bits
  Mode 0x03c5: 640x350 (+1920), 24 bits
  Mode 0x03c6: 640x350 (+2560), 24 bits
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0383: 640x400 (+1280), 15 bits
  Mode 0x0384: 640x400 (+1280), 16 bits
  Mode 0x0385: 640x400 (+1920), 24 bits
  Mode 0x0386: 640x400 (+2560), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0310: 640x480 (+1280), 15 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+1920), 24 bits
  Mode 0x0321: 640x480 (+2560), 24 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0313: 800x600 (+1600), 15 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+2400), 24 bits
  Mode 0x0322: 800x600 (+3200), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0316: 1024x768 (+2048), 15 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+3072), 24 bits
  Mode 0x0323: 1024x768 (+4096), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

then i edited my /boot/grub/menu.lst
and removed "quiet splash" and the other "quiet" at the end of the main kernel boot. (also added vga=0x0323)

I removed the slapsh because it looks ugly on 1024x768

Apparently so other cards shows different values for each computer. And if i want 1280x800 i need to compile the kernel with the fglrx video driver, and thats something its way out of my leage.... YET :twisted:

Don't get me wrong i don't like too much the slapsh screen. But i wanted to be in the right screen resolution. The thing i dont understand is that with out no vga value imputed my splash screen looks really good. (Im guessing 1280x800) but my TTYs are all screw up.

I think i can declare this post solved, but if someones knows why the splash screen looks good with no vga value, maybe this can be the key for a "forced" widescreen vga boot?

Thx for sticking to my thread guys, i learned a lot thanks to you :)

---

