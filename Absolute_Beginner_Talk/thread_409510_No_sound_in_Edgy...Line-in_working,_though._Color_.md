---
title: "No sound in Edgy...Line-in working, though. Color me perplexed."
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by Esben Kramer on 2007-04-14
Hi.

I have no sound. Not even the cute tadaa-drums on start-up. As the title says, I can play my LP's just fine through line-in, but maybe this is just hardware-driven? What could be going on? Any thoughts?

Thanks in advance.
Esben

---

### Post by thornomad on 2007-04-14
did sound ever work? you can try running alsamixer (i think that's what it is) and make sure your volume levels are muted. alsamixer runs from the command line.

---

### Post by Rab22 on 2007-04-14
If your line-in is working properly, then your sound card will work.

Make sure that your output channels are not muted in alsamixer, and verify that you are using the correct sound device for output.

---

### Post by ComplexNumber on 2007-04-14
> **Esben Kramer said:**
> Hi.

I have no sound. Not even the cute tadaa-drums on start-up. As the title says, I can play my LP's just fine through line-in, but maybe this is just hardware-driven? What could be going on? Any thoughts?

Thanks in advance.
Esben
go to main menu -> system -> admnistration -> login window. go to the Accessibility tab. are any of the sounds ticked? test them to see if they make a sound.

---

### Post by Esben Kramer on 2007-04-14
It worked before the last update. I've checked the alsamixer and checked it again - everything looks fine, I think. The soundssettings in the GNOME-panel doesn't do me any good either no matter how much I tinker with it.

---

### Post by Esben Kramer on 2007-04-14
> **ComplexNumber said:**
> go to main menu -> system -> admnistration -> login window. go to the Accessibility tab. are any of the sounds ticked? test them to see if they make a sound.

I tried it, and it doesn't. Any suggestions?

---

### Post by Esben Kramer on 2007-04-14
> Go in KMix ( or the same program on Gnome )
Uncheck Audigy Analog/Digital Output Jack 

Some other guy had the same problem, only in Kubuntu. I can't figure out how to do this in GNOME?

---

### Post by ComplexNumber on 2007-04-14
> **Esben Kramer said:**
> I tried it, and it doesn't. Any suggestions?
i had EXACTLY the same problem. the difference with me is that it was random as to when the bangos sounded or not. i noticed that when the bangos sounded as i logged in, that meant that my sound was working fine. when it didn't sound, various applications such as gtick(metronome), solfege(ear training program), and hydrogen(drum machine) were all mute....even though i could play mp3's and ogg files just fine. [this ]("http://ubuntuforums.org/showthread.php?t=336973")is the thread that i started and where i found my solution.
i don't know if that helps. probably not because i was kinda vague as to why it was happening. i never truly found out the cause. dealing with people's sound problems can be very complex in some cases.

---

### Post by Skidpad on 2007-04-14
> **Esben Kramer said:**
> It worked before the last update. I've checked the alsamixer and checked it again - everything looks fine, I think. The soundssettings in the GNOME-panel doesn't do me any good either no matter how much I tinker with it.

I think the key to all of this is the statement "It worked before the last update".  I lost my sound (laptop) during this last update.  If you search for "no sound" you will find quite a few threads on it.

Here's a good one: [http://ubuntuforums.org/showthread.php?t=407863](http://ubuntuforums.org/showthread.php?t=407863)  Let us know how it goes!

---

