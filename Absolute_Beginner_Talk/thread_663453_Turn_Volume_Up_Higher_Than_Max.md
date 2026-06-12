---
title: "Turn Volume Up Higher Than Max"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2008-01-10
Is this possible?  It seems like Ubuntu's default "maximum volume" is quite low.

On XP I usually left the master volume at 20-30% and media on full and that was enough to hear any movie fine through my head phones or on the speakers.  Here I have the sound all the way up on the headphone's volume control or the speaker's volume control, the volume control in the upper right hand corner is all the way up, and the media player's volume is all the way up - and it's BARELY tolerable - Is there any way to amp it up higher?

PS:  alsamixer is up all the way too.

---

### Post by Xavieran on 2008-01-10
You may need to turn PCM up as well...

Generally I just keep everything maxed and use manual control...:)

---

### Post by erginemr on 2008-01-10
By issuing "alsamixer" from the terminal, you will reach a text-mode volume mixer. If you are lucky, you should also have a section for headphones. 

Play with the settings to your liking, but I would not recommend you to surpass 0 dB gain for PCM (see the attached screenshot), as when upped to 100%, I began to hear distortions in the sound.

---

### Post by forestpixie on 2008-01-10
> Generally I just keep everything maxed and use manual control...

:D

I also found with my card that I needed to turn up the front control as it was that which was keeping it down

---

### Post by Syndacate on 2008-01-10
> **Xavieran said:**
> You may need to turn PCM up as well...

Generally I just keep everything maxed and use manual control...:)

Uhh...how do I do that?  (I don't even know what PCM is)


[quote=erginemr]By issuing "alsamixer" from the terminal, you will reach a text-mode volume mixer. If you are lucky, you should also have a section for headphones.

Play with the settings to your liking, but I would not recommend you to surpass 0 dB gain for PCM (see the attached screenshot), as when upped to 100%, I began to hear distortions in the sound.[/quote]

If you read the original post you'll see I did that.  First post, last line.

Both the headphones and master in alsamixer are up all the way.

[quote=forestpixie]I also found with my card that I needed to turn up the front control as it was that which was keeping it down[/quote]

front control?

---

### Post by monte48lowes on 2008-01-10
The different sound sources have different volume controls, depending on your sound card. Using 'alsamixer' and raise the volume on everything. Use the TAB key to cycle through the various sections of alsamixer.

Mike


PS. I hope I am not the only one picturing a volume knob that goes to eleven.

:guitar:

---

### Post by forestpixie on 2008-01-10
> front control?

the card has 5.1 capability or some such - I however am not interested, never mattered in windows - feisty gave it a volume slider and it wasn't till I was mucking about one day (with the amp on 11 I might add) that I realised it as affecting the output

> I hope I am not the only one picturing a volume knob that goes to eleven

No - I don't think you are :D

worked in a hi-fi shop many years ago - I got hold of a bunch little stickers with 11 on and stuck them on the vol controls. No sense of humour that man... worked in a bakers shortly after

---

### Post by erginemr on 2008-01-10
> **Syndacate said:**
> 
If you read the original post you'll see I did that.  First post, last line.

Both the headphones and master in alsamixer are up all the way.


Sorry, you are right, I didn't notice. (I was at work at that time and didn't have time to thoroughly read your post.)

Sometimes, Ubuntu is way too much enthusiastic in identifying your on board sound card and use it instead of a secondary PCI sound card if present. Can this be your case (you should see your sound card brand at the top left of alsamixer)? What is your sound card brand by the way?

There is another config under Main Menu -> Preferences -> Multimedia Systems Selector. Playing with its settings might help.

For some geektalk on PCM, see:
[http://en.wikipedia.org/wiki/PCM](http://en.wikipedia.org/wiki/PCM)

---

### Post by Syndacate on 2008-01-11
> **erginemr said:**
> Sorry, you are right, I didn't notice. (I was at work at that time and didn't have time to thoroughly read your post.)

Sometimes, Ubuntu is way too much enthusiastic in identifying your on board sound card and use it instead of a secondary PCI sound card if present. Can this be your case (you should see your sound card brand at the top left of alsamixer)? What is your sound card brand by the way?

There is another config under Main Menu -> Preferences -> Multimedia Systems Selector. Playing with its settings might help.

For some geektalk on PCM, see:
[http://en.wikipedia.org/wiki/PCM](http://en.wikipedia.org/wiki/PCM)

No prob.

I have an SB Live! and an onboard sound card (IC7-G mobo).  I just witched to the mobo's sound card and it appears to have a higher max, nothing ear deafening, but it's a bit louder than it was before.

---

### Post by Syndacate on 2008-01-11
> **erginemr said:**
> Sorry, you are right, I didn't notice. (I was at work at that time and didn't have time to thoroughly read your post.)

Sometimes, Ubuntu is way too much enthusiastic in identifying your on board sound card and use it instead of a secondary PCI sound card if present. Can this be your case (you should see your sound card brand at the top left of alsamixer)? What is your sound card brand by the way?

There is another config under Main Menu -> Preferences -> Multimedia Systems Selector. Playing with its settings might help.

For some geektalk on PCM, see:
[http://en.wikipedia.org/wiki/PCM](http://en.wikipedia.org/wiki/PCM)

No worries.

I have an SB Live! and onboard sound on my IC7-G mobo.  Right now I'm using the SB Live! - it was good enough in Windows.

I switched to onboard sound and it "tests" fine but regular sounds (ie. videos) aren't sounding here?  Hard to tell anything about the volume from the limited sound.

---

### Post by forestpixie on 2008-01-11
did you switch to the onboard sound from within kubuntu without having to turn it on in the bios - 

If so you could try turning it off in kubuntu and in the bios as well - so the only sound card which is on is the sb live

---

### Post by Amstell on 2008-01-11
I have all my volumes up and just use the volume keyboard shortcut to adjust it.  Works great.  I have used the ALSA mixer and that works but don't need it after I adjusted it manually.  Good l uck

---

### Post by Syndacate on 2008-01-11
> **forestpixie said:**
> did you switch to the onboard sound from within kubuntu without having to turn it on in the bios - 

If so you could try turning it off in kubuntu and in the bios as well - so the only sound card which is on is the sb live

I didn't disable it in the BIOS yet but I just switched to the onboard sound today - and it's a bit louder, still not VERY Loud - but there's interference now when I do other things (it makes noises when I scroll and such - interference noises).  You think that disabling the onboard in the BIOS would make it louder?

---

