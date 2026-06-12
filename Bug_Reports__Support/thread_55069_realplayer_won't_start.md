---
title: "realplayer won't start"
date: 2005-08-07
forum: Bug Reports / Support
---

### Post by TravisNewman on 2005-08-07
apt-get installing realplayer from backports installs fine, but it won't start. No error text, nothing, it just doesn't start.

Installing it from the .bin works fine.

---

### Post by SFN on 2005-08-07
Thta's odd. It runs fine here. Just double-checked it to make sure. Ran it both from the menu and as a plugin in Firefox for ifilm.

I'm sure I didn't do the bin install. I'm way too lazy for that.

---

### Post by mingus on 2005-08-07
[QUOTE=panickedthumb]apt-get installing realplayer from backports installs fine, but it won't start. No error text, nothing, it just doesn't start.

Installing it from the .bin works fine.[/QUOTE]

Same here.  When run from the terminal, nothing.  System monitor reports the processes are running.

The .bin you got from the realplayer.com site?  Also doesn't work?

EDIT:  Fixed with making the change to esd.conf

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

I had noticed that previously under Preferences/Multimedia Selector that while ESD would test ok, Alsa and OSS would not.  Yet sound was fine.  Turned off sound server in Preferences/Sound, made change to esd.conf, reset that option, now Realplayer works incl video, as does the Firefox plugin.

---

### Post by npaladin2000 on 2005-08-07
[QUOTE=mingus]Same here.  When run from the terminal, nothing.  System monitor reports the processes are running.

The .bin you got from the realplayer.com site?  Also doesn't work?[/QUOTE]

Hear hear. Don't work. Same deal.

---

### Post by jromer on 2005-08-07
Knowing this might be a different situation but hoping it might help you like it did me...

I had the situation where I run RP and it doesn't play...then 30-60 secs later the file starts. (I believe this would only happen the first time I'd start RP for the session...)

I ended up going into system settings->sound audio and changed the Auto-suspend setting from 30 sec to 10 sec. 

Now RP launches,,,still a little delayed but OK.

---

### Post by lomomo on 2005-08-08
try disabling sound server (esd), when enabled realplayer is not working for me too. i posted a bug report about it.

You can disable sound server using menu system->preferences->sound (i'm not using english version, so it may be not exactly that) and reboot. Or you can just open a terminal and type: killall esd.

It works for me, but i need to enable/disable esd when i want to use realplayer or totem.

---

### Post by mingus on 2005-08-08
[QUOTE=lomomo]try disabling sound server (esd), when enabled realplayer is not working for me too. i posted a bug report about it.

You can disable sound server using menu system->preferences->sound (i'm not using english version, so it may be not exactly that) and reboot. Or you can just open a terminal and type: killall esd.

It works for me, but i need to enable/disable esd when i want to use realplayer or totem.[/QUOTE]

Note my post above.  Did you change the /etc/esound/esd.conf file?

---

### Post by lomomo on 2005-08-08
ooppss! i didn't changed the esd.conf...    :roll: 

i just changed the file and it now works fine. What's the meaning of that options?

---

### Post by mingus on 2005-08-08
[QUOTE=lomomo]
What's the meaning of that options?[/QUOTE]

Enables esound to hand-off to another sound server in 2 seconds.

---

### Post by sujitkumar on 2005-09-10
the solution given above is worked perfectly....
thank u very much...
very very much...

---

### Post by idn on 2005-09-11
Well done mate! Fixed it for me :)

[QUOTE=mingus]Same here.  When run from the terminal, nothing.  System monitor reports the processes are running.

The .bin you got from the realplayer.com site?  Also doesn't work?

EDIT:  Fixed with making the change to esd.conf

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

I had noticed that previously under Preferences/Multimedia Selector that while ESD would test ok, Alsa and OSS would not.  Yet sound was fine.  Turned off sound server in Preferences/Sound, made change to esd.conf, reset that option, now Realplayer works incl video, as does the Firefox plugin.[/QUOTE]

---

### Post by blitzny on 2005-09-13
I can't wirte to the esd.conf. It says I am not the owner..... Wtf?

---

### Post by idn on 2005-09-16
you have to do it as root. 

sudo gedit /etc/esound/esd.conf

---

