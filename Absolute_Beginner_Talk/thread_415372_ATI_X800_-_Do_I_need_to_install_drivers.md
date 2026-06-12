---
title: "ATI X800 - Do I need to install drivers?"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by ljcasey on 2007-04-20
Hi, 
Just installed fiesty, great. 
Do I need to install ATI drivers? Everything is working ok (even the effects). But im guessing only the propriety drivers will be installed?
Will I get better performance if  I download the proper drivers?

---

### Post by kittyhawk63 on 2007-04-20
> **ljcasey said:**
> Hi, 
Just installed fiesty, great. 
Do I need to install ATI drivers? Everything is working ok (even the effects). But im guessing only the propriety drivers will be installed?
Will I get better performance if  I download the proper drivers?

Try it out, If you're happy with it, leave it alone. It is hard to get ATI cards to work. You can go to ati.com and check out to see if there is a newer driver for your card. I highly recommend that you leave it as it is.
kh

---

### Post by ljcasey on 2007-04-20
It is fine now, but I was hoping to be able to play some games, (WoW) but Im guessing my FPS will suffer with the propriety drivers... Oh well I well cross that bridge when it comes to it. 

Tried installing the ATI drivers from ati.com but it has a problem with the version of X for some reason... :confused:

---

### Post by kittyhawk63 on 2007-04-20
> **ljcasey said:**
> It is fine now, but I was hoping to be able to play some games, (WoW) but Im guessing my FPS will suffer with the propriety drivers... Oh well I well cross that bridge when it comes to it. 

Tried installing the ATI drivers from ati.com but it has a problem with the version of X for some reason... :confused:

I would go a couple of days, up to a week, and wait until all the geeks with ATI cards do their tweaking and then post a request with your issue.
kh

---

### Post by Seisen on 2007-04-20
If it isn't broke don't fix it.

---

### Post by kittyhawk63 on 2007-04-20
> **Seisen said:**
> If it isn't broke don't fix it.

That's my motto...unless I just gotta look inside. lol

---

### Post by commonplace on 2007-04-20
First, you have your terms mixed up. The proprietary drivers are the ones from ATI/AMD. What comes with Ubuntu isn't the proprietary drivers -- for legal reasons.

Second, if everything is working fine, as others have said, by all means, leave it! :) ATI cards are a major, major pain in the butt to get working, so if yours is already working, I'd be thankful and just leave it alone. (Trust me, I have an ATI card, and it's no fun.)

Lastly, yes, the proprietary drivers from ATI's web site won't work in Feisty yet. Feisty came with X.Org 7.2. ATI's drivers only support up to 7.1. I'm sure they'll update their drivers soon-ish.

/Kevin

---

### Post by Comzee on 2007-04-20
One of the down sides to ATI is their horrible Linux driver support.
But the thing is, Ubuntu doesn't play games like CSS or BF2. So why do you need super charged drivers?

---

### Post by kittyhawk63 on 2007-04-20
Do a backup before you start tweaking your driver. Here is the terminal command. To avoid typing error copy/paste the first line into terminal.

sudo cp -i /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

To restore it when booting type in the safe boot mode:

sudo cp -i /etc/X11/xorg.conf.bak /etc/X11.xorg.conf

I would write this down somewhere and keep it handy.
kh

---

