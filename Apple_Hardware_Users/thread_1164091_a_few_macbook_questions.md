---
title: "a few macbook questions"
date: 2009-05-19
forum: Apple Hardware Users
---

### Post by drewjurecka on 2009-05-19
I've recently installed Ubuntu Studio Jaunty on my 1,1 macbook, replacing OSX entirely.
I'm loving it but am having a few problems:

1. Linux doesn't boot automatically.  If I hold down "alt (option)" on startup, I get a boot camp menu that offers it as "windows".  When selected, that works fine, but if I don't startup with boot camp it runs on a blank white screen for 10 minutes before giving me a question mark folder (no HD found).  Any idea how to tell it to automatically find the Linux partition on startup?

2.  How do I disable the awful "DONGGGGGG" startup sound?

3.  Ubuntu starts up with no problems, but generally freezes on shutdown (85% of the time), forcing me to do a hard shutdown.  Where do I start troubleshooting this problem?

4. The screen brightness control is way out of whack.  it alternates between brighter, darker & totally off when using the brightness control slider or the keyboard key... it seems like it's spooling through all of it's brightness settings, but in the wrong order.

I tried to start up from a rEFIt CD to deal with the startup issue, but can't get the computer to start up from it.  Is there a way to install a bootable version of rEFIt on a usb key?

I will say that despite these minor problems this computer runs WAY better on Linux than it ever did on Mac OSX, for some reason.  It's not doing any of the hanging and freezing it used to do.

Thanks for any help on this.

---

### Post by maflynn on 2009-05-19
> **drewjurecka said:**
> 
2.  How do I disable the awful "DONGGGGGG" startup sound?

AFAIK, you can't its part of the firmware/POST boot up

> 
3.  Ubuntu starts up with no problems, but generally freezes on shutdown (85% of the time), forcing me to do a hard shutdown.  Where do I start troubleshooting this problem?

Me too (MacBook Pro 5,1) and I cannot go into sleep mode, well actually I cannot wake it up after sleep.

> 
4. The screen brightness control is way out of whack.  it alternates between brighter, darker & totally off when using the brightness control slider or the keyboard key... it seems like it's spooling through all of it's brightness settings, but in the wrong order.

Check out this [link]("https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty")it may have the answers you're looking for

> 
I tried to start up from a rEFIt CD to deal with the startup issue, but can't get the computer to start up from it.  Is there a way to install a bootable version of rEFIt on a usb key?

I installed rEFIt on my OSX partition and it works fine there. I recommend keeping a small OSX partition so any firmware updates or any need to access OSX for any reason.

> 
I will say that despite these minor problems this computer runs WAY better on Linux than it ever did on Mac OSX, for some reason.  It's not doing any of the hanging and freezing it used to do.
I've found OSX to be pretty stable, I've not had any KPs in a long time, but that doesn't mean I don't like ubuntu. In fact I've been using that more then OSX. I still keep a OSX partition because I use Aperture/iPhone and some other assorted applications that are mac only.

---

### Post by barnex on 2009-05-19
Hi,
I have ubuntu exclusively on my macbook 1,1. It took a while, but I could eventually solve all my problems (so hang on!).

[https://help.ubuntu.com/community/MacBook1-1/Jaunty](https://help.ubuntu.com/community/MacBook1-1/Jaunty)  helped me a lot.

I got rid of the DOOONGGG sound by booting in macos with an old hard drive, muting the volume, then I swapped my ubuntu hard drive in and now the startup sound is gone.

In my old mac system, I had rEFIt installed (not the cd), I did not use boot camp. I now also have the ? icon, but still it boots to linux after a few seconds. Not sure though if installing rEFIt on my previous system had anyting to do with this.

Hope this helped and your other problems get fixed soon.

---

### Post by cyberdork33 on 2009-05-19
> **drewjurecka said:**
> 1. Linux doesn't boot automatically.  If I hold down "alt (option)" on startup, I get a boot camp menu that offers it as "windows".  When selected, that works fine, but if I don't startup with boot camp it runs on a blank white screen for 10 minutes before giving me a question mark folder (no HD found).  Any idea how to tell it to automatically find the Linux partition on startup?bless it. See the FAQ.

> **drewjurecka said:**
> 2.  How do I disable the awful "DONGGGGGG" startup sound?

> **barnex said:**
> I got rid of the DOOONGGG sound by booting in macos with an old hard drive, muting the volume, then I swapped my ubuntu hard drive in and now the startup sound is gone.

It is controlled by the system volume. I have a utility called Psst in OSX that automatically mutes the volume just before shutting down so it never sounds. That doesn't really help in Ubuntu though. I don't know if adjusting the volume in Ubuntu has any effect.


> **drewjurecka said:**
> 3.  Ubuntu starts up with no problems, but generally freezes on shutdown (85% of the time), forcing me to do a hard shutdown.  Where do I start troubleshooting this problem?Diagnosing shutdowns is very difficult because there is not log of shutdown... you can boot without the ubuntu splash and you might be able to see what is going on during shutdown.

> **drewjurecka said:**
> 4. The screen brightness control is way out of whack.  it alternates between brighter, darker & totally off when using the brightness control slider or the keyboard key... it seems like it's spooling through all of it's brightness settings, but in the wrong order.This is a known issue, a bug, and there is not a lot of help here other than searching the forum and finding what people have tried.

> **drewjurecka said:**
> I tried to start up from a rEFIt CD to deal with the startup issue, but can't get the computer to start up from it.  Is there a way to install a bootable version of rEFIt on a usb key?you can boot from the CD by holding 'c' during startup. You can also hold 'alt' like you do for booting into Linux to boot the CD.

You can install rEFIt to a USB drive though. just download the archive and unzip it to your drive. You may need to bless it to get it to work though (and you will have to hold alt again on startup to select it).

 > **maflynn said:**
> Me too (MacBook Pro 5,1) and I cannot go into sleep mode, well actually I cannot wake it up after sleep. For the 5,x mahines it is likely a ACPI issue. there is a bug on this.

 > **maflynn said:**
> I installed rEFIt on my OSX partition and it works fine there. I recommend keeping a small OSX partition so any firmware updates or any need to access OSX for any reason.
You can also install OSX to an external drive if you'd rather.

> **barnex said:**
> In my old mac system, I had rEFIt installed (not the cd), I did not use boot camp. I now also have the ? icon, but still it boots to linux after a few seconds. Not sure though if installing rEFIt on my previous system had anyting to do with this.

Hope this helped and your other problems get fixed soon.
I think that there is a problem with the setting of the bootable partition correctly. you should be able to bless rEFIt and have it boot by default (or bless the linux partition).

---

