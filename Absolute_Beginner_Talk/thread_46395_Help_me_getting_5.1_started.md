---
title: "Help me getting 5.1 started"
date: 2005-07-04
forum: Absolute Beginner Talk
---

### Post by mutey on 2005-07-04
Hello,

first of all, i am using 2 soundcards. one is onboard, the other one is a soundblaster audigy 2 ZS.

Both work fine, I can listen to music on both devices. Music plays on all 5 speakers and the subwoofer works great.

But when I want to watch movies with 5.1 sound the sound is still upmixed to all speakers. I have no surround sound.

I am using the xine lib and alsa, and yes I have chosen 5.1 surround as my speaker arrangement. 

This is my asound.conf:

```

pcm.card1 {
type hw
card 1
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:1,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}

```

---

