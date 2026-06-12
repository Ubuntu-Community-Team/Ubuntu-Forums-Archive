---
title: "sound too low"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by cmaranhao on 2006-10-05
i have a problem and i hope you can help me solve it. at this moment i don't know if i have a hardware problem or software problem.

i am playing some mp3's in amarok but the sound it way lower than it used to be.. yesterday the sound volume was normal but today, i have the sound system at its maximum and the volume is no where near what it used to be.

i also tried some other movie files and the sound is lower than before.

the master volume (near the clock) is at 80% like it was..

can anyone help me? there were some new updates this morning so i don't know if these messed with the sound volume.

---

### Post by jd65pl on 2006-10-05
I think some of the updates may have an influence on this as there is a library for xine, someone more knowledgable may be able to help you out but its not unlikely this has been caused by the update.

---

### Post by cmaranhao on 2006-10-05
i can't remember if there was a xine update today.. anyway, i hope someone can help me.. the sound is way lower than it should be..even with the volume at its maximum

---

### Post by deadgobby on 2006-10-05
There is or was an upgrade for ffmeg I can recall.

---

### Post by jd65pl on 2006-10-05
I have just had an update of

```
libxine-main1(1.1.1+ubuntu2-7.3)
```

I think its the library for audio visual stuff

---

### Post by cmaranhao on 2006-10-05
so what can i do to have the full power of my sound system again?

---

### Post by jd65pl on 2006-10-05
You could revert to the previous version of the package to see if that fixes it by doing the command below to get a different version.

```
sudo apt-get install libxine-main1=1.1.1+ubuntu2-7
```

---

### Post by cmaranhao on 2006-10-05
> **jd65pl said:**
> You could revert to the previous version of the package to see if that fixes it by doing the command below to get a different version.

```
sudo apt-get install libxine-main1=1.1.1+ubuntu2-7
```

just downgraded but the sound volume stayed low :???: any other suggestions?

---

### Post by jd65pl on 2006-10-05
Have you rebooted since downgrading? I'm not entirely sure what else to suggest

---

### Post by cmaranhao on 2006-10-05
yes, i rebooted my pc..

last night, i was listening to some music and the sound was ok.. today, after upgrading (i don't know if it has something to due with this )the sound is too low, i doubt this is a hardware problem.

:???:

---

### Post by Ben Sprinkle on 2006-10-05
Try manually searching the repo's for your library or downgrade to previous?

---

### Post by cmaranhao on 2006-10-05
i already made the downgrade to the previous xine but with no results.. is this the only way to solve this? i don't think my sound system had any problem since last night..

---

### Post by Ben Sprinkle on 2006-10-05
I have had issues with my sound also untill my speakers died, I found that getting the libmp3-mad and libmp3-ugly was somewhat helpful in fixing my sound issues. It works for all music player programs also.

---

### Post by cmaranhao on 2006-10-05
what do those packages do to the sound?

i searched them in synaptic but they aren't there

---

