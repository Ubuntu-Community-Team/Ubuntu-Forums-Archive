---
title: "maple fonts via ssh"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by teitur on 2006-12-17
Since i'm a absolute beginner i post this question here first and if it's the wrong place maybe someone can redirect me.

So, my problem is that i'm running maple 8.01 using a ssh connection to my account at my school. Everything works fine (calculations, plots etc.) except mathematical fonts seem to be unavailable. If i do e.g. 
> int(f(x),x);
mapel will display the result as

ó
ô f(x) dx
ö

instead of drawing an integral sign. So, I don't know, does anybody know what's lacking or at least where I should start to look for the error.

By the way, fonts work fine if I run maple 10.? at another account in the States (I'm located in Stockholm). Also, before my other computer with debian (unstable) broke down this morning, maple via ssh was running flawlessly on that one. I'm running ubuntu edgy (mostly, .. i think).

---

### Post by Ecthelion on 2006-12-17
> So, my problem is that i'm running maple 8.01 using a ssh connection to my account at my school. Everything works fine (calculations, plots etc.) except mathematical fonts seem to be unavailable. If i do e.g.
> int(f(x),x);
mapel will display the result as


You can install maple on ubuntu if you want.
I've done it using [this howto]("howtohttp://ubuntuforums.org/showthread.php?t=283473&highlight=maple+10+edgy") and it works just fine.
Or doesn't your school give the possibility to download the maple10linux software?
(maybe you could ask them?)(or even sent a mail to maplesoft... Maybe they'll help)

---

### Post by Delkster on 2006-12-17
> **teitur said:**
> mapel will display the result as

ó
ô f(x) dx
ö

instead of drawing an integral sign. So, I don't know, does anybody know what's lacking or at least where I should start to look for the error.

What character set is the remote account set to use? You could check the locale settings with the 'locale' command when logged in to the remote machine.

Ubuntu uses UTF-8 by default, so if the remote machine also uses it, the problem may be in fonts or something. I'd check the locale settings first, though.

---

### Post by teitur on 2006-12-17
Thanks Delkster, you are right. On my computer the locale output is
teitur@judas:~$ locale
LANG=en_US.UTF-8
LANGUAGE=en_SE:en
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

and on the school server it is
annika:~>locale
LANG=
LC_CTYPE=en_US.ISO8859-1
LC_NUMERIC="C"
LC_TIME="C"
LC_COLLATE="C"
LC_MONETARY="C"
LC_MESSAGES="C"
LC_ALL=

I don't know to much about locales though. Do I really need to change the locale variables on my computer to get the fonts right. I tried to change the character-encoding of the terminal window (which I realize has probably little to do with the problem) and not to unexpectedly that had no effect. I'm not to proud of the formulation, but I guess what I'm trying to say is what do I do next?

---

### Post by Delkster on 2006-12-24
> **teitur said:**
> I'm not to proud of the formulation, but I guess what I'm trying to say is what do I do next?

Sorry I haven't been around in a while. I don't have time to elaborate an answer now but I still haven't forgot about the whole thing and I'll check back after Christmas.

---

### Post by Delkster on 2007-01-03
Have you had any luck yet?

I don't know almost anything about Maple but I'd probably try one of the following:

- Change the terminal character set to ISO-8859-1 when you run Maple. This is a bit tedious, though, and it seems that you may have already tried it.
- Try running Maple with a UTF-8 locale on the server. I don't know if Maple works well with this but you might want to give it a try. Try commanding for example "en_US.utf8" on the server before running Maple.

---

