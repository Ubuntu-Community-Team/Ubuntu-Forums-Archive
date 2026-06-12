---
title: "[SOLVED] Monitor Power?"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2008-02-24
Monitor Power Management

I'm sorry if this is covered, I checked similar threads but can't seem to find one that's getting at what I want to get at (or I found one, but it was for Kubuntu).

I don't want my monitor to shut off - ever, unless I tell it to by pressing the power button.

I went into the screen saver and it says it regards the computer as idle after 2 hours, there's no way to set it to "never regard computer as idle" - I'm guessing when it goes idle is when it's killing the monitor.  Though like if I'm afk for awhile and come back, I just have a black screen after turning the monitor back on and have to move the mouse around and tap the control key a few times to finally get a prompt to unlock it.

I checked power management and both sliders are set to "never" for turning stuff off.

How do I stop this from powering down the monitor?  i want it to be so when I come back, regardless of how long I've been away, and hit the monitor switch, I still have the screensaver that I selected going - no "power down" crap :|.

TIA

---

### Post by ahaslam on 2008-02-24
Try setting the following in your xorg.conf, under the monitor section:
```
    Option         "DPMS" "false"
```
Also ensure there're no entries resembling the following under server layout:
```
    Option 	   "StandbyTime" "10"
    Option 	   "SuspendTime" "20"
    Option 	   "OffTime" "30" 
```
I run a light system & needed the all of this to enable power management.

---

### Post by Syndacate on 2008-02-25
> **ahaslam said:**
> Try setting the following in your xorg.conf, under the monitor section:
```
    Option         "DPMS" "false"
```
Also ensure there're no entries resembling the following under server layout:
```
    Option 	   "StandbyTime" "10"
    Option 	   "SuspendTime" "20"
    Option 	   "OffTime" "30" 
```
I run a light system & needed the all of this to enable power management.

There was none of that.

I added the first line under the monitor section, I'll see if it works when I leave a lil later and let you know if that helped.

---

### Post by Syndacate on 2008-02-28
Okay, sorry for the long response, I haven't gotten to post due to finals until yesterday.

So I changed the settings in xorg.conf - I made sure there was nothing like that in the server layout section and added that line to the monitor section.

End result, no go, still gets kicked into sleep mode or something.

Or maybe it's not sleep, I don't know what it is, but what I do know is that when if I turn my monitor on after it's been idling for some time and nothing else, the monitor light will blink - or if my laptop is plugged into the analog port it'll switch to my laptop.  This means that it's not receiving a signal from the computer.

So it's obviously cutting the signal somewhere, for some reason, when I lock it it goes into screensaver - and if I come back in 30 minutes the screensaver is still up, yet if it's 4 hours later there will be no signal at all to the monitor.  Black screen regardless if it's on, off, or anywhere in between.

---

### Post by Syndacate on 2008-03-01
Anybody?

---

### Post by hogwartsnigel on 2008-03-05
HI try this from another post..but be warned it worked for the person in that post but disabled my dual monitor set up for me and therefore I went back to by original xcorg file
"You’ll need to edit /etc/X11/xorg.conf and add at the end "

"# To prevent Blank Screen from popping up every 10 minutes
# when xgl is run as a session on display :1,
# when all the power management settings
# you normally find only concerns display :0
Section "ServerFlags"
    Option "blank time" "0"
    Option "standby time" "0"
    Option "suspend time" "0"
    Option "off time" "0"
EndSection "

Hope it helps you...
If anyone IS following this thread I too would appreciate help
Me AMD3200 Nvidia fx5700 dual monitor Mitsubishi DP2070sb and Dell 1905fP
as stated the above xcorg addition enables screensaver display but disable dual monitor, reboot I get a single screen and 1 monitor in standby...anyone help?

---

### Post by Syndacate on 2008-03-21
> **hogwartsnigel said:**
> HI try this from another post..but be warned it worked for the person in that post but disabled my dual monitor set up for me and therefore I went back to by original xcorg file
"You’ll need to edit /etc/X11/xorg.conf and add at the end "

"# To prevent Blank Screen from popping up every 10 minutes
# when xgl is run as a session on display :1,
# when all the power management settings
# you normally find only concerns display :0
Section "ServerFlags"
    Option "blank time" "0"
    Option "standby time" "0"
    Option "suspend time" "0"
    Option "off time" "0"
EndSection "

Hope it helps you...
If anyone IS following this thread I too would appreciate help
Me AMD3200 Nvidia fx5700 dual monitor Mitsubishi DP2070sb and Dell 1905fP
as stated the above xcorg addition enables screensaver display but disable dual monitor, reboot I get a single screen and 1 monitor in standby...anyone help?

Thx, sorry for the long response - I just gave up - I was all ready to add this thing and I was just like "screw it - I don't care anymore" - it hasn't bothered me since I stopped putting up screensavers, so whatever.

Sorry for the waste of time I guess :(

Thanks, anyways.

---

