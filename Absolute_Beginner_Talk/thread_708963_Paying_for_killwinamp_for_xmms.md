---
title: "Paying for killwinamp for xmms"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2008-02-26
Hello,

I just love Linux. I intent to use it for real. For real meaning for home use, business use, and everything. One thing I always used in windows was Killwinamo. A little app to close winamp/windows after 1 minute/song.

All I can say is that I just need this for Xmms. It puts me to sleep so well..

I know you can somehow do it on the command line. I don't want this. I just want something to click when i'm tired. If somebody can build something with the same functionality as killwinamp, but then for xmms, I'll pay him/her for it. Tell me what you want for it and we'll come to an agreement.

I'll post the result on here, and anybody can use it as well...  (GPL and all that stuff..)

Who puts me to sleep?

---

### Post by northern lights on 2008-02-27
As far as xmms is concerned, I couldn't say, but "amarok" has a "stop after current track option"...

---

### Post by nanotube on 2008-02-27
put the following lines into a text file:
```
#!/bin/bash
sleep 60
pkill xmms
```

save it as, say... killxmms.sh, on your desktop

change attributes to make it executable (right click, properties, permissions)

then all you have to do is double click on it, and it will kill xmms after 60 seconds.

enjoy :)

---

### Post by disturbedite on 2008-02-27
i'd like to recommend you upgrade to audacious.  xmms development died a long time ago.  audacious is its "successor" if you will.  its purpose is the same as xmms's was, only it is still actively developed.

---

### Post by kramer65 on 2008-02-27
I must be honest. I started this thread this night coming home from a night out. Immediatly after writing it I crashed into my bed and slept..

To my surprise I sse this post this morning.. haha.

Thanks a lot anyway! Nanotube, that is such a good tip!!

Is there also a way to close xmms/audacias after 1 track?
Or is there a way to make a little graphical interface in which you can set the number of seconds?

---

### Post by julian67 on 2008-02-27
If you use Audacious then Ctrl+M=stop after current song (or you can check a box in the gui if you prefer).

---

### Post by disturbedite on 2008-02-27
yes you can close audacious after one track.  right-click, then go to Playback --> Stop after current Song.

there is also the option "No Playlist Advance".

---

### Post by nanotube on 2008-02-27
if you want to stop after current track, and do decide to switch to audacious, then ctl-m (or selecting 'stop after current track' from the menu) will do it very nicely, as the previous posters suggested.

if you want a gui entry box where you can type the seconds of delay, here's a simple script you can use:

```
#!/bin/bash
DELAY=$(zenity --entry --title="Audio stop delay" --text="Enter delay (in seconds):" --entry-text="60")
sleep $DELAY
audacious --stop
```

for the last line, i assume you are using audacious, so you can issue a stop command to the default session. you can of course put anything in there, like 
```
pkill audacious
```
to kill audacious (and not just stop it)
```
pkill xmms
```
if you are using xmms and want to kill it

or really anything your heart desires :)

just save the file to your desktop, set it to executable, and you're good to go.

i set the default in the text box to 60, but you can of course edit that as well to be anything you like...

enjoy :)

---

