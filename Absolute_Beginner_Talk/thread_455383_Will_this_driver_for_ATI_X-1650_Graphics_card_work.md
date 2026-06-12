---
title: "Will this driver for ATI X-1650 Graphics card work??"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-05-26
Hi,
 I've tried twice to enable the (restricted) driver for my ATI X-1650 graphics card  and have lost access to Ubuntu both times. 

I've searched the AMD/ATI site and they list a Linux driver for the ati card with these versions of linux:

Automated installer and Display Drivers for XFree86 4.3 and X.Org 6.7, 6.8, 6.9, 7.0, 7.1 

Does Ubuntu Feisty or Ubunto Studio call in any of these versions? 
pardon me if it's a noobie question. I appreciate any help anyone could offer.

Many Thanks, Frank

---

### Post by starcraft.man on 2007-05-26
Frankly (:p) ATI has kinda snubbed the Open Source place (whether its intentional or not is irrelevant) they just haven't done much to make their drivers for us run any better (where as my nvidia drivers purr) I am saddened by that, they are a Canadian (were) company and well, makes me feel bad.

I'm pretty sure Feisty uses 7.2, but it should still be able to install and work, I know other people have gotten X cards working in Feisty. 

Did you try [Envy?]("http://www.albertomilone.com/nvidia_scripts1.html") It usually works, I think even X cards. Install the deb, then select it from Applications > System Tools > Envy and click automatically install ATI. This should do it and answer yes to prompts and it will reconfigure your xorg.

Other than that, I can only say look at the x guide for feisty that is stickied at the top of the beginner section (above the main threads), I don't know anymore. Send a letter to ATI if this has frustrated you a lot, then we can get them to do something about it, I know I won't buy anymore ATI cards (dad has one, but he uses XP so he doesn't mind).

---

