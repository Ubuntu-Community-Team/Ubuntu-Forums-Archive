---
title: "Sound/driver not recognized"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by DapperMe17 on 2006-11-12
This afternoon I decided to install Dapper 6.06, after testing Edgy 6.10 on LiveCD (No Edgy...locked up on install).

Install was done on a freshy wiped hard drive (Winblows98http://ubuntuforums.org/images/smilies/icon_smile.gif
:)).

Sound was fine in the Edgy LiveCD, but unfortunately there is no sound, or sound card listed under Dapper.

My sound card is an AMC97codec .

Does anyone know of an easy solution?    

Thanks!

---

### Post by cabbageoz on 2006-11-13
G'Day,mine did the same thing with AC97.Found it after awhile only because I still had the headphones plugged in. Swap the speaker Jack with the headphone 
jack and all is well.On mine it is the centre jack on the rear of box.
Regards](*,)

---

### Post by DapperMe17 on 2006-11-16
I'm sorry, but toggling the plugs hasn't worked for me. 
Any other ideas?

Is my soundcard supported in Dapper? It's listed as above.

---

### Post by polly1 on 2006-11-16
Hi

Try this [http://www.ubuntuforums.org/showthread.php?t=197082](http://www.ubuntuforums.org/showthread.php?t=197082) for help.

Also try this command in a terminal     Sudo alsamixer       which will show if your sound card has been recognised

---

### Post by polly1 on 2006-11-16
Hi 

Sorry the command should have read "sudo alsamixer

---

### Post by DapperMe17 on 2006-11-16
Thanks for your reply.

I wasn't complete on the audio card info...

Riptide Audio/Conexant Modem Combination Card 
(Rockwell Chameleon Combo card...AMC97 Codec Controller)

Funny thing...Edgy 6.10 LiveCD gave me sound, whereas Dapper 6 LiveCD & fresh install doesn't.

If this isn't supported, would purchasing an updated sound card do the trick?

---

### Post by DapperMe17 on 2006-11-17
Update...
Both livecd versions of Ubuntu & Kubutnu V6.10Edgy acknowledge my Riptide card & produce sound.

Xubuntu's (would be my preference) livecd V6.10Edgy acknowledges my Riptide card as an alternative to "auto" in the sound settings, but I don't get sound. Should there be a welcome sound upon the desktop loading, as is in Ubuntu & Kubuntu?

---

