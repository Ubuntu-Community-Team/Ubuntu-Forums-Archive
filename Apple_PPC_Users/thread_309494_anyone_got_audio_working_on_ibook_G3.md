---
title: "anyone got audio working on ibook G3"
date: 2006-11-29
forum: Apple PPC Users
---

### Post by albesan on 2006-11-29
hello team,
Just wondering if anyone had any experience making sound work on an ibook g3
I had a look at the comprehensive guido to sound and tried to follow the steps. Looked at the apple specs for my model but it doesn't list the soundcard model ????? beats me.

any help would be appreciated.

a.

---

### Post by brenx on 2006-12-01
try ```
modprobe snd-powermac
```

---

### Post by albesan on 2006-12-01
hey brenx, thanks for the advice.

I did run the code on a terminal but, what is it supossed to do?
I didn't get any output.

A bit more background info, since I posted the thread I've downgraded to Dapper and I do hear the drums on start up but I'm still trying to work out how to play CDs, let alone rip them.

again, thanks for your reply and if you wish to expand on what the code modprobe snd-powermac is supossed to do it would be a great help.

a.

---

### Post by Gen2ly on 2006-12-02
Albe, I too am using an iBook, a rev. A first edition clamshell type.  I installed using the alternate Ubuntu install and got the problem you did.  I have tried using the regular install once before and sound worked normally.  

     I just ran the "modprobe snd-powermac" code and restarted..  didn't see any regular volume bar.  I tried the code once more and went to System / Preferences / Sound.  There I changed the settings from Auto to Powermac DACA.  It works now!  Hope this stays after reboot. :)

Saw on another forum a person had written into etc/modules:

> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

r128
agpgart
uninorth_agp
genrtc
snd_powermac
apm_emu
sbp2
snd-powermac
sr_mod

Wrote snd_powermac and snd-powermac into my /etc/modules.

:After Reboot:

Woot success!  My volume bar works and though I haven't tested it thoroughly it appears to work.

---

### Post by albesan on 2006-12-02
hey Dirk,

Thank you for the advice I got it sorted through easyubuntu, I think.
Anyway it is working now, not really sure how it happened...

a.

---

### Post by Gen2ly on 2006-12-03
EasyUbuntu doesn't have that option though.  This above solution will do the job.

---

### Post by nodorizzi on 2006-12-19
> **Dirk.R.Gently said:**
> Albe, I too am using an iBook, a rev. A first edition clamshell type.  I installed using the alternate Ubuntu install and got the problem you did.  I have tried using the regular install once before and sound worked normally.  

     I just ran the "modprobe snd-powermac" code and restarted..  didn't see any regular volume bar.  I tried the code once more and went to System / Preferences / Sound.  There I changed the settings from Auto to Powermac DACA.  It works now!  Hope this stays after reboot. :)

Saw on another forum a person had written into etc/modules:



Wrote snd_powermac and snd-powermac into my /etc/modules.

:After Reboot:

Woot success!  My volume bar works and though I haven't tested it thoroughly it appears to work.






I did this on mine and it worked great.  I too had this same problem with the alternate CD.

---

