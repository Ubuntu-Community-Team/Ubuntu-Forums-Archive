---
title: "updating Gnome?"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Cpt.Flint on 2007-03-05
Hello again :) 

My PC is rather old. It's Celeron 2Ghz with 256MB of RAM. I'm running Ubuntu 6.06 Dapper. Yesterday I decided to try KDE and installed it. And I noticed that KDE runs faster than Gnome on my pc. But the point is that I like Gnome more :) 
So what can I do about it? 
The difference is significant. Should I upgrade Gnome to 2.16? Will it run faster? And if so - can I update Gnome without updating Dapper to Edgy? And stuff like that... 

PS. I tried XFCE as well but didn't like at all...

---

### Post by jamyskis on 2007-03-05
> **Cpt.Flint said:**
> Hello again :) 

My PC is rather old. It's Celeron 2Ghz with 256MB of RAM. I'm running Ubuntu 6.06 Dapper. Yesterday I decided to try KDE and installed it. And I noticed that KDE runs faster than Gnome on my pc. But the point is that I like Gnome more :) 
So what can I do about it? 
The difference is significant. Should I upgrade Gnome to 2.16? Will it run faster? And if so - can I update Gnome without updating Dapper to Edgy? And stuff like that... 

PS. I tried XFCE as well but didn't like at all...

Your PC isn't that old :D

If you have a decent graphics card, I've found that installing the AIGLX X.org server extension speeds the desktop up a little if you don't use Beryl with it (as is the accepted norm). If you're looking to upgrade to GNOME 2.16, I'd recommend installing Edgy (which is all-round faster and now a bit more stable) instead of trying to install it manually, which may well create dependency hell for you.

---

### Post by Cpt.Flint on 2007-03-05
Thanks for the answer :) 

and a couple of more questions. What's the safest way to upgrade?

gksu &#8220;update-manager -c &#8221;

This one?
Also - when I update do I need to change the repositories? 

And by the way - my video card is integrated intel card. Should I install AIGLX X.org?

---

### Post by jamyskis on 2007-03-05
> **Cpt.Flint said:**
> Thanks for the answer :) 

and a couple of more questions. What's the safest way to upgrade?

gksu “update-manager -c ”


Safe is relative. update-manager -c is the generally accepted best way to upgrade, although I (and from what I see, others too) had problems with the transition. I eventually just burned all my important stuff onto 2 DVD-RWs, wiped the hard drive and installed Edgy fresh. It's a little more work but I found the system was a lot more stable for it. You should **always, always, always** backup data before doing anything major to your system like this.

> 
Also - when I update do I need to change the repositories? 

If you do an update-manager -c then it'll update the repositories itself. If you have any third party repositories in there, they will be disabled, just in case they don't support the version you're upgrading to. You can reenable them or modify them afterwards from your sources.list or from Synaptic.

> 
And by the way - my video card is integrated intel card. Should I install AIGLX X.org?

Errrrm..oh dear. I know that Intel do have some integrated video chipsets that Linux supports natively, complete with 3D, but I'm not sure if AIGLX does support them. According to **[this link]("http://www.ossgeeks.co.uk/?p=70")** it should work - just stop when you come to "Instaling Beryl", or by all means go on with it if you fancy playing around with Beryl (at own risk, of course! :mrgreen: ).

---

### Post by Cpt.Flint on 2007-03-05
Thanks again for the answers :) 

I'll back up, try to update and see if Gnome works any faster :roll:

---

### Post by Cpt.Flint on 2007-03-06
The updating form Dapper to Edgy is now taking more than 24 hours. The system started downloading a little more than 1 GB of stuff yesterday at around this time. It downloaded the stuff for around six hours and by the time now it is still applying the changes... 

So is this normal? Or something is wrong?

I think that it would have taken less time if I just downloaded the edgy CD and install everything from scratch :confused:

---

### Post by Cpt.Flint on 2007-03-07
OK - the update is finally over. But how can I see if it updated? When I go to "System -> About Ubuntu" it says 6.06. The same is with "About Gnome" - it says 2.14.3...

Is there a command in the terminal or something that I can check the exact version?

---

### Post by Perfect Storm on 2007-03-07
Did you reboot?

---

### Post by Cpt.Flint on 2007-03-07
Yup - I rebooted the system and it's still Dapper...
Any way - I downloaded the Edgy CD and try to upgrade from there. If it fails again - I will reinstall again on blank HDD :) It will be my seventh reinstall within a week but I guess practice makes excellence... :)

---

### Post by Perfect Storm on 2007-03-07
Did you change the word dapper to edgy in your sourcelist (also a good idea to disable un-official sources when you at it).

---

### Post by Cpt.Flint on 2007-03-07
> **Artificial Intelligence said:**
> Did you change the word dapper to edgy in your sourcelist (also a good idea to disable un-official sources when you at it).


Too late now. I'm already installing a fresh Edgy :)  Hope that Gnome 2.16 will work faster on my pc. Thanks for the advices anyway ;)

---

