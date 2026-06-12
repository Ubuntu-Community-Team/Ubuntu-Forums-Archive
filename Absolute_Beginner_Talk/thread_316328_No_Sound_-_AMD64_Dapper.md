---
title: "No Sound - AMD64 Dapper"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by Old Jimma on 2006-12-10
Hi:

My machine is a AMD64 running Dapper. When I pull down system > preferences > sound , there are 3 choice for sound card...

USB Audio Codec
NVIdia CK804, and
MPU-401 UART

I've got a 1/4" plug in that green outlet running from the back of my computer to the RCA inputs in the back of my stereo amp.

THe sound has worked before. I'm not sure what I need to do to make it work again. 

Any suggestions?

THanks,
Phil Smith
DUluth, GA

---

### Post by daou on 2006-12-10
The NVidia CK804 probably is the correct one to use. Right click the volume icon (top right) and choose preferences. Choose the Nvidia CK804 device. Make sure it controls "Master". Make sure your sounds aren't muted (this has been a problem before ;) ). Right click the volume icon again and choose "Open Volume Control" this time. Make sure your master and PCM levels aren't too low (I recommend you don't raise PCM above 75%).

If all this fails then it might be hardware related.

---

### Post by Old Jimma on 2006-12-13
Hi and thanks for your reply...

THe sound now works, but only comes out of one of the 2 stereo speakers. Is it possible to get sound from both speakers?

Thanks,
Phil Smith
DUluth, GA

---

### Post by Old Jimma on 2006-12-13
Hi!

I wiggled the jack that goes into the audio card... and pulling it half way out.... both speakers work.... why the heck is this??

Thanks!
Phil Smith

---

### Post by Sigudian on 2006-12-31
the reason you may get both channels running if your jack is halfway in, is because both of the connectors on the jack is touching the one connector that transmits sound.


i have the same audio card as you, on board on my asus A8N deluxe(or maybe permium, i dont cus know i sendt my delux in again and i think i got a premium back) and the one of the two channles comes out from the on board jack, and the other channel comes out from the front jack on my case. 

although if i disconnect the front jack both of the jacks do not send sound.
im giving up on this sound card in linux, i also had the same problem in windows but my brother in law said he fixed the problem(he had same mother board) by updating drivers, and linux drivers do not afaik exist, luckily my brother may have a usb sound card he does not use.

---

