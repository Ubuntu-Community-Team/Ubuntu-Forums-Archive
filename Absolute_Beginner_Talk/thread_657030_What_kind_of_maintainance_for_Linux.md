---
title: "What kind of maintainance for Linux?"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by cutetux on 2008-01-03
Hello. This is a n00b question.

In Windows, we need to regularly to defrag the disk, clean and repair the registry in which I usually use CCleaner., and etc.

I learned that in Linux we don't need to defrag the hard disk and Linux don't use registry system like in Windows. So please tell me, is there anything that we should do regularly in order to keep the Linux run smoothly?

---

### Post by jeffus_il on 2008-01-03
Logon regularly,
If you cut you teeth installing yours,
Install on a friends machine.

---

### Post by kpkeerthi on 2008-01-03
Don't loose your sleep over defragging and reg cleaning in linux. 

But there are few [things]("http://ubuntuforums.org/showthread.php?t=140920") you can do to cleanup unnecessary junk. 

In addition, periodically clean up your ~/.thumbnails folder using a cron. Put this command in your crontab to remove thumbnails that were not used in the last 14 days.
```

find ~/.thumbmails -name *.png -atime +14 -exec rm '{}' ';'

```

---

### Post by lila on 2008-01-03
Another good thing is to periodically clean (physically) the inside of your tower.  You can do this with a vacuum cleaner (try and empty the bag before, just in case it swallows anything you want to retrieve).  Check connections beforehand, so there's nothing loose.  
Better than a vacuum is one of those air pistols you can hook up on a compressor, but not everyone has access to one of those.
Do this about once a year under normal conditions, I do it more often because of dusty environment.
And yes, go through stuff regularly and throwout tings you don't need (or store them on cds or whatever) to free up space.
Lots of fun with your new system,
Lila

P.S. I asked exactly the same question a couple of years ago when I first started out with Ubuntu - time flies:)

---

### Post by Borbus on 2008-01-03
Compressed air is MUCH better than a vacuum cleaner, and not just because it's safer. I used a vacuum cleaner for years and never bothered to buy compressed air because I thought the static danger from a vacuum was ********. I found a can of it recently, though, and blasted it into my CPU cooler... LOADS of dust came out, the vacuum cleaner couldn't get any of that out (and, for the record, it was a decent Dyson vacuum cleaner :D ).

---

### Post by hyper_ch on 2008-01-03
Just keep your software updated ;)

---

### Post by n8bounds on 2008-01-03
Exactly, just stay updated. It's also generally accepted good practice to Burn an Ubuntu Live CD every few days and pass it out at public gatherings.

---

### Post by Myglaren on 2008-01-03
> **Borbus said:**
> Compressed air is MUCH better than a vacuum cleaner, and not just because it's safer. I used a vacuum cleaner for years and never bothered to buy compressed air because I thought the static danger from a vacuum was ********. I found a can of it recently, though, and blasted it into my CPU cooler... LOADS of dust came out, the vacuum cleaner couldn't get any of that out (and, for the record, it was a decent Dyson vacuum cleaner :D ).

I regularly take my machines in to where I work and use the compressed air lines to blow the crap out (this one is due now).
DO make sure you lock the fans when doing this though, a spinning fan can generate back EMF that can damage semiconductors.  Just stick a non-conductive rod into the blades (carefully!)  A wooden skewer is ideal.

---

### Post by jeffus_il on 2008-01-03
Yes, I guess we all have our idiosyncrasies, Sounds like a good idea if you have access to compressed air, I am not less  idiosyncratic, I remove the CPU fan from the aluminium finned cooler and remove the cooler from the CPU itself, wipe and vacuum the fan, wash the fins and then regrease it with that heat conducting gunk and reassemble, I have met people who get by without these strange rituals, but I guess I need them.

---

