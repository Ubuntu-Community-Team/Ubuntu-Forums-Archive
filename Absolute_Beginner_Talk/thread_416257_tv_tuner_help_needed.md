---
title: "tv tuner help needed"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Gmbrdilos on 2007-04-21
I got ubuntu installed a few hours ago and I love it.
My only problem right now is trying to get my tv tuner to work.
Its an nVidia NVTV by XFX
here is the link manufacturer's page: [http://xfxforce.com/web/product/listConfigurationDetails.jspa?productConfigurationId=1026](http://xfxforce.com/web/product/listConfigurationDetails.jspa?productConfigurationId=1026)

can someone help me plz

---

### Post by Gmbrdilos on 2007-04-21
anyone?

---

### Post by Gmbrdilos on 2007-04-21
a little help will be apreciated :(

---

### Post by Drakkor on 2007-04-21
Have you tried the TVTime software ? Works great for me !  :)

---

### Post by Drakkor on 2007-04-21
It's in the Synaptic Package Manager

---

### Post by Gmbrdilos on 2007-04-21
I may have I am not sure, but so far whatever I tried, nothing would detect the signal. I have heard that NVTV cards are designed specificly for xp media center edition but I wondered if there was a way arround it.

---

### Post by cyberlite on 2007-04-21
trySynaptic and download nvtv worked with me....

---

### Post by Gmbrdilos on 2007-04-21
could you be more specifc on how to do that? this is my second day using linux, thanks

---

### Post by Drakkor on 2007-04-21
Go to System>Administration>Synaptic Package Manager , do a search for either.

---

### Post by Gmbrdilos on 2007-04-21
ok I installed both but my card doesnt show up on the list in NVTV, and tvtime just says no signal and doesnt let me change any options

I don't know if this is important info or not, but my tv tuner is separate from my videocard, and its on a PCI slot by itself

---

### Post by jacksonz123z on 2007-04-21
I have a Winfast TV card.  I had to place a text file in /etc/modprobe.d that contained my cards driver specifications, which are "options bttv card=35 tuner=38".  You will probably need to try something like this.  In which case you will need to track down your cards specs.  I think I found details just by Googling.  Tvtime is my favourite.

---

### Post by Drakkor on 2007-04-21
If you right click in tvtime, do you get a setup menu ?

---

### Post by Gmbrdilos on 2007-04-21
yes menu shows up and I click input configuration, then change video source, but when I click change video source nothing happens I am not shown any options

---

### Post by Drakkor on 2007-04-21
Try "Channel Management" , maybe the mode is wrong ? PAL instead of NTSC ?

---

### Post by Gmbrdilos on 2007-04-21
no its on NTSC alright, I didn't think this would be easy, I know for a fact that the manufacturer requires xp media center for it to operate, but there are a lot of smart people out there and I though maybe someone knows how to go arround it.

---

