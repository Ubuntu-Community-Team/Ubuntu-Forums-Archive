---
title: "Real Player gone quiet"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by getaboat on 2007-02-03
I'm trying to listen to BBC radio using Real Player 10. This has worked fine in the past. Now though all connects OK looks, it is playing but no sound!. Other apps (Rythmbox etc) work OK. I've tried stand alone and setting a symbolic link so it finds realplay on the path but no joy. Oddly if I try to  use RealPlayer to play MP3 files it says they are in use.

This had been an intermittent prob in the past but shutting all other apps and starting again - sometimes the occaional re-boot - had got it going - not today.

Any pointers welcome.

---

### Post by klytu on 2007-02-03
> **getaboat said:**
> I'm trying to listen to BBC radio using Real Player 10. This has worked fine in the past. Now though all connects OK looks, it is playing but no sound!. Other apps (Rythmbox etc) work OK. I've tried stand alone and setting a symbolic link so it finds realplay on the path but no joy. Oddly if I try to  use RealPlayer to play MP3 files it says they are in use.

This had been an intermittent prob in the past but shutting all other apps and starting again - sometimes the occaional re-boot - had got it going - not today.

Any pointers welcome.

It sounds like the problem might be multiple applications trying to use your soundcard at the same time. I am not sure, but what leads me to theorize this is that you state both that shutting down all other apps and starting again sometimes corrects this issue and that when you try to use RealPlayer to play MP3s it says they are in use. 
[URL="http://ubuntuforums.org/showthread.php?t=205449"]
[COLOR="Red"]**This thread**[/COLOR] [/URL]may be helpful to you.  Read the whole thread but pay particular attention to the section "Getting more than one application to use the soundcard at the same time"

Also, did you confirm the volume on RealPlayer is turned all the way up when you listen to BBC news? I had an odd situation for a while where my RealPlayer volume control worked exactly the opposite of the way it should have. When I would adjust the volume downward on the graphical control, the volume would increase; when I would adjust it upward, the volume would decrease! This issue corrected itself somehow and I never figured out why it happened in the first place.

---

### Post by getaboat on 2007-02-04
Thanks. I've been working my way through that - but no luck so far. Still I found our why everything was so loud! I'm going to get a cheap sound card - rather than on board. Will report back - I may be some time......................

---

### Post by getaboat on 2007-02-05
Progress!

Elsewhere in these forums I found that RealPlayer uses OSS (I'll wiki it later).

and using the info in the link above (thanks)  

I got around to 
> aoss realplay
then select realplay from the BBC gives me sound!

To save having to go into terminal I set up a script in /usr/local/bin called "realplay" to do the aoss for me. 

It's still a bit clunky getting into the player - having to acknowledge two prompts - but I will sort that out next.

It looks to me like the auto detect feature in gstreamer-properties for output gets stuck having made its decision whether to go ALSO or OSS - but I haven't tested that further.

Finally, in the README for RealPlayer (I know - RTFM) it says to > export AUDIO=/dev/dsp2 to force OSS. I tried but I did'nt seem to work for me - anyone know what this would be trying to do?

---

