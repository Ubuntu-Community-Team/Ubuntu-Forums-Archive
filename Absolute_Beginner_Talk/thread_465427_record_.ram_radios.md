---
title: "record .ram radios"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by medya on 2007-06-05
how I can record the radios which are played in Real Player ?

---

### Post by Crafty Kisses on 2007-06-05
I'm not sure what you're asking but if you want to record a stream, there is a program called "Audacity" which works pretty well with the proper codecs installed, to get Audacity go in terminal and type:
```
sudo apt-get install audacity
```
Hope this helps. :p

---

### Post by e6626550w on 2007-06-05
> **medya said:**
> how I can record the radios which are played in Real Player ?

The little recorder called 'sound recorder' works like a charm in recording a station that I may listening to with realplayer. It is installed in the  7.04 under 'Applications/Sound & Video. Not fancy looking but it works and allows you to save as an MP3 which is probably what you want. 

eileen...

---

### Post by medya on 2007-06-06
you mean I put the microhphone infront of the speaker and record the streaming radio ? oh no thats painfull...

---

### Post by FuturePast on 2007-06-06
use mplayer.
```
$ mplayer -dumpstream http://path.to/stream.ram
```

---

### Post by medya on 2007-06-06
any better GUI way ?

---

### Post by 3rdalbum on 2007-06-06
> **medya said:**
> any better GUI way ?

Yes: Go to Applications > Accessories > Terminal.

Now select the following string of text:

```
mplayer -dumpstream http://path.to/stream.ram
```

Switch to the Terminal you just opened and middle-click. Delete the fake URL given and replace it with your real URL (you can paste it in). Press Enter.

-------
Sorry this was a bit flippant, but really it's so easy to do it via the CLI. Writing a GUI frontend for this would take a lot of time and not really be any easier to do.

---

### Post by Blofeld on 2007-08-05
Oh yes it would!!!
For example it would spare from having to suss out which directory streamripper is saving to, and how to stop recording, and stuff like that, especially as recording an audio stream is something that I only ever do once in a blue moon.

---

