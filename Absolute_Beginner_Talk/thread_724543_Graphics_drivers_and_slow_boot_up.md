---
title: "Graphics drivers and slow boot up"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by DarkMartyr on 2008-03-14
I had the 64bit set of linux restricted drivers installed on my 32bit ubuntu. Everything was working fine except my graphics. My screen resolution won't let me go higher than 800x600 and my screen should go much higher than that. I had the nvidia-glx-new driver installed. I uninstalled the 64bit restricted set and installed the i386 set. I downloaded envy, had it install my nvidia graphics driver. I restarted and have to reinstall my madwifi driver because it wasn't showing up anymore? Also ever since i uninstalled the 64bit set my ubuntu has been booting up really slow. The first reboot it asked me to configure the graphics, run in low graphics mode, or shutdown. I configured them. Was that the problem? Boot up goes like this.

Grub loads I pick the first ubuntu default.
some shell output pops up, screen goes black.
stays black until I hit the power button then it flashes with some green lines across the bottom and it goes to the ubuntu loading screen. This now hangs at the 3/4 mark (about) until i again hit the power button.

So my question has several parts for those who say tl;dr

Does it matter if I was using the 64bit or 32bit driver set (im running i386 ubuntu 7.10)?
Did I screw things up by configuring the graphics on that reboot?
Why won't my screen go higher than 800x600 resolution?
Why did I have to redo my madwifi install after installing my graphics via envy?

---

### Post by dokdoom on 2008-03-14
Next time you start X open up a terminal and type

ls -ltr /var/log

Chances are near the bottom of the list will be an Xorg.0.log

tail the Xorg.0.log and google the error.

tail /var/log/Xorg.0log |grep EE

Good luck.

---

### Post by DarkMartyr on 2008-03-15
just realized my audio drivers are screwed up now too? maybe I should just revert to the 64bit?

Tailing the file returned no errors.

---

