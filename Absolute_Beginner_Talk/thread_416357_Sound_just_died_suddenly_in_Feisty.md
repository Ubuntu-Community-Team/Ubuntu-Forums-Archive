---
title: "Sound just died suddenly in Feisty"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by b4lr0g on 2007-04-21
Hi,

I was listening to the music in the Rythmbox off my ipod and suddenly the sound just died in the middle of a song. No error message. Nothing. The song kept playing without sound and when I used my earphones I was able to hear the sound.

I tried re-installing ALSA but no luck.

Any help?

---

### Post by DougieFresh4U on 2007-04-21
Have you right clicked open the volume control in upper right corner to see what is checked there (open volume control)

---

### Post by b4lr0g on 2007-04-21
> **DougieFresh4U said:**
> Have you right clicked open the volume control in upper right corner to see what is checked there (open volume control)

Everything is way up in the mixer. Nothing's muted, if that's what you're asking. I don't see any checkboxes there.

The thing is the sound just died *suddenly* and only on speakers. :confused: I think if there was anything wrong there, there wouldn't have been any sound in the first place.

---

### Post by dangerpl on 2007-04-21
Try this command and tell me if it works
> 
 kill $(lsof -t /dev/dsp* /dev/audio* /dev/mixer* /dev/snd/*) ; sudo modprobe -r $(lsmod |grep ^snd |awk '{print $1}') && sudo modprobe snd-hda-codec && sudo modprobe snd-hda-intel model=auto

---

### Post by b4lr0g on 2007-04-21
I saw that command in the other thread and tried it. I even restarted the machine. Still no luck :(

---

### Post by dangerpl on 2007-04-21
What sound card do you have?

---

### Post by b4lr0g on 2007-04-21
Soundcard is Conexant HD. My laptop is HP Pavilion dv6127

---

### Post by b4lr0g on 2007-04-22
Just like that, without doing anything, it just started working again. Weird!!!

---

