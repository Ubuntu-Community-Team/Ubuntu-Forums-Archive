---
title: "Firefox freezes"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by KsR on 2006-10-12
hi all
i am using ubuntu dapper..
The problem occurs whenever i am using firefox...whenever i open a site which has sound of some sort,
...for example, like when i use googletalk(the one in gmail).
now in googletalk whenever somebody sends a message and u are browsing some other page u hear a sound(like in yahoo messenger) informing u about the message.... So whenever this happens firefox freezes..and i have to force quit..this happens also when i open online game sites..eg gamegecko.com..the games with sound cause firefox to freeze...
what can be the problem??
also in sites like gamegecko.com..i am unable to use the Arrow keys to play the games...??...:-k 
:confused: :confused: ...

---

### Post by dmizer on 2006-10-12
with firefox closed, try this:
```
sudo aptitude install alsa-oss
gksudo gedit /etc/firefox/firefoxrc
```
find the line that says:
```
FIREFOX_DSP=""
```
and replace it with this:
```
FIREFOX_DSP="aoss"
```
that should resolve your problem with firefox locking.

as for your other problems with flash, you'll proably be best just to wait until adobe releases its linux version of flash 9 in a couple weeks? months?

ps: you'll find very few people using "u" instead of "you" on this forum.

---

### Post by KsR on 2006-10-13
thanks for the information..
but actually I have already applied the commands you have given.  I got that information from a previous thread in which information was given on how to get sound on videos in youtube.com. Still i checked again and the firefoxrc file already has the line
FIREFOX_DSP="aoss"
Incidently Firefox doesn't freeze when I am viewing videos on youtube..:-k 

ps...will use 'you' from next time..:)

---

### Post by dmizer on 2006-10-13
well, your problem is related to sound mixing.  there's a way in gnome to set the default sound mixer to alsa, but i can't remember how to do it.

i would also suggest making sure anything else you use that makes use of the soundcard also has alsa mixing instead of oss.

take a look at this thread if you haven't already: [http://www.ubuntuforums.org/showthread.php?t=205449&highlight=how+to+make+sound+work+gnome](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=how+to+make+sound+work+gnome)

also, try opening a terminal and typing: firefox

then firefox will open and when it crashes it will exit with an error message that will help with pinpointing the source of your issue.

---

