---
title: "[SOLVED] installing with ati x1900xt monitor out of range"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by shegs on 2007-12-15
ok to start, I am pretty new to linux (hence the beginers forum) but have fiddled with it a few times. and I have avoided a true install for a while because of hardware issues with my x1900xt crossfire setup. I want to keep my crossfire for when I want to use windows for games, but I am having issues when it comes to installing and running linux.

1) live cd wouldnt work. I would get a black screen hang, even in VGA mode. I had to run alternate install. install worked like a charm.

2) install is finished but my default booting would give same black screen. verified vesa drivers through 'safe mode' boot, same issue. 

ran startx from  'safe mode' and got an error with pci(7,0,0,0) *strange since it defaulted me to pci(6,0,0,0). figured it found the wrong card and just neded to be changed to 7. ran startx from 'safe mode'. it booted fine and I was in a version of the gui, but I couldnt logout of root and back in as my user.

3) reset and tried to boot normal to find a slightly different hang. still black screen with a 'frozen' 'hourglass' cursor, and some glitch colors towards the top of the screen (red and green pixels on the top 2 or 3 lines of pixels).

figured the range was probably going out of range. rebooted safe mode to change the resolution and range to something that I know would work 1024x768x60 (max res is 1680x1050x60) saved it and reset to try normal mode again

4) now I get an screen with several un aligned copies of the gui over itself... the only way I could dscribe this is when I had an old crt from in the early 90's and you set the refresh out of range it would think it was alright and then just show several overlapping but unaligned versions of the gui inclufing mouse... 

I have been all over everything and all I want is to be able to install the drivers I heard are out so I can have some hardware support for my cards or card if it will limit me like that. but I seem to always be stuck around here. if it were possible to mount my thumbdrive via the 'safe mode' area I could pull my wifi cards drivers from there and install them and then install the ati drivers from inside of 'safe mode'. but I dont know how to mount my usb while in 'safe mode'.


if someone could help me with any of these problems (more the last few then the first few) I would greatly appreciate it. 

thanks for whatever help you can give

---

### Post by shegs on 2007-12-15
bump

---

### Post by Pumalite on 2007-12-15
Monitor?

---

### Post by Pumalite on 2007-12-15
Did you try 'ati' as driver?

---

### Post by shegs on 2007-12-17
sorry for my delayed response

but i got it working to a degree, I have more issues but this one is resolved.

from my past attempts at getting this to work I know that vesa was the only way out of the box to get any type of screen.

anyway I knew my monitor's range was max 60 but every time I thought I changed it, it seemed to revert back out of range. so I don't know. I ended up just doing a reconfigure and manually putting the range in there and it worked

thanks

---

