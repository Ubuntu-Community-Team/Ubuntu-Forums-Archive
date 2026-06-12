---
title: "volume control has only two &quot;tracks&quot; and maximum volume is not high enough"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by ryu kun on 2006-09-09
Hello everyone!

I have a HP Pavilion dx5158ea laptop. My primary OS is Ubuntu 6.06. My ALSA driver version is 1.0.10rc3. I have two audio related problems/questions:

1. Volume Control (Volume Applet 2.14.3) only shows two tracks (channels) for playback: *Master* and *PCM*. It's the same when I use *HDA Intel ALSA Mixer* and *Generic OSS Mixer*. I'd like to have at least bass and tremble "tracks" (channels) as well. How can I have them, or if there is any, can you please suggest a graphic equalizer running in background to enchant the sound of my laptop?

2. Maximum volume of my laptop is not as high as it is in Windows XP.

Thank you in advance for your replies.

---

### Post by NESFreak on 2006-09-09
1. would be cool to have it. dont know the answer

2. pcm audio is infact pcm vol * master vol wich is logic because the pcm output goes to the master output. so setting both pcm and master on for instance 80% wil result in 0.8*0.8 = 0.64 or 64%

NESFreak

---

### Post by ryu kun on 2006-09-18
> **NESFreak said:**
> 1. would be cool to have it. dont know the answer

2. pcm audio is infact pcm vol * master vol wich is logic because the pcm output goes to the master output. so setting both pcm and master on for instance 80% wil result in 0.8*0.8 = 0.64 or 64%

NESFreak

So, how can I increase the maximum volume?

---

### Post by skymt on 2006-09-18
> **ryu kun said:**
> So, how can I increase the maximum volume?

Short answer: turn both (PCM & Master) all the way up.

---

### Post by ryu kun on 2006-09-18
> **skymt said:**
> Short answer: turn both (PCM & Master) all the way up.

Thanks for the answer but they are already at maximum but volume is still low.

---

