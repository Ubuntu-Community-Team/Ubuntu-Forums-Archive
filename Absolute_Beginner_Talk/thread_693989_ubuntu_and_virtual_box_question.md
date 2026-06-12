---
title: "ubuntu and virtual box question"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2008-02-11
okay on my laptop i am running virtual box i got 2gb of ram so it runs fine. now my only problem is my screen resolution for the virtual box it is eaither 800x600 or smaller is there anyway that i could force it to load in like 1024x768 its a 15.4 inch monitor 1280xXX something any ideas?

---

### Post by Incense on 2008-02-11
Have you installed the guest add-ons? That may help.

---

### Post by Wiebelhaus on 2008-02-11
> **fedex1993 said:**
> okay on my laptop i am running virtual box i got 2gb of ram so it runs fine. now my only problem is my screen resolution for the virtual box it is eaither 800x600 or smaller is there anyway that i could force it to load in like 1024x768 its a 15.4 inch monitor 1280xXX something any ideas?

Run in term

"sudo dpkg-reconfigure xserver-xorg"

Then run threw the xserver setup and choose the resolution you want and if you like after that hit "crtl+f" for full screen in Virtualbox and repeat to get out of full screen.

---

### Post by fedex1993 on 2008-02-11
> **Incense said:**
> Have you installed the guest add-ons? That may help.

quest what do you mean guest addons?

---

### Post by TechDragon on 2008-02-11
when you power on the machine, click on devices, the last option will be install guest services.  Do so it makes it run a lot better and grants more options.

Also the version out of the repo is the Open Source version.  If you download the non-open source version from their site it has more options.  Such as USB support.  It is still free, just not open

---

### Post by Incense on 2008-02-11
> **fedex1993 said:**
> quest what do you mean guest addons?

When the VM is running, click on Devices, then Install Guest Add-On's. If you are running windows, you'll see an autorun install wizard pop up. This will install Video, and Mouse drivers. When you reboot the VM, you can just stretch the screen, or change the screen res. If you're running windows, this will also enable seamless mode (CTRL-L) where your windows will show up on your linux desktop outside the VM. Kind of cool. Hope that helps!

---

