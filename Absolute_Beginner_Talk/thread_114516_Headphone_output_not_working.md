---
title: "Headphone output not working?"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by TikkiRo on 2006-01-08
[SIZE="3"][COLOR="Purple"]I've got a Trust headphone setup, but currently am using separate headphones to the 4.1 system - so basically I have my speaker output running through the Trust 'box' and out again which is working fine.  The headphones are then in the line out (I think) connection as it's a mic headset and so both are in their required sockets BUT I can't get output to the headphones currently.  Works fine in Windows so unsure why it's not automatically doing so in Linux - sorry for the poor description, but I'm disabled, and my tower isn't the easiest to get round the back of just now to check what's where.  Hopefully someone will have a good enough concept of the likely problem to not need more info on it - any ideas welcomed.  You've all helped incredibly in the week I've used this OS - in such a short time I've had help on all sorts of issues that's been awesome, and SO fast usually too.  Hopefully the trend can continue with this query?  TIA.:cool: :) [/COLOR][/SIZE]

---

### Post by Arktis on 2006-01-08
Well, I'm guessing your soundcard only has one stereo output and you're using that for the speakers while your headset's mic is plugged in properly but not it's earphone part, which is plugged into something entirely incorrect.

I had to get an adapter down at radioshack for my headset, so that I could use both by having the speakers and the headset plugged into the adapter and the adapter plugged into the sound card.  The adapter has a little switch on it that lets me click back and forth between the headset and the desktop speakers.  You probably need something like this.

---

### Post by TikkiRo on 2006-01-09
Actually do have a splitter and it's in use, but my brain sadly isn't.  I know I know the solution here, but for some reason its escaping me entirely.:(  But you did manage to make me at least investigate a bit further than I did at first, and no doubt if I keep on plugging at the problem, something will 'click' and hopefully I'll get it sorted, as it's become a huge issue now in preventing my transferring fully over to Linux as my primary OS.  I do audiotyping which involves transcribing reports using the headphones as the work is confidential (but also awkward to do on speakers), so really now need to resolve this issue.  Just frustrating as it's not an issue in Windows as I've just rechecked it, so can't see it really being a lead problem?  Thanks for your input tho.

---

### Post by Arktis on 2006-01-09
Aha, so it works under windows.  I'm not clear if it's your earphones that don't work, just your mic, or both.  If it were anything besides just the mic that wasn't working, then I'm baffled.

Perhaps you've got something muted.  Enable everything in your volume controls.  Applications > Sound & Video > Volume Control, then Edit > Preferences, place a tick in every checkbox, close, and proceed to investigate the status of all your playback, capture, and switches settings.  You may also want to do the same thing using a different driver (oss vs alsa) as you should have two drivers for each sound system for each card you have.  In the Volume control app you opened, File > Change Device.

I hesitate to say this because I don't want to missdiagnose the problem, but there may also be the small possibility that your driver isn't fully implemented and lacks the proper functionality you need.  Is it made by the manufacturer, or was some poor guy forced to reverse engeneer it or create it from released specifications and therefore is it incomplete?

---

### Post by TikkiRo on 2006-01-10
[QUOTE=Arktis]  Perhaps you've got something muted.  Enable everything in your volume controls.  Applications > Sound & Video > Volume Control, then Edit > Preferences, place a tick in every checkbox, close, and proceed to investigate the status of all your playback, capture, and switches settings?[/QUOTE]

[FONT="Comic Sans MS"][SIZE="3"][COLOR="Purple"]Arktis - you're a GEM - got it in one.  Took me a while to find it, but discovered the settings in the Sound/Capture/PCM was off - shifted that up and suddenly rocking the house down!!   Thanks SO much as it was really doing my head in, trying to figure out why the sound was also always so low in some applications.   Think part of the problem arises from the way in which each media program has its own volume control which seemingly is separate to the main one (in windows usually if you turn down the volume on any media program it affects ALL others I think?) - at any rate totally SORTED - thank you SO much!! :KS :KS :) :D [/COLOR][/SIZE][/FONT]

---

### Post by Arktis on 2006-01-10
w00t! :razz:

---

