---
title: "What the VOLUME!?"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by emotionlovesyou on 2008-04-17
This is sort of odd. My volume controls on my keyboard all seem to work fine except for the mute button. What's strange is when I press the mute button nothing happens but on-screen a slash is displayed through the speaker as if it's muted. Strange.

---

### Post by unutbu on 2008-04-17
Hm. This is a wild stab in the dark -- perhaps your sound card has multiple channels and the mute button is muting the wrong channel? 

If you have an alsa card, run alsamixer from a terminal window. You should see a number of different channels. Use the right/left arrow keys to move from channel to channel. Press 'm' to mute a channel. Play a song and test which channel's mute controls what you hear.

Once you know the channel you need to mute (let's say it's the 'Front' channel), then the following command will mute your computer:

```
amixer set Front mute 1>/dev/null
```

Depending on your window manager, there should be a way to link the mute button  keypress to a command such as the one above.

I certainly don't know if this is the best solution. Hopefully someone more knowledgable will comment...

---

### Post by unutbu on 2008-04-17
Also, this page may help:
[http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys](http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys)

---

