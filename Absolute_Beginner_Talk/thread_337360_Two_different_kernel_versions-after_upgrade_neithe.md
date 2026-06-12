---
title: "Two different kernel versions-after upgrade neither work now -- what happened??"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-01-12
Ok here is the skinny--I installed Ubuntu 6.06.1 (install CD) while on the road (truck driver) without an internet connection and everything went just fine. I showed the 12-15-26 386 kernel installed and all worked great. I got home last night and hooked up my ethernet line and it was recognized and activated just fine. In a few minutes I got an update notification ( icon in upper right hand of screen) saying there were updates available. Included in these updates was the 12-15-27 386 kernel. I installed the updates with synaptic and all looked to be fine. I powered up this morning and on the screen showing OS's I read the 26 386 kernel with recovery mode, and the 27 386 kernel also with recovery mode, memtest, and Windows XP. When I select the 12-15-27 386 option (supposedly the newer version I guess) I get a message during boot-up saying "PXE-E53: No boot filename received" and then  black screen with non blinking cursor in upper left. Any way I can fix this or will I have to reinstall again with ethernet cable plugged in? Thanks for the help--I really need it.

---

### Post by jerrynewt on 2007-01-12
Error correction the kernel versions are 2.6.15-26-386 and 2.6.15-27 386 both with recovery mode and memtest86 along with Windows XP. Sorry for the mistake.

---

### Post by Modernity on 2007-01-12
Have you tried booting in the 26 version?

---

### Post by jerrynewt on 2007-01-12
Yes and I get an error saying" error- failed to start X server" and asking me if I want to view the X server output to diagnose the problem. When I hit enter (yes) it says warning! error! not implemented! Then a message saying "The X server is now disabled. Restart GDM when it is configured correctly". Now I'm really lost. I haven't made any changes from last night other than the 27 386 update. Did the update fail to put the 27 386 kernel in boot partition? Sure hope I can fix this as I don't want to have to do a reinstall again. Thanks for the quick reply.

---

### Post by Modernity on 2007-01-12
It seems as if your problem is snowballing, so if no one else has any suggestions, I would just start over.

---

### Post by jerrynewt on 2007-01-12
Ok I found a post telling someone how to reconfigure X server and tried it and it worked! All I was getting after the warning messages was command line option (no GUI). Anyone know why the 27 386 kernel won't work at all?

---

### Post by jerrynewt on 2007-01-12
Well I uninstalled the NVidia driver that I installed last night and everything went back to normal. No problems at boot, both 2.6.15-26 and 27 kernels and their respective recovery modes, memtest86 and Windows XP show up as choices to boot to. Maybe just a hiccup or the NVidia driver was messing with things. Thanks for the input!

---

