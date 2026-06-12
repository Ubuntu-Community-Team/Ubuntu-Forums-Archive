---
title: "iMac G5 w/ 8.04"
date: 2008-05-18
forum: Apple Hardware Users
---

### Post by David Starling on 2008-05-18
I'm using an iMac G5 w/ Ubuntu 8.04. I just recently installed it and I have two problems:

1) Instead of turning the monitor off after the set time in the "Power Management" preference, it just turns it black (i.e. the backlight in the LED is still on). Why is it doing this?

2) It seems to recognize my airport card, but it won't give me a list of available networks to join. I know the card works under OS X, and I know my wireless router is working as well.

Thanks so much for your help! (in advance :KS)

---

### Post by stream303 on 2008-05-18
I've never been able to get my early PPC iMac to do any real power-management, other than blanking the screen for years now.  I guess we're still waiting on the manufacturers to open up their ppc specs for the devs...

About the best I can do is to run an automated shutdown in a terminal in case I walk away and forget about it, ie:

```
sudo shutdown -h +360
```

Which will shut it down 6 hours later...
(ctrl-c to stop it, before shutting down manually)

I'm not doing wireless so can't help there.  Otherwise, still a nice box!

---

### Post by David Starling on 2008-05-19
Thanks for your idea, Stream. 

Unfortunately, I don't like to turn off my computer. I'd rather the processes continue (like, for instance, a download), so I just want the monitor off. Is there a linux command just to do that?

---

### Post by khelben1979 on 2008-05-19
Is it stable?

---

### Post by mchladek on 2008-05-19
I haven't tried this on 8.04 yet, but on my iBook under 7.04 turning the brightness all the way down using the keyboard would actually turn the screen off (backlight and all).

---

### Post by stream303 on 2008-05-19
The system is stable, there just isn't much in the way of power management other than on/off and cpu frequency scaling. :)

Unfortunately the docs for the hardware seem pretty much locked up, so unless the devs have something up their sleeve...

At this point, if power management is a big issue, I'd recommend running OSX actually.  I do this from an external firewire drive when I need to do so.

It's not that bad actually - I recently reinstalled OSX 10.4 and just did a combo-update to 10.4.11, applied the latest security update, installed X11, disabled ipv6, disabled the dashboard, stopped spotlight from indexing the drives, and run Firefox, Thunderbird, Sunbird, VLC, Gimp, Abiword or OpenOffice.  Since the terminal is bash by default, with vi, emacs, nano available, it seems quite possible to avoid some of the annoyances without having to even get customized with 3rd-party OSX repositories.  Something to consider...
 
An interesting thing happens when running OSX from an external firewire drive with Ubuntu on the internal - you'll eventually hear the internal drive go to sleep while running OSX.  Nice.

I love Ubuntu, but thought I'd toss this out if power management is a showstopper. :)

---

### Post by David Starling on 2008-05-20
I'm guessing there's no linux command to adjust the brightness of the LCD for PPCs? 

> **mchladek said:**
> I haven't tried this on 8.04 yet, but on my iBook under 7.04 turning the brightness all the way down using the keyboard would actually turn the screen off (backlight and all).

I can't seem to get this to work. I think the reason is that the keyboard is hard-wired to the graphics controller on an iBook or something, but on my iMac is through USB. Thanks for the idea, though!

---

### Post by stream303 on 2008-05-20
On a G5 iMac, unfortunately no - at least on my early Rev-A model.

You can fake a slight amount of adjustment by using the xgamma command, ie

```
xgamma -gamma 0.8
```
where I typically use anywhere from 0.5 to 1.5, 1 being the default.  If you find something you like to be permanent, you can put it in your xorg.conf file.  Xubuntu actually has a nice gamma configuration utility if you want to go this route - but beware of doing any photo editing with a strange gamma setting.

btw, you can get rid of the Apple startup-bong with

```
sudo nvsetvol 0
```

although this will get reset if you boot back into OSX.

---

### Post by David Starling on 2008-05-22
Alright, thanks for your help but I think I'm going to just use OS X on my iMac and ubuntu on my PC.

---

### Post by tippyknit on 2008-05-23
I've been using Ubuntu 8.04 on my iMac G5 processor...

AirPort: With my mac (and everyone else's mac that I've installed Ubuntu on), you have to use a hard-wired connection and download the restricted driver (found under system -> administration -> restricted drivers). Then Ubuntu will have the firmware to enable wireless networking.

Does that work for you? I know that it works on some macs, but I'm not sure about the newest iMacs and such...

---

