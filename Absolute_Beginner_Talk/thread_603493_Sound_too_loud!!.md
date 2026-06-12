---
title: "Sound too loud!!"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by sicknature on 2007-11-05
I'd managed to get my sound card working by switching over to my onboard sound card and with:
 
> 
 pcm.dmixed {
   type dmix
   ipc_key 1234
   slave.pcm "hw:0,2"
 }
 pcm.!default {
   type plug
   slave.pcm "dmixed"
 }

Now I got a new problem. No matter how low I set the volume to, the volume is waaaaaaaaaaaay too loud. Just like playing it at a volume of 100%. Even if I'd mute all the channels, and set the volume control only to PCM, it seems like it's still playing @ 100%. I'd also used alsamixer to bring all volume down to 0 and it doesn't solve the problem as well.

---

### Post by TheLions on 2007-11-07
have you checked all inputs/outputs or you have just some like master, pcm and mic?
had you tried with oss mixer?

---

