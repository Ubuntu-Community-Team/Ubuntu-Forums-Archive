---
title: "kaffeine withdrawal"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by niteblind on 2006-06-25
hi all,

anyone got any idea how i sort this out? I understand the kaffeine shich comes as standard on kubuntu will play mp3s. well mine wont.

If i click play it jumps straight to the end of the track so i think the codec is mising only thing is xmms will play the track fine so the codec is somewher on the pc.

anyone got any suggestions?
niteblind

---

### Post by drtvasudevan on 2006-06-25
have a look at [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
that shd help

tv

---

### Post by niteblind on 2006-06-25
i seem to alreadu have all te codecs listed there anything else i can check. is there a way to check and see if kaffeine is pointing to the corect codec for mp3?

niteblind

---

### Post by Jucato on 2006-06-25
Ubuntu does not provide built-in MP3 (and other propriety formats) support. Although Kaffeine and Amarok CAN play MP3s, you have to enable it by downloading the necessary codecs. For KDE multimedia apps, you only need one: libxine-extracodecs from the multiverse repositories. 

Follow the link drtvasudevan gave and scroll down to the part about MP3 and Kubuntu Dapper. Take note to follow the instructions specifically for Kubuntu Dapper only.

---

### Post by gingermark on 2006-06-25
Are you using the xine engine? If you are using Dapper then it is likely you are, but it's worth checking.

---

### Post by niteblind on 2006-06-25
okay i think this may be the issue i cannot find libxine-extracidecs in the repositories i have. does anyone know where i should be looking to fine one that it is on. I will probably need an FTP one as i have a dumb router that is blocking the http ones (dont ask and dont buy belkin)

niteblind

---

### Post by gingermark on 2006-06-25
it's located in multiverse. Basically when you see "universe" in your sources.list you type "multiverse" after it. Dunno about ftp, but if you have trouble maybe you could browse to and download it from [http://packages.ubuntu.com/dapper/libs/libxine-extracodecs](http://packages.ubuntu.com/dapper/libs/libxine-extracodecs)

---

### Post by niteblind on 2006-06-25
thanks for the response i had tried that earlier but when i opened it with firefox nothing happened so i though i was doin somehting wrong. being that u suggested it i tried again and this time saved it to disk before running it and now i can play mp3s  WOOHOO!!!

now just gotta find a way to install a mouse theme i can see properly and a few other bits and bobs and then hopefully i can leave u lot in peace (at least for an afternoon or 2 :D)

cheers all for the help

niteblind

---

