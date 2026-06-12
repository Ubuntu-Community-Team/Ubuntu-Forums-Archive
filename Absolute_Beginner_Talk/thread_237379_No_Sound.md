---
title: "No Sound"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by Lopsicle on 2006-08-16
Most of the time when I boot up Ubuntu I have no sound, sometimes I may have to restart 3 or 4 times before it will work. I still have windoz on another hard drive and this works ok.This problem has only just started since changing to Dapper. Anyone have any ideas why this is happening? :rolleyes:

---

### Post by Kobalt on 2006-08-16
Hello,
what kind of soundcard do you have ?

---

### Post by Lopsicle on 2006-08-16
I'm not sure, how do I find out? ;)

---

### Post by araz on 2006-08-16
I have the same problem.

lspci:
> ...
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
...

---

### Post by xpod on 2006-08-16
I had a similar prob when i first got up and running.
Although i could listen to music via rhythmbox(radio & cd`s)i could`nt hear sound online with google video,you tube etc etc.

This was only something i discovered AFTER installing automatix and getting the usual java& flash etc..I could see video but still had no sound.

Dont know if this is similar.....mabey try your radio on rhythmbox THEN see what else your not getting sound from....OR have you mabey already tried EVERYTHING i suppose??...better to ask now eh

Just a thought......It was a couple of simple lines of code that sorted me out but i dont know EXACTLY what they did(yet) SO you`d need to see if this is the same prob i had first.......Is your video fine etc etc


PS...look in your device manager.....SYSTEM/ADMINISTRATION/DEVICE MANAGER

you`ll find your sound cards name in there i believe

---

