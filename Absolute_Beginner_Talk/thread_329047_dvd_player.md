---
title: "dvd player"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by rbhigday on 2006-12-31
I am trying to watch dvd movies on my laptop.I dl totem movie player and xine movie player and TOTEM does not play dvd and xine says my dvd is encrypted which it not i just bought it at walmart.

Thanks

Rich

---

### Post by deadgobby on 2006-12-31
Did you install the codecs?

---

### Post by rbhigday on 2006-12-31
> **deadgobby said:**
> Did you install the codecs?

Codecs? Yep i am a newbie? guess i will go look in the repository for these

---

### Post by NeoLithium on 2006-12-31
[This]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs") should help you get the proper codecs installed :)

---

### Post by qamelian on 2006-12-31
> **rbhigday said:**
> I am trying to watch dvd movies on my laptop.I dl totem movie player and xine movie player and TOTEM does not play dvd and xine says my dvd is encrypted which it not i just bought it at walmart.

Thanks

Rich

If it's a purchased DVD movie then it very probably is encrypted. You need to install libdvdcss2 to be able to decrypt the disc. Very few commercial releases are not encrypted. Usually only old, low budget releases for which copy right is expired. Instructions are available at:
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/dvdplayback.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/dvdplayback.html)

---

### Post by 3rdalbum on 2006-12-31
> **rbhigday said:**
> I am trying to watch dvd movies on my laptop.I dl totem movie player and xine movie player and TOTEM does not play dvd and xine says my dvd is encrypted which it not i just bought it at walmart.


You can enable DVD playback by going to this link and following the instructions: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

Your DVD is encrypted. The vast majority of commercial DVDs are encrypted, and are decrypted on-the-fly by standalone DVD players and licensed DVD playing software. Since the decryption keys are costly for software developers to obtain, and you paid nothing for this operating system, they are not included. The library that you installed through the above link is unlicensed, and illegal in your country.

---

### Post by rbhigday on 2006-12-31
> Stubby: gstreamer dvd plugin not ported to Edgy yet. following instructions will not work properly

does that mean i have to wait till they are ported to edgy?

---

### Post by rbhigday on 2006-12-31
Thanks everyone for the help, the dvd's now load :)

---

### Post by Sigudian on 2006-12-31
you could always do it as easy as just installing VLC, this is the most fantastic media player i know, and afaik it runs movie files form its raw format eliminating the need for codecs, and yes it runs DVD's out of the box(even iso's of DVD movies) witout the need of any codecs.

---

### Post by macogw on 2006-12-31
> **Sigudian said:**
> you could always do it as easy as just installing VLC, this is the most fantastic media player i know, and afaik it runs movie files form its raw format eliminating the need for codecs, and yes it runs DVD's out of the box(even iso's of DVD movies) witout the need of any codecs.

I get sound and no picture on the Matrix and Matrix Reloaded and AFI "I Heard a Voice" on VLC.  Movie Player with xine backend + codecs is working fine though.

---

### Post by Sigudian on 2006-12-31
> **macogw said:**
> I get sound and no picture on the Matrix and Matrix Reloaded and AFI "I Heard a Voice" on VLC.  Movie Player with xine backend + codecs is working fine though.
try to run
```
 % sudo apt-get install libdvdcss2
``` it might be because of different region, and this is a plugin for VLC to support region free.

EDIT:
"universe" repository is needed to be enabled for that command to work

---

