---
title: "Awful sound quality"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by MilesPrower on 2006-03-18
When I use XMMS to play mp3s on Ubuntu, the quality is awful (Much like when you turn speakers up too loud), even at very low volumes. I'm strongly considering using this as my main desktop, but I really can't live with awful quality music.

Is there any way I can fix this? My soundcard is integrated, "Realtek" I believe.

Thanks.

---

### Post by NeghVar on 2006-03-18
I had this same problem. Your not going to like the answer but when I reformatted and used Automatrix to get a bunch of stuff It seems to have fixed itself. I asked on here and got no response so I was left to that.

---

### Post by MilesPrower on 2006-03-18
Well I only just reformatted this morning (Managed to screw Ubuntu up again, damn my curiosity :P).

I'm lost when you say Automatrix though, could you elaborate please?

---

### Post by NeghVar on 2006-03-18
Automatrix:

[http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405)

It worked for me, there is an option about fixing sound in Gnome, I'm not sure if it had anything to do with fixing it or not or if it was fixed when I reformated. I don't claim to be an expert btw, just saying what worked for me.

---

### Post by MilesPrower on 2006-03-18
Cheers mate, i'll fiddle around with that.

If anyone else has any other suggestions feel free to give them to me though! :P

EDIT: Currently in the middle of compiling Wine, i'll give it a try after and tell you how it goes.

---

### Post by therunnyman on 2006-03-18
Hi Guys,

I'm wondering if there's an easier way...

Sounds like your gain is messed up somewhere, most likely software-side.  Have you tried fiddling with the master volume (double-click the speaker icon next to the time and date or, alternately, running Alsamixer in a terminal [just open a terminal and type sudo aslsamixer])?

Here you can look at your device too.  This machine has two sound devices, so I had to select my main device, and set the API to ALSA, as opposed to OSS (both work, by the by).

Apps, too, have volume controls, generally represented with a speaker icon in the app.  Try those, too.

therunnyman

---

### Post by MilesPrower on 2006-03-18
[QUOTE=therunnyman]Hi Guys,

I'm wondering if there's an easier way...

Sounds like your gain is messed up somewhere, most likely software-side.  Have you tried fiddling with the master volume (double-click the speaker icon next to the time and date or, alternately, running Alsamixer in a terminal [just open a terminal and type sudo aslsamixer])?

Here you can look at your device too.  This machine has two sound devices, so I had to select my main device, and set the API to ALSA, as opposed to OSS (both work, by the by).

Apps, too, have volume controls, generally represented with a speaker icon in the app.  Try those, too.

therunnyman[/QUOTE]

Wow, thanks, I lowered the PCM channel a load, and turned up my speakers. Worked perfectly.

Cheers for the speedy response!

---

### Post by therunnyman on 2006-03-18
Good, good, glad to have helped.

It's strange that you'd be getting gain overload (that's fancytalk for the sound you were hearing) from an onboard soundcard...just for reference, what other volume adjustments show up in your control window besides "PCM"?

therunnyman

---

