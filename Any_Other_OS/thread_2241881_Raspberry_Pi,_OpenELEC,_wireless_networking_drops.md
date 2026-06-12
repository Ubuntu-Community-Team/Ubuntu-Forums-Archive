---
title: "Raspberry Pi, OpenELEC, wireless networking drops"
date: 2014-08-28
forum: Any Other OS
---

### Post by dave131 on 2014-08-28
I have 2 Raspberry Pi's set up as cheap media centers in 2 different places in the house.  Since there is no way to route ethernet cables to them I am using Tenda USB wireless adapters with them.  Since the Pi (original Model B's, not the new Model B+) have limited current available for the USB ports, and that 1 port is used by a USB flash drive used for the OS and the other connects to a powered USB hub, the wireless adapters are plugged in to the USB hubs.  The hubs have their own AC power so they don't overload the Pi's.  The hubs currently have the wireless adapters, "powered by the hub" USB disk drives and either a USB IR receiver (on 1 of them) or  wireless mouse (on the other).  I hope that's enough background.

What happens:  the wireless network connections on the Pi's show as active on the OpenELEC configuration screen, but I can't ping the systems and when on the Pi's it's apparent networking has somehow stopped since when I go to weather it never retrieves anything.  If I simply disable/enable the wireless on the Pi's then they are visible again and the weather works, etc..  They stay like this for a while, then they just disapear again.  At 1 point quite a long time ago I tried putting in a ping to the router for every 5 minutes or so, and while it kept the networking "alive", it messes up playback in XBMC.

The Pi's have a "reserved" IP address in the router, so whenever they come online they get the same IP address each time.

The router side is one of those Comcast "one does everything" boxes - internet, phone, TV.

---

### Post by varunendra on 2014-08-29
While the possibility of the culprit being something else can't be denied, I very much doubt the USB hub in this case. I have a 4-port i-Ball externally powered USB hub, and my USB 3G-Modem never connects when connected to it (it doesn't even get detected most often). I know the WiFi dongle and a GSM/3G modem are entirely different beasts, but it even causes the usb keyboard miss the keys _very_ often when typing in normal speed (20-30 wpm). That missing of keys, clicking of mouse, occasional disconnection of external Hard Disk... all point their fingers to one inherent problem of USB hubs, powered or not - The delay in "Polling Interval" across different ports.

Can you test the wifi dongle by connecting it Directly to the available usb port on the RPi? Is the current not sufficient to even power the card and the dongle both?

---

### Post by dave131 on 2014-08-29
I guess what I could try is putting the USB flash drive for the OS (it still does the inital boot off the SD card, but uses the USB flash drive for everything else except media storage) in the hub and put the USB wireless network adapter straight in the Pi.   What's strange to me is that it works fine for playing a movie over the wireless to my tablet when I do the reset so I can access it.  When it's idle that's when it acts like something has timed out.

I'm busy today so I probably won't be able to try that until the weekend.

Thanks.

---

### Post by dave131 on 2014-09-02
Well, I forgot to do that.  What's interesting is that it's still up after 3 days - I can still successfully ping it.  I don't understand why, but I won't complain.  When I finally notice that it is no longer reachable I'll switch them.

---

### Post by varunendra on 2014-09-02
Let's hope it keeps working. Most people would prefer to live with the mystery than knowing and fighting with the problem. :p

---

### Post by dave131 on 2014-09-02
Well, this gets interesting.  Just a minute ago I made sure I could still ping one of the Pi's.  Went to file manager and was able to open it.  Went to terminal and ssh'd to it.  At which point the Pi's wireless network connection appears to have locked up again.  Going to try moving the adapter and flash drive around now and wait several hours and see how that is going, and then try these same steps again.  I really wish I actually knew something about networking so I'd have some idea of what should be going on, how to look for troubleshooting data, etc..  Are there any beginners guides to networking so they start at the basics and work their way up to some of this stuff?

Thanks for the help.

EDIT:  Tried swapping the wireless adapter to the Pi port and the USB flash drive used for running the system to the USB hub.  After plugging everything back in - the Pi never boots.  Even the little green activity light that shows if anything is happening doesn't go green.  Tried swapping everything back - no go.  So, somehow I now seem to have fried my Pi.  Great.

---

### Post by varunendra on 2014-09-02
> **dave131 said:**
> EDIT:  Tried swapping the wireless adapter to the Pi port and the USB flash drive used for running the system to the USB hub.  After plugging everything back in - the Pi never boots.

Could the USB 2 vs USB 1 issues causing trouble here too? Just posted something about it, please check if you have a similar situation : [http://ubuntuforums.org/showpost.php?p=13113490](http://ubuntuforums.org/showpost.php?p=13113490)

If the flash drive is essential for running the OS, it must be on a USB2 bus. If it already is, then could again be the 'polling interval' lag causing the OS to freeze. Does it boot again if you connect it to the available port directly again?

---

### Post by dave131 on 2014-09-02
Still working on the system.  The SD card it starts boot from went bad, so I've been rebuilding it. The Pi's don't have a powe switch, so I first disconnect the USB hub, then pull the power cord on the Pi.  This is obviously not the best way to do things, but with wireless down I couldn't "halt" the Pi.  So, by disconnecting the USB hub it removed a flash drive the OS runs from and I multiplied things by "pulling the power".  Took the card to my laptop and while I can copy some things to it, it fails in the boot area, and that is all I'm using it for - just the initial part of the boot so it can know to go to the flash drive and load the image and run.  So, I've been trying to recreate that SD card.  When initially done it won't have the flash drive linked to it since that requires more work.  So, I can leave the flash drive completely out of the equation and connect the wireless to the Pi directly.  Only the disk drive will be plugged in to the Pi and it's not required to boot, etc..  So I can try that for a while and see if it helps.  Nothing timing dependant for the OS will be on the hub that way.

---

### Post by dave131 on 2014-09-06
varunendra - I think you solved this for me!  It's been 4 days since I tried and I can still ping that Pi.  So it must be the timing issues you were mentioning with using the hub and its polling must be it.  I'll make the change now to the other locally and to some others I have done.

Thanks!

---

### Post by varunendra on 2014-09-06
> **dave131 said:**
> So it must be the timing issues you were mentioning with using the hub and its polling must be it.

YAY!! :popcorn:

Thank you for the awesome and precious feedback! Helps building confidence about a theory until something to the contrary comes by. :)

---

### Post by dave131 on 2014-09-10
Another 3 days - this makes 7 - and it's still working!  Thanks again!

---

### Post by dave131 on 2014-09-12
9+ days and still working!!  Now I know what to do with the other 1 in the house and to the others I've done for other people.

---

### Post by dave131 on 2014-09-20
An entire week since the last time I tried, and I've even reloaded the OS on my laptop, and it still works!!  Thanks for bringing the timing issue to my attention.  I never thought about the polling on the hub and since I don't know what the polling sequence and frequency is, and obviously can't change that as we can do on networks, indeed plugging the wifi adapter directly in to the Pi.

So, anyone who might be reading - this will be my last post in this thread because......IT'S WORKING!!

---

### Post by varunendra on 2014-09-21
> **dave131 said:**
> I never thought about the polling on the hub and since I don't know what the polling sequence and frequency is, and obviously can't change that as we can do on networks, indeed plugging the wifi adapter directly in to the Pi.

I think it is hardcoded in the USB drivers and is also limited by USB standards and chip limitations. As such, I don't think much can be done about polling interval unless there is some radical change in the USB technology. So it is a fundamental problem, and has been affecting anything that can't cope with the additional delay caused by additional ports.

The thing that troubles me most is that almost everywhere on the net, where they talk about adding USB hubs (internally or externally) to gain extra ports, it is never mentioned that it is not the same thing as a dedicated USB chip connected to a PCI bus, and problems may occur with some devices. Mostly there is either no such information, or misinformation.

Thank you so much for continued testing and confirmation about this. I'm sure it will answer many mysterious "Why's" of future readers. :)

---

### Post by dave131 on 2014-09-22
It is interesting - I remember back when USB was just a "thought" but not the real world yet.  The ideal solution to adding devices to your PC!  Simple plug and play!  As you mention, the average user (I don't know, maybe they don't care or don't want to know) doesn't seem to realize all of the traffic from those devices are going through a single pipe (the controller) so the more devices, the slower the bus gets.  I don't know about USB, but it *was* also true on some other things that the bus's through put was only as fast as the slowest device on that "network" (for lack of better words).  So, *IF* it holds true with USB, it also means that if you have a USB3 device and a USB 1 or 2 device then having a USB3 device on that bus would be defeating the purpose.  

What's really interesting to me is polling  and sequence on a USB bus to begin with.  I guess I was thinking more along the lines of a network where everyone could try to talk basically "at the same time" instead of waiting to be polled.  I guess it makes sense that it be on a USB bus, I just never really thought about it until you mentioned it.  Anyway - you have solved my problem!  This also means that all the trouble I was having with using Samba on the Pi should be gone now as well, since it would appear that the networking side dropping would of course cause the shares to not be available!!  ;)   Need to check the file manager and see if I can continue to access the Pi that way as well - that used to fail after a little while also!

---

