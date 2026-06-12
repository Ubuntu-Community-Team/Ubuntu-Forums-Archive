---
title: "WoW - can login, video freezes right away, audio works"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by morweni on 2007-10-14
Afternoon! I have been able to fix loads of different issues with my first real good install of Ubuntu.. but I am having issues with WoW... not that I intend to play it.. but rather to get it to work! Any game to work :)

I am able to login to WoW, however once loading in-game, video completely freezes (gives me perhaps 1 second to move around then freezes). Audio on the other hand, does work, and continues to work after video freezes.....

End up having to force the laptop to reboot, any thoughts?

```

adria@minime:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6334 (8.34.8)

adria@minime:~$ 

```

WoW command line : wine "/home/adria/.wine/drive_c/Program Files/World of Warcraft/Launcher.exe" -opengl

thank you!

---

### Post by tshirtz1013 on 2007-10-16
Did you install all of the updates ? Also I did not have as good of luck running WoW in wine as i did in Cedega. you may want to check out [Cedega 6.0]("http://www.transgaming.com/products/cedega/6.0/")

---

