---
title: "Play wma files in Ubuntu"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-08-29
When I first started using Ubuntu Dapper about 5 weeks ago, I managed to persuade Rhythmbox to load my 35 GB of wma music file and everything worked fine.
Then I re-installed Ubuntu about 2 weeks ago and have not been able to get Rhythmbox to even load, let alone play, my wma files.
I'm sure I have all the correct codecs (including the wm32 codecs) installed (I used this guide: [http://www.ubuntuforums.org/showthread.php?t=70227&highlight=play+wma+music+files](http://www.ubuntuforums.org/showthread.php?t=70227&highlight=play+wma+music+files))
and my wma files play fine in Xine.
However, I don't seem to be able to get the whole CD loaded at once to Xine and therefore I must play the songs one at a time (or so it seems).

Any ideas as to what I might be forgetting here or, alternatively, is there a media player that will more readily accept wma files?

---

### Post by moore.bryan on 2006-08-29
*i went through much the same problem... i dumped rhythmbox for amarok and loved it, BUT it ate my memory like nobody's business.  xmms was the one almost everyone suggested and after i got used to it, i can't imagine i tried anything else.*

---

### Post by jorn on 2006-08-29
Have you tried to remove and reinstall Rhythmbox or start it in terminal to look for errors?
> rhythmbox

---

### Post by PaulFXH on 2006-08-29
Thanks for the replies.

jorn: What I get when I start Rhythmbox in terminal is:  "Unable to start mDNS browsing" which doesn't really clarify anything for me. Any ideas?

moore.bryan: As I don't really have any emotional attachment to Rhythmbox, I am quite prepared to migrate to another media player as long as it does what I want which is:
i) allow me to load my 35 GB of wma music files
ii) play them album by album (rather than just song by song).
iii) provide some nice visualizations (although this is less essential)

Right now, although Xine works (song by song basis only), I can't get a squeak out of xmms although it is there.

Would really appreciate some further guidance on this critical issue:D

---

### Post by justin whitaker on 2006-08-29
> **PaulFXH said:**
> Thanks for the replies.

jorn: What I get when I start Rhythmbox in terminal is:  "Unable to start mDNS browsing" which doesn't really clarify anything for me. Any ideas?

moore.bryan: As I don't really have any emotional attachment to Rhythmbox, I am quite prepared to migrate to another media player as long as it does what I want which is:
i) allow me to load my 35 GB of wma music files
ii) play them album by album (rather than just song by song).
iii) provide some nice visualizations (although this is less essential)

Right now, although Xine works (song by song basis only), I can't get a squeak out of xmms although it is there.

Would really appreciate some further guidance on this critical issue:D


mDNS? It's looking for something online...(have no idea why...maybe to update the WMA metadata?).

Personally, I hate Rythmbox, and if there were a vote this minute to get rid of it in favor of Amarok, Banshee, or pretty much anything else, I would say aye. Really poor choice for a default audio app. 

Some other players with WMA support are:

MoreAMP: [http://sourceforge.net/projects/moreamp/](http://sourceforge.net/projects/moreamp/)
wxMusik: [http://musik.berlios.de/](http://musik.berlios.de/)
MOC:[http://moc.daper.net/](http://moc.daper.net/)

How attached are you to the WMA format though? I'd seriously consider converting them to something else.....

---

### Post by PaulFXH on 2006-08-29
Thanks Justin.
My only attachment to wma files is that I use wmp11 in WinXP which, whatever about Windows faults, is ALWAYS available and reliable.
I know I could convert my music files to mp3 format but this would mean taking up another 35 GB of disk space (or probably slightly more).

I'll try the media players you suggested, however, I've already tried three today (xmms, Xine and rhythmbox) and only Xine comes remotely close to what I need (although, mysteriously, Rhythmbox used to work fine).

---

### Post by justin whitaker on 2006-08-29
> **PaulFXH said:**
> Thanks Justin.
My only attachment to wma files is that I use wmp11 in WinXP which, whatever about Windows faults, is ALWAYS available and reliable.
I know I could convert my music files to mp3 format but this would mean taking up another 35 GB of disk space (or probably slightly more).

I'll try the media players you suggested, however, I've already tried three today (xmms, Xine and rhythmbox) and only Xine comes remotely close to what I need (although, mysteriously, Rhythmbox used to work fine).

You tried reinstalling Rythmbox? 

Banshee is a fork of RB, you might try that instead. Also, check your sound system: what backend are you using for RB? You might be able to switch it to use the xine engine instead. 

Also, have you tried using WINE? 

[http://frankscorner.org/index.php?p=multimedia](http://frankscorner.org/index.php?p=multimedia)

According to FC, iTunes, Foobar, and earlier versions of WMP all can be made to run on Linux via Wine. I know personally that Foobar runs on Crossover Office....but amarok is as good. :rolleyes:

---

### Post by PaulFXH on 2006-08-29
> You tried reinstalling Rythmbox? 
This was suggested earlier and I might try it later.

> Also, check your sound system: what backend are you using for RB? 
I can play radio stations on Rhythmbox with perfect sound.

> Also, have you tried using WINE? 
Hmmm, that's a thought.

Actually, I haven't mentioned that my main (or perhaps only) problem with Rhythmbox is that I can't get the songs/albums/folders to load from where I have them stored.
Indeed, I find this to be a little unclear as to how to manage this. I click on Music>Import File (or Folder) and Open what I want in the dialog box that opens. However, there is no "Import" button. So, how do you tell Rhythmbox to "go ahead and load this stuff" after you've decided exactly what you want to load?

When I got it to work before, I just clicked the open button a lot and eventually, everything on the partition where I have the wma files started loading.
This time, however, even though it's reading the disk for about 10 minutes, nothing at all loads.
Weird, huh?

---

### Post by PPAAUULL on 2006-08-29
Dude, all you have to do is the windows codecs in this how to. [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) hope that help. It worked for me. you could also use Automatix.

Paul

---

### Post by sbassett on 2006-08-29
> **PaulFXH said:**
> This was suggested earlier and I might try it later.


I can play radio stations on Rhythmbox with perfect sound.


Hmmm, that's a thought.

Actually, I haven't mentioned that my main (or perhaps only) problem with Rhythmbox is that I can't get the songs/albums/folders to load from where I have them stored.
Indeed, I find this to be a little unclear as to how to manage this. I click on Music>Import File (or Folder) and Open what I want in the dialog box that opens. However, there is no "Import" button. So, how do you tell Rhythmbox to "go ahead and load this stuff" after you've decided exactly what you want to load?

When I got it to work before, I just clicked the open button a lot and eventually, everything on the partition where I have the wma files started loading.
This time, however, even though it's reading the disk for about 10 minutes, nothing at all loads.
Weird, huh?

Paul -

Make sure you have Gstreamer bad and ugly plugins loaded first. These will only be loaded if you have universe and multivers enabled within Synaptic. Your best bet is to do a search for Gstreamer within Synaptic. Also, that mDNS message is just a notification, this is a "zeroconf" client, the type used to share music back and forth within other music programs such as iTunes.

---

### Post by PaulFXH on 2006-08-29
Hi sbassett
You hit the nail right on the head!
Although I had installed some Gstreamer stuff already, obviously they weren't the right ones.
As soon as I'd loaded up the ones you suggested (and a few more--as I'm impatient:( ), Rhythmbox responded to my attempts to get it to load from my wma files.
I'm listening to Rhythmbox as I write.
Thanks to everybody for helping me through this one
Paul

---

