---
title: "\DEV - which erties for the many devices are 'real'"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by John Boy on 2008-02-23
I have an application which reads data from the audiodev and it has a default of /dev/dsp but when I look in my etc directory I have many similar entries. from previous reading here, I believe that my sound card is HDA and there is indeed an entry for that and for adsp one for dsp and one for audio. Is there a command which I can give to see whether dsp/adsp/audio/hda is the correct way to address the device ? I get an initialisation error with /dev/hda. When I point it to adsp the app can initialise iit but times out without getting any data, I suspect even though there is mike input.

             Thanks,

                          John

---

### Post by yabbadabbadont on 2008-02-23
/dev/hda is your primary IDE harddrive....

---

### Post by John Boy on 2008-02-24
Thanks very much for this information. My sound system is High Definition Audio. Through trial and error I found out that /dev/dsp is the correct handle for the sound card but still have the basic question which would help answer the following which is, if I were to add another sound card which /dev handle would I use for it ? Thanks again,

---

### Post by yabbadabbadont on 2008-02-24
It would most likely end up as /dev/dsp1, then /dev/dsp2, and so on.

---

