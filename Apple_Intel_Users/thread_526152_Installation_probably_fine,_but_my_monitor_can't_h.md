---
title: "Installation probably fine, but my monitor can't handle the resolution/frequency"
date: 2007-08-15
forum: Apple Intel Users
---

### Post by Dingbats on 2007-08-15
I have followed _[this]("http://ubuntuforums.org/showthread.php?t=339998")_ guide to install Ubuntu on my Mac Pro. I installed it with the alternate 64-bit 7.04 CD, with the text installer. It seems to have installed fine, and I didn't even have to do any of the workarounds the guide talks about, because Grub just installed without problems!

But there's a little problem. When I choose Ubuntu in the Refit menu, Grub boots it up and the loading bar shows up, but after it's done loading, the screen goes black and complains that it can't handle either the resolution or the frequency (which it is isn't clear). The monitor I normally use is a Philips 19" widescreen LCD monitor with a native resolution of 1440x900 and can handle 60 and 75 Hz. I have also tried it with another similar monitor and an older CRT monitor, but none of them could handle it either.

So, probably the installation is fine, but I can't use the new system because my monitor won't show it.

During the installation there was one part where you could tick a number of boxes to choose which resolutions would be handled (as I interpreted it), and I'm not completely sure I managed to tick the 1440x900 box. I selected it and pressed return, but I'm not sure it was ticked.

So I see two options here:

a) Reinstall Ubuntu and make sure I actually tick that box, or
b) Boot into Ubuntu and change the settings from there without seeing what I'm doing.

The first option feels a bit risky, because what if I'm not that lucky this time and Grub fails to install like it "should"? And the second option would need someone to tell me exactly what keystrokes to press to change the settings, and I'm not even sure it's possible.

What else can I do? :?

---

### Post by cyberdork33 on 2007-08-15
you should be able to get to a terminal after X fails to start... that is unless you are just completely losing everything...

Try hitting CTRL+ALT+Fx where x = 1 to 6

---

### Post by Dingbats on 2007-08-15
So you mean Ctrl-Alt-1...6 or Ctrl-Alt-F and then 1 to 6, or what? :?

Anyway, what should I do when in the terminal?

---

### Post by pxwpxw on 2007-08-15
that is F1=functionkey1 ....

When at the command line
```

 lspci

```
will list your video card
Then 
```

 sudo dpkg-reconfigure -phigh xserver-xorg
#### or if that does not give enough options
 sudo dpkg-reconfigure xserver-xorg
## and to try it
 startx

```
Will give you another try at setting the driver for your video card and the resolution, but you could try 1024x768 to start.

```

 sudo reboot

```
To reboot from command line.

---

### Post by Dingbats on 2007-08-15
> **pxwpxw said:**
> that is F1=functionkey1 ....
:roll: Of course.

I will try your suggestions, back in a while!

---

### Post by Dingbats on 2007-08-15
Ok, so I tried this but uhm... anyway, lspci listed this:

```
$ lspci
00:00.0 Host bridge: Intel Corporation 5000X Chipset Memory Controller Hub (rev 30)
00:02.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x8 Port 2-3 (rev 30)
00:03.0 Non-VGA unclassified device: Intel Corporation 5000 Series Chipset PCI Express x4 Port 3 (rev 30)
00:04.0 PCI bridge: Intel Corporation 5000X Chipset PCI Express x16 Port 4-7 (rev 30)
```

I'm not sure how to interpret that.

Then I tried sudo dpkg-reconfigure -phigh xserver-xorg, and it showed me that menu again where I could tick boxes for resolutions, and I ticked 1440x900 with the spacebar and pressed OK. Then I waited for like five minutes without anything happening. So I switched to another shell and back again and then there was a warning that I might overwrite a possibly customized something and I don't think anything had happened.

Then I tried the command without the -phigh option(s?) and it prompted me to choose which driver I wanted and other stuff I wasn't sure of, so I switched to another shell and rebooted, and here I am.

So... I guess sudo dpkg-reconfigure -phigh xserver-xorg didn't work properly and I'm not quite sure how to go on? :?

From OS X's system information I get this (translated from Swedish where necessary):

> NVIDIA GeForce 7300 GT:

  Styrkretsmodell (don't know the English word, lit. "governing cicuit model"):	NVIDIA GeForce 7300 GT
  Type:	Monitor
  Bus:	PCIe
  Card place:	Slot-1
  VRAM (totally):	256 MB
  Manifacturer:	NVIDIA (0x10de)
  Unit ID:	0x0393
  Revision ID:	0x00a1
  ROM revision:	3011
  Monitors:
Monitor:
  Status:	No monitor connected
Philips 190CW:
  Resolution:	1440 x 900 @ 75 Hz
  Depth:	32 bit color
  Core Image:	Supported
  Main monitor:	Yes
  Mirror:	Off
  Connected:	Yes
  Quartz Extreme:	Supported
  Rotation:	Supported

---

### Post by cyberdork33 on 2007-08-15
ok well that is a bit helpful. Using nVidia card.

can you checkout your xorg.conf file?

to edit/view it you can use:
```
 sudo nano /etc/X11/xorg.conf
```In the device section for your video card, check what driver it is trying to use. The default should be 'nv'. If that is what it says, then you can try changing it to 'vesa' (a generic driver) to get X started. If that works, then I would venture to guess that you need to get the propietary nVidia driver to get everything working properly.

Also, it is odd that youe lspci is not listing your video card. Was that ALL of the output?

---

### Post by Dingbats on 2007-08-15
> **cyberdork33 said:**
> ok well that is a bit helpful. Using nVidia card.

can you checkout your xorg.conf file?

to edit/view it you can use:
```
 sudo nano /etc/X11/xorg.conf
```In the device section for your video card, check what driver it is trying to use. The default should be 'nv'. If that is what it says, then you can try changing it to 'vesa' (a generic driver) to get X started. If that works, then I would venture to guess that you need to get the propietary nVidia driver to get everything working properly.
In that case, where can I get hold of that driver?

Anyway, is it necessary the case that X doesn't start? All I know is that my monitor can't show whatever is sent to it after the boot up, but does that necessarily mean X isn't running?

> Also, it is odd that youe lspci is not listing your video card. Was that ALL of the output?
Absolutely everything. At least everything I saw, but everything was a bit messy, so there's a slight chance that it was cut off or something.

---

### Post by cyberdork33 on 2007-08-15
> **Dingbats said:**
> In that case, where can I get hold of that driver?

Anyway, is it necessary the case that X doesn't start? All I know is that my monitor can't show whatever is sent to it after the boot up, but does that necessarily mean X isn't running?

I guess not... I thought it was crashing. Ok let's try this.

```
sudo apt-get install linux-restricted-modules-generic
```Then change the driver in your xorg.conf to 'nvidia'. 

Otherwise, you can try the vesa driver, and when the desktop comes up use the normal method to install the nvidia driver (restricted driver manager)

If that doesn't work we can try the newer driver from the nvidia website.

---

### Post by Dingbats on 2007-08-15
Progress! I'm now writing this from Ubuntu! :D

I changed "nv" to "vesa" in xorg.conf. I tried startx in the shell afterwards but it gave an error message saying it was already active. So I rebooted and it worked!

But I can't get the resolution over 1024x768, and the frequency is stuck at 61 Hz, while my monitor prefers 75. How do I fix that (I've heard people talk about something called 915resolution, is that it?)?

Anyway, I feel relieved! Not a long way left now! :)

EDIT: You beat me, but I'm not sure your post is relevant now?

---

### Post by cyberdork33 on 2007-08-15
> **Dingbats said:**
> I'm not sure your post is relevant now?

yes it is, vesa is not going to give you 3d performance or anything that you will want. vesa was just to get X to actually start.

---

### Post by Dingbats on 2007-08-15
WOOOHOOO!!!! :D :D I installed the drivers with the restricted drivers manager, and rebooted, and IT WORKS! :D

Thank you very very much! Now there's probably gonna be hundreds of other problems to deal with but now I can at least see what I'm doing! :)

:D

---

### Post by cyberdork33 on 2007-08-15
> **Dingbats said:**
> WOOOHOOO!!!! :D :D I installed the drivers with the restricted drivers manager, and rebooted, and IT WORKS! :D

Thank you very very much! Now there's probably gonna be hundreds of other problems to deal with but now I can at least see what I'm doing! :)

:D

Hopefully, that is the most of your worries. If you could please modify your original post and add [Solved] to the subject line. Thanks.

---

