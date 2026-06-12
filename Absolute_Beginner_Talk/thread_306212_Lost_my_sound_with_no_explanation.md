---
title: "Lost my sound with no explanation"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2006-11-24
Okay, five minutes ago, I was listening to my mp3s and going about my regular day . . .then my world came to a screeching halt. For some reason, none of the audio players in Dapper will play sound, although the player is still playing the song in the computer . . .I've made no changes to anything . . .it just stopped. It did not happen mid-song, either. Just when I decided to play another song. Help me!!

---

### Post by deadgobby on 2006-11-24
Did you reboot and see if you can repeat the error?
Gobby

---

### Post by PurplePenguin on 2006-11-24
If you reboot and don't hear the Ubuntu jingle, you might need to run alsamixer and unmute or turn something up (for me, PCM, I think, sometimes mysteriously gets turned down to 0, which turns all of my sound off).

---

### Post by Kadmium on 2006-11-24
First, check alsamixer. If everything is okay there, check if you have selected the right output module in your media players.

I find it very useful to explicitly tell the media player to use ALSA as the sound output module.

---

### Post by kristarella on 2006-11-24
This happened to me as well. I installed alsamixer and there was some things that were muted or turned right down. Thanks for the help!

---

