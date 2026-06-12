---
title: "ASUS M2A-vm hdmi ?"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by deadmnky on 2008-01-25
is any one here using an ASUS M2A-VM hdmi motherboard if so what bios did you flash to when you set it up. i used the 1603 and for some reason have no dvi output at all>
i remember reading about some issues but it was a little dated i believe. if the any one here is using this board and can help with this situation i would greatly appreciate it.

---

### Post by roboxking on 2008-01-25
I'm also using that motherboard, but I just used the default BIOS, and so far, I haven't received any problems with it. sorry I can't be much of help. Also which processor and version of Ubuntu are you using?

---

### Post by deadmnky on 2008-01-26
amd 64athalon x2 or amd 6400+ depends on how you want to put it. 7.10 gutsy gibbons
do you use the dvi out put or vga?

---

### Post by deadmnky on 2008-01-28
it was a bent pin slot on the motherboard it all works now. i had no problems getting in to ubuntu either thanks to all who tried to help.

---

### Post by miesnerd on 2008-02-03
i  have the same board and am having a TON of problems.
I just bought it last week and also bought (seperately) 2x2 GB of OCZ DDR2 ram.
Will they not work? They dont seem to want to work. 
Ive been trying to tweak the bios to get the mobo to let me get through a boot with them.
I had (before the memory upgrade) 1 GB installed and everytrhing worked perfectly.
Now, if it lets me boot all I get is the message " Disk boot failure, Insert system disk and press enter".

So ive been trying to boot into a live cd to see what i can/cant do.
Wont ever let me all the way thru a live cd boot. Either the computer locks up or the display goes dark. 
Since you guys have the same bios, can you tell me what all the settings should be?

Thanks

Miesnerd

---

### Post by deadmnky on 2008-02-04
so i just checked the list of vendors for compatible ddr2 and did not see ocz as a vendor it supported. personally i have 2 corsair 1024mb cards and have no problems with it so far. i will post my bios settings when i restart the computer got a couple of downloads, never mind here they are and a restart is required so ill let you kow what particularly are you interested in the bios.
did you get the hdmi card working for a second monitor?

---

### Post by deadmnky on 2008-02-04
so i looked at the bios i dont recall anything out of place its all hd audio my settings were mostly automatic. onboard vga, 2048 memory was available. i was wondering if maybe there was a problem with the version of linux. i dont know but can 32 bit systems handle more than 4 gigs of ram it seems i want to think that i heard that 32 windows could not handle more than that in ram i could be wrong or mis remembering something. are you using all four slots if so try putting the 1 gig you had before in slots 1a+2a then tthe 4 gig you have in slots 1b+2b see if that would work. does it say you have the mem available in you bois info?

---

### Post by falstaff on 2008-02-12
Audio Output over HDMI is supported with latest ALSA Version 1.0.16. This will be included in Hardy...

cya
falstaff

---

### Post by miesnerd on 2008-02-12
So sorry to not update. I updated my bios and changed the speed of the ram. I updated from 1404 to 1603 and just about everything is smooth sailing. I have 5 GB of ram working on a 64 bit OS that is screaming along, and it couldnt be better. I should be getting my second monitor in the mail here soon so I'll try to remember to update you guys as to the HDMI working with that bios.

Miesnerd

---

### Post by bpasham on 2008-02-16
> **deadmnky said:**
> so i just checked the list of vendors for compatible ddr2 and did not see ocz as a vendor it supported. personally i have 2 corsair 1024mb cards and have no problems with it so far. i will post my bios settings when i restart the computer got a couple of downloads, never mind here they are and a restart is required so ill let you kow what particularly are you interested in the bios.
did you get the hdmi card working for a second monitor?

[FONT="Garamond"][SIZE="4"]I dont think it is related to the compatibility of RAM but is definitely the problem with 690G drivers included with this version of kernel. They will not work with more that 4G RAM.
simple workaround is to reduce to just little bit less that 4G. It the GRUB kernel parameters, pass the parameter MEM=4095MB, and this should solve your problem of not booting.[/SIZE][/FONT]

---

### Post by seapahn on 2008-02-25
> **falstaff said:**
> Audio Output over HDMI is supported with latest ALSA Version 1.0.16. This will be included in Hardy...

cya
falstaff

Anyone actually have audio working over HDMI on this board (m2a-vm)? 

I have almost everything working except that. The graphics started to be fairly decent with the 8.2 Catalyst drivers (released 2/13/08). I have decent 3D with opengl. No xv so video playback is somewhat choppy but at least I know that is not supported yet.

HDMI video is working ...  I have dual head DVI and HDMI.
S/PDIF Audio working using Alsa 1.0.16 drivers. Can get correct 5.1 playback on my amplifier. 

The HDMI soundcard does show up as a second card. But I have had no luck actually using it. System becomes rather unstable (strange freezes) when I do try to use it.  I have not tried unplugging the cable connected to the S/PDIF output on the HDMI card that came with the board.

---

### Post by miesnerd on 2008-02-25
seapahn-
can you tell me a little about your graphics card setup. Did you get the onboard dual head to work or do you have another graphics card?

I gave up trying to get the onboard radeon dual head to work and broke down and ordered a graphics card today. Let me know.

---

### Post by seapahn on 2008-02-26
Yes onboard with the hdmi connector running to my 42" lcd and the dvi connector running to a 19" LCD. It was a lot of trial and error mainly because I was going through several different versions of the driver and several different methods of installing/configuring. 

What really helped me out was Alberto's **[Envy](http://albertomilone.com/nvidia_scripts1.html)** which automates a lot of the steps. Give that a try.

But basically I am running the latest 8.2 catalyst drivers off of AMD's site. Doing 

aticonfig --initial=dual-head 

generated the basic xorg.conf file that I then tweaked a bit. If you post where exactly you are having trouble with things, maybe I can be a bit more specific. But if you are having trouble just getting the ati driver to work right, give Envy a try even though I am not 100% sure that's what did it for me (it was the last thing I remember that made things work suddenly ... especially with OpenGL). 

If you run fglrxinfo, you should see ATI technologies Inc listed there for both screens and not Mesa or anything else.  The OpenGL version string on mine is 2.1.7676 for now.


Edit: Forgot to say I also did:

sudo /usr/sbin/update-rc.d -f atieventsd remove 

and also renamed the file /etc/ati/authatieventsd.sh to something else since this atieventsd daemon seemed to lock things up when I was trying to restart x or reboot. I don't think I need anything it does but not sure if it is needed or not. I seem to be much happier without it. :)

---

### Post by miesnerd on 2008-02-26
I'll give envy a try when I get home. I had thought (I guess, erroneously) that it was only for nvidia, and not ATI.

Would you mind posting your xorg.conf just in case?
Oh, and I assume you have two different desktops setup? Resolutions? Man, im pumped and I want details.

---

### Post by philinux on 2008-02-26
I'm about to buy a pc with this board. Does the 7.1 live cd boot successfully? 64 or 32 bit.

---

### Post by miesnerd on 2008-02-26
my advice would be to go to asus's website and get your bios updated before you do anything. My board booted just fine with both cd's but when i went back to add ram (started with 1 GB, updated to 5 GB) I had probs at first simply because my version of the bios was 1404 not 1604.

---

### Post by miesnerd on 2008-02-26
> **seapahn said:**
> Yes onboard with the hdmi connector running to my 42" lcd and the dvi connector running to a 19" LCD. It was a lot of trial and error mainly because I was going through several different versions of the driver and several different methods of installing/configuring. 

What really helped me out was Alberto's **[Envy](http://albertomilone.com/nvidia_scripts1.html)** which automates a lot of the steps. Give that a try.

But basically I am running the latest 8.2 catalyst drivers off of AMD's site. Doing 

aticonfig --initial=dual-head 

generated the basic xorg.conf file that I then tweaked a bit. If you post where exactly you are having trouble with things, maybe I can be a bit more specific. But if you are having trouble just getting the ati driver to work right, give Envy a try even though I am not 100% sure that's what did it for me (it was the last thing I remember that made things work suddenly ... especially with OpenGL). 

If you run fglrxinfo, you should see ATI technologies Inc listed there for both screens and not Mesa or anything else.  The OpenGL version string on mine is 2.1.7676 for now.


Edit: Forgot to say I also did:

sudo /usr/sbin/update-rc.d -f atieventsd remove 

and also renamed the file /etc/ati/authatieventsd.sh to something else since this atieventsd daemon seemed to lock things up when I was trying to restart x or reboot. I don't think I need anything it does but not sure if it is needed or not. I seem to be much happier without it. :)

I'll check it when I get home, but if my recollection serves me correctly, it wont even use both monitors at the same time. Now this isnt 100% true, when i was playing around with xinerama and the like, at one point I had it set up where it was dual monitors, but they were showing me the same display, not 2 separate desktops or even 1 big desktop.

---

### Post by miesnerd on 2008-02-26
ok i happened to be able to come home for lunch. I downloded envy, auto install ati driver
ran fglrxinfo and got:

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!


ran aticonfig --initial=dual-head 
and got:

Found fglrx primary device section
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

but, both my monitors are giving me the same display. But what I want is that they give me two different displays...oh yeah, and its in crappy graphics safe mode.

---

### Post by seapahn on 2008-02-26
Here's my current xorg.conf file. I took out the comments and the "InputDevice" sections. This is with the latest asus bios (1016 if memory serves me right) and the primary display set to the onboard one in the bios (don't remember exact wording but it's something like pci-e, onboard, hdmi or something). Not sure if that makes a difference. The two displays are running as separate X's. The 19" LCD is 1920x1280 and the HDMI connected to the TV is at 720p resolution (1280x720 I think).  Hope this helps.  PS: The Video Overlay and XVideo stuff seems irrelevant and as you can see i've been trying everything but that's my setup right now as it is so I left them there. :)

```
Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
  screen "aticonfig-Screen[1]" leftof "aticonfig-Screen[0]"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Extensions"
	Option		"XVideo"	"enable"
	Option		"Composite"	"Enable"
EndSection

Section "Module"
	Load		"dri"
	Load		"glx"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[1]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[1]"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
	Screen	1
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[1]"
	Device		"aticonfig-Device[1]"
	Monitor		"aticonfig-Monitor[1]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by seapahn on 2008-02-26
> **philinux said:**
> I'm about to buy a pc with this board. Does the 7.1 live cd boot successfully? 64 or 32 bit.

One thing that I remember having to do is to set "Plug and Play OS" to "yes" in the bios. Without it, the kubuntu installation would freeze at some point. Good advice about the latest version too ... don't do anything before updating bios!  But after that, the 7.1 (64 bit)  install went fairly smooth though getting everything to work right will take a while (accelerated video, correct sound, etc).

---

### Post by seapahn on 2008-02-26
> **miesnerd said:**
> Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!


As far as glx, llibgl1-mesa-glx is installed on mine but not sure if that makes a difference.

Here are some snippets from my Xorg.0.log:
```
...
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
...
*a BUNCH of lines of type:*
(WW) AIGLX: 3D driver claims to not support visual 0xd4
...
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
...
*a BUNCH of lines of type:*
(WW) AIGLX: 3D driver claims to not support visual 0x86
(II) GLX: Initialized DRI GL provider for screen 1
...

```

> **miesnerd said:**
> aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

Did you do **sudo** aticonfig ...?

---

### Post by miesnerd on 2008-02-26
SEAPHAN-
thank you SOOO MUCH. Now all I have to do is get my resolutions working, but for the first time I acutally have decent resolution working (not 800x600 safe mode on both screens-- what an eyesore).

Now I have to ask, what all can I do with compiz on this setup?
I have ordered that second card. Unless Im adding 2 more monitors (and Im not) is there anything I can do with that card, or should I just return it?

---

### Post by miesnerd on 2008-02-26
as an update, I stil am having probs with the resolution. In fact, graphical tool seems to be worthless at this point. I attempted to add resolution options to xorg.conf, but now im wondering, can I force one monitor to display at 1440x900 and the other at 1290x1024? If so, please show me where to add the line or option to achieve this. Thanks.

---

### Post by seapahn on 2008-03-10
Still having resolution problems?

I just checked in to say I finally got the frickin thing to work with XV video overlay! The **latest 8.3 Catalyst driver** added the feature for the x1250 that's on this motherboard. Of course I spent another 2-3 hours trying to figure out how the hell to make the HDMI have video overlay and the DVI be secondary ...

The answer for me was adding:

        **Option      "SwapScreens" "on"**

 to the first Section "Device" in the xorg.conf file.  **This made my HDMI output be "primary" (with xv)** while the DVI that's connected to a 19" LCD be secondary (and thus have no xv support).  Sheeeesh why are things so complicated to figure out at times! But once you do figure out, it seems so easy :lolflag:  Now why only the primary device gets xv and not the secondary, it's beyond me (it's a known issue by ati)

... but strangely enough, the fps reported by glxgears is about 1000 on my primary screen and only 600 fps on my secondary screen no matter which actual device is doing the displaying of primary/secondary (keepin same resolution of 1280x720 on HDMI and 1280x1024 on DVI). This was this way even before xv but I hadn't bothered to "swap" the screens and had just figured that HDMI is inherently slow ... but I was wrong in my assumption. It's somehow driver related.

As far as resolution, I just change mine from the KDE settings ... either there or the amdcccle that gets installed as part of the fglrx drivers from ati.

---

### Post by gergej77 on 2008-03-12
1603 bios works fine, I have no DVI problems.

---

### Post by aznel on 2008-04-24
I have been pulling my hair out trying to get HDMI output working with a ASUS M2A-VM HDMI.  HDMI works while linux is booting until the X login screen appears.  After that I cannot even get HDMI output from a text console.

HDMI output does not work even in single monitor mode.  Running "aticonfig --query-monitor" shows that tmds2 is connected, but after I run "aticonfig --enable-monitor tmds2" I get nothing on the HDMI output.  Everything works perfectly when I use the DVI or VGA outputs.  I am using latest ASUS BIOS (1705), and the latest proprietary ATI drivers (8.4).

Strangely, if I boot into Ubuntu using the install CD I get output on the HDMI port.  So, I know this is possible.  I have attempted to use the xorg.conf posted by seaphan to no avail.  What am I doing wrong!?  Please show me your working configuration!

---

### Post by seapahn on 2008-04-28
My configs are posted in this thread. I am running dual-head with HDMI as primary going to my 42" tv and DVI going to a 19" LCD. HDMI audio simply does not work yet with anything that I have tried. So try to get the video working before even considering trying to solve the HDMI audio problem.

Make sure you have the latest bios and install the latest ATI drivers (uninstall any old versions first). FYI, I have not tried the latest ATI drivers yet. Mine are the ones that they released in March (8.3 catalyst).

---

### Post by Esey on 2008-05-01
I've resolved my problems with HDMI audio launching alsamixer
and the unmuting eic958 device (selecting it and then pressing "m").
Of course, then you have tu select ATI HDMI alsa device in your application.

For hdmi video, I've the same problem as aznel.
If I use Catalyst 8.39 then I have hdmi output (clone of dvi screen), and hdmi audio.

With the latests drivers, during startup hdmi works, but when the X driver is loaded it became blank "forever". I've tried the configuration suggested by seapahn, but it still doesn't work. aticonfig and amdcce say that there're two screens, in clone mode, and I have also xvideo extensions, but hdmi video is blank. In bios, I've tried to select both OnboardVGA end PCI-e as primary device, but the only thing that chang is the order of HDMI and DVI output in amdccce or aticonfig.

---

### Post by didiertxo on 2008-05-04
Hello to all, and sorry for my poor english.

I've got the same mobo.

With ubuntu gutsy (7.10) I achieve dual-head vga and hdmi with ATI drivers. HDMI audio also.

I've installed hardy (8.04) and, for now, the only way to run HDMI output is the vesa drivers on the fresh install. When you install proprietary drivers through ubuntu hardware drivers, or install directly latest ati drivers, or through Envy, you lost the hdmi output. aticonfig --query-monitor recognizes that tmds2 is connected, but i get nothing after enabling it.

I didn't get hdmi audio.

Anyone has Hardy Heron running correctly through HDMI output? Is there any way to do it?

Thanks in advance.

---

### Post by Esey on 2008-05-04
I've noticed the same problem with ubuntu 8.04.

Envy or the restricted drivers manager of 8.04
install an ati proprietary driver newer than 8.39
(the one installed in 7.10).

The good thing is that the newer driver supports
xv acceleration and so on, but it seem that
HDMI output cannot work.

Esey

p.s. I've noticed that something if I return
to driver 8.39 I've have to shutdown the system.
Reboot is not sufficient. It seems that hardware
remains in an inconsistent state that is not 
resetted by a reboot.

---

### Post by GSMD on 2008-07-12
Guys, has anyone managed to make the damned thing (hdmi + sound) work with the stock driver that comes with Hardy (it's 8.3 basically)?
Here's my xorg.conf:
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
#        Driver          "fglrx"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        VertRefresh     60.0 - 60.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1920x1080"
        EndSubSection

EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection
```
And with fglrx driver section connected out I get the image on tv (mythtv is extremely slow though). With fxlrx driver enabled it's exactly the same as you've described: black screen and nothing else.

Has anyone had any luck with 8.6?

---

