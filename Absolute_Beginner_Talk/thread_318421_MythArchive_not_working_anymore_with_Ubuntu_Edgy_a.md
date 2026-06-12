---
title: "MythArchive not working anymore with Ubuntu Edgy and MythTV 0.20"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by piec2 on 2006-12-14
I'm using MythTV 0.20 under Ubuntu Edgy and the setup went fairly smoothly.
Now I am testing MythArchive to burn a recorded show to a DVD.
I've used MythArchive several times to try to archive to DVD and I cancelled it several times (I was just testing to see if the archving started, what the log was saying, etc.)

Now it doesn't seem to work anymore. 
The log displayed appears to be the last log when I interrupted it (using the Cancel button) and it doesn't seem to do anything anymore. 
There isn't any hard drive activity, so I'm sure its not transcoding/archiving. 

Could it be that some "cancel" flag in the database is stuck and I need to manually reset it? If so, how do I do that? 

ANybody ever got this problem?

---

### Post by piec2 on 2006-12-14
I looked at the Python source code and found that it was indeed a lock file preventing MythArchive from doing its job.
Here's how I fixed it:
```
root@mythpc:/# rm /var/lib/tmp/logs/mythburn.lck
root@mythpc:/# rm /var/lib/tmp/logs/mythburncancel.lck
```

---

### Post by teet on 2006-12-16
> **piec2 said:**
> I'm using MythTV 0.20 under Ubuntu Edgy and the setup went fairly smoothly.
Now I am testing MythArchive to burn a recorded show to a DVD.
I've used MythArchive several times to try to archive to DVD and I cancelled it several times (I was just testing to see if the archving started, what the log was saying, etc.)

Now it doesn't seem to work anymore. 
The log displayed appears to be the last log when I interrupted it (using the Cancel button) and it doesn't seem to do anything anymore. 
There isn't any hard drive activity, so I'm sure its not transcoding/archiving. 

Could it be that some "cancel" flag in the database is stuck and I need to manually reset it? If so, how do I do that? 

ANybody ever got this problem?

It does the same thing for me.  To fix the problem, go into the folder that you specified mytharchive to use for it's temporary workspace (e.g. on my box, I have it set to use the folder /video/temp ) and delete all the folders (there should be 3 folders).  Then you should be able to start over again.

I would say this is a bug in the interface.  If for whatever reason you cancel a job before it's completed, it tries to complete the job each time you run mytharchive.

-teet

---

### Post by teet on 2006-12-16
> **piec2 said:**
> I looked at the Python source code and found that it was indeed a lock file preventing MythArchive from doing its job.
Here's how I fixed it:
```
root@mythpc:/# rm /var/lib/tmp/logs/mythburn.lck
root@mythpc:/# rm /var/lib/tmp/logs/mythburncancel.lck
```

I still haven't gotten mytharchive to burn a dvd.  It goes through the ffmpeg stuff and makes all the menu items for the dvd.  Mytharchive then bails out with this error message:

```

Error: failed while running dvdauthor. result: 1

```

I tried this "fix" but it said that I didn't have these files (and yes, I tried adding 'sudo' in front of the commands too).  Any help would be appreciated.

-teet

---

### Post by superm1 on 2006-12-16
> **teet said:**
> I still haven't gotten mytharchive to burn a dvd.  It goes through the ffmpeg stuff and makes all the menu items for the dvd.  Mytharchive then bails out with this error message:

```

Error: failed while running dvdauthor. result: 1

```I tried this "fix" but it said that I didn't have these files (and yes, I tried adding 'sudo' in front of the commands too).  Any help would be appreciated.

-teet

Look a little closer at the log files in /tmp/logs.  They should describe exactly what is happening.  I personally have similar troubles when trying to go from HD to DVD.

---

### Post by fuct000 on 2006-12-28
> 
Quote:
Originally Posted by teet View Post
I still haven't gotten mytharchive to burn a dvd. It goes through the ffmpeg stuff and makes all the menu items for the dvd. Mytharchive then bails out with this error message:

Code:

Error: failed while running dvdauthor. result: 1

I tried this "fix" but it said that I didn't have these files (and yes, I tried adding 'sudo' in front of the commands too). Any help would be appreciated.

-teet
Look a little closer at the log files in /tmp/logs. They should describe exactly what is happening. I personally have similar troubles when trying to go from HD to DVD.

I've got the same problem, no logs in /tmp/logs and I can't see any problems within /var/logs
I'm trying to create an ISO image to copy off to another machine and burn, rather than burning it on this machine.

---

### Post by superm1 on 2006-12-28
> **fuct000 said:**
> I've got the same problem, no logs in /tmp/logs and I can't see any problems within /var/logs
I'm trying to create an ISO image to copy off to another machine and burn, rather than burning it on this machine.

If this works, then I'll ask you do you have 2 DVD drives in your computer?  At least for me, I've seen that mytharchive doesn't listen to what you set the burning device to be.  You can try changing the symlink /dev/dvd to the correct drive and see if this resolves it.  But again, there should at least be a log in /tmp/logs from mytharchive.

---

### Post by fuct000 on 2006-12-30
I've finally found the log, the errors are

[SIZE="1"]**ERROR: [mplex] Need to split output but there appears to be no %d in the filename pattern /recordings/archive//work/1/final
.mpg
WARN: attempt to update aspect ratio from 16:9 to 4:3; skipping

INFO: Video pts = 0.184 .. 187.904
INFO: Audio[8] pts = 0.264 .. 188.040
STAT: VOBU 391 at 52MB, 1 PGCS
WARN: GOP is not closed on cell 1 of source /recordings/archive//work/1/final.mpg of pgc 1
INFO: Generating VTS with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: pal
INFO: Aspect ratio: 16:9
INFO: Resolution: 704x576
INFO: Audio ch 0 format: mp2/2ch, 48khz 20bps

ERR:  Cannot jump to chapter 2 of title 1, only 1 exist
ERR:  in VTSM pgc 0, button 2
************************************************************
ERROR: Failed while running dvdauthor. Result: 1
************************************************************[/SIZE]

I think thats caused by me trying to add chapters to the video.  I'll try it when I get home without chapters and see if it works better.

As for the location of the logs.

> But again, there should at least be a log in /tmp/logs from mytharchive.

I found this not to be the case, I found the logs in ***[mythArchive working directory]*/logs**

---

### Post by superm1 on 2006-12-30
> **fuct000 said:**
> I've finally found the log, the errors are

[SIZE=1]**ERROR: [mplex] Need to split output but there appears to be no %d in the filename pattern /recordings/archive//work/1/final
.mpg
WARN: attempt to update aspect ratio from 16:9 to 4:3; skipping

INFO: Video pts = 0.184 .. 187.904
INFO: Audio[8] pts = 0.264 .. 188.040
STAT: VOBU 391 at 52MB, 1 PGCS
WARN: GOP is not closed on cell 1 of source /recordings/archive//work/1/final.mpg of pgc 1
INFO: Generating VTS with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: pal
INFO: Aspect ratio: 16:9
INFO: Resolution: 704x576
INFO: Audio ch 0 format: mp2/2ch, 48khz 20bps

ERR:  Cannot jump to chapter 2 of title 1, only 1 exist
ERR:  in VTSM pgc 0, button 2
************************************************************
ERROR: Failed while running dvdauthor. Result: 1
************************************************************[/SIZE]

I think thats caused by me trying to add chapters to the video.  I'll try it when I get home without chapters and see if it works better.

As for the location of the logs.



I found this not to be the case, I found the logs in ***[mythArchive working directory]*/logs**
Ah didn't realize you had changed the working directory.  I personally haven't tried making chapters, so please do post back if that resolves the issue.

---

### Post by fuct000 on 2007-01-03
Yeah, it now works fine when I don't try and create chapters within the videos.

Now just to work out how to strip the adverts out :)

---

### Post by superm1 on 2007-01-03
> **fuct000 said:**
> Yeah, it now works fine when I don't try and create chapters within the videos.

Now just to work out how to strip the adverts out :)

Well some further education on this matter:

Basically you have the commercial flagger run on the show.

You go to the play area, and play the video you want.  Press E to go into Editor mode.  Press Z to load your commercials cutlist.

Now you can press pgup/pgdown to switch between cuts.
Up and down will control the time jump.  Left and right move you left and right.  Press space to move your cutpoints.
When your done press escape.

Now mytharchive will allow you to use the commercial cutlist to snip from the recordings that are burned or you can do a mpeg2-mpeg2 transcode in the play menu to remove them permanently.

---

