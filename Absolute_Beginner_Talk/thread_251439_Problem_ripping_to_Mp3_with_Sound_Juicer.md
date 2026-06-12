---
title: "Problem ripping to Mp3 with Sound Juicer"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by Sweet Spot on 2006-09-05
Having read the "first encounter with an iPod" thread, and realizing that I haven't ripped any CD's since having installed Ubuntu (again),  I decided to give it a whirl. I don't mind ripping to Ogg since I use it with my DAPs (iRiver IHP 120 and ROCKbox'd iPod 5 gen), but sometimes I do like to rip to Mp3 as well. 

So I followed the instructions from the Sound Juicer Manual as quoted by someone from the other thread: > If you need to store tracks in the MP3 format (for example, if your portable music player only supports MP3 and not Ogg Vorbis), you will need to create a new profile. To do this, click on Edit Profiles, click New, and name the profile MP3.

Select the MP3 profile and click the Edit button. Set GStreamer Pipeline to audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=196 ! id3v2mux

Set the File Extension to mp3, and select the Active check box. You will have to restart Sound Juicer to see the new audio profile.

This profile uses the LAME MP3 encoder, so you will need to have the GStreamer LAME plugin installed. 
Followed that to the T, including having installed the GStreamer LAME plugin, and already had LAME installed (used Automatix for many extras) but when I try to rip to Mp3, I get this error message:

> Sound Juicer could not extract this CD.
Reason: Internal GStreamer error: negotiation problem.  Please file a bug at [http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer](http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer) . 
Ripping to Ogg, no problem. To Mp3, no go. Yes, there are quite a few GStreamer plugins that I see which aren't installed, but the ones mentioned, are. Anybody know what the issue might be ? I'm using version 2.14.4 of Sound Juicer btw. 

Thanks, 
Doug

---

### Post by Sweet Spot on 2006-09-05
Bumpy.

---

### Post by Sweet Spot on 2006-09-05
Bumping because it's gonna fall back to the double digit pages.

---

### Post by Sweet Spot on 2006-09-05
:-k:?:O:)

---

### Post by click4851 on 2006-09-05
I feel for yah man, I beat my head on this little "issue" for about as long as you have. I gave up and went back to Grip. I understand the whole open source thing, but if grip can do mp3's that easy, sound juicer should be at least that easy.

---

### Post by Sweet Spot on 2006-09-05
That's too bad. Because the Sound Juicer interface is really simple and changing the bitrate is too. I know there are other things, so there's no harm in looking I suppose. 

Doug

---

### Post by k|d&lt;FuNkY&gt;FrY on 2006-09-05
I just configured mine with the following Pipeline...only! 

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc

Update your .mp3 profile and let me know how it works out! I was able to rip to .mp3 without a hitch. 

I used this site as a quick reference! 

[http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html](http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html)

~b-Dub

---

### Post by k|d&lt;FuNkY&gt;FrY on 2006-09-05
this pipeline seems to work on my end...

Let me know otherwise! 

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=256

---

### Post by Sweet Spot on 2006-09-05
LOL, ok, let me install it again, and I'll let you know shortly ! 

Doug

---

### Post by Sweet Spot on 2006-09-05
Eureka Sir  ! That did the trick just right ! Thanks a lot ! That's .... 3 exclamation marks ! Damn, make that 4.... :mrgreen:

Now to get rid of Grip. Thanks again.

Doug

---

### Post by click4851 on 2006-09-05
Now your talking, maybe this should be in Automatix...I might have to load up Soundjuicer again...

---

### Post by k|d&lt;FuNkY&gt;FrY on 2006-09-06
Excellent -- I'm glad it worked for you! :p

---

### Post by nevle on 2006-09-17
I am having mp3 problems (wont play in nautilus on dble click) yes i have done allthe obviuos.After adding the pipeline to sound juicer when i go back into the preferences it shows the output as mp3(mp3 document) is this what yours shows or should it be mp3(mp3 audio)??

---

