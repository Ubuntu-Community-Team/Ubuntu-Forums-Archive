---
title: "Help with streaming realmedia"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by Mortuis on 2006-03-20
I'm trying to get streaming media to work.  I installed mplayer and the mozilla mplayer plugin and that works great on most pages, but there's one page I frequent ([http://www.uctv.tv](http://www.uctv.tv)) and I can't play any streams from there.

An example url would be:
[http://webcast.ucsd.edu:8080/ramgen/UCSD_TV/11468.rm](http://webcast.ucsd.edu:8080/ramgen/UCSD_TV/11468.rm)

At work I can run these streams, including the exact stream above, with no problem on my windows computer.  I mention this not to complain, only to verify that the link in question is good.  I use realplayer on windows and the file plays just fine.  So I tried installing realplayer on ubuntu.

The one that the graphical installer gives me is RealPlayer 8, which didn't work, so I uninstalled it.  So I tried googling and found a .deb file for RealPlayer 10, I installed that and that didn't work either.  So I uninstalled that and found out how to install the RealPlayerGOLD10.bin file found at [http://www.real.com/linux](http://www.real.com/linux).  Someone on IRC recommended I have it install to /usr/local/bin/real, which I did, and while the software loads and everything without any error messages, it still won't play the file when I do "Open Location", it just sits there perpetually saying "Contacting webcast.ucsd..".  I've tried opening the file in FireFox and the mozilla-mplayer software tries to connect to the stream for awhile and eventually gives up, giving me an error message saying that there is no stream at that url.

I'm at a loss for what to do from here and would appreciate any help.  For what it's worth, I tried loading my windows harddrive on this computer and running the stream and it worked fine.  So I'm certain that there are no issues with my connection at home.

---

### Post by GMachine_24 on 2006-03-20
Hey there:

Well, as a UCSB graduate and former attendee at many a Campbell Hall snooze-a-thon lecture on art history or philosophy, you can imagine my surprise when I clicked on your link and, voile, there I was again, back in the good old confines of UC Santa Barbara.

Anyway, I clicked on the link, RealPlayer (I have version 10.X.X.X blah blah blah Gold) worked fine streaming at 225 kbps but there was no sound . . . so... I'm not sure what's up with that. But the streaming video looked great. (Actually the sound works fine, too. See below).

I have just a PIII 900 with 8XX MB of DRAM.

Actually what happens is your computer downloads a small real media file and then your real player opens that and somehow connects to the real media stream....and off you go. At least that's my understanding but I am no expert.

Try "right clicking" on the link and open it in a new tab. That's what I did.

Edit: Ok, I win prize for klutz of the year. I had accidentally hit the power button on my speakers while attempting to turn the volume up - and instead turned them off. The sound works fine.

---

### Post by Mortuis on 2006-03-20
Heh, I'm retroactively envious of the amount of Philosophy lectures your alma mater has listed on the site.  My school was very sparce in that regard, maybe one or two a semester.

I played around a little, and managed to download the file then launch it from there and inexplicably it works just fine.  However, it's not ideal to have to manuially download and execute the file.   I'd prefer RealPlayer to execute when I click on the hyperlink or something.  At least I know the appliction works now though.

I tried opening the hyperlink in a new tab as you suggested, however mplayer is trying to handle the stream.  Is there a way I can direct firefox to use realplayer for .rm and .ram files?

---

### Post by Mortuis on 2006-03-20
I take it back.  It is only working sporadically.

I tried opening the file just now and it played the video with no sound.  I went into Tools->Preferences->Hardware and checked "Disable custom sample rates", exited the program, relaunched RealPlayer, then opened the file again and it played with sound.  So I went in and unchecked "Disable custom sample rates", exited the program, relaunched RealPlayer again and opened the file again, no sound.  Figuring this way the problem, I went ahead and checked "Disable custom sample rates" again, closed RealPlayer, launched RealPlayer, and opened the file, and still no sound.


I checked the helix forums and saw the suggestion to do "ps ax | grep real"  to see if there were other realplayer processes running at the time.  I don't see any when I don't have realplayer loaded.  When realplayer is running I get:
john@uriel:~$ ps ax | grep real
11452 ?        S      0:00 /bin/sh /usr/bin/realplay
11459 ?        Sl     0:02 /usr/local/bin/real/realplay.bin
11461 ?        S      0:00 /usr/local/bin/real/realplay.bin
11462 ?        S      0:00 /usr/local/bin/real/realplay.bin


I tried this a couple times and got the same results each time.  At this point I feel like when I load the file in realplayer it will randomly give me sound.  So I googled "test realplayer" and got 
rtsp://62.169.4.75:554/real-home/testvideo_e.rm
from the first page it loaded.  I tried opening that location, but realplayer sat there as if I entered nothing.

I then tried opening the previous file again, and it loaded with sound.  I stopped it immediatly and tried opening the file again and  it worked.  I try loading rtsp://62.169.4.75:554/real-home/testvideo_e.rm and it works with sound too.

Now I'm confused, so I close realplayer, open it, and try to load the previous file, no sound.  I try loading rtsp://62.169.4.75:554/real-home/testvideo_e.rm, nothing.  I close realplayer, load rtsp://62.169.4.75:554/real-home/testvideo_e.rm, nothing, load the previous file, it works.



It seems like in order to play the philosophy lecture from uctv, I need to load the player, open this location rtsp://62.169.4.75:554/real-home/testvideo_e.rm (which fails to load) THEN open the file on my harddrive which opens the stream to the philosophy lecture.

Just to verify, I tried it a few more times.  And it defenitly seems to only open the file when I first try (and fail) to load rtsp://62.169.4.75:554/real-home/testvideo_e.rm.

This is very strange behavior.  I'm going to go to bed now and hope that magic occurs overnight, or that the restarting of my computer when I wake up fixes things.

If anyone else has had this sort of problem, please let me know how you fixed it!

---

### Post by GMachine_24 on 2006-03-21
Hi:

Sounds like you did a lot of work.

I know there's a way to "associate" Real Player with the rm files if another app is opening them by default - however I'm not sure how to do this. Usually when you first attempt to play a Real file a box will pop up and ask if you want to save the file or open it with a program and there is a line that asks if you always want to take this action with this kind of file - and you can check it.

If you Google or search these forums I'm sure you can find how to associate Real Player with rm files. Perhaps that will help.

In the dim recesses of my memory there seems to be a recollection that Linux/Ubuntu can only have one sound player/program running at a time . ..perhaps I'm not remembering correctly but you might want to check that out if you have an mplayer app open at the same time.....

---

### Post by GMachine_24 on 2006-03-21
Try this:

In Mozilla, go to

Tools>Download Manager and a window will pop up listing files you have downloaded. Clear them all. Close the box.

Now, click on your rm url from your previous post

i.e.

[http://webcast.ucsd.edu:8080/ramgen/UCSD_TV/11468.rm](http://webcast.ucsd.edu:8080/ramgen/UCSD_TV/11468.rm)

and see if a box doesn't open asking what you want to do with the file.

When I did this, I got a box that asked if I wanted to open the file with Real Media, save the file, etc. and if I wanted to take this action by default in the future.

It's worth a try.

---

### Post by noswal on 2006-03-21
I just loaded the link in Xine (gxine 0.4.4) and it plays sound & vision, find it in Synaptic package manager

---

