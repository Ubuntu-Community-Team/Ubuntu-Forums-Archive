---
title: "Network &amp; Video card install help"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by williamburn on 2007-07-03
Morning:

I have a Dell Latitude D610 and i am having some trouble connecting to my home network via wireless and the video card settings are not running optimally.  I have come here, to the forums, as a last resort.  I have scoured the Internet and even called Dell trying to figure this out on my own, but no luck.

So here is my network card info:  from the command:  lshw

*-network
                description: Wireless interface
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                physical id: 3
                bus info: pci@03:03.0
                logical name: eth1
                version: 05
                serial: 00:16:6f:19:33:58
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
                resources: iomemory:dfcff000-dfcfffff irq:18

According to Dell i have an ATI M22csp/64 mobile video card.  Now the video is working at 1024 x 768, but that is the only resolution that i have.  I was hoping to have the option to make the resolution view a little smaller.

here is the video:  

*-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 03
             size: 256MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
             resources: iomemory:dff00000-dff7ffff ioport:ec38-ec3f iomemory:c0000000-cfffffff iomemory:dfec0000-dfefffff irq:16
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 03
             size: 512KB
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: iomemory:dff80000-dfffffff


Thank you again for the help

---

### Post by negreenfield on 2007-07-03
I have the exact same setup and finally figured out at least the wireless portion.  If you have your SSID hidden, you need to make it visible.  Unfortunately I couldn't figure out a way to get it to work till I saw coffeecat's post in this thread:

[http://ubuntuforums.org/showthread.php?t=477304&highlight=2200BG](http://ubuntuforums.org/showthread.php?t=477304&highlight=2200BG)

I have WPA and could never get it to show up until I changed my SSID from hidden to shown, I then rebooted Ubuntu (don't know if I had to) and it finally started working right.  Before my wireless never even showed up, this time not only did it show up in the top right portion of the screen it showed all the available wireless networks, I clicked on mine, and then it could tell it was WPA.

As for video, I'm still working on that.  I'll hang around the thread and post if I figure it out or if I find an answer.

---

### Post by negreenfield on 2007-07-04
Well, don't know if TC is still interested but I figured out the video portion and it looks great now

[http://ubuntuforums.org/showthread.php?t=141499&highlight=D610](http://ubuntuforums.org/showthread.php?t=141499&highlight=D610)

And for me this worked in that thread

[http://www.kcore.org/?menumain=4&menusub=2](http://www.kcore.org/?menumain=4&menusub=2)

---

