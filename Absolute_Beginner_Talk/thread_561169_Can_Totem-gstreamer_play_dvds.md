---
title: "Can Totem-gstreamer play dvds?"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by bwallum on 2007-09-27
Hello

This is a hoary old question but here goes.

I can play dvds on VLC player but sound is sometimes troublesome. The sound crackles, I try messing with the equaliser option and sometimes get no crackling sound, sometimes not. libdvdcss2 is installed from the Medibuntu repo.

So I thought i would try Movie Player. Up pops Movie Player Totem (with gstreamer). In the tab Movie>Play Disc....I can see that it recognises the dvd with the correct title.  I then get the following message when I click on Play Disc....

"Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it. Please install the necessary plugins and restart Totem to be able to play this media."

I have read the various guides but none of them lead me to identifying what the plugin might be.

Can Movie Player (gstreamer) play dvds? Where can I get the plugin?

Bob

---

### Post by angryfirelord on 2007-09-27
Add the medibuntu repository first.
[http://medibuntu.sos-sts.com/repository.php]("http://medibuntu.sos-sts.com/repository.php")

As for gstreamer, I'm not sure. I've always used xine for dvds on totem, but if you don't know what to install, I'd install every gstreamer related thing in the repository (except for dbg and doc ones) and see if that plays your DVDs.

---

### Post by divague on 2007-09-27
If you want to play dvds in totem you have to install totem-xine, it will remove totem-gstreamer, and i think you need to install libxine-extracodecs too.

---

### Post by tbroderick on 2007-09-27
It should be able to. Is gstreamer0.10-ffmpeg and gstreamer0.10-plugins-ugly installed?

---

### Post by bwallum on 2007-09-27
Thanks for the response

I have

gstreamer0.10-ffmpeg 
and

gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse

installed according to Synaptic

I don't have the debug or doc files installed.

What should I check next?

Bob

---

### Post by mcduck on 2007-09-27
> **bwallum said:**
> Thanks for the response

I have

gstreamer0.10-ffmpeg 
and

gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse

installed according to Synaptic

I don't have the debug or doc files installed.

What should I check next?

Bob

How about libdvdcss2?  You need that one to view any commercial DVD movie, as those movies use CSS encryption..

That package is not in Ubuntu repositories, but you can get it from  Medibuntu repositories: [http://medibuntu.sos-sts.com/]("http://medibuntu.sos-sts.com/")

---

### Post by bwallum on 2007-09-27
yep...libdvdcss2 on board...next?

---

### Post by m9ke on 2007-09-27
bwallum, I get the same error when I try to play *some* DVDs.  

However sometimes Totem hangs or crashes after throwing this error.

I had installed two plugins that I became suspicious of after the crashes: gstreamer 0.10 (for mms and others); and gstreamer 0.10 (for aac and others).  Both were labeled "bad".  When I read the description I learned that "bad" really just means not fully tested.  I un-installed both.

I get the impression it's encryption related because the DVDs that crashed my system were recent releases, but the DVD that played fine was an ancient release that is unlikely to be encrypted.

I will lurk on this thread to see if I can learn anything that might help solve my problem, or if I can contribute anything that might help solve yours.  Thanks for bringing this up!

m9ke

---

### Post by P235 on 2007-09-27
The ubuntuguide.org page highlights some codecs that may be of help to you.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_play_DVDs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_play_DVDs)

---

### Post by mcduck on 2007-09-27
Also it might be a good idea tto check hat the DVD you are trying to play doesn't have any additional copy protection. At least Sony's ARccOS can be a problem. (VLC at least handles that one pretty well).

---

### Post by bwallum on 2007-09-28
Thanks all

Question:Can totem-gstreamer play dvds?
Answer:No (at 28/9/07)

However, the good news is Movie Player can play dvds.

P235's answer is sound, namely uninstall all totem-gstreamer stuff and install totem-xine. Check out:-
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_play_DVDs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_play_DVDs)

Thanks again everybody, all very much appreciated.

Kind Regards
Bob

---

### Post by bapoumba on 2007-09-28
@ angryfirelord: moved you post in here, as the OP had deleted the first post of the duplicate thread :)

---

### Post by angryfirelord on 2007-09-28
> **bapoumba said:**
> @ angryfirelord: moved you post in here, as the OP had deleted the first post of the duplicate thread :)
Guess I should check where I post. :oops: Thanks!

---

### Post by m9ke on 2007-09-30
I was not ready to give up on Totem and gstreamer, because I had just installed a raft of plugins before stumbling on this thread.  I got it to work well enough that I can't agree that Totem/gstreamer can't ever play commercial DVDs.  I am not posting this to be disagreeable, only because other folks who search out this thread might want this info.

As I mentioned earlier I had installed two plugins that I became suspicious of after the crashes: gstreamer 0.10 (for mms and others); and gstreamer 0.10 (for aac and others). Both were labeled "bad". When I read the description I learned that "bad" really just means not fully tested. I un-installed both.

Then as mcduck suggested I installed libdvdcss2.

The result with these and no other changes:  crashes went away.  I was able to play one DVD that I could not play before.  When I tried to play the second DVD I couldn't play before, Totem refused to play it, with an error claiming I needed a different plugin to play it.  I was able to quit Totem gracefully after this.  These two DVDs are recent release commercial DVDs that are probably pretty well encrypted. All old DVDs I have tried seem to play fine too.

So I had enough success to say I don't agree that Totem can't play commerical encrypted DVDs at all, ever.  My hunch is the second DVD has different or more encryption.  I could probably get it to play with some more poking around for plugins.

Again, only reason I am chiming in here is to let folks know that in some cases Totem/gstreamer can play DVDs.  dwallum, congrats on solving your prob with different software!  Shows there is more than one way to play a DVD in Ubuntu, a good thing I think!

---

### Post by bwallum on 2007-10-01
I have just updated to Gutsy and find that the default is MPlayer not Movie Player. MPlayer runs with gstreamer and fires up out of the box (once you select your desired plugin from a simple radio button window)

Gutsy is a bit flaky still when using an nvidia card. The upgrade loops at the card selection window during first boot. I overcame this by turning off the computer using the power switch instead of pressing the ok button. I also had to select the 2.6.20-16 kernel from the grub menu at start up. The 2.6.22-12 kernel stays in the loop and I havn't worked out how to get past the loop.  Gutsy runs all my stuff ok once you get the desktop up. If you are tempted to try it beware of the install clitch just mentioned.

VLC player is also a very good dvd player and seems to run much better in Gutsy, the sound does not crackle (as I found in Fiesty).

Bob

---

