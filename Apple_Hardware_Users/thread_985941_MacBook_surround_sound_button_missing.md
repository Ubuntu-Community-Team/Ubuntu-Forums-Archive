---
title: "MacBook surround sound button missing"
date: 2008-11-18
forum: Apple Hardware Users
---

### Post by regebro on 2008-11-18
The sound in my MacBook is terrible. As far as I can figure out from other answers here, this is because MacBooks have three speakers, but Ubuntu by default only uses the two small ones.

The solution to this seems to be to unmute the "Surround" speaker in the Mixer. Problem is: I don't have any such think in my mixer, neither in the "Volume Control" app or in alsamixer.

Anybody know what's going on?


MacBook 4,1 2.4Ghz.
Ubuntu 8.10.

---

### Post by regebro on 2008-11-18
Also, the external microphone doesn't seen to be working. 

I have the snd_hda_intel driver, but /proc/asound/card0/codec#0 says "Codec: Realtek ALC889A", I don't know if that's normal?

---

### Post by issih on 2008-11-18
Ditto on a Macbook 3.1.

I've tried fiddling quite a lot, and have never managed to stop the sound being annoyingly tinny.

---

