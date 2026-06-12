---
title: "nvidia GeForce splash screen freezes"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by schibs on 2007-11-26
Long time lurker who finally registered as I could use some help regarding my video driver.

I'm attempting to update the drivers for an nvidia GeForce MX 200 video card in order to take advantage of compiz fusion. (The system works fine with the "nv" driver installed.)

When I update using the Restricted Drivers option, I end up with a black screen.

I re-loaded the system and used Envy. It works really well until I reboot. At that point the nvidia splash screen hangs and I have to reset the system.

I can boot into the recovery mode and access the Envy command line program.

Right now the computer has been re-loaded and envy installed. I'm looking for any ideas on how I can fix this so that I can take advantage of the capabilities of the video card and avoid buying a different video card.

Thanks.

---

### Post by jken146 on 2007-11-26
In recovery mode:
```
dpkg-reconfigure xserver-xorg
```

---

### Post by schibs on 2007-11-30
Thanks jken146,

The "dpkg-reconfigure xserver-xorg" command helped with my troubleshooting attempts.

I used Envy to uninstall the nvidia driver and this time I used the Restricted driver. Now it boots fine until I reach the nvidia splash screen. It freezes at this point with no CPU or mouse activity.

Any ideas?

---

### Post by el_itur on 2007-12-03
I have the same issue. Some background: the driver was working flawlessy, util today that i have to change the cooler of the cpu so I took my box to the service and i tested it there, everything was working fine, even the desktop effects, when I take the box back to my home the boot procces was fine util the desktop has to came in. 
Then the screen just halted like when the computer is turned off.
The card works with nv though, The issue is with the propietary driver, I don't know what's wrong and I have no luck to go to a TTY (none works the screen just looks like the machine is down)

---

