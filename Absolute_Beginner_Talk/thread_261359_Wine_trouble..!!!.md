---
title: "Wine trouble..!!!"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by lifemaximum on 2006-09-20
hello everyone, new user here

i tried the winecfg code ... the configuration window opened and when i was reading through the setting and making adjustement it went off and than i saw this msg in the terminal
[COLOR="Red"][I]
faz@faz-laptop:~$ winecfg
ALSA lib seq_hw.c:456snd_seq_hw_open) open /dev/snd/seq failed: No such file o r directory
Creating link /home/faz/.kde/socket-faz-laptop.
can't create mcop directory[/I][/COLOR]


so what should i do now ?


and one more thing i got the package for [COLOR="Blue"**]cinelerra_2.0.0-1svn20060611.1_i386.deb** [/COLOR]the movie editor i believe, i got the debian package and used the debain package installer to install it ...

but i got a error msg saying [COLOR="Red"]Error Dependancy is not satisfiable[/COLOR]...so any suggestions???
Edit/Delete Message

---

### Post by DerHesse on 2006-09-20
*but i got a error msg saying Error Dependancy is not satisfiable...so any suggestions???*

You did not use Synaptic? Try it, Synaptic will resolve the dependencies. (use install or reinstall) :razz:

---

### Post by Zorlin on 2006-09-20
I have the same problem,
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /root/.kde/socket-aurora-linux.
can't create mcop directory
whenever I try to open the audio tab in Wine :sad: 
Lol, its starting to get annoying, playing WoW with no sound is sort of... you know, :rolleyes: annoying?
I use Ubuntu Dapper Drake 6.06 LTS x86. I'll try installing Wine again from scratch... :( Anyways, time for bed.
Yes, I'm a 13 year old kid :P
;x
Tried reinstalling, didnt work.
same problem.
pm me if you have answers, cya

---

### Post by deadgobby on 2006-09-20
Agree that you should install by using synaptic. So when you get into synaptic, uninstall and then reinstall.
Gobby

---

### Post by CatKiller on 2006-09-20
You could try re-installing alsa-base and alsa-utils if you're having problems with sound. AFAIK, /dev/snd/seq is a MIDI device, and shouldn't be needed to play WoW, but my MIDI works fine with timidity and fluidsynth and I've never wanted to play WoW so YMMV.

I don't know why it would want to put anything in /root/.kde - are you running it as root on a Kubuntu system or something?

---

### Post by Zorlin on 2006-09-21
No, plain old Ubuntu 6.06...
;x
I tried reinstalling it with synaptic, didnt work...
I tried sudo winecfg but that didnt work either.
All I want is to be able to edit the sound configuration so I can play WoW with sound -.-
Is there some way of editing the sound config manually? :D
EDIT: Tried some stuff, got it to open the sound config eventually, thanks for your help.
Sound is still screwed, so I'm gonna reinstall alsa.

---

### Post by lifemaximum on 2006-09-22
yea me too.. i duno what happen..I had the sound working properly...the next time.. i tried.. it didn work...wine to me...it doesn't seem very stable.. sometimes it closes down by itself...

is there any other substitute for wine?

---

