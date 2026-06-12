---
title: "GEForce FX 5200, Dell GX60, No dice"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by p0st_n00bz on 2007-11-19
Hi everyone,
Long time reader, first time poster. Like a bunch of other people, I am having trouble with Ubuntu and NVIDIA. I have an Optiplex GX60 with 7.10 on it. It boots fine if the GEForce card is not installed and I use the built in video out (which I do not want to use in the long run). I have read a million post about similar problems, but can't find a solution that works for me. I tried installing the drivers from the command prompt. Didn't work. I installed them with Envy, didn't work. 

What happens is that I will put the card in, and boot the machine. It works briefly, until I get an Ubuntu splash screen with a progress bar at the bottom. It goes less than 1/4 of the way across, and that's it. If I take the card out, it boots fine.

Some people suggested booting off the CD, but I have the exact same problem there. I cannot get it past this splash screen. 

FWIW, I had this problem on earlier versions as well. I appreciate any thoughts/suggestions you might have.

---

### Post by stido on 2007-11-19
try editing/modifying your xorg.conf using this settings and see if it works:

```
Section "Device"
	Identifier	"nVidia Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"	"256x192"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
EndSection
Section "Module"
	Load		"glx"
EndSection
```

---

### Post by p0st_n00bz on 2007-11-19
thanks, stido. I assume I'll have to remove the card to do that, since I can't boot with it in. I give a shot and see what happens.

---

### Post by stido on 2007-11-19
don't forget to put the 5200FX back in after editing :D

good luck!

---

### Post by p0st_n00bz on 2007-11-19
ok, so I tried that, and I still get the same splash screen with the progress bar that stops in the same spot.

However, I am willing to admit I may have not done it right.

I booted from the live CD, and opened the terminal, typed "sudo nano /etc/X11/xorg.conf" and edited the file that came up, saved it, shut down, plugged in the card, rebooted, and here I am.

Did I do it wrong, or could it be something else?

---

### Post by dpar on 2007-11-19
Can you boot in verbose mode and see what is failing to boot?

---

### Post by stido on 2007-11-19
hmmm.... the problem might not be directly related to 5200FX then...

i agree:
> **dpar said:**
> Can you boot in verbose mode and see what is failing to boot?

---

### Post by p0st_n00bz on 2007-11-19
I tried to boot from the CD while the card was in, and hit ctrl+alt+f1. I'm not entirely sure what's going wrong, but "error_code+0x72/0x80" appears a few times, among other things.

---

### Post by Orbital75 on 2007-11-19
Very strange, I have that same card and it works just fine.....

---

### Post by fenian on 2007-11-19
I think you may need to disable the onboard video from the bios.

---

### Post by p0st_n00bz on 2007-11-19
I went into the bios, but there doesn't seem to be the option to disable the onboard video. I can disable the PCI cards, but nothing onboard. I changed the IRQ number of the nvidia card (which also changed the onboard card's number, they seem inextricably linked) and when I booted, the same hang happened, but that error was gone. The last line is still ======================== though.

Oh well, tomorrow is another day. Thanks for all the help so far.

---

### Post by p0st_n00bz on 2007-11-20
just out of curiosity, would I be better off switching to a card with an ATI chipset instead of NVIDIA?

---

### Post by p0st_n00bz on 2007-11-20
ok, so I tried adding the onboard graphics to the blacklist as explained [here]("http://ubuntuforums.org/showthread.php?t=434865&highlight=fx5200&page=2") and still no luck.

I may nuke the beast and start over, which will be a bummer because I got MythTV working finally and now this.

---

### Post by stido on 2007-11-21
no, adding it to the blacklist probably won't help either. best is still to disable it in BIOS. which BIOS manufacturer is yours? or what's the mainboard type? 
there has to be a way to disable the onboard video. ](*,)

---

### Post by p0st_n00bz on 2007-11-21
Hmm, well the BIOS version is A02, and going to the Dell website, I can download version A09, so mine must be woefully out of date. So maybe if I update that it will give me the option to disable the onboard graphics.

Looking up the specs with my tag at Dell gives me this info:
PLANAR (MOTHERBOARD)..., GX60, 845GL

Not sure if that is useful. I need a floppy to update the BIOS, so it will have to wait until I can snag one from work (mostly Macs at home).

Happy Thanksgiving!

---

### Post by fenian on 2007-11-24
With the later bios you can disable the onboard graphics.

---

### Post by p0st_n00bz on 2007-11-24
Good to know. I'll give this a whirl Monday after work and report back.

---

### Post by p0st_n00bz on 2007-11-26
ok, so I updated the BIOS, but I still don't see a way to disable the onboard video. I get options for "auto" or "onboard" and it's on auto, and I get the same problem. 

Any ideas? Am I missing something in the BIOS?

---

### Post by p0st_n00bz on 2007-11-26
UPDATE

I uninstalled and reinstalled the driver using Envy. It still did the same hang as usual. I took the card out, and booted trying to use the on board graphic card, and I get a black screen. I was able to connect via VNC from another computer, and looking at the xorg.conf file, it was configured for "failsafe device." That sounded serious, so I didn't change any of those settings. Could this be because I installed the driver and told it to configure automatically while the card was not installed?

---

### Post by fenian on 2007-11-28
At the black screen you get when x fails to load you should be able to log in with your username and password,you still won't have a gui,but you can reset xorg to default setting with the commnd....

> sudo dpkg-reconfigure -phigh xserver-xorg

then run the command...

> sudo reboot

to reboot.
As for the bios settings I think you nedd to choose onboard rather than auto.

---

### Post by p0st_n00bz on 2007-11-29
if I choose Onboard, it only lets me use the built-in video. If I choose auto, it boots to the Geforce card, but it still hangs. I've gotten so I can boot to the built in card, and make sure the nvidia driver is active, but I still get the problem. If I open the nvidia control panel, it tells me I need to reconfigure the nvidia x-windows. If I shut off gdm, I can't read the screen at that point. If I boot in  recovery mode (to the onboard card, obviously, it hangs on the other still, even in recovery) and run the command they tell me to, it still doesn't work.

---

### Post by embart on 2008-04-11
hello mate!
have you managed to make GX60 + nVidia working together?

I have same problem but with GF MX 4000 64MB, onboard video works like a charm ;) but not with nVidia card.

I have updated the bios to A09, but it did not solved anything.

I have tried Ububtu, but also a couple of Mandriva versions and it always hangs up.

in Ubuntu system hangs on "Hot Plug subsystems" - if that helps to disover the solution.
I have also tried to disable the USB controler in BIOS as it has same IRQ as VGA cards, but did not help at all.

The only one that worked was Dam*ed Small Linux (DSL) but I would prefer to have anything more on that PC....

---

### Post by d3adp00l on 2008-04-11
different computer, different card, but same problem.

I have the bios option to boot from onboard or pci, if I choose onboard, everything works fine, if I choose pci, it boots fine, but when UB loads the screen goes black, and I have to plug into the onboard to get a picture, if I do UB works fine, but how do I tell it not to use the onboard and to use the pci card instead?

I looked at the video screen settings in settings and it shows that both drivers are loaded, but it doesn't give a choice on which to use as default. And honestly its getting to the point where its almost not worth it. Is there a GUI to tell the OS which to use, or is it gonna be a bunch of command prompt stuff?

Funny thing is xp has the reverse issue, if I boot with the onboard, when it loads the screen goes black, and I have to switch the vga cable to the pci card to get a picture, and xp doesn't show any driver for the onboard at all. 

Oh what fun...

---

### Post by p0st_n00bz on 2008-04-15
I haven't actually gotten this working, but this project has been put more or less on hold for a little while.

---

