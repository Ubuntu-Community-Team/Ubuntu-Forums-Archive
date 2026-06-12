---
title: "Initial Frustrations."
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by Bus_Driver on 2007-01-23
So - 

I admit - I know pretty much ZERO about Linux.  But I am pretty windows savvy - and tend to be the tech guy for most of my friends.

I have a desire to learn more about linux and the overal model is a strong appeal to me.

I had some initial install problems - I d/led the beta install program on a whim - and it didnt wor for me - no biggie - I erased, and installed from a LIVE CD.  The partitioning was a bit strange, but I got passed it - and now I have a dual boot w/ ubuntu and XP.

I have a few minor problems - and I am hoping that you guys can help me - keep in mind I am a COMPLETE newbie.

and thank you all in advance for any help you can provide.

1 - The BOOT ORDER of my computer - I'd like XP to be #1 - and be the one that loads if I don't hit anything right away - is this possible to switch?

2 - for some reason 8 out of 10 times when I load into Ubuntu - it only shows the 800x600 or 600x480 options.  The 1024 or higher resolutions arent even options.  Sometimes it works - but others it doesn't.  I haven't been able to decipher why it's happening or how to change it.  I'd like 1024 to just be the default resolution - (or at least be an option).

3- wireless internet - I have a supposedly strongly compatible wireless card. (the LInksys Wireless G PCI adapter - the model # escapes me at the moment.. but I d/led the drivers - unzipped them - and put them on my USB thumb drive since it seems to be the only common link from my windows to linux at the point (i havent' mounted the drives yet - i think that's what it's called)  but I cant seem to get it working.  Someone told me to run the terminal program and type run ndiswrapper -i thedriver.inf  but it's not doing anything - do I have to d/l the ndiswrapper program ?  cuz it says it's not found.

once all these probs are done - then I want to mount the HDs.. and then actually start playing w/ Linux more closely - but until these 3 problems are recitified - I feel as if I am in a holding pattern.

I TRULY appreciate any help you can provide me.

---

### Post by mikewhatever on 2007-01-23
To make windows boot first, you need to customize the GRUB menu. This page tells you howto [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by K.Mandla on 2007-01-23
1 - Yes, you'll need to edit the /boot/grub/menu.lst file, and set the *default* option to the number of the entry for your windows partition. Remember that the first option is numbered 0, and they increase after that. So I think, in general, Windows is listed as option 3. But don't hold me to that.

Similarly, there is a timeout setting that you can modify. I was under the impression that dual boots defaulted to a 30-second timeout, but it has been a while since I built one. Either way, you can adjust that setting as you see fit.

2 - It's possible there's an inconsistency between your driver and your video card, but more likely than that, you can fix your resolution issues with this command:

```
sudo dpkg-reconfigure xserver-xorg
```
That will spawn a series of options, one of which is resolution settings. If it still doesn't work after that, you can manually edit your xorg.conf file to include the setting you want.

And if it still doesn't work after *that*, you're in that deep, dark no-man's land where you have to calculate the refresh rates for your monitor and enter them manually into the xorg.conf file.

But don't worry. I've never had to do that, and for what I've seen, it's *very* rare.

3 - Can you tell us which model and version it is, specifically? is it a WMP54G version 3 or something like that? Different wireless cards have different chipsets, and regardless of the maker or the model, it's the chipset that you're really after.

P.S.: Welcome! :D

---

### Post by Bus_Driver on 2007-01-23
hey - 

OK - I will attempt those fixes.. I am gonna read thru that huge grub page.. but is it a simple task if I want to move my XP to #0 - or should I just change the default to the windows and leave it be?

I do believe I have the WMP54G card - no idea what version of it I have - or how to find that out.

edit - 

I just read a snippit of the grub on the way to move windows to #1.. simple enough (#0 I guess to be exact) :)

---

### Post by j19sch on 2007-01-24
> **K.Mandla said:**
> 2- <snipped> And if it still doesn't work after *that*, you're in that deep, dark no-man's land where you have to calculate the refresh rates for your monitor and enter them manually into the xorg.conf file.
Check the manual of your monitor first, that's where I found the settings for my monitor. (Or search on the manufacturer's site.)
BTW, I didn't enter the settings because I had to fix something. I just like to have the correct settings in xorg.conf. And it was easy, since a few years back I actually did need to set the rates manually while using Debian.

---

