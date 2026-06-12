---
title: "Problems with new mac mini (March 2009) and lirc"
date: 2009-03-14
forum: Apple Hardware Users
---

### Post by makkus on 2009-03-14
Hi guys.

Bought one of these new mac minis recently, blew away Mac OS (of course) and installed Ubuntu Intrepid. 

Most of the stuff worked out of the box, the only problem I'm having is getting the Apple Remote Control (from my old Macbook pro -- they don't ship remotes with the mac mini anymore) to work properly.

Installed lirc and used the mac-mini driver. lirc actually gets all the button presses right. The only thing is: it doesn't recognize when I press the same button several times in a row. In that case it thinks it was *one* long button press. For example, if I press the Play button a few times (quickly), irw it gives me something like this, which is the same as if I would have pressed the button once, just longer:

[FONT="Courier New"]0000000087ee8104 00 PLAY Apple_A1156
0000000087ee8104 01 PLAY Apple_A1156
0000000087ee8104 02 PLAY Apple_A1156
0000000087ee8104 03 PLAY Apple_A1156
0000000087ee8104 04 PLAY Apple_A1156
0000000087ee8104 05 PLAY Apple_A1156
0000000087ee8104 06 PLAY Apple_A1156[/FONT]

If I wait about 1 second in between button presses, the counting starts from 00 again, as it should be.
Also tried to create my own lircd.conf using irrecord. But when I come to the last part where you are supposed to press one button repeatetly very fast, it doesn't proceed until I alternate between two buttons, even if I wait longer between keypresses...
I'm not sure what to do about that. Idea, anyone?

Cheers,
Makkus

P.S. the receiver even seemed to recognize my old dvico MCE remote control. It's even able to correctly identify the different buttons. But it shows the same inability to differentiate between one longer press and several shorter ones...

---

### Post by CREEPING DEATH on 2009-03-14
> **makkus said:**
> ... the Apple Remote Control (from my old Macbook pro -- they don't ship remotes with the mac mini anymore...

Not surprising, the Mini long ago ceased to be worth buying.  When they were less than $300 they were great, but at current prices they flat out aren't worth buying.

CD

---

### Post by makkus on 2009-03-14
> **CREEPING DEATH said:**
> Not surprising, the Mini long ago ceased to be worth buying.  When they were less than $300 they were great, but at current prices they flat out aren't worth buying.

CD

I'm quite happy with it, really. For me it is definitely worth it, couldn't find anything else with similar specs (which, I know are not really high-end, but just right for me) and the noise/energy level and of course the size.

Now, if I could just get the remote control working, I would be one entirely happy camper...

---

### Post by cyberdork33 on 2009-03-15
> **makkus said:**
> I'm quite happy with it, really. For me it is definitely worth it, couldn't find anything else with similar specs (which, I know are not really high-end, but just right for me) and the noise/energy level and of course the size.

Now, if I could just get the remote control working, I would be one entirely happy camper...
Alternative:
[http://system76.com/product_info.php?cPath=27&products_id=83](http://system76.com/product_info.php?cPath=27&products_id=83)

There was a post about getting the Apple Remote working correctly recently... Mayb it wil help:
[http://ubuntuforums.org/showthread.php?t=1077778](http://ubuntuforums.org/showthread.php?t=1077778)

---

