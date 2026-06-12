---
title: "Wine windows too small and unresizable"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by Denta on 2006-08-12
When I run som apps in wine, the windowsize doesn't get right and the appwindow is bigger then the winewindow and therefor I can't see all content. Somehow the wine window seems impossible to resize? Is there a commandline swtich or something for this? Running KDE...

---

### Post by orb9220 on 2006-08-12
That window belongs to winecfg for configuring apps after they been  installed by wine. It is not used to run applications. That image shows you have not added any apps to the winecfg. Click on add and then browse to installed apps and add them to winecfg so you change the default settings.

Then the program is run from a shortcut or term window with the commmand:

wine "C:\Program Files\DVD Shrink\DVD Shrink 3.2.exe" as an example.

---

### Post by Denta on 2006-08-12
> **orb9220 said:**
> That window belongs to winecfg for configuring apps after they been  installed by wine. It is not used to run applications. That image shows you have not added any apps to the winecfg. Click on add and then browse to installed apps and add them to winecfg so you change the default settings.

Then the program is run from a shortcut or term window with the commmand:

wine "C:\Program Files\DVD Shrink\DVD Shrink 3.2.exe" as an example.
I know, but the screenshot was a perfect example of my problem, look at how it is impossible for me to press "OK" in this window. This problem appears in many of the applications i run via wine. The wine-window simly is to small for the whole applications window  to fit in it and it seems to be impossible to resize.

---

### Post by orb9220 on 2006-08-12
Oh Ok I see now its a screen resolution setting.
Can you change resolution by going to system>perferences>screen resolution?

If it is already set to hightest there then you will have to post your graphics card or chipset type so we can help with getting the right video drivers and configuring your xorg.conf file for higher resolutions.

---

### Post by Denta on 2006-08-12
> **orb9220 said:**
> Oh Ok I see now its a screen resolution setting.
Can you change resolution by going to system>perferences>screen resolution?

If it is already set to hightest there then you will have to post your graphics card or chipset type so we can help with getting the right video drivers and configuring your xorg.conf file for higher resolutions.
Hmm, my bad english makes it hard for you to understand my problem. The resolution is not wrong either, i I'm running my tft native 1280*1024. The image I posted was just a cropped one, have a look at the one in this post.
 
All applications I run with wine opens in a wine-window called wine-desktop and most of the time that winows is too small to fit the contents of the app.How do I resize it or even better run applications without having them to do so in a winewindow?

---

### Post by orb9220 on 2006-08-12
Ok the only thing I can think of is version of wine.

I just got an update for it this morning. Did you get a wine update?

Run the update manger from adminstration tools and see if thier is another update avialable to fix this.

There is also other threads of this complaint. Search on wine and see it others had a fix for this.

Sorry I couldn't be more help.

---

### Post by steve.horsley on 2006-08-12
I have never seen that "wine desktop" window before. The applications I run in wine always have a native Gnome window. See attached screenshot. I would concentrate on why wine things are being put inside that window.

I would add that I have no idea why you get that window. But I don't think it's normal.

---

### Post by eneth80 on 2007-07-12
I had the same problem: i could not reach the "ok" button with the mouse. But i could press Enter, have you tried it? do winecfg, modify Desktop Size in Graphics and press enter (ie OK).

---

