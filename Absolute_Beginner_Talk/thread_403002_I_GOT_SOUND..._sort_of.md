---
title: "I GOT SOUND... sort of"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by zzzPOOHzzz on 2007-04-06
ok i have sound on my GAIM but thats about it haha...

i dont know why it wont do it for anything else.... (mp3's, dvd's ogg's... whatever)


any tips?

thanks again

---

### Post by gh0st on 2007-04-06
It sounds as though somethings may be turned down or muted in the mixer. Try double clicking the speaker icon next to the clock in Gnome.

Have a look in there and see if there's anything turned down or muted, if you got sound in Gaim then I can't be a hardware problem I don't think. That would be a good place to start. Let me know what happens and we can take it from there.

Good luck :)

---

### Post by nhandler on 2007-04-06
Or you can enter 'alsamixer' in a terminal. That will let you modify a few more sound levels than the graphical version. Look for anything that does not have a green box below it. That means it is muted. You can unmute it with the M key. The left/right arrows scroll which bar you are at. The up/down arrows increase/decrease the volume.

---

### Post by gh0st on 2007-04-06
> **Cheater said:**
> Or you can enter 'alsamixer' in a terminal. That will let you modify a few more sound levels than the graphical version. Look for anything that does not have a green box below it. That means it is muted. You can unmute it with the M key. The left/right arrows scroll which bar you are at. The up/down arrows increase/decrease the volume.

Yeah good call Cheater I forgot to mention that DOH!! :)

---

### Post by zzzPOOHzzz on 2007-04-06
ive got everything turned up... and its not working...


nforce4 mobo... using optical out (spdif)

---

### Post by sirhalos on 2007-04-06
I think it is more the case you do not have the restricted codecs installed. MP3 for example requrie an extra download because they are not an open source item. Please vist [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) for more information on how to install the restricted formats.

---

### Post by punzak on 2007-04-06
Make sure that you have all of the required repositories installed.  It sounds like your OS isn't recogizing certain filetypes.

open synaptic > search "mp3", "aac", "m4a", etc.

---

### Post by zzzPOOHzzz on 2007-04-08
ive tried all of this and its still not working... now my gaim sound doesnt even work... :(

---

### Post by gh0st on 2007-04-08
> **zzzPOOHzzz said:**
> ive tried all of this and its still not working... now my gaim sound doesnt even work... :(

You said you are using the SPDIF digital out, can you get analog sound out of the card at all?? I just wondered if it was something related to the SPDIF specifically. If you can get analog sound OK then it looks like the SPDIF out need configuring. I've heard people mention this before but I'm not very up on it, sorry :( 

Have a look at these threads, they all concern nForce4 digital sound in Ubuntu. Maybe something in there can help. Sorry I can't do more to help.

 [http://ubuntuforums.org/showthread.php?t=253725](http://ubuntuforums.org/showthread.php?t=253725)

[http://ubuntuforums.org/showthread.php?t=282255](http://ubuntuforums.org/showthread.php?t=282255)

[http://ubuntuforums.org/showthread.php?t=183525](http://ubuntuforums.org/showthread.php?t=183525)

Looking through these it seems a lot of people are talking about installing a new alsa sound driver to get their SPDIF working properly. I don't know if thats any use to you or not.

I wish you the best of luck anyway, hope yo get it sorted soon :)

---

### Post by zzzPOOHzzz on 2007-04-09
man this stinks... im tryin everything... and nothing is working... thanks for all the help though...


:(

---

