---
title: "How to record music?"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by paker on 2007-04-08
I want to teach simple songs to a group of men. I have the scores but cannot play keyboard with both hands. Someone suggested that I just play the melody and have the keyboard to the other sound. Here are my questions:

Q 1) I have built-in sound on the motherboard. I think it is AC97 sound. Do I need to buy a sound card?

Q2) What program can I use to record the keyboard and "lower the song by a few notes"? The men don't want to sing high notes.

FYI, I use Ubuntu 6.10 Edgy 32 bit. Thanks for advice.

---

### Post by ronocdh on 2007-04-08
Well, assuming you've already tried Audacity (sudo apt-get install audacity if you haven't), the next thing I would recommend is [http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/).

As far as transposition goes, that's a pretty advanced feature, and I'm not sure even Rosegarden offers it. And if I read your post correctly, you'll be recording your own playing, so can't you just play the music lower and record it that way?

Much luck, and please post back if you find a way to lower the notes! =)

---

### Post by Tylo on 2007-04-09
If you have a keyboard with a MIDI interface, you could potentially record directly to a MIDI program.

Looks for a MIDI to USB cable. I have no guarantee that any of this will work in Linux though, as I've never tried it myself.

There should be some MIDI program for Linux, I imagine, but I haven't explored this myself.

---

### Post by Patrick K on 2007-04-09
Audacity comes a pitch change plugin. You could record then change the pitch. I record with Audacity a lot but have never use this plugin so can't say how well it works.

---

### Post by heimo on 2007-04-09
> **Tylo said:**
> 
There should be some MIDI program for Linux, I imagine, but I haven't explored this myself.

I haven't used midi myself, but there are definitely free midi sequencers for Ubuntu, at least rosegarden and muse. And for multitrack sound recording and editing (digital audio workstation) there's ardour, for EQ/compressor jamin. At least the last two require jack (audio server) which may be a bit tricky to setup (for me it was).

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)
[http://www.muse-sequencer.org/](http://www.muse-sequencer.org/)
[http://ardour.org/](http://ardour.org/)
[http://jamin.sourceforge.net/](http://jamin.sourceforge.net/)
[http://jackaudio.org/](http://jackaudio.org/)
(all these are available through Ubuntu repositories, no need to download and install or compile anything)

---

### Post by paker on 2007-04-09
Thanks for the tips. I will start with Rosegarden, and also will be waiting for the release of Ubuntu Studio.

I am a total newbie and someone please answer this question for me. Once I buy a keyboard, I will have to connect the keyboard midi to computer midi. But I don't have a midi port on the back of my computer. Do I have to buy a sound card with midi port? Thanks.

---

### Post by Patrick K on 2007-04-10
Many gameports server double duty as a MIDI port. You'd have to get an adapter. AC97 supports MIDI but it might not be implemented on your system. So check the BIOS to see if MIDI is supported on your MoBo.

---

### Post by Tylo on 2007-04-11
There's also a good chance there are some MIDI to USB adapters out there, so you could go through your USB drive. Not positive though, :confused:

---

### Post by freeflyer57 on 2008-01-03
> Well, assuming you've already tried Audacity (sudo apt-get install audacity if you haven't)

Audacity worked perfectly. I selected my language and started recording. Thanks for the post.

---

