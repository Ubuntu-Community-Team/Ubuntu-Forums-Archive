---
title: "Totem and ALSA ???"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by dalani on 2006-02-11
Whenever I try using Totem to play MP3,  I keep getting the following message: ```
ALSA device "default" is already in use by another program.
```

CAn anyone elucidate this??

---

### Post by wolfmaniac on 2006-02-11
me 2 facin the same .

installed all the drivers
configured the sound to work but not able to solve it.

also when i play divx and dat files in gxine i donot get sound with vedio .can some one help.

gxine plays VOB files properly

---

### Post by dalani on 2006-02-12
Looks like we must solve this one ourselves. I did some quick checking and it seems it be  a missing codec problem. The distro does not ship with all the codecs needed.

Personaly I find all this annoying. Because MP3 and other formats are lossy ie. they degrade the studio CD digital audio quality by compressing the file for downloading. 

I have Totem on my box and it does not play back any of my *.avi videos from my digital camera. Can anyone post a wiki/ howto that explains Ubuntu's real audio/video capabilities and/or limitations with instructions to make media ready???

An aside: the Multimedia prospects look bleak for linux if big players like Intel and MS push ahead with more proprietory standards.

---

### Post by BoyOfDestiny on 2006-02-12
In terms of sound devices being in use, I blame esd. Open up a terminal, type "sudo killall esd", then try playing it. If it's a codec problem, try using an app like beep-media-player and make sure libmad is installed.

If it turns out ESD is the problem, go to System->Preferences-> Sound, uncheck enable sound server, and use System->Preferences multimedia selector and choose alsa as the default output. 

good luck

---

### Post by dalani on 2006-02-13
Bang On! that solved it! I ran «sudo killall esd» at the terminal and ALSA is re-enabled. thanks dude

---

