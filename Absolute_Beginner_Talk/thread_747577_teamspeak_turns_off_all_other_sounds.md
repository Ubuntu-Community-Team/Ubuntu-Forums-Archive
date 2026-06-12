---
title: "teamspeak turns off all other sounds"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by FlashBastardDX on 2008-04-06
Here is my problem. Whenever I start ventrilo, or teamspeak, all my other sounds stop working. Does anyone know why this is, and how I might fix it. I'm using a USB headset, but I have speakers hooked up with a decent soundcard.

---

### Post by Matthewslf on 2008-04-07
I get the same problem. It is becuase the programs take control over the entire sound card so that they don't get interrupted. Try looking into PulseAudio.

---

### Post by hyper_ch on 2008-04-07
install "aoss" and then prepend the ts2 start command with "aoss"

---

