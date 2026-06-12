---
title: "iMac with broken screen, Ubuntu LiveCD, and external monitor"
date: 2012-01-18
forum: Apple Hardware Users
---

### Post by qyot27 on 2012-01-18
Back in October the screen of my parents' iMac (which was one of the early Intel models, from 2006 - which means its warranty was expired) broke.  They eventually got fed up and bought a new one, and let the Geniuses transfer the data to the new iMac.  Except for the small part of the process where not all of my mom's data got transferred (none of the photos and none of her iTunes library past the letter T, if I recall correctly).  I even checked manually through Finder - the missing data is not there at all, unless they did something really stupid and put it in a non-$HOME location.

Now, it would be easy for me to just open up the old iMac, take out the HDD and pop it into an enclosure for them, but since the diagnostic report we got back said that the only thing wrong with it is the non-working screen, I wanted to try and get it to a state that allows us to still *use* it.  And so the external monitor idea came up.  I bought a Mini-DVI to HDMI adapter and tried to hook it up to our HDTV.  Nothing.  No video output, and how can we manage to log in if we can't even see what's going on?

I remembered, quite late in this process, that I used to use an Ubuntu LiveCD on this iMac to do some encoding work, and that it should have the hfsplus read-only support I'd need to copy the rest of the data off to a flash drive.  So I hooked it all back up again, and tried whatever tidbit of information I could find to see if I could boot directly from the LiveCD, hoping that the LiveCD could make it see the external monitor/TV and allow us to actually use it again.

Again, though, no video output at all.  I'm not even sure if I was able to even tell it that it needed to boot from the CD.  My experience with using the LiveCD before required using the mouse to select that option after bringing up the boot selection screen.  Without video output, I'd be blindly clicking around.  I found some info that purported to say that Option+C would force CD booting, but after doing that and waiting for like 5-10 minutes, there still wasn't anything showing up on the external display.  I deliberately knew I had to use an *older* version of the LiveCD (in this case, I went with 9.10, since that's what the LiveCD I used to use for encoding on it was) that automatically booted into the Live session instead of forcing the user to click on the Try button.  Because I feared that I wouldn't be able to see what I'm doing to be able to use the mouse and it would need to be fully inside of the environment to detect the external display.  Maybe that's part of the problem, and a newer version would be more equipped to handle external displays over HDMI, but then the question is how to force it to automatically log into the Live Session.



My question, therefore, is whether the LiveCD can even manage to find and use external displays in the Live Session, and whether this could just be an iMac-related annoyance that can only be resolved by me taking the hard drive out and using an enclosure to get the rest of the data off.

Barring all of this, would physically removing the LCD from the iMac and trying this again force it to see the external as the *only* screen hooked to it and therefore work as it should?  I'd have to remove the screen anyway to get the HDD out, but I'd like to avoid this route if I can.  A usable iMac I can exploit for its processing power and burning drive (which I could do with just Ubuntu installed on it, if I could get this external monitor thing sorted out and the remaining data properly transferred) is better than nothing.

---

### Post by guidop on 2012-01-22
If you want to just get the data off the disk, connect the broken Mac to another Mac (or a PC running GNU/Linux with HFS support) using a firewire cable. Boot the broken Mac while holding down the 'T' key to put it in target disk mode. You should be able to mount the drive on the other Mac/PC and at least read the data on the drive. 

Intel Mac Startup Key Combinations:
[http://support.apple.com/kb/HT1533]("http://support.apple.com/kb/HT1533")


As far as your display problems go, I suspect your graphics card may have failed, and no display will work with it. You may be able to find a replacement part, but unless you're really good at complex DIY repairs, I'm not sure it would be worth fixing. Here are a couple of Apple Support forum threads on the type graphics cards I think might be in your model:

[https://discussions.apple.com/thread/2265985?start=0&tstart=0]("https://discussions.apple.com/thread/2265985?start=0&tstart=0") 
[https://discussions.apple.com/thread/2579255?start=0&tstart=0]("https://discussions.apple.com/thread/2579255?start=0&tstart=0")

---

### Post by qyot27 on 2012-01-22
> **guidop said:**
> If you want to just get the data off the disk, connect the broken Mac to another Mac (or a PC running GNU/Linux with HFS support) using a firewire cable. Boot the broken Mac while holding down the 'T' key to put it in target disk mode. You should be able to mount the drive on the other Mac/PC and at least read the data on the drive. 
Now just to get a 6-pin to 4-pin FW400 cable.  The laptop I've got Ubuntu on has a 4-pin port.

> As far as your display problems go, I suspect your graphics card may have failed, and no display will work with it. You may be able to find a replacement part, but unless you're really good at complex DIY repairs, I'm not sure it would be worth fixing. Here are a couple of Apple Support forum threads on the type graphics cards I think might be in your model:

[https://discussions.apple.com/thread/2265985?start=0&tstart=0]("https://discussions.apple.com/thread/2265985?start=0&tstart=0") 
[https://discussions.apple.com/thread/2579255?start=0&tstart=0]("https://discussions.apple.com/thread/2579255?start=0&tstart=0")
That's what I feared also, but when they took it into the Apple store (and then to one of the certified repair centers to see if they could get a cheaper price) for a diagnostic the tech said it was just the LCD screen itself that failed, and that a new one would set them back $500 (which they decided not to do because it would only have a 90-day warranty).  Since I wasn't there, I have to rely on what they told me second-hand.  The initial failure was that while my mom was using it, the display froze, and when she restarted it, the screen just stayed off/black.  And I also believe it's the 17".  It was using a GeForce, but I can't remember the exact model.



What about using an external graphics card?  I found a few that claim to be able to use USB 2.0 and connect to VGA, DVI, and HDMI.  Like this one: [http://www.amazon.com/USB-HDMI-External-Resolution-1920x1080-1600x1200/dp/B005UKG4KU](http://www.amazon.com/USB-HDMI-External-Resolution-1920x1080-1600x1200/dp/B005UKG4KU) .  The only thing I'd fear is that it wouldn't be recognized without drivers, and if there's no display to see it (and the CD drive is still occupied by the Live CD; it didn't want to eject it, although if the Live CD can recognize and boot with the external card, great), that's a problem.

---

### Post by guidop on 2012-01-23
Sorry, beyond my expertise. The following comments are just guesses and speculation:

Apple displays really are that expensive, and generally not worth replacing out of warranty.

A frozen screen seems more like a video card, not an LCD problem. Could be wrong, though. 

Maybe you can make and external monitor work, but need to see the primary screen to select it.

If you start the iMac up and shine a flashlight or bright light on it at the right angle, you may be able to see faint images on the display.  If so, the inverter or backlight is probably bad.

The Sabrent part info says it will work with OS X, but you have to install software first.  Hard to do without a display.

There is an Ubuntu thread about the Sabrent, but doesn't look like they had much luck:
[http://ubuntuforums.org/showthread.php?t=1669296]("http://ubuntuforums.org/showthread.php?t=1669296")

---

