---
title: "Macbookpro 8,1"
date: 2012-04-23
forum: Apple Hardware Users
---

### Post by watgrad on 2012-04-23
Hello,
Searched the forums but not finding too much info on this.

I was wondering if anyone has been experimenting with Ubuntu 12.04 on macbookpro?  I had great difficulty getting 11.10 to work on my MBP8,1

It runs now - with the update to 12.04 being released soon, I wondered if anyone had tried the pre-release versions on MBPs?

The community page ([https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)) only shows results for MBP5,3 ...

---

### Post by gennatolls on 2012-04-23
EDIT: I forgot apple switched to AMD graphics, that could cause some trouble. I have Nvidia graphics.

It runs very well, it has a lot of bug fixes for mac. I have been using it since alpha 1. I have a mid 2010 macbok pro (Im to lazy to figure out which one that is as far as 8.1 or what have you). I haven't used it in a few days but it has worked flawlessly until the last update i did. The update broke something with the touchpad. When I wake it from suspending the touchpad doesn't correctly work, you have to push the pad down like a button press then hold it to move the mouse. This is fixed by logging out and back in. I've only noticed this from waking from suspend. It could be patched out by now. I would give it a go, it was much better than 11.10 on mac.

Good luck,

---

### Post by watgrad on 2012-05-02
I post this here in case other mac users are thinking of installing 12.04...

So I took the leap...I first installed 12.04 via the update path from 11.10 to 12.04.  I found the system to be unstable and had to tinker quite a bit to get everything working.  Even so, there were sporadic crashes. 
 
So I decided to start over and do a clean install - this went much more smoothly.  The only tinkering I had to do was add the mpodroid/mactel ppa, install b43-fwcutter and firmware-b43-installer to get WiFi working.

System seems more stable, however compiz does occasionally crash still. - perhaps a problem with display drivers?

Battery life is much, much better than with 11.10.

---

### Post by gennatolls on 2012-05-02
> **watgrad said:**
> I post this here in case other mac users are thinking of installing 12.04...

So I took the leap...I first installed 12.04 via the update path from 11.10 to 12.04.  I found the system to be unstable and had to tinker quite a bit to get everything working.  Even so, there were sporadic crashes. 
 
So I decided to start over and do a clean install - this went much more smoothly.  The only tinkering I had to do was add the mpodroid/mactel ppa, install b43-fwcutter and firmware-b43-installer to get WiFi working.

System seems more stable, however compiz does occasionally crash still. - perhaps a problem with display drivers?

Battery life is much, much better than with 11.10.
Did your Audio Out led stay on (red led inside audio jack) ? I had to manually set mine off with amixer

---

### Post by watgrad on 2012-05-03
> **gennatolls said:**
> Did your Audio Out led stay on (red led inside audio jack) ? I had to manually set mine off with amixer

It is off - not because of anything that I had to tweak.  Tested it and all is working.  I did have several crashes today - software center and x server ... not sure why, and don't know enough to sort it out quickly.  Will have to look into it on the weekend.

---

### Post by gennatolls on 2012-05-04
If you don't have jupiter installed, I have found it works very good for my Macbook as far as battery life and keeping the heat down.

---

### Post by mode7 on 2012-05-04
Don't know about battery life.. usually keep my Macbook plugged in.

12.04 is a much smoother setup experience than 11.10. Partly because the disc can boot into a live setup without using a usb drive, and because you no longer must use gdisk from OS X to fix the hybrid MBR after each setup.

It's a shame that the b43 firmware is still not included!
At least compat-wireless no longer needs to be installed.

My optical out light has been on as well. I don't recall it doing that in 11.10. As said, you can mute it with amixer and whatnot, and the light will turn off. It is the SPDIF/IEC958 line.

---

### Post by gennatolls on 2012-05-04
I tried setting a script as a start up program to disable it upon boot. It shows up on the start up applications list, and I have the proper permissions but fails to execute. Any Ideas? Its just as following:
```
 #!/bin/bash
amixer set IEC958 off

```I could be missing something, I haven't written shell scripts in quite a while.

---

