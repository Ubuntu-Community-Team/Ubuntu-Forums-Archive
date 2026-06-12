---
title: "Regarding DISPLAY command"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by devosion on 2007-12-14
This is something that has been bugging me since I began running Guild Wars with an ATI card with fglrx driver, and glx. And im hoping somebody can perhaps give me some detailed information on why this works the way it does and if there is a way around this.

So whenever I am running Guild Wars run through I run the following command.

> DISPLAY=:0 WINDEBUG=-all wine "/home/devosion/.wine/drive_c/Program Files/Guild Wars/Gw.exe" -dsound -windowed


Now the reason i am running it like this is because I read somewhere that fglrx and glx operate on different 'displays'. So in order for certain graphical capabilities that use a program I would need to switch the display from that which glx uses, in this case 1.

The reason I know this is the case is because whenever I run the command without DISPLAY=:0 I dont get any textures in Guild Wars, and the framerate is slowed substantially.

The problem is though when I run it in windowed mode I lose my bar at the top of the window in display .0, but when it is in .1 it is till there. This can be problematic when im trying to get around windows because no matter which workspace I switch to the Guild Wars window follows.

So my question is why does fglrx and glx operate on different displays? Is there a way around this with my ATI x1950 radeon? And if there is than can I do it without using the abysmal aticonfig 'program'?

---

