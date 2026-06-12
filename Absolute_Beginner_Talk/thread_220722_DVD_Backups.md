---
title: "DVD Backups"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by OU812 on 2006-07-22
In a thread I read that ubuntu doesn't have any good dvd backup programs. Well, here are 4 that I would highly recommend:

1. lxdvdrip - Has a few dependencies. Command line tool, but uses a config file to do all the dirty work.

[http://openfacts.berlios.de/index-en.phtml?title=lxdvdrip](http://openfacts.berlios.de/index-en.phtml?title=lxdvdrip)

2. dvdshrink/xdvdshrink - dvdshrink is the command line app and comes bundled with xdvdshrink, which is a gui tool. It needs a few dependencies and xdvdshrink needs perl and gtk2. Note: This is NOT the windows app.

[http://dvdshrink.sourceforge.net/](http://dvdshrink.sourceforge.net/)

3. k9copy - for kde users. Has some dependencies, but has a nice gui interface.

[http://k9copy.sourceforge.net/](http://k9copy.sourceforge.net/)

4. dvd95 - for gnome users. I just installed this yesterday. Nice interface. Comes as an .rpm so make sure you install alien from the repo.

[http://dvd95.sourceforge.net/](http://dvd95.sourceforge.net/)

Note: I found these apps using google or browsing this site

[http://www.softpedia.com](http://www.softpedia.com)

john

---

### Post by orb9220 on 2006-07-22
I'm sorry i is spolied on windows DVDshrink and it runs fine under wine,

HOW-TO: Install DVD Shrink with Wine

[http://ubuntuforums.org/showthread.php?t=78611](http://ubuntuforums.org/showthread.php?t=78611)

Works great because alot of the ones you mentioned require different programs for ripping and compressing.

One step to rip to iso or dvd folder with compression.
And able to set compressions for different parts "extra's" to max so there is more room for the main movie. 

Deselect languages you don't need. Even use to take two disk long movies like Lawerence of Arabia and Cleopatra and ripp both down and merged to a long movie have gotten 4hrs+ this way.

Havn't found anything in linux yet that powerful. Hoping tho soon?

---

### Post by Skia_42 on 2006-07-22
I have been able to handle all of my DVD burning with dvd95, it is easy to se and it does have a nice interface. I endorse it...

---

### Post by Kilz on 2006-07-22
I do make backups of DVDs I own. Then I put the original in its case on a shelf. K9copy enabled me to get rid of dvdshrink under wine, one of the few remaining windows programs I was still running. It runs fine under gnome even though its a kde program.
The version 1.0.4 is [available from this German repository]("http://www.kubuntu.de/index.php?option=com_content&task=view&id=48&Itemid=70") and it fixes a lot of bugs and has a setting to adjust for the size of the iso/disk.

---

### Post by OU812 on 2006-07-23
@orb9220: k9copy is equivalent to dvdshrink windows (ironically, dvdshrink linux version is not). Follow the link provided by kilz to download k9copy (the dependencies are in the repo) and free yourself from windows just a little bit more.

john

---

### Post by orb9220 on 2006-07-24
Sorry but tried it, not quite there because movie complete to hd takes about 10 mins more plus it does not allow for customize compressions on different parts of the dvd.

I liked to do a customize compression on extra's which gives me a few les % on the main movie.

And also the whole title 1 thru 20 with no difference in finding the main movie versus extra's,the size bar at bottom gives no info whatsoever I didn't even know if movie was compressed until I went and looked at the finished iso.

The movie took 67 mins to rip then another 4-5 mins. to burn the iso for a 72 mins. Same title took 58 mins total in shrink.

But I will keep trying and using different ones till I find one that has the features that shrink has.

Till then it's shrink

---

### Post by OU812 on 2006-07-24
@orb9220: You're right - I completely forgot about those options! I don't think I've seen a linux app that can do all that. Well, here a few features of linux apps that I don't think dvdsrhink has...

lxdvdrip can back up an entire dvd9 to 2 dvd5's - without loss of quality since it does this without shrinking (OK you will probably never use this feature).

xdvdsrhink can back up multi-episode disks with shrinking - so like lxdvdrip, but this time multiple discs makes sense because you're splitting between episodes.

I bring this to your attention because I can't quite find an app that does everything I want. So I settle for a bunch of different ones. Good thing I have time and room.

john

---

### Post by orb9220 on 2006-07-24
Yes a few do look promising and I am keeping my eyes open.

One problem I can't seem to fiqure or get an answer too is that nautilus and nero can burn my verbatim 16x disc in 8 mins but k3b and gnomebaker take 15 mins. which is 4x speed,

That makes me wary is everyone using different was to handle dvd burners?
And there is no standard. Since in windows any app I use to burn seems to be able to burn 16x at 16x.

Just hoping it gets better and better for ubuntu.

---

### Post by OU812 on 2006-07-24
I've been creating an .iso and using cd/dvd creator (places menu), but then again I've only had ubuntu for a few days and am still learning how well the base apps work. Moving on ... I don't know how fast this app is at burning, but installation is simple (untar and do ./install.sh) and all dependencies should be in ubuntu base system. It's a shell app, but it has a nice menu system. Anyway, try bashburn.

[http://bashburn.sourceforge.net/](http://bashburn.sourceforge.net/)

john

---

