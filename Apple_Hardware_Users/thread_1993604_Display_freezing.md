---
title: "Display freezing"
date: 2012-06-02
forum: Apple Hardware Users
---

### Post by lunchb0x91 on 2012-06-02
I recently installed lubuntu 12.04 on an old PPC Mac mini, model #A1103, and it will work fine for about 5 minutes. After that, the display will freeze and I have to force a shutdown. Does anyone know how I can fix this?



note: I am currently booting with the 'video=ofonly' option.

---

### Post by rsavage on 2012-06-02
> **lunchb0x91 said:**
> 
note: I am currently booting with the 'video=ofonly' option.
 
why?

---

### Post by lunchb0x91 on 2012-06-02
> **rsavage said:**
> why?

It drops to a shell on boot otherwise.

---

### Post by rsavage on 2012-06-02
You'll have to look at your Xorg.0.log to see why it boots to a command prompt.  You could try radeon.modeset=0 as an alternative boot option.
 
video=ofonly will enable KMS (see the PowerPC FAQ).  KMS is very unstable under PowerPC and radeon.  If you boot with video=ofonly radeon.agpmode=-1 then you may cut out your freezing.

---

### Post by EuroCity on 2012-06-03
I can confirm that on my iBook G4 the setting:

**video=ofonly radeon.agpmode=-1**

... works well, without freezes; and you also get the "real" graphical bootsplash (even if still with false colours).

---

### Post by EuroCity on 2012-06-03
BTW, if you want to make this setting permanent (applied automatically at every boot), just do this in the Terminal:

**gksudo gedit /etc/yaboot.conf**

... and add **video=ofonly radeon.agpmode=-1** to the *append = "quiet splash"* sections (inside the quotes); save, and finally do a:

**sudo ybin -v**

... to update the Yaboot configuration.

---

