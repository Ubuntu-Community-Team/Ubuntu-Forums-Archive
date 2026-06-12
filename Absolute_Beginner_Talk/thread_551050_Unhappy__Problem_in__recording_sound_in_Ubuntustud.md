---
title: "Unhappy  Problem in  recording sound in Ubuntustudio 7.04"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by cybersaurabh on 2007-09-14
i have just installed ubuntu studio 7.04.
upgraded it with apt-get upgrade and apt-get dist upgrade.
all went fine but when i tried to record my sound using mic by sound recorder
it didnt worked. i am able to hear sound but no recording.
my mic is working fin in windows xp sp2.
earlier it worked fine in ubuntu dapper.

when i record a sound it shows the number of seconds of recording.
but when i play it nothing happens. whenever i try to save this file
an error occurs

Could not save the file "Invalid Parameters"

My device is Realtek Alc 880 and i am using ALSA for sound capture.

Please help me to fix it.

---

### Post by bwhitaker on 2007-09-14
Do you have the microphone selected and not muted?

Check
```

gnome-volume-control

```
If you do not have the speaker icon in your task bar.

---

