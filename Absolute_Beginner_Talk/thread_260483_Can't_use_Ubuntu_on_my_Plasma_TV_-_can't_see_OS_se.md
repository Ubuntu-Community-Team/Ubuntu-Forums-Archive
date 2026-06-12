---
title: "Can't use Ubuntu on my Plasma TV - can't see OS selection commands"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by gnielsenjp on 2006-09-18
Hi everyone,
I'm a newbie at Linux, but actively trying to learn. This weekend I installed Ubuntu on my PC connected to my plasma TV. I'm using a ATI Radeon 9600 card with the ATI DVI to component video adapter. Previously for Windows only boot I had no problems. But since I installed Ubuntu, during boot I can not see the OS selection screen - so Ubuntu boots by default and I can't see anything on my display. If I press the down arrow a few times and then enter after powering on the system I can select Windows - even though I can't actually see the prompt display.

Any suggestions?

Is there anyway to make Windows the default booting OS instead of Ubuntu?

I'm considering to uninstall Ubuntu on this PC and just run it on my desktop. Unfortunately I have no clue on how to remove Ubuntu.

Any feedback is appreciated!

Greg

---

### Post by GoneWithTheWind on 2006-09-18
I've not used Ubuntu yet so this reply is coming totally from interest and ignorance.  However have you tried changing the background desktop display?  I think there are some other choices besides just the basic one.

Okay, back to first installation.  #-o :-\"

---

### Post by MetalMusicAddict on 2006-09-18
> **gnielsenjp said:**
> Hi everyone,
I'm a newbie at Linux, but actively trying to learn. This weekend I installed Ubuntu on my PC connected to my plasma TV. I'm using a ATI Radeon 9600 card with the **ATI DVI to component video adapter**. Previously for Windows only boot I had no problems. But since I installed Ubuntu, during boot I can not see the OS selection screen - so Ubuntu boots by default and I can't see anything on my display. If I press the down arrow a few times and then enter after powering on the system I can select Windows - even though I can't actually see the prompt display.

Any suggestions?

Is there anyway to make Windows the default booting OS instead of Ubuntu?

I'm considering to uninstall Ubuntu on this PC and just run it on my desktop. Unfortunately I have no clue on how to remove Ubuntu.

Any feedback is appreciated!

Greg
I actually think its the DVI video adapter doing it. What inputs do you have on your Plasma? I have RBG and DVI on mine. Do you have a HDMI input?

---

### Post by gnielsenjp on 2006-09-18
My plasma display is pretty old, no DVI or RGB inputs. Only hi-def input it has is component video.
Do you recommend a get a new video card? Any suggestions on ones that will definately work with component video?

Greg

---

### Post by Magnes on 2006-09-19
Well, then you should get used to it or try to change grub to graphical one (don't remember how to do it though) or change to lilo. To change the default starting system in grub edit the /boot/grub/menu.lst - there is a "default" position with number. Windows will probably be 3 or 2 or sth like that (you could set it to for example 10 or higher - then it will select the last position in the menu - the windows I asume).

---

### Post by MetalMusicAddict on 2006-09-19
> **gnielsenjp said:**
> My plasma display is pretty old, no DVI or RGB inputs. Only hi-def input it has is component video.
**Do you recommend a get a new video card?** Any suggestions on ones that will definately work with component video?

Greg
I just bought a nVidia 7900 GT. It has Component Video out. This card is pricey though and PCI-E.

But if your really into the HTPC thing I would just wait till you get a new plasma.

Usually everyone goes through, "Yea, Its big but I could go bigger" :) Im upgrading from my 43" to a 55" in Febuary.

What is your res set to in windows? I run 1280x720. Does it look fine? Is it just at boot? Does you BIOS info come up correct? Is it just GRUB that isnt displayed correctly/at all?

---

