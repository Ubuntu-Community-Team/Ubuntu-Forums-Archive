---
title: "Is Nautilus Integral?"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by ofb on 2008-01-17
I'm poking around right now to see if I can make this 7.10 a little faster. Seems to be getting more sluggish.

I ran 'free' in terminal and it only showed one MB free, so opened System Monitor and found CPU spending most of it's time at 100%. That's not normal for this machine at rest.

Checked My Processes, and nothing unusual. Checked All Processes and Nautilus is bouncing from 75-100%, spending 10 or so seconds On, then goes away for a couple of seconds, and then back On. It's still doing that dance as I write this. 

There's no harddrive activity. Current open apps are just Opera, Term, Sys Monitor, ClawsMail, and Gedit.

What's Nautilus doing? Can (and should) I stop it from doing that?

And just for curiousity, is Nautilus more than just a File Manager? Like could I remove it? (I use Konq for file browsing.)

---

### Post by kpkeerthi on 2008-01-17
[http://psychocats.net/ubuntu/nonautilusplease](http://psychocats.net/ubuntu/nonautilusplease)

---

### Post by FuturePilot on 2008-01-17
You probably ran into this bug
[https://bugs.launchpad.net/bugs/150471]("https://bugs.launchpad.net/bugs/150471")
That's definitely not normal for Nautilus. It seems to crash for some reason and then get stuck in a loop when trying to restart.
If you're going by free you need to look at the Cached Memory as that will give you the true amount of memory in use. The other stuff is not in use by anything but cached for faster access.

---

### Post by DirtDawg on 2008-01-17
> **kpkeerthi said:**
> [http://psychocats.net/ubuntu/nonautilusplease](http://psychocats.net/ubuntu/nonautilusplease)

Thanks for the link. Nautilus has been crashing on me a lot lately too. 

However, I'm not ready to commit as the page states the scripts "don't work perfectly." Any details available?

---

### Post by ofb on 2008-01-17
Yay, a new bug... man, gusty gibbon has just not been Ubuntu's proudest release.

But thank you - very nice to have a quick answer to this.

Now to psychocats, I do know about that. What I'd like to get clear is does that mean Nautilus (or whatever is default) is integral? Like, you have to have a file manager designated as default so the system can use it?

DirtDawg - I should mention the "Page updated January 1" on psychocats is not 2008 -- so you shouldn't presume those have been tried on 7.10. Proceed with caution.

---

### Post by kpkeerthi on 2008-01-17
> **DirtDawg said:**
> 
However, I'm not ready to commit as the page states the scripts "don't work perfectly." Any details available?
Yeah.. I don't understand what he means by "these scripts will finish the job, even though they don't work perfectly". LOL :) 

I myself haven't tried it. I can only suggest you try the script. It also comes with a script to restore nautilius if something doesn't work quite well. 

Sorry I can't be of much help.

---

### Post by DirtDawg on 2008-01-17
> **ofb said:**
> 
DirtDawg - I should mention the "Page updated January 1" on psychocats is not 2008 -- so you shouldn't presume those have been tried on 7.10. Proceed with caution.

It's cool, I still use 7.4 anyway. Maybe a good thing considering the number of complaints I've heard about 7.10.

---

### Post by DirtDawg on 2008-01-17
> **kpkeerthi said:**
> Yeah.. I don't understand what he means by "these scripts will finish the job, even though they don't work perfectly". LOL :) 

I myself haven't tried it. I can only suggest you try the script. It also comes with a script to restore nautilius if something doesn't work quite well. 

Sorry I can't be of much help.

Okay, thanks anyway.

---

