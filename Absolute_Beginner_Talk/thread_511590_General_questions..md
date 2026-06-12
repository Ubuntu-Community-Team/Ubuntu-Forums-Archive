---
title: "General questions."
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by KevinBristol on 2007-07-28
Hey, I just installed Kubuntu Fiesty Fawn on my laptop. I had tried it before, but a couple things weren't working, so I decided to try again when I had the time.

So.. now that I have the time, there a couple of things I would like to do:

[LIST=1]
[*]Change the screen resolution.
[*]Setup the mouse; it's a touchpad.
[*]Get my wireless working.
[*]My audio isn't working either.
[*]Get access to a network drive on another computer.
[/LIST]

I'll give you some more information on each..

[INDENT]1. Right now it's set at the highest choice there is( 1024 x 768 ), but I would like to set it at a higher resolution, I can't remember what it was at in Windows XP, but my graphics device is:  **Intel 82852/855GM Integrated Graphics Device.**

2. It's acting fine, but whenever I tap the pad it left-clicks, which was a setting in Windows XP, but I could enable/disable it. My touchpad is a:  **Synaptics Touchpad.**

3. In the network connections settings, it shows that I have a Wireless Network Device, which is disabled. If I try to enable it, it just goes back to disable after a couple seconds. I can get online using the ethernet cord from my router. I have a:  **Broadcom BCM4306 Wireless LAN Controller.**

4. I have a: **Intel 82801DB/DBL/DBM Audio Controller.**

5. The drive is on a PC on my network, which runs Windows XP.[/INDENT]

I'm sure all of these have been answered before, but I searched and didn't find anything that I could really understand. I posted this in the Beginner Talk forum because, I am just a beginner, so I don't know a lot of this OS yet. So, if there are links to them, just post 'em here and I'll take a look.

Thanks for reading,

Kevin Bristol.

---

### Post by KyleBrandt on 2007-07-28
1:  You are going to have to edit you xorg.conf which is in /etc/X11/xorg.conf , You can type "sudo nano  /etc/X11/xorg.conf" Just find the numbers that look like resolutions and edit them:-)  You should probably back it up first.  "Sudo cp xorg.conf xorgbackup.conf"  If you run into trouble, you can hit ctrl-alt-backspace to restart the X server, or Ctrl-Alt-F2 to get to a command line and restore the xorg file.

3.  Two options for that wireless card, bcm43xx driver or the ndis wrapper.  I use the bcm43xx, for me it worked right of the box after installing bcm43xx-fwcutter.  I think I had to run some sort of command like "bcm43xx-fwcutter bcmwl5.sys" and then it worked for me.  Sorry I can't be of too much help on this, there are a ton of threads on it.

---

### Post by tomcheng76 on 2007-07-28
2: Read [here]("http://pearle.ca/archives/9")

---

### Post by zanglang on 2007-07-28
Not sure about 3 and 4 because I'm not a Kubuntu user, but let's see,

1. Try installing the package '915resolution', and then reconfigure your X server settings. For more details see here:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

2. Aren't Synaptics touchpads always tap to click...? Did you want to disable that behaviour and just use the buttons? Try installing 'ksynaptics' or 'qsynaptics', that should give you some options to play with.

5. You'll need to set up Samba. Follow this guide:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by KevinBristol on 2007-07-28
> **zanglang said:**
> Not sure about 3 and 4 because I'm not a Kubuntu user, but let's see,

1. Try installing the package '915resolution', and then reconfigure your X server settings. For more details see here:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

2. Aren't Synaptics touchpads always tap to click...? Did you want to disable that behaviour and just use the buttons? Try installing 'ksynaptics' or 'qsynaptics', that should give you some options to play with.


1: Followed that guide, worked perfectly, now using a nicer and clearer resolution.

2: I updated everything through Adept Manager, then installed 'ksynaptics', placed the code specified in tomcheng76 link. It now allows me to disable it.

Haven't tried number 5 yet, I'll leave that for tomorrow.. thanks for the help everyone!

If anyone could lead me to a guide for BCM43xx Broadcom Wireless Drivers, it would be greatly apperciated, and something to fix my audio device :) 

Thank you.

---

