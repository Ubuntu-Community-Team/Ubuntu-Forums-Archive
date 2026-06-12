---
title: "Ubuntu 11.0.4 Magic Mouse recognized but wont connect"
date: 2011-11-25
forum: Apple Hardware Users
---

### Post by rlinsurf on 2011-11-25
I first went to the Bluetooth menu, selected Setup new device, it found my mouse, and I went to connect. It then asked for a PIN. I had no idea what it was asking, so I clicked cancel. Then I noticed there were settings for device type and PIN, unfortunately this time, no matter what I did, it wouldn't display the mouse under devices. I then  went under the Bluetooth menu again, and saw that the mouse was listed, so I selected Connect. It again asked for the PIN. This time, I entered "0000" as was listed for Mice under the PIN settings in the Bluetooth setup window. It didn't work. And now it wont connect, recognize the mouse as a new device, or let me do anything with it.

Sorry, that should be Ubuntu 11.10.

Help!

---

### Post by rlinsurf on 2011-11-25
Well, it's sort of solved. I went into System Settings-->Bluetooth, eliminated the mouse, and then set it up again, using the Device type-->Input and PIN 0000. This time, it connected and the Bluetooth settings said it was fine. I then had to hold down the mouse to actually get it to connect, and then entered the PIN. Then it started working.

Unfortunately, the driver is so fast, it's almost unusable. It speeds around so quickly you barely know where it's going to be at a given moment. I went into System Settings-->Mouse and Touchpad and saw that the Acceleration and Sensitivity were already set to the lowest settings.

So now what?

PS. It also looks like a right-click is pasting in the contents of clipboard whenever I click. Is there some way to turn that off?

---

### Post by RagnarDa on 2012-04-13
Is there a fix for the sensitivity issue? I'm running ubuntu 12 beta and it's still there. Also, the fixes thats out there doesnt work, seems to be for older Ubuntu's. I've tried changing in xinput and modprobe but nothing works.

---

### Post by tom.davidson58 on 2012-04-16
I just had the exact same issue with my magic mouse.  The solution is to turn up the sensitivity.  I know that doesn't make much sense but when I first paired my mouse to my Ubuntu 11.10 server box the mouse was jumping all over the place so I played with the settings and turning up the sensitivity seems to be what did the trick.  My magic mouse works perfectly fine.  As for the issue with your right click, I am unable to reproduce that on my machine so I'm not sure what the fix would be there.

---

### Post by RagnarDa on 2012-04-19
No, turning sensitivity up did'nt work for me but this command did:
```
xinput --set-prop "Mouseemu virtual mouse" "Device Accel Constant Deceleration" 2.5
```where 2.5 is the sensitivity setting you want (higher = slower mouse).

To make the change on every login:
```
gedit ~/.xsessionrc
```
and add the xinput - line and save the file.

I am so glad that I finally figured this one out! I'm running Xubuntu Precise.

---

### Post by RagnarDa on 2012-04-20
> **rlinsurf said:**
> PS. It also looks like a right-click is pasting in the contents of clipboard whenever I click. Is there some way to turn that off?
I think the click is interpreted as a middle-button click. Try moving your finger a little more to the right or maybe try disable middle-button paste functionality with
```
xmodmap -e "pointer = 1 9 3 4 5 6 7 8 2"
```

---

### Post by RagnarDa on 2012-04-20
Btw, anyone knows how to enable horizontal scrolling on the magic mouse, if that's possible?

---

