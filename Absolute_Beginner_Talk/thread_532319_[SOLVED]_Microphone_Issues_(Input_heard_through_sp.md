---
title: "[SOLVED] Microphone Issues (Input heard through speakers, but not detected by any app"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by SuperAndy on 2007-08-22
I have a NVidia built in soundcard, which i use in Ubuntu as an ALSA device. The output works fine, but the microphone is a bit odd.

If i talk loudly into it, i can hear it through my speakers. But no apps will detect it. I dont seem to have a capture device either, which i think i should do. there is just the ALSA device, and the OSS device, both input.

Am i missing some crucial package or something?

---

### Post by schorsch on 2007-08-22
What do you see if you type "alsamixer" in a terminal and press <TAB> after it starts? You should see the "Capture" Window. It is possible that you have to unmute one channel or pull it up.

---

### Post by SuperAndy on 2007-08-22
ah, seems like it was through the 'capture' channel. turning that right up lets me record audio.

and i can now use it in skype. brilliant!

cheers for that

however, it is a bit quiet. everything is maxed out. is the any way i can manually increase the gain?

---

### Post by schorsch on 2007-08-22
Uhm, sorry, if everything is already maxed out I have no further idea. Perhaps the input jack of your system is not amplified? I had this on my old laptop and I had to buy an active headset to communicate via skype ... sorry ...

---

### Post by SuperAndy on 2007-08-22
that is a possibility

cheers for your help. at least i am getting an input

---

### Post by sailor2001 on 2007-08-22
in your volume control/edit/preferences you can tick a mic boost (+20db)

---

### Post by schorsch on 2007-08-22
Well, if you think this tread is solved, please mark it as solved via the "Thread Tools" availabe as a link in the upper right as it may help other users, too.

---

### Post by SuperAndy on 2007-08-22
i already have that engaged. seems like i need an active mic. thanks for the advice.

and ok, cheers

---

