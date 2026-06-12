---
title: "ASUS G74S - juuust a few issues..."
date: 2011-09-29
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ubersoft on 2011-09-29
On Tuesday I got a sweet new toy.

It's an ASUS G74S. It is a flat-out amazing laptop -- it beats any desktop computer I've ever used in my lifetime. Easily. That said, I'm having a few issues with it Linux-side and I'm fishing for advice, because while the symptoms appear to be similar to some of the past topics on this forum, none of the suggested fixes work.

I am running Kubuntu on it -- currently Oneric Beta 2. For the most part it works great -- it automatically detected my sound card (with only one issue that I'll get to in a minute), it automatically detected my wireless card, it installed the proprietary linux drivers without any issues at all whatsoever... it is a fully-functioning laptop.

However, there are four things it won't do that are sort of confounding. I'll list them here:

>- First problem -<

The laptop has backlit keyboards, which can be turned on or off via the Function + F3 and Function + F4 key combinations. This works on my Windows 7 partition, and does not work at all in Kubuntu Oneric. The backlight is turned off and won't come on for anything.

A year ago there was this:

[http://ubuntuforums.org/showthread.php?t=1461454&highlight=ASUS+G51JX](http://ubuntuforums.org/showthread.php?t=1461454&highlight=ASUS+G51JX)

These fixes seemed to help some, but they haven't worked for me. I think I know why, which I'll get to in a minute.

>- Second problem -<

The touchpad is fully functional in Kubuntu, but whenever I log in I get a message saying that it can't be detected. Further, the Function + F9 key combination, which is supposed to turn the touchpad off... won't. I don't really like touchpads so I just turned it off in BIOS, but I still get the message when I log in that the touchpad can't be found.

>- Third problem -<

The third problem is basically what I think is causing the first and second problem. While troubleshooting why the Function keys weren't working, I used the acpi_listen command to try to capture what each key was sending... they weren't sending anything. At all. *none* of the keys were, that I could tell, except maybe Function + F1 (sleep mode). And yet there are Function keys that work -- I can use the Function keys to turn wireles on and off, to muck about with screen brightness (at least, the function keys get the KDE brightness bar to display, though moving that bar up and down doesn't actually seem to make the display brighter or dimmer), and control the volume on the laptop (louder, softer, mute). So the function keys, at least some of them, do work... but they don't seem to work using acpi, because acpi_listen captures nothing at all.

This is despite the fact that I have acpi_osi="Linux" in my grub2 configuration, and I have an ASUS Laptop keyboard layout selected in System Settings.

>- Fourth problem -<

The sound card works great, even with PulseAudio. What I'm especially excited about is that Kubuntu recognizes when I've plugged in headphones and automatically mutes the speakers -- this is something my old laptop never did. Unfortunately, the sound that comes out of the headphones is too low to hear. I can hear a faint echo of noise coming out of them, but I have no way of making them any louder.

So... all of these problems have been reported in the past, on this very forum, but as I read through their histories they all skewed differently. The fixes for my first and second problem focus on getting a misconfigured acpi setup to work properly, but as per the third problem it doesn't seem like my laptop is actually using acpi at all, so those fixes seem useless for this laptop. And finally, all the posts I saw trying to fix headphone volume problems were dated 2007-2009 and none of them were actually resolved in any significant manner -- so there's not a lot to work form there.

Any of you have any thoughts or advice? As it is I can live with these problems, but obviously I'd love to be able to get the kinks ironed out. Especially the backlit keyboard part!

I have read that the G73SW laptop uses WMI not ACPI, and it may be that the G74S does the same. In which case I may be out of luck. But here's hoping!

---

### Post by ubersoft on 2011-10-01
Would it be bad form to post a similar thing in the general laptop support forum? I don't want to spam the forums, but I want to increase the number of potential responses, too.

---

### Post by mörgæs on 2011-10-02
When you get it all to work, it would be great if you could add a brief guide here:

[http://ubuntuforums.org/showthread.php?t=1543006](http://ubuntuforums.org/showthread.php?t=1543006)

---

### Post by ubersoft on 2011-10-02
I'd be happy to, but I can't find any information on any of this, so I don't know if I'll ever figure it out. :)

---

### Post by Greeblesnort on 2011-10-04
That's odd. I just finished setting up 10.04 (tried 11.04, didn't care for it) on my shiny new G74S and am not seeing those issues. 

I'm currently working my way thru the system tests. I will chime back in when that's done. I've rather gotten away from system support, but I might be able to help some.

Edit:
so, I'm still setting everything up the way I want, but I've not run across any function that plain doesn't work except for some of the Fn keys (specifically, turning off the touchpad). install touchpad-indicator fixed that. 

Are you using the desktop-x86_64 install?

---

### Post by ubersoft on 2011-10-20
I didn't try touchpad-indicator -- will have to give that a shot. The fact that you aren't seeing those issues is encouraging. So you actually have a working backlight keyboard linux-side?

---

