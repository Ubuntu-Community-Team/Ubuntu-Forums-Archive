---
title: "Trying to get 12.04 working on iMac G5 - White Screen - trying all sorts of things"
date: 2012-05-05
forum: Apple Hardware Users
---

### Post by spaceballl on 2012-05-05
Hi All!

Well, I'm trying to get Ubuntu 12.04 up and running on my iMac G5, and I'm not having too much success. So if I just do a default install of 12.04 on my G5, i get the following screen:

[IMG]http://upgrd.com/images/kevin/singles/white-screen.jpg[/IMG]

I've read the thread [here]("http://ubuntuforums.org/showthread.php?t=1937940"), and I think the issues are related. I've tried using the xorg.conf file there, and it doesn't seem to do anything for me. I've switched the resolution values to 1440 x 900. When I reboot with that xorg.conf file, I don't have any improvement. It's the same.

Alternatively, if I reboot with the yaboot parameter of "nouveau.modeset=0", I can then SORT OF see the desktop but the graphics are all jumbled. Looks like something out of a hippie music video. Clearly some sort of distorted graphics issue.

If I reboot with "nosplash video=ofonly" I still get the same white screen above.

I'm guessing the way to fix this is with a fixed xorg file. I can edit the xorg file BARELY if I log in with the "nouveau.modeset=0" option. So I think the strategy is to log in with that... and then modify my xorg.conf file.

Also, to be clear, I didn't start w/ a default xorg.conf file. I created one, and I stuck it into /etc/X11

I think that's the right spot. Anyhow, I'm very grateful for any help you can provide me to get this up and running. Thanks! If I can get it going, I'm thinking about putting an SSD in it and maxing out the RAM... just for giggles :-)

---

### Post by TheSkunkMan on 2012-05-05
Hey I just had that same problem with a fresh install on my PC. Try changing the setting when you sign in to 2d (You click the round ubuntu symbol thing near the sign in info and then select 2d). It worked for me.

---

### Post by spaceballl on 2012-05-07
Does that mean I'll have to use Unity 2D instead?

---

