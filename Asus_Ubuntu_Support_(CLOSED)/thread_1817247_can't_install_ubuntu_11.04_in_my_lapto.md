---
title: "can't install ubuntu 11.04 in my lapto"
date: 2011-08-03
forum: Asus Ubuntu Support (CLOSED)
---

### Post by amitpramanik on 2011-08-03
i have a new ASUS P52 laptop(intel core i5-480m processor,4GB RAM,500 GB HD) and i tried to install ubuntu 11.04 version (64 bit ) from dvd image but failed. That dvd works when i select the option TRY UBUNTU

---

### Post by tommpogg on 2011-08-03
Could you give us more info?
What went wrong? Where did the installation stopped? Has any error been displayed?

---

### Post by tijs14tijs on 2011-08-05
It could be that your chipset is not supported by Ubuntu, i've seen several cases with the Asus P5Q chipset. [http://ubuntuforums.org/showthread.php?t=890604]("http://ubuntuforums.org/showthread.php?t=890604")

But if it does boot on cd i guess it is something else.. Probably a graphics issue, do you get the Xorg screen? Maybe your graphics card is not supported or not working correctly, this could happen when you load the wrong graphics driver. 

Did previous versions of Ubuntu (10.10) boot on your pc?
11.04 has Unity which works good but sometimes gives a little trouble at the start.

You can try Ctrl+Alt+F1 which leads you to the terminal.
Alt+SysRq+k restores your session, if your install freezes you can try this.

If the install on ubuntu doesn't work, you can install ubuntu in windows. Just use Wubi.exe on the CD :)

Or does it stop at the installation itself?
Can you please be more specific at what issues you are encountering?

---

