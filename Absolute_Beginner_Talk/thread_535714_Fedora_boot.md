---
title: "Fedora boot"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by R0B071CxN1NJ4 on 2007-08-26
I would like to find a premade patch for ubuntu 7.04 feisty to change the boot-up to be like fedora. I'm sure it can be done but i do not currently have the programming knowledge to do this myself. could anyone create one or refer me to the location in which one might be found. Thanks!

---

### Post by tuxcantfly on 2007-08-26
From what I remember, the different between the Fedora and Ubuntu boot screens (I assume you're referring to GRUB) was that the fedora one had a nice fancy background. If you check /boot/grub/menu.lst, there should be some line that says "splash" towards the beginning; just go to /boot and find that file, copy it over to your ubuntu /boot (it was splash.xpm or something like that), and add in that line referring to splash.xpm in the fedora menu.lst to the ubuntu /boot/grub/menu.lst

---

### Post by tuxcantfly on 2007-08-26
Or, if you were referring to the actual bootup splash screen, I don't think that can be safely done (might break your system), because fedora and ubuntu use different systems for that; ubuntu uses usplash while fedora uses a mini xserver to do the bootup rendering, and I doubt that package is available in ubuntu. However if you google around for usplash themes (there's plenty out there) you might find one that you like better than ubuntu's default one, or there might be one similar to fedora's; they usually just come in a nice deb package ready to install or they'll give you directions on the site.

---

