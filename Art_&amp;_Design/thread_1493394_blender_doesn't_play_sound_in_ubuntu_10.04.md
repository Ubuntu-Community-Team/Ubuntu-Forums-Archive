---
title: "blender doesn't play sound in ubuntu 10.04"
date: 2010-05-25
forum: Art &amp; Design
---

### Post by Salvagluque on 2010-05-25
Hello

I've this problem with blender (2.49b & 2.5 alpha 2). it doesn't play any sound strip in the sequencer or game logic. Nor scrubbing nor playing it back.

I found out this with a terminal

export SDL_AUDIODRIVER=alsa && blender -g noaudio

IT opens blender but nothing. The terminal just keeps writing

NO AVAILABLE AUDIO DEVICE

Also tried adding SDL_AUDIODRIVER=alsa in /etc/environment with gedit.

How can I make it to detect it.

thanks in advance

---

### Post by Salvagluque on 2010-05-26
I found the way to solve it by opening a terminal, I have tried it in the 2.49b version, and works there.

export SDL_AUDIODRIVER=pulse && blender -g noaudio

To ubuntu do it automaticly. open a terminal and write:

sudo nautilus

then add your password.
This will open a browser, in which you will serchh this address  /etc/.
Feom there look for environment and open it by right-clicking and selecting gedit.

In the text editor write this at the end of it
SDL_AUDIODRIVER=pulse
then save it, restart the cpu and enjoy.

remember to activate sync and scrub in blender.

---

### Post by stoneage on 2010-09-27
Thank you, solved for me too 


   :)

---

