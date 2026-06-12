---
title: "[SOLVED] Sound stops working on MBP 4th gen (Penryn)"
date: 2008-06-14
forum: Apple Hardware Users
---

### Post by MichaelSwengel on 2008-06-14
Hey all...

This has happened to be twice now. Having just reinstalled Ubuntu yesterday, I set up my audio by adding the line 

```
options snd_hda_intel model=mbp3
```

to /etc/modprobe.d/options

On first reboot, sound works great. After that, I have absolutely no sound in Ubuntu - even with the levels at max.

I've done everything I know how to do. Volume is at max in OSX. I've reset the PRAM. Reinstalled Alsa...

Any ideas?

Thanks,
MS

---

### Post by MichaelSwengel on 2008-06-15
*bump*

No idea, folks?

---

### Post by [woodstock] on 2008-06-15
I have a Macbook Pro 3.1, but sometimes I experience a similar problem.
From time to time, the sound device gets muted (I don't know the cause of this behaviour, nor does this happen regularly) and I have to unmute the channels via "alsamixer" in a terminal. I have to use the terminal, because, strangely, unmuting via Gnome mixer won't work.
BTW, I do not need to add that line in /etc/modprobe.d/options to make the sound work.
Maybe this works for you, too.

---

### Post by MichaelSwengel on 2008-06-17
Alright. I got it fixed. FINALLY. As it turns out, Alsa HAD been muted. I didn't need to use a command or anything. I used Synaptic and installed "AlsaMixerGUI." The PCM line was fine, but somehow the "front" line had been muted. I have no idea how or why, but it works fine now. :) :guitar:

---

### Post by cyberdork33 on 2008-06-17
please mark as solved from the thread tools menu.

---

### Post by MichaelSwengel on 2008-06-19
> **cyberdork33 said:**
> please mark as solved from the thread tools menu.

Ah! Right. Sorry. ](*,)

---

### Post by cyberdork33 on 2008-06-19
> **MichaelSwengel said:**
> Ah! Right. Sorry. ](*,)
no problem. Not many people do it now anyway :)

---

### Post by MichaelSwengel on 2008-06-20
True...but it helps when we do. :)

Thanks again.

---

