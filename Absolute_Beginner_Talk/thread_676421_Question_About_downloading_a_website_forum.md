---
title: "Question About downloading a website forum"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by bhougland on 2008-01-23
Hey everyone-

  I just downloaded Ubuntu a couple weeks ago, and later Xubuntu, and am loving it!  I was initally scared of the command line, but am now understanding how much power one has that knows what he is doing.  Also, the package manager and the awesome freeware has got me hooked. Anyway, just wanted to get that out there, with this being my first post and all.


I read about downloading a website and found that Gwget can do the job, but I still have some question on this.

I want to download the contents of an entire forum as a sort of archive of information (its not this forum, btw).  

Can Gwget do this? 
 
How much space would a fairly large forum take up?

If so, what is the best way?


Thanks guys!

---

### Post by jpeddicord on 2008-01-23
To download any site, first go to Edit > Preferences in Gwget, Recursive tab. Check the first box (Download page requisites) and up the depth level to something like 5. The depth is how many links it will follow and spider out from before deciding that it's done enough. That could get you anywhere from 10 to 1000 pages, and if it's a forum, probably the latter.

Close the preferences, and hit the New button. Type in the site URL and you're good to go. :)

---

### Post by bhougland on 2008-01-24
Thanks for the answer, but as I am not that proficient at building website I have a few more questions.

Is each reply considered a seperate link, or is each page pertaining to a thread considered an individual link?

How much space would this take up (ballpark figure)? ...I only have 30 gigs and its not that important to me.

Will Gwget ask me what folder I want it in or will it download into some default folder?

Thanks for any info!

---

