---
title: "Low sound volume"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by fastb on 2007-04-19
I've just installed feisty and sound works fine except it is so low. I have a toshiba laptop which has an analog volume control. I increase it to maximum so I can hear the noise but the volume of the sound is still low. I go to the volume control and the master is to the maximum.


What should I do?

Thanks

---

### Post by Seisen on 2007-04-19
Type this in the terminal
```
alsamixer
```

Just expermiment with each setting and to mute or unmute, press the "m" key. If its green its not muted.

---

### Post by fastb on 2007-04-19
Done that. I cant even adjust the master bar, just PCB. The master is always on 00. And I noticed that the sound sounds like it scratches.

---

### Post by mand0 on 2007-04-19
> **fastb said:**
> Done that. I cant even adjust the master bar, just PCB. The master is always on 00. And I noticed that the sound sounds like it scratches.

Did you use the left and right arrow keys to move to the other columns ?

---

### Post by fastb on 2007-04-19
Ofcourse. I have also gone to the sound manager where you can select different sound mixers and sttuff. I tried different, but no success.

---

### Post by dangerpl on 2007-04-19
I also have a Toshiba laptop... I muted the mic which i dont have but still the volume kinda jumps... its low most of the time and from time to time it jumps up to full..

---

### Post by granite230 on 2007-04-19
I also have a Toshiba laptop. Same problem. If I type *alsamixer *in the terminal I see the slidebars but the master volume stays at 0. Arrow up has no effect on that master slider... :confused:

---

### Post by bobtherocket on 2007-04-19
Same issue...:P

---

### Post by cam2009 on 2007-04-19
same problem here. it jumps back and forth from mute, almost mute, and normal. toshiba satellite a105.

---

### Post by bobtherocket on 2007-04-21
[http://ubuntuforums.org/showthread.php?t=416207](http://ubuntuforums.org/showthread.php?t=416207)

Just spreading the word....:P

---

### Post by alinuxfan on 2007-04-22
I am having the same problem with my toshiba laptop!!
Dangit


Adam

---

### Post by WishMaster on 2007-04-23
I *had* this problem with Acer TravelMate 661LCi.
The "alsamixer" command fixed it for me (PCM mixer was almost muted)

---

