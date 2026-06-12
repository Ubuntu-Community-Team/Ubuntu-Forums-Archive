---
title: "audio lagging during video playback"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-08-02
while watching videos/movies, my audio will glitch and lag for the remainder of the video. the audio won't match the videos by a sec or two.

i'm running an amd3400, 512mb, decent nvidia video card, and onboard sound.

what would fix this issue?

edit: i've used totem, mplayer, and vlc..they all do the same thing.

---

### Post by Paerez on 2006-08-02
What program are you using?

---

### Post by shanepardue on 2006-08-02
> **Paerez said:**
> What program are you using?

i'm assuming you replied before i edited, haha

---

### Post by patrick295767 on 2006-08-02
> **shanepardue said:**
> while watching videos/movies, my audio will glitch and lag for the remainder of the video. the audio won't match the videos by a sec or two.

i'm running an amd3400, 512mb, decent nvidia video card, and onboard sound.

what would fix this issue?

edit: i've used totem, mplayer, and vlc..they all do the same thing.

Did you try the last codecs from mplayer website 
(for your /usr/lib/win32) ?
  
You might review the sound config with :
sudo alsamixer
that can be sthg wrong but I highly doubts
 
ps -A 
top
to check if maybe there is proc. taking all the cpu.
 
strange

---

### Post by shanepardue on 2006-08-02
> **patrick295767 said:**
> Did you try the last codecs from mplayer website 
(for your /usr/lib/win32) ?
  
You might review the sound config with :
sudo alsamixer
that can be sthg wrong but I highly doubts
 
ps -A 
top
to check if maybe there is proc. taking all the cpu.
 
strange

i got the codecs from automatix so i'm assuming they're somewhat up to date.

as far as the processor, it's looking fine..no overload there.

---

### Post by Paerez on 2006-08-02
are you running Ubuntu AMD64, and if so, does the problem go away if you use Ubuntu 32 bit?

---

### Post by shanepardue on 2006-08-02
> **Paerez said:**
> are you running Ubuntu AMD64, and if so, does the problem go away if you use Ubuntu 32 bit?

nah, i'm using 32bit dapper.

it's like something happens after awhile making the sound fall back a second for the remainder of the video. it's very intermittent. sometimes it won't do it for awhile of watching the video. also, if i fast forward or rewind quite a bit, it will knock it off.

---

### Post by Paerez on 2006-08-02
have you tried using mplayer and giving it a large cache? I use a 4096 cache in mplayer to stop the skipping. I get video+audio skips (they stay in sync but they freeze up). Enabling the cache fixed it.

---

### Post by shanepardue on 2006-08-02
i'll definitely try that out..that sounds promising. right now i'm at work so i'll have to check it out tonight..i'll reply with results.. thanks!

---

### Post by Paerez on 2006-08-02
I would suggest at least 1024 (its in k, by the way). I use 4096 because i have a laptop and sometimes the HD decides to spin down while I am watching something. Setting it really high, like 16384, makes scanning through the file very HD intensive and slow. So go with 1k-8k.

---

### Post by hw-tph on 2006-08-02
I have the same audio lagging with mplayer if I use the default audio output, which is Alsa. Try specifying -ao oss (**mplayer -ao oss filename.mpg**) and see if that helps. If it does you can specify it in you ~/.mplayer/config.


Håkan

---

### Post by shanepardue on 2006-08-02
> **hw-tph said:**
> I have the same audio lagging with mplayer if I use the default audio output, which is Alsa. Try specifying -ao oss (**mplayer -ao oss filename.mpg**) and see if that helps. If it does you can specify it in you ~/.mplayer/config.


Håkan
i noticed [this ]("http://www.ubuntuforums.org/showthread.php?t=186594&highlight=flash+audio")thread that poses a similar problem. flash player in firefox is out of sync also. i bet the alsa default output is my problem.

---

### Post by shanepardue on 2006-08-02
> **hw-tph said:**
> I have the same audio lagging with mplayer if I use the default audio output, which is Alsa. Try specifying -ao oss (**mplayer -ao oss filename.mpg**) and see if that helps. If it does you can specify it in you ~/.mplayer/config.


Håkan
i noticed [this ]("http://www.ubuntuforums.org/showthread.php?t=186594&highlight=flash+audio")thread that poses a similar problem. flash player in firefox is out of sync also. i bet the alsa default output is my problem.

p.s. sorry bout the double-post..isp at work is ridiculous.

---

### Post by Paerez on 2006-08-02
aoss does help firefox, it may help mplayer too.

And it's not your isp at work, the forum is having some duping issues.

---

### Post by Paerez on 2006-08-02
dupage

---

### Post by shanepardue on 2006-08-02
i tried using alsa-oss for mplayer and flash...the mplayer issue i'm beginning to believe it was the file (or codec issues)...i tried opening firefox with the a-oss and it still lags..is this something that can be fixed or do i need a new soundcard?

---

### Post by shanepardue on 2006-08-07
audio lags only on compressed video i've learned..i've tried the a-oss to no avail..do you think it's a hardware issue?

i've tried the same video on a different pc with mac osx and it works fine.

---

