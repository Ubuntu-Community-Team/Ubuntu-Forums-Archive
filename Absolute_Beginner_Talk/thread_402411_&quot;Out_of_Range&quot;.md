---
title: "&quot;Out of Range&quot;"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by cc48510 on 2007-04-05
I downloaded and burned Ubuntu 6.1.0 CE (i386) [and later Ubuntu 6.0.6 (i386) to see if it would work - it didn't either]. I booted from the CD and selected "Start/Install Ubuntu". But, when it finished loading the first screen, the screen went black and displayed "Out of Range".

I searched the web for solutions, but all the other posts involved this happening after installation was complete. Since, nothing has been installed [as it does this before the installer even comes up] the sudo dpkg-reconfigure xserver-xorg solution will not work...because as soon as I reboot, the settings revert to default [since it is running from the CD] and if I hit Ctrl+Alt+F7 [without rebooting] it still shows "Out of Range".

**Monitor:** Westinghouse 17" Widescreen LCD ([http://www.westinghousedigital.com/details.aspx?itemnum=29](http://www.westinghousedigital.com/details.aspx?itemnum=29))
**Motherboard:** MSI K8NGM2-NBP ([http://www.msicomputer.com/product/p_spec.asp?model=K8NGM2-NBP&class=mb](http://www.msicomputer.com/product/p_spec.asp?model=K8NGM2-NBP&class=mb))
**Processor:** AMD Athlon 64 3500+
**Memory:** 512MB Kingston DDR-400

I'm using the built in D-Sub (Analog) video.

---

### Post by Bachstelze on 2007-04-05
After you reconfigured your Xorg, do

```
sudo /etc/init.d/gdm restart
```

to restart X without rebooting.

---

### Post by cc48510 on 2007-04-05
Another problem...

$ sudo /etc/init.d/gdm restart

> Stopping GNOME...[OK]
Starting GNOME...[[COLOR="Red"]fail[/COLOR]]

---

### Post by cc48510 on 2007-04-06
I tried 7.04 Beta and it loaded, but the screen is split in 25/75 with the bottom 25% on the top and top 75% on the bottom separated by a black area, with a black area on the right. Hopefully, that will be fixed when I get it installed and install the driver for my on board video [which I had to find elsewhere as MSI has only Windows drivers on their download page - even their Live Update only works on Windows.]

---

### Post by cc48510 on 2007-04-07
7.0.4 Installed and Running...nVidia driver corrected picture problem.

---

