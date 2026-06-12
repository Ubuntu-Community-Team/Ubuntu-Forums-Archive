---
title: "Ubuntu Breezy Badger and Dell 4600"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by outdoorsman on 2006-06-02
I have tried installing Ubuntu on my Dell 4600 a number of times, both live cd and full install, and every time it ends with a colorful jumbled screen.  I hear sounds and because I'm familiar with Ubuntu a little bit (I was able to install it just fine on my Thinkpad T21) when I enter my password and username (even though I can't see it because of the wierd screen) I hear sounds like it's starting up, the screen just stays wierd.  When I install it, it I don't get any failed messages and it looks like everthing goes fine, it's just when I try to start the OS itself.  I'm also dual booting with windows xp home edition. I was going to try to install kubuntu, but I'm not very confident this will be any different...any help would be really appreciated.
thanks in advance,
Justin

---

### Post by adam.tropics on 2006-06-02
It sounds like the wrong video driver is loading.
Press <ctrl><alt> F2, and see if you go to console, if so log in, and run

```
sudo dpkg-reconfigure xserver-xorg
```

and select the correct driver for your video card. If you're not sure, go for vesa temporarily, as this will at least get you in the graphical environment from where you can correct things in a more familiar setting!

---

### Post by outdoorsman on 2006-06-02
looks like you put me on the right track adam.tropics, but I'm still having trouble.  When I do what you said, I get a message saying <server-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/xll/xorg.conf.200606020127
from there it just stops and I'm not sure what to do, so I ctrl-alt-del and restart ubuntu all together.  When it tries to start up, now the screen is just blank with sound........got any other tips?

---

### Post by adam.tropics on 2006-06-02
when you get to
> 
<server-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/xll/xorg.conf.200606020127

does it have an input option, ie yes/no:

press enter. The proper conclusion of 'dpkg-reconfigure xserver-xorg' should return you to the normal user prompt.

---

### Post by outdoorsman on 2006-06-02
whe it gives me the lines I wrote in my last post, it then displays justin@justinb:~$ with a blinking _

I can't just press enter or it shows the same thing again, I can't log in from there or I get an error, and when I type yes, it displays a continuing list of "y's" over and over again.  I'm really lost.  I am using a Nvidia GeForce4 MX 440 with AGP8X in case that helps.  I just did "vesa" like you said because I wasn't sure what else to pick from that list....

---

### Post by adam.tropics on 2006-06-02
yes, that's all good so far then. Try

startx <enter>

---

### Post by adam.tropics on 2006-06-02
Sorry, forgot, you moved to a different screen,

<ctrl><alt> F7 should return you to the screen that wouldn't previously startx,
then,

<ctrl><alt><del>

If that or a reboot doesn't do it for you, then I would suggest you still have the wrong driver. Don't know your hardware so can't really be sure.

---

### Post by outdoorsman on 2006-06-03
Thanks for all the help adam.tropics...I apreciate it.  I found a driver that I think might fix it, but I'm not sure how I can install it so linux will recognise it (I downloaded it on the partition with windows in it).  If I can't see anything in the linux partition, is there any way to install the driver?....thanks again

---

### Post by outdoorsman on 2006-06-03
WOOOHOOOO....I'm now typing this in Ubuntu...I finally got it.  I just wanted to write out what I did to finally get it to work.  

sudo apt-get install nvidia-settings nvidia-glx linux-restricted-modules-686
sudo nvidia-glx-config enable

than I restarted the computer and it works
thanks for the help

---

