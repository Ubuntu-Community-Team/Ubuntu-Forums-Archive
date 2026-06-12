---
title: "Volume Screeching"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2007-09-02
I had to tweak my audio settings to get my microphone working for Skype, but now whenever I increase my volume past 85-88%, this loud screeching noise plays. Is there anyway of fixing this without comprimising my running Skype? If not, is there at least a way so that I can lock the volume to not go over the limit (in case i increase it accidentally)?

---

### Post by intense.ego on 2007-09-02
Hasn't anyone else had this problem?

---

### Post by intense.ego on 2007-09-03
anyone?

---

### Post by hamishw on 2007-09-03
Yes, 
It is to do with feedback between the microphone ( I assume it is built in) and the speakers, they are probably very close together and so what is coming out of the speakers is then going back into the microphone and it goes round and round until it builds into a loud screech!
I am on a windows (I know, sorry) PC at the mo and so cannot look to check but from memory you need to double click the volume control on the bar on the desk top, from there you will see various sliders which also have on / off switches for the speakers/microphone etc. Try a variety of settings with those and you should be able to sort it out. Otherwise, maybe a USB microphone which would be further away from the speakers would help.
Hope this helps,
Hamishw

---

### Post by intense.ego on 2007-09-04
I will try fiddling with the volume control bars to see if there is a solution, thank you. The odd thing is that  below 85% there is no noise at all and then when it goes past that, the noise is extremely loud.

---

### Post by irish_flu on 2007-09-04
Some sort of "headset" would also take care of this problem.  As the other poster noted, it's the close proximity of the mic to the speakers that is causing the problem.

---

### Post by jordanmthomas on 2007-09-04
Also, you shouldn't have your PCM setting in the volume controls over about 80%.  If you turn PCM down a little, you're able to turn Master up without the annoying noises.

---

### Post by intense.ego on 2007-09-04
I tried fiddling with the settings, but nothing helped. I tried reducing the PCM, but even at 0, there little or no improvement. If I can't solve the problem, does anyone know if I can limit the volume to 85%?

---

### Post by alienexplorers on 2007-09-04
i found the only way to stop it is to mute the microphone when not in use or lowering the volume until the screeching stops.

---

### Post by intense.ego on 2007-09-04
Is there a shortcut for doing this or do I have to open volume control everytime?

---

### Post by Kitsun on 2007-09-04
> **intense.ego said:**
> Is there a shortcut for doing this or do I have to open volume control everytime?

Why should there be a software solution to a hardware problem, its not logical.

---

### Post by jordanmthomas on 2007-09-04
Yes there is.  Bare in mind I am not sure exactly which slider you moved to fix it, but amixer should do the trick:
```
amixer -q set Master 2- unmute
```
This example lowers the volume of the Master channel by 2 and (if muted) unmutes it.
Modify as needed, put it in a shell script, and throw it in your startup programs for Gnome.

---

### Post by intense.ego on 2007-09-05
Thank you very much.

---

