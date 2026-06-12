---
title: "No selection for 1024 x 600 (16:9) screen resolution"
date: 2011-12-23
forum: Asus Ubuntu Support (CLOSED)
---

### Post by marco_polo99 on 2011-12-23
I've got an Asus 1015PE and recently upgraded to Natty (although my problem began before the upgrade).  Currently I have only 3 monitor resolutions to choose from and they are all 4:3, but my screen is 1024 x 600 (16:9).  I'm running on 1024:768 which puts the bottom the window off the bottom of the screen so any commands or search bars at the bottom are not visible unless the window is partially minimized.

I used xrandr to create a new 1024x600 mode, but when I apply it the whole thing is shifted down and I have a  bar at the top of the screen.  I feel like I'm close, but something is missing.  Any help?

---

### Post by donc786 on 2011-12-30
Bump, same prob here.

---

### Post by adrien214 on 2012-01-18
are you running unity? what happens when using unity2D ?

---

### Post by tigehunter on 2012-02-14
I have the same problem as described by MarcoPolo. I couldn't have said it better.

Any news?

Thanks

---

### Post by roger_1960 on 2012-02-19
Hi

I suggest you try an 11.10 live USB stick and see if that solves it.  I get a 1024x600 option using Unity 3D on an Asus 1011PX (which is a very similar spec I believe)

---

### Post by tigehunter on 2012-02-22
Thanks for the reply Roger!
I've tried running with the live USB key and no improvement. Out of curiosity, I formatted and did a clean re-install and that also did not show any improvement. Still no 16:9 screen resolutions.

The 16:9 resolutions are not only unavailable once Ubuntu has loaded but also right from when power has been pressed. Even in the bios, part of it is off the bottom of the screen. The strangest thing is that every once in a while (maybe once out of 15 boots), the 1024 x 600 resolution is available. But then it is gone again the next time the computer is turned on.

I`ve noticed that some windows users have the same problem with this model of EEEPC (mine's actually a 1015PEM): [http://forum.eeeuser.com/index.php?/topic/84114-1015-pem-windows-7-screen-resolution-problem/](http://forum.eeeuser.com/index.php?/topic/84114-1015-pem-windows-7-screen-resolution-problem/)

And their solution was to obtain a different version of the proprietary graphics driver. That, however, is not an option for us, it would seem (or so I've been able to find out). Unless if someone comes up with a real game-changing solution, I think I'm going to tough it out until 12.04 comes out.

But by all means, I'd love to hear your suggestions as this problem is really annoying!

---

### Post by dbergeba on 2012-03-02
I have exactly the same problem. I have already tried to modify xorg configuration, using xrandr as described elsewhere, but nothing worked out. 
  I guess this is something related to kernel and eeepc screen, but no idea how to solve it. I also guess that this issue will be solved in 12.x.

Please, if someone finds a solution, please post it.


Thanks

---

### Post by tigehunter on 2012-05-04
I installed 12.04 a few days ago on the same 1015 PEM described above. It's very nice. But my problem persists: The computer thinks its screen is 1024x768 (not just ubuntu, but the bios and all of the various welcome screens as well) instead of 1024x600. The result is that everything extends off the bottom of the screen (kind of like if the virtual desktop were bigger than the screen) and resizing in xrandr produces a screen of the right size but that starts from the bottom of the old "screen", meaning the top 168 pixels are cut off at the top and everything is still hanging below sight as before.

I tried updating the BIOS on the off-chance that some newer firmware may have any effect and also updated my display drivers from the x-updates ppa ([https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)). Still no effect.

Please let me know what information you need to help me solve this as it is getting quite frustrating!

---

### Post by tigehunter on 2012-09-06
Hello! Has there been any new developments on this subject?

No new updates have fixed anything :(

Conversely, is there somewhere more appropriate that I should post this instead?

---

