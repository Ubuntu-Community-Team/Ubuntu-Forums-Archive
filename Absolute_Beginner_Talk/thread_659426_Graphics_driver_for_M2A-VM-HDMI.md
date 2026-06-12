---
title: "Graphics driver for M2A-VM-HDMI"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by JayKav on 2008-01-05
I appreciate there has been a lot of discussion on this but having just spent a straight 15 hours trying to get this to work I'm hoping someone will have some new info.

System: Asus M2A-VM-HDMI with AMD X2 64 bit, X1250 integrated ATI graphics.

What I have done:


Fresh install of Ubuntu 7.10 64 bit
Update
Enable all repositories
Then either:

1. Download and install  ati-driver-installer-8.443.1-x86.x86_64.run

Result: Screen goes to a lower resolution (800x600). Catalyst control centre appears on menu but does nothing (won't start)

2. Install using the restricted drivers manager.

Result: Again a lower resolution display. 

3. [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Low resolution display again. I got a message saying I was using a restricted driver. 
fglrxinfo gives:

Xlib: extension "GLX" missing on display ":0.0"
...

(I had to manually modify the xorg.conf file as the aticonfig command caused a seg fault.)


I've tried a few other things as well and using a combination of methods I once got the full resolution back but no tv-out. 

I'm afraid I'm at the point of going back to XP but if there's anyone who has actually got this to work I'd be grateful if they could give me the complete recipe.

Btw, I have the new bios in the MB. HDMI is enabled in the bios.

Thanks,

Jay

---

### Post by gn2 on 2008-01-05
As far as I know the restricted driver manager only uses the version of driver that's in the repository, which may not be the most recent.

You could try using Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) which will install the most recent driver.

Also could be worth having a look or posting in the 64-bit Forum: [http://ubuntuforums.org/forumdisplay.php?f=134](http://ubuntuforums.org/forumdisplay.php?f=134)

---

### Post by JayKav on 2008-01-06
> **gn2 said:**
> As far as I know the restricted driver manager only uses the version of driver that's in the repository, which may not be the most recent.

You could try using Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) which will install the most recent driver.

Also could be worth having a look or posting in the 64-bit Forum: [http://ubuntuforums.org/forumdisplay.php?f=134](http://ubuntuforums.org/forumdisplay.php?f=134)


Thanks. Envy at least installed something. I have the full resolution back but nothing else. All the aticonfig commands give an error 'bad file descriptor' for xorg.conf. I can't see any other method for changing the graphics modes (no catalyst cc for example).

---

### Post by gn2 on 2008-01-06
> **JayKav said:**
> any other method for changing the graphics modes

What exactly do you want to change?

---

### Post by JayKav on 2008-01-06
> **gn2 said:**
> What exactly do you want to change?

Firstly get the screen resolution back to 1024x768 so I can see everything (e.g. trying to install catalyst with 800x600 is nearly impossible as you can't see all the buttons so you have to guess how many times to press tab before pressing enter. Really, just how complicated does this have to be?).

Secondly, to get TVout to work. The command line aticonfig just gives errors due to xorg.conf being renamed to something else. No idea why this is happening.

---

### Post by zasf on 2008-01-06
> **JayKav said:**
> Firstly get the screen resolution back to 1024x768 so I can see everything (e.g. trying to install catalyst with 800x600 is nearly impossible as you can't see all the buttons so you have to guess how many times to press tab before pressing enter. Really, just how complicated does this have to be?).

Secondly, to get TVout to work. The command line aticonfig just gives errors due to xorg.conf being renamed to something else. No idea why this is happening.

make sure you are running fglrx driver with fglrxinfo, then you can use 'sudo dpkg-reconfigure xserver-xorg' from the terminal to reconfigure xorg. It's a window like text interface, if you don't know an answer just press 'enter' so that the default value is taken. Make sure you enable the resolutions you want.

---

### Post by JayKav on 2008-01-06
> **zasf said:**
> make sure you are running fglrx driver with fglrxinfo, then you can use 'sudo dpkg-reconfigure xserver-xorg' from the terminal to reconfigure xorg. It's a window like text interface, if you don't know an answer just press 'enter' so that the default value is taken. Make sure you enable the resolutions you want.

fglrxinfo looks ok. Gives ATi, X1250, OpenGL 2.1.7170

reconfiguring seems to work ok although I was surprised it didn't recognize the video card. However, aticonfig still gives the same error (bad file descriptor /etc/X11/xorg.conf)

---

### Post by JayKav on 2008-01-06
> **JayKav said:**
> fglrxinfo looks ok. Gives ATi, X1250, OpenGL 2.1.7170

reconfiguring seems to work ok although I was surprised it didn't recognize the video card. However, aticonfig still gives the same error (bad file descriptor /etc/X11/xorg.conf)

Oops, forgot the 'sudo'. I'll try again.

---

### Post by zasf on 2008-01-06
> **JayKav said:**
> fglrxinfo looks ok. Gives ATi, X1250, OpenGL 2.1.7170

reconfiguring seems to work ok although I was surprised it didn't recognize the video card. However, aticonfig still gives the same error (bad file descriptor /etc/X11/xorg.conf)

what do you need aticonfig for?

---

### Post by JayKav on 2008-01-06
ok so aticonfig now doesn't give any errors but I can't enable the tvout. Looking at other posts this is where everyone else seems to have got to as well. Do I assume tvout is a windows-only feature?

---

### Post by zasf on 2008-01-06
I never use it, so I actually don't know for sure.

Still I remember having read on [phoronix]("http://www.phoronix.com/scan.php?page=news_item&px=NjI2NQ"), that this is an upcoming feature in ati open source driver. I would check fglrx open issues and read some more phoronix articles to get the answer.

---

### Post by JayKav on 2008-01-06
> **zasf said:**
> what do you need aticonfig for?

To enable TVout. The aticonfig seems to run ok although it always says the changes don't apply to the current session. Now when I run mplayer it says the video output device isn't accessible.

Anyway, thanks for your help. At least I made some progress but I think the conclusion is that I have to go back to XP for a while yet.

---

