---
title: "graphics screwed up again!"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by waggingwabbit on 2008-04-17
ok...so i hear that ATI sucks with ubuntu, so i got my bros nvid 6600gt. i tried enabling restricted drivers with ATI and it screwd everything up so i reformated. now with this 6600gt i cant get more than 1024x7XX resolution and 50 or 60 refresh. my monitor is a samsung 175v with 1280x1024 native res. so i tried the things on this post: [http://ubuntuforums.org/showthread.php?t=497787](http://ubuntuforums.org/showthread.php?t=497787) (im on gutsy btw) and now im having the same problem i had with the ATI. when i start up the comp, i tries to load up the graphics or something and can't. i get a grey error box message and my mouse corsur is a black "X". the resolution is down to 800x600 now and my tablet isn't working properly either. in NO WAY AT ALL did i even touch anything related to that in xorg. i changed the "nv" to "nvidia" and saved it, but i changed it back before restarting cuz i wasnt sure about it. then i also tried installing nvidia-settings, but it got rid of nvidia-glx-new... how do i fix this and get my native res?

---

### Post by warbread on 2008-04-18
Can you post your xorg.conf file?

---

### Post by abhiroopb on 2008-04-18
Firstly uninstall everything that you tried. If you haven't made a lot of changes perhaps even reformat (but this is last resort).

Then go to system>administration>restricted drivers managers. If the graphics card is still ticked untick and restart, and then tick it again (basically uninstall and re-install).

After you have it USUALLY it should detect the resolution automatically.

If not do the following:

trying opening a terminal and typing 

```

nvidia-settings

```

there should be options here to change your resolution.

I personalyl don't recommend using the screen and graphics tool as it hindered more than helped me!

---

