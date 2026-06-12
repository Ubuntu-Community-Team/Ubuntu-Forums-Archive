---
title: "new to linux... sound problems someone please help!!!"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by terabandit on 2006-07-09
i have just installed ubuntu for the first time so far i'm impressed although  having a small issue with the sound, heres my problem... the system sound works i can listen to cd's play dvds but the problem is the sounds really quite i can hardly hear it... i have tryed the alsamixer thing and everythings maxed out. i've done heaps of research with no results, can someone help i do a podcast and i need the sound working asap ! 

     Thankz all !  ](*,)

---

### Post by woedend on 2006-07-09
does adjusting the alsamixer up and down do anything at all?  it may not have the correct card detected?

---

### Post by terabandit on 2006-07-09
i'm starting to think that it dosn't have the right card detected... i have a HP Pavilion dv8308TX laptop... how do i know if i have the correct driver installed... ? and or how do i correct this ?

    thankz for the help !

---

### Post by siccness on 2006-07-09
Quick research then, I think your audio is: Conexant High Definition Audio Drive (which might be RIPTIDE?)

Edit:
[http://h10025.www1.hp.com/ewfrf/wc/softwareList?lc=en&cc=au&dlc=en&product=3201111&lang=en&os=228](http://h10025.www1.hp.com/ewfrf/wc/softwareList?lc=en&cc=au&dlc=en&product=3201111&lang=en&os=228)

---

### Post by terabandit on 2006-07-09
ok so the windows xp driver is this one [http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?lc=en&cc=au&lang=en&os=228&product=3195787&dlc=en&softwareitem=ob-40639-1]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?lc=en&cc=au&lang=en&os=228&product=3195787&dlc=en&softwareitem=ob-40639-1")

but the HP website dosent have support for linux... how do i find a linux driver and install the dam thing... ?

driver needed ( Conexant High Definition Audio Drive )

---

### Post by siccness on 2006-07-09
Try this, open up a terminal and type:

```
sudo alsaconf 
```

Follow what it says, and see if that has any results.

---

### Post by terabandit on 2006-07-09
nah... it told me " command not found " ... any more ideas?

---

### Post by siccness on 2006-07-09
> **terabandit said:**
> nah... it told me " command not found " ... any more ideas?

Eek, it's not installed. Ok, load up Synaptic, and search for "ALSA". See if you can find anything that says either alsa-utils or alsa conf - or anything that looks right :)

Sorry, I'm not in Ubuntu at the moment to have a look myself

---

### Post by terabandit on 2006-07-09
ok... so i do have the alsa-util'z installed .. should this command work in the console ?   ( sudo alsaconf ) ? i type it in and it prompts me for my password then just comes up " command not found "  anymore suggestions ?

---

### Post by terabandit on 2006-07-09
with driver support for linux how can i find a good driver for my laptop ? cause Ubuntu has loaded a basic defualt i think... its loaded ( Generic 14f1 ID 5047 ) if that makes sense to anyone... can i correct this, because i have a weird feeling it will correct my sound problem . 


            CHeer'z Andrew

---

### Post by woedend on 2006-07-09
i think you need alsa-tools(if thats still a package).
if you still can't get it, you can TRY this
[http://www.linuxant.com/drivers/riptide/install.php](http://www.linuxant.com/drivers/riptide/install.php)

but I can't make any promises or help much as 
a)not positive its your driver
b)haven't installed it.

---

### Post by terabandit on 2006-07-09
i tryed installing the driver... just got a few errors no luck ...any other idea's?

---

### Post by terabandit on 2006-07-09
Conexant AC-link  audio system ~ thats whats in my laptop still can't find a driver.. please anyone help! i have a podcast due out soon need this thing working...   apreciate any kind of suggestion or input !

---

