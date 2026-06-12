---
title: "[SOLVED] How do I use my phone as a modem on ubuntu."
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by ~~Tito~~ on 2007-07-09
I did it before i installed it by tethering it, but I have to have active sync and install the driver for it from the install cd. I have wine but when I run the cd it doesn't display anything. (I have the Blackjack) If any one successfully did this with their Blackjack please let me know.

(If this is in the improper forum please move it to the right place Mods)

---

### Post by ~~Tito~~ on 2007-07-09
Bump, Bump, Bump

---

### Post by ~~Tito~~ on 2007-07-09
Respond please.

---

### Post by ~~Tito~~ on 2007-07-09
Anyone? I need this so when I'm in the car I can use Linux and the internet.

---

### Post by Vague on 2007-07-09
[http://favias.org/node/45](http://favias.org/node/45)

I know this is the Absolute Beginners forum, but if no one's responding, using the search button and/or Google can often help.  I'm not sure if his method actually works, as I don't have a Blackjack, but I was able to find that.

---

### Post by ~~Tito~~ on 2007-07-09
I use both but usually the things that come up aren't what i want.

---

### Post by dragonwings on 2007-07-09
try seting it up as you would any modem 
but this time from usb i guees thats what your using.

To get my serial port modem to run with a usb adapter
i had to change /dev/ttyS0   to /dev/ttyUSB0

NOTE: USB is in capitals and the 0 is a zero not a letter

i hope this helps you

---

### Post by Vague on 2007-07-09
> **~~Tito~~ said:**
> I use both but usually the things that come up aren't what i want.

Fair enough.  I only said it as that was my second Google result when I searched for it.

More here (from a forum search): [http://www.summet.com/blog/2007/01/27/using-bluetooth-pan-dun-on-samsung-blackjack-with-linux/](http://www.summet.com/blog/2007/01/27/using-bluetooth-pan-dun-on-samsung-blackjack-with-linux/)

---

### Post by ~~Tito~~ on 2007-07-09
How would I connect? By using internet shaing on the phone. (It uses the phone as a modem)?

---

### Post by ~~Tito~~ on 2007-07-09
And how do i start it in ubuntu?

---

### Post by ~~Tito~~ on 2007-07-09
1. Open gnome-ppp as root by either creatinga desktop launcher with "gksudo gnome-ppp" as the command line or typing that into the command line your self.
   2. Enter credentials
         1. [email]ISP@CINGLARGPRS.COM[/email] for the username
         2. CINGULAR1 as the password
         3. *99# as the phone number.
   3. Click setup
         1. Click detect to auto detect your modem (it shoudl find it as ttyACM0)
         2. Click init string andmakemake the following changes:
               1. Init 2 should read: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
               2. Init 3 should read: AT+CGDCONT=1,"IP","isp.cingular"
   4. Close "setup" and click on connect. After a sort pause at "Waiting for prompt" it should connect you.

Can someone make this more detailed on #3-#4 not to detailed.

---

### Post by ~~Tito~~ on 2007-07-09
bump

---

### Post by ~~Tito~~ on 2007-07-11
BUMP 

I want to know because I'm going to Boluxi Mississippi to see my friend box and if my hotel doesnt have a free Ethernet connection then i want to use my phone. I'm not lying he is fighting Roy Jones. I swear on my grandmas ashes.

---

### Post by ~~Tito~~ on 2007-07-11
Someone please help me.

---

### Post by ~~Tito~~ on 2007-07-11
Well help me please!! 
:mad::mad::mad::mad::mad:
I type the command it says but it gives me the password I do it then it just does nothing.

---

### Post by ~~Tito~~ on 2007-07-11
Can you please help me I'm desperate.

---

### Post by Vague on 2007-07-11
Just a suggestion, but you might have more luck asking over in the Networking & Wireless category.  I know there have been a couple threads both there and in the how-tos about using cell phones as modems, so there are at least a few experienced people who might be able to help you out.  Sorry I can't be of any more help, but I don't really have any experience with what you're doing.

---

### Post by ~~Tito~~ on 2007-07-11
I got it to work finally, apparently gnome-ppp wasn't installed as i thought it was, I'm using it now. :KS:KS:KS:KS:KS thanks to the guy who gave me that link.

---

