---
title: "Speakers not detected?"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by trixx on 2007-09-04
Ok. I have Cyber Acoustics speakers. 2 flat normal ones, one subwoofer. I had Ubuntu a while ago, then reinstalled XP on a seperate partition, lost grub, but now managed to get into Ubuntu with OpenSuSE installer, saying boot installed system. Now, my speakers don't work, and when I try to double click the audio control icon, the little speaker in my taskbar or whatever you want to call it, I get this message:

No volume control GStreamer devices/plugins found.


What's happened? These are NEW speakers, that I got while in XP... my old ones worked fine in Ubuntu. Help please?

---

### Post by the.phantom on 2007-09-04
think it is saying no soundcard?

does anything show up ion 
system>preferences>sound>devices
or system>admin>device manager?
not a expert here just trying to help

---

### Post by trixx on 2007-09-06
Possibly, I'm in Windows ATM, but I don't use a soundcard, I use the built in ones. On the mobo or whatever you feel like saying :P

---

### Post by Hobo Joe on 2007-09-06
Yeah, that's the problem, it's not detecting your integrated card.

You need to tell it to use that card, which you can do by following these instructions:

```

sudo asoundconf list

```
That will show you any sound card(s) that are on your computer, for example, for me, I had two, one was 'nVidia', then other was 'Live', so to make the computer use the 'Live' card, I typed this command:
```

sudo asoundconf set-default-card Live

```
Depending on the name of your card, just replace Live.

---

### Post by trixx on 2007-09-09
Nothing comes up when I type sudo asoundconf list...

just asks for my pw, and then a new command line, christopher@pomroy..... what do I gotta do?

---

