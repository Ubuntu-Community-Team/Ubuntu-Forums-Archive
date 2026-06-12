---
title: "problem with Sound Juicer"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by sparhawk on 2005-12-09
I am logged in under my boyfriend's name. He's the IT guy, he knows it all. He just told me if I had any questions I could ask them here, and he set the forums as our homepage. I have not had any difficult adjusting to Ubuntu after years of using Windows, since all I really use is the web browser, Gaim and I listen to audio cds on the computer all the time now because my stereo speakers are broken. 

So I put in the second disc of a 3 disc set. I had not played disc 1 at all. Put the disc in, Sound Juicer opened, and it listed all the tracks from disc 1. It is not playing those tracks, it is playing the correct songs, the songs that are actually on disc 2, but it lists the wrong titles. If I skip down to another track it will play, say track five, of disc two. The first two discs happen to both have six tracks. Tried closing Sound Juicer, and then opening it again, then tried replacing the disc. Each time I still got the wrong track listing. 

I tried the third disc of the set and this one works fine, lists the correct tracks and everything. So it's just the second disc. Do you think it's the disc or the player? I realize I can rename the tracks when I play disc 2 and then I guess it will recognize them by the correct names then, but I'm curious as to why it came up like that. Anyone else noticed this?

---

### Post by davmac on 2005-12-10
I suspect it's a problem with the data source. Sound Juicer accesses CDDB (CD Database). Based on the unique ID of the CD it brings back the list of tracks stored at CDDB. A simple mix up between disk 1 and 2 when the data was originally populated would cause your problem.

Hope this helps,

Dave Mac

---

### Post by ncappel1 on 2006-01-28
Hello, this problem has happened to me too. It also may be because when CDDB is searching to the track listing, it matches the disk's ID number with the number of tracks on it. This means that two CDs from the same set with the same number of tracks are liable to get confused very easilly.

It's a good thing the CD only has 6 tracks on it and not 25 or 30! changing all the information for each individual track name could take some time!

---

