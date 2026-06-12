---
title: "A beagle ate my hard disk!"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-08-08
Re Beagle, I just found that the /home/user/.beagle directory is over 2 GB, which is roughly 10% of my entire hard disk space.  I. e. it's humongous!
Is a Beagle directory that large (proportionally speaking) normal?
I'd appreciate if you could have a shufty at your .beagle directory and tell me what you think, ta.

(Rant:  I only wanted Beagle to *index* my HDD, not *mirror* it ...) :(

---

### Post by Al3xK3aton on 2007-08-08
The problem is that your hard disk is too small. Come on man, this is 2007.

---

### Post by beren.olvar on 2007-08-08
> **Al3xK3aton said:**
> The problem is that your hard disk is too small. Come on man, this is 2007.

come on.. thats kind of microsoft minded, dont u think?

my .beagle/ is about 300M, i think u should unload some plugins, like pdf o web history search,
and delete that indexed data

gl

---

### Post by Blofeld on 2007-08-09
> **Al3xK3aton said:**
> The problem is that your hard disk is too small. Come on man, this is 2007.

Quisling!!!

---

### Post by Blofeld on 2007-08-09
I deleted the ~/.beagle folder, which took several hours (!).  Beagle then automatically created a new ~/.beagle folder which is currently 6 MB large, and Beagle still works fine.
It seems to me that Beagle simply fails to delete out-of date indexes (indices).
Deleting the ~/.beagle folder also fixed the glitch that Beagle previously always told me that indexing was in process.

---

### Post by Lord Illidan on 2007-08-09
Still, 20 gb is too small :P

---

### Post by proalan on 2007-08-09
beagle has very big resource needs when running on low end systems. It maxed out my cpu ate up hard drive space, caused system instability and performance degradation. I asked myself "do you really need this program?" and got rid of it.

There is an alternative search/indexing program called 'tracker' which I tried briefly that is far more respectful to system resources. 
the other alternative is 'googledesk' but I'm told it's indexing capabilities are limited.

---

### Post by Blofeld on 2007-08-09
Thanks Alan.
I wasn't aware of Tracker.  Apparently it's primed to become default on Ubuntu (replacing Beagle?).  However it didn't cut it for me as the search results are patchy to say the least, you can't configure it and it doesn't even tell you when it's finished searching.  Or maybe I'm simply too refined and demanding?
I'm now giving Google Desktop a try.  BTW it needs a reboot to start -- I thought that was only necessary under Windows!
Another problem I had with Beagle was that with some of the files it found, I couldn't get it to tell me where they were located, which reminds me of the joke where a man asks "Do you have the time?", and the other man says yes and walks off ...
Anyway, so far my impression is that there is a wonderful choice of search tools only that neither of them just does what it says on the tin. :(

---

### Post by Hospadar on 2007-08-09
Tracker works fine, just make sure you are searching in the right place.  beagle automatically looks into files for your search, but by default tracker only looks at the file names.  Also by default tracker only looks in your home folder (not the entire filesystem)

---

### Post by Blofeld on 2007-08-09
That's worth while knowing, thanks Hospadar. ;-)
However I just found that Tracker does look inside files, at least simple text files.
Tracker also seems to be ignoring hidden files, am I right?

NB don't look but I think you have a duck sitting on your head.

---

### Post by proalan on 2007-08-09
I've not found a really configurable desktop search application myself yet. Konqueror does a ok job but effectively just uses 'locate' command.

Too much emphasis on indexing, I mean once you've found a file do you really need to index the search results? 

Currently I have to resort to the command line 'grep' to locate files with specific search parameters (pattern matching). 

'find', 'locate', 'type' are useful commands.

---

### Post by ultralame on 2008-02-19
Uh, my system has been locking up.  I finally figured it out.  I had a 28GB .beagle folder.  WTF?!

apt-get remove beagle, thank you.

---

### Post by rainwalker on 2008-02-20
Tracker is what Ubuntu comes with by default...? 
I've had nothing but horrible experiences with Tracker, it wouldn't find anything I searched for and it was a pain to use from the Deskbar applet thing.

---

### Post by dbera on 2008-02-20
> **ultralame said:**
> Uh, my system has been locking up.  I finally figured it out.  I had a 28GB .beagle folder.  WTF?!

apt-get remove beagle, thank you.

It is a known problem and is apparently fixed in 0.3.0 (hardy has one of the later versions and someone ported it to Gutsy too)

---

### Post by spiderbatdad on 2008-02-20
beagle is a virus

---

