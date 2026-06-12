---
title: "AAAAA! Wine!"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by nikoPSK on 2007-09-20
wine won't emulate a few progrmas of mine that I used for widows... PVR software, peggle (great game btw). I am looking for a fix/ alternative.

I have 512 RAM
GeForce 5200 (envy updated):KS

---

### Post by aktiwers on 2007-09-20
For PVR try MythTV.
```

sudo apt-get install mythtv
```

---

### Post by Daveth on 2007-09-21
so why do you think Peggle does not run in Wine?

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=8257&iTestingId=12844](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8257&iTestingId=12844)

given both gold and platinum staus there.

---

### Post by nikoPSK on 2007-09-21
But I don't get video/ picture... Mabye I could disable compiz... :confused: I have a decent graphics card: nvidia geforce5200 and 512 RAM

---

### Post by ryanVickers on 2007-09-21
yeah, disabling a window manager lie that is always a good idea :)

but, I don't think that will help, however - that site lists everything as perfect even when it won't work at all!  They must have done some really strange things to make them all work, and so I don't doubt it's a great product, but for the average user, don't expect 10% of those listed apps to work!!!

---

### Post by nikoPSK on 2007-09-21
Synaptic package manager stopped working now!!! my freind pressed like cntrl something backspace and now it's all screwed!

---

### Post by ryanVickers on 2007-09-21
was it control _**alt**_ backspace by any chance :)

---

### Post by nikoPSK on 2007-09-22
yes. It logged me out. Because the earlier time he had been at my house I had showed him the cube (compiz is dooooown so I was using metacity). It logged me out and spm (synaptic...) went down on me. Apparently I need to re-install wine doors but i keep getting error messages in Gdebi...:confused:

---

### Post by sailor2001 on 2007-09-22
ctrl/alt/backspace only resets the session....at the bottom left is 'options' to set the sesstion like you want it.  From there you have to put in username & password

---

### Post by skymera on 2007-09-22
a 5200?

that card is wayy dated now.

the 9800 is out soon :)

maybe upgrade, i did and everything works fine :D

---

### Post by kish on 2007-09-22
Try running wine from the terminal.

```
 wine ~/.wine/drive_c/Program\ Files/the_game
```

so on..
Figure out the error.

---

### Post by nikoPSK on 2007-09-22
good 'nuff for me:lolflag:

Anyways we're getting a new iMac and I'm going to put gutsy on it. Both come out in October (leopard) so I can wait 'till then.

Starcraft2 only like 3 weeks away!!!! OMG!!!

---

### Post by FuturePilot on 2007-09-22
Were you in the middle of installing something when X got restarted? You might need to run
```
sudo dpkg-reconfigure -a
```

---

### Post by nikoPSK on 2007-09-22
wine-doors has been and issue for me lately too... I'm trying to install half-life 2 and it freezez on the executing installer part.:confused:

---

### Post by nikoPSK on 2007-09-22
And I can't seem to un-install anything...
:confused:

---

### Post by nikoPSK on 2007-09-25
Anyways I will use this thread for all my wine related problems:

When I'm running apps in wine (starcraft, peggle deluxe, Peggle extreme) Sometimes the sound quits. And ostly just for the program but sometimes for my whole system. It takes a few times peeping around in my integrated peripherals (I press del at startup) and seeing if onboard is enabled. And a few re-starts. That annoys me. 

Second. Peggle's 3d acceleration won't work. Apparently my computer isn't up to standards. It worked in Xp and I'm wondering If wine isn't telling peggle something or there is a work-around to this.

:confused:

---

### Post by nikoPSK on 2007-09-25
(I have to use on-board because ubuntu isn't finding my sound blaster audigy)

:confused:

---

### Post by ryanVickers on 2007-09-25
> **nikoPSK said:**
> ...

Second. Peggle's 3d acceleration won't work. Apparently my computer isn't up to standards. It worked in Xp and I'm wondering If wine isn't telling peggle something or there is a work-around to this.

:confused:


Yeah, 3D acceleration doesn't seem to work at all, and some programs won't even start!  Interestingly enough, pontifex works fine, and it seems actually *better* than on "real" windows! :p

---

### Post by nikoPSK on 2007-09-25
hmmmm... Have any solution on the sound blaster drivers? They're supposed to be integrated...:confused:

---

