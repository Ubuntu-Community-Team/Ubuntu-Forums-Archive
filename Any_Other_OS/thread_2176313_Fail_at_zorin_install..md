---
title: "Fail at zorin install."
date: 2013-09-23
forum: Any Other OS
---

### Post by nathan10 on 2013-09-23
Hello, I am trying to install Zorin OS 7 Core on my mother's HP Pavilion g6. It has the same hardware it had when she first bought it, and it came with Windows 7. I tried to boot it from a USB Drive. I know the USB with Zorin worked because I've used it on another computer. I had to set the boot order to the USB drive first because it wouldn't boot automatically. The first three options in the menu, "Default", "Boot the live system", and "Boot in safe graphics mode" all did the same thing. They would show the boot up screen with the little ambiance waves around the Z for about 30 seconds, and then it would just freeze showing the boot up screen and it wouldn't do anything else after 20-30 minutes (as long as I left it to boot). The "Start the installer directly" Did something different. It showed the boot up screen for about 2-3 minutes and then the screen went black and came on with the boot up screen and a little gray bar spanning across the top. Then the screen suddenly changed to a jumble of pixels that looked like the computer crashed or something, it slowly faded to white, and then back to the boot up screen and gray bar, which it got stuck at and wouldn't do anything else. I've tried Ubuntu 12.04, 12.10, and 13.04 as well as Linux Mint 15 and they all did very similar things to this. I got no help from anywhere else so I don't have much hope here, but please, if you have any idea what this might be please respond! Thank you.
'

---

### Post by QIII on 2013-09-24
*Moved to **Other OS/Distro Support***

---

### Post by nathan10 on 2013-09-30
I'm not getting any help, am I?

---

### Post by The Cog on 2013-09-30
I don't suppose many users here are familiar with zorin. From your description, it's not the same installer that Ubuntu uses.

Your description sounds to me as though it might be problems with video drivers. In the recent Ubuntu installers, you can press enter early in the boot process (while there is an icon of a little man and a keyboard on screen) and then you get some options. F6 gets you some extra options were you can set an option called **nomodeset**  which can help a lot with video driver issues. It might be worth a try. I dont know if zorin has a similar option.

Failing that, I have seen others suggest replacing your shiny new video card with one that is a few years old for the duration of the install, on the basis that the installer can't handle very recent cards but that after install you can install updated drivers.

---

### Post by mastablasta on 2013-10-01
> **nathan10 said:**
> HP Pavilion g6. It has the same hardware it had when she first bought it, and it came with Windows 7. '

pheh models... what are the specs? specifically GPU.

and yes do try nomodeset boot option.

---

