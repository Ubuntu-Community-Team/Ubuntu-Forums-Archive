---
title: "Sound from front speakers only!"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by old_geekster on 2007-01-17
I am using  the on-board sound module (karajan) on my DFI UT nF4 Ultra-D motherboard.

In WindowsXP Pro, I had to clone the front speakers to get the rear speakers to work.  How can I get them to work in Ubuntu?

I will appreciate any help.

---

### Post by Garyu on 2007-01-17
Not sure about your hardware, but this worked for me:

1) install alsa sound support and alsamixergui
2) in alsamixergui, make sure that the PCM and Front are enabled. For older versions (if you're running Dapper), check that "Duplicate front" is enabled. If it doesn't work, play around a bit. Or try alsamixer in a terminal. 

Also, from the main menu, choose System -> Settings -> Sound and then make sure that ALSA is your sound system. 

BTW, on one of my computers the jacks for surround and subwoofer and so on was switched compared to Windows. So you might want to try and move the jacks around and see if you notice a difference.

Hope this helps.

---

### Post by phansiizwe on 2007-01-17
In alsamixer, my front, rear and center speakers are controlled via the "PCM Front", "PCM Center" and "PCM surround" sliders. If they don't appear in the GUI from the start, look for them under: Edit -> Preferences

This probably depends on the soundcard/soundchip.

---

### Post by old_geekster on 2007-01-17
Thanks for the replies.  I have done everything that the two of you suggested.  This has not solved my problem.

I checked the speaker plugs to my sound module.  What I found is by reversing the plugs, I gain the front speakers.  Then, I don't have the rear speakers.

I guess that is why with the Windows setup, I had to clone the speakers to get both to work.

I'll keep experimenting.

---

