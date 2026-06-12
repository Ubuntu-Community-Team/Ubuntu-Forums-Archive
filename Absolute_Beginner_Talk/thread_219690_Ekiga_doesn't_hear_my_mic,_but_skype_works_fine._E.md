---
title: "Ekiga doesn't hear my mic, but skype works fine. Ekiga was working before."
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-07-20
hello, i can't get ekiga to hear what i say on my mic. But things are okay when i use skype. what's wrong? ekiga used to work fine before.

---

### Post by fabiand on 2006-07-20
Hey,

you might try to configure ekiga via the wizzard again ...
can't remeber where to find it ... but isn't far away..

---

### Post by hanzj on 2006-07-20
fabiand,
i have tried the "First Time Configuration Assistant" (Edit/Configuration Druid). Is that what you are referring to?

---

### Post by hanzj on 2006-07-21
I have also tried twinkle and it doesn't work.
When I call sip:500 ekiga net, which is the echo test, I can hear the lady's oice, but I cannot hear my own voice being played back (being echoed) back to me.

Removing and then re-installing ekiga doesn't help.

please help

---

### Post by fabiand on 2006-07-21
Hey,

try to set a different audio device in the preferences.

---

### Post by hanzj on 2006-07-21
fabland,
i can't. alsa is the only choice.

---

### Post by hanzj on 2006-07-21
I have some info that may be related to this. I really think this info is connected. Here it is:

n System/Preferences/multimedia Systems Selector, when I press the "Test" key under Default Audio Plugin (while ALSA is the Plugin which is selected), I get an error message

" Advanced Linux Sound Architecture: Could not open resource for reading."

---

### Post by hanzj on 2006-07-21
SOLVED!

 I went to VolumeIcon->RightClick->Open Volume Control-> Capture Tab.


Though Capture/Mic was on, Capture/Capture was off. So toggled Capture/Capture back to "on".

I was also able to get rid of the echo in my voice. Before, when I said "Hello", I heard back "Hello-lo-lo-lo". But I muted the
Capture/Capture, and no more echo.

Now I need to figure out how to get rid of the echo the other party hears of his own voice when I do a call via a finarea service (SIP to SIP (which is really to a phone)).

---

