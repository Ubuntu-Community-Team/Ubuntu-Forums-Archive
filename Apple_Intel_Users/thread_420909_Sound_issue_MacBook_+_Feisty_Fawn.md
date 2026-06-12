---
title: "Sound issue MacBook + Feisty Fawn"
date: 2007-04-24
forum: Apple Intel Users
---

### Post by infodesk06 on 2007-04-24
Hey All, 
I am a total *nix newbie, so forgive me if I leave out something important or am not getting something obvious. I will answer  any questions you have about the problem. Also sorry if this is a known problem; I could not find it documented anywhere.  I am running 7.04, fully upgraded, on a **MacBook  Core Duo 2.0 with 2gigs ram**. I have a clean install, give or take the fixes to get the hardware configured, like 915resolution and gsynaptics -- nothing outside the community support guide to 7.04 on the MacBook. 

THE PROBLEM is in the system volume control function (the one mapped to the F3-F4-F5 keys). I noticed today when I apt-get'd the flashplugin-nonfree updates that my system volume control was no longer tied to actual volume. At max system volume, sound is tinny and distorted and at minimum, sound is much quieter and more bassy but still on. At no point does the volume go to mute.

I remember reading that there are three (four?) speakers in the MacBook, and I can only guess that whatever system controls the sound is not aware of the audio being sent to one or more of the speakers, and is leaving one or more speakers on accidentally. 
I am interested to know if this is an isolated incident or if it has been duplicated. Please help! I want my volume control to work!
Thanks again, sorry if this is a newbie question. I would have filed a bug report but I get the feeling that I might be missing a technique or an existing patch or package fix.

PS after playing around with AlsaMixer as suggested in another thread it seems that one set of speakers is controlled by the FRONT bus and another by the MASTER bus. Both are affected by the PCM bus. Does this help? Thanks again!

---

### Post by dopira on 2007-04-24
I'm having the same problem too. I just got this problem after I updated to Feisty. I'm running it on a Dell 9300 but it's exactly the same problem as you described. There is a separate bass-y sound that seems to be independent of the master volume control, even when on mute. 

This is sorta a temp-fix but I went into alsamixer in terminal and changed the "Mono Out" setting from "Mix" to "Mic". I don't have that sound at all now anymore and mute actually mutes.  I'm not sure if this helps at all but good luck.

---

### Post by viciouslime on 2007-04-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/102818](https://bugs.launchpad.net/ubuntu/+bug/102818) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm afraid this is a bug :( Please add comments to the bug report.

---

### Post by ronocdh on 2007-04-24
Have you tested with headphones? I have a MBP, so sorry if this seems like I'm reaching too far, but for me the problem was a simple fix: I just went into the Sound control panel and changed what the keys were controlling! There had initially been set to "Front" or something ridiculous like that, which I think worked for headphone volume. Anyway, I just chose "Speakers" and now it works! Brightness control doesn't yet, though. =/

Sorry, I just Advanced Search for the post where I discovered this (wanted to give credit to whoever enlightened me!), and I can't find it. Ah well. Please post back with your results.

---

### Post by trevelyn on 2007-05-06
i have this problem, hrmm, ahh the sound works but sounds really crappy through the speakers, well the right side sounds perfect and the laft side sounds like a blown tweeter.  I plugged in my senheisser hd 280 pro's and the right side ONLY works..  i was thinking of reconfiguring the soundcard, and i always used "alsaconf" (i am from the slackware background) and i have read that ubuntu left it out saying it was "uneeded" (apt-get install alsaconf" says the package isnt in exsistance.  any ideas??? thanks in advance - trev.

---

### Post by russo.mic on 2007-05-10
ronocdh,  sometimes the simplest solutions are the best ones, yet the most overlooked.  

I now feel stupid.  

Just set it to PCM guys,  that will control any PCM audio comming through your headphones or speakers.

Thanks a million!

---

### Post by trevelyn on 2007-05-11
well anyways after my reinstall the sound worked great. ???  i dont know what happened to my computer but now the numlock keys and caps lock keys work fine too but the fan died ???
also whenever i had the sound issue there was a red led light lit up pointing out of the headphones jack anyone ever see that??  wierd.

---

### Post by ronocdh on 2007-05-11
Thanks for reporting the success, guys! Good to see things working well around here every now and then. ;)

I personally have to set up my fan again, as I've recently reinstalled, because this bugger burns like a demon. And Trevelyn (nice name), that red light is because our soundcards also have optical out! Ubuntu doesn't quite know how to handle it, so that's why sometimes--especially in the dark--computing feels like watching an episode of Close Encounters of the Third Kind.

---

### Post by trevelyn on 2007-05-16
well the fan eventuly came back on, thanks for the nick compliment, and everything is running much more smoothly now, except when i try to use skype, or the microphone period.  i get no response when i plug in an external microphone. :( The iSight hasnt worked since i upgraded so i havent bothered trying the built in mic, .. there i tried nothing.. anyone get the microphone working on the macbook??

---

