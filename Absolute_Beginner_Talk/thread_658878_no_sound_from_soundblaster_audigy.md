---
title: "no sound from soundblaster audigy"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by razorbak on 2008-01-05
Just installed 7.10
There is no sound coming frommy Soundblaster Audigy Card.
When I play mp3 files using gxine nothing happens at all ie the time line does't even move.
With VLC the time line moves but no sound. Did I choose an obscure brand of souncard or something? (sarcasm sorry)

I dont know if videos work yet as I cant access any of my video files via the network yet (user name and password required that doesn't exist - more sarcasm).
Actually nothing has worked without having to fiddle or go to the command line and type codes.  Was up most of the night with various problems.  Not very impressed with UBUNTU to be honest at the moment.  I am however determined to struggle on.

---

### Post by c0met on 2008-01-05
Hi,

I have an Audigy2 card and it works fine in 7.10. From my experience, there are three areas that are worth checking. Below are what my system's settings as well as some suggestions to try.

(1) **[COLOR="DarkGreen"]System >> Preferences  >> Sound[/COLOR]**
[LIST]
[*]All the **[COLOR="Purple"]Sound Playback[/COLOR]** text boxes are set to **[COLOR="DarkRed"]Autodetect[/COLOR]**
[*][COLOR="Purple"]**Sound Capture**[/COLOR] text box is set to [COLOR="DarkRed"]**ALSA**[/COLOR]
[*][COLOR="Purple"]**Default Mixer Device**[/COLOR] is set to [COLOR="DarkRed"]**Audigy 2 ZS (ALSA)**[/COLOR]
[/LIST]

(2) Double-click on the speakers up near the exit button. This will open up the [COLOR="Purple"]**ALSA Mixer**[/COLOR] Panel. Make sure that there are no crosses (i.e. muting) for the speaker aspect you wish to hear. Also check that volumes are up.

(3) When you run your choice of sound-player software, just check that the volume of the player is also up. Sometimes, this seems to be turned down.

I hope this gives you some ideas that will help you solve the problem.

Kind regards,
c0met

P.S. If you find a solution that is different from what I have mentioned above, please take a minute to post it in the forum as it will possibly help others.

---

### Post by Daveth on 2008-01-05
I'm with comet on this one and I have never had any real problems with my Audigy 2 either. In addition you might want to add alsamixergui with Synaptic, which will allow you easily to play around with things like 5.1 speaker mixing volumes and such like. It adds it to Applications/Sound & Video.

We are both assuming that you have the right codecs installed, of course!
Please post back if you get no joy with any of this.

---

