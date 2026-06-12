---
title: "Splash Screen Colours on PowerPC?"
date: 2009-05-12
forum: Apple Hardware Users
---

### Post by SilkySean on 2009-05-12
Hi, I'm running Ubuntu 9.04 on the old imac PowerPC G4 - no fancy graphics cards or anything like that. Just wondering, on the ubuntu splash/loading screen at startup, the colours are all messed up like a rainbow, is it supposed to be like this? If not, is there anything I can do to correct it? Everything else works fine within reason - bar no Flash Player GRRRRRRRRRRRRRRRRRRRR

---

### Post by Benboom on 2009-05-12
Hey, SilkySean, I'm running 9.04 on a G4 desktop and I see the same thing. I notice that when I reboot from Ubuntu the messed up image is different, however - it's a corrupt image of my Ubuntu desktop. I believe the rainbow thing you are talking about is just a hosed version of your previous desktop. If I start Ubuntu after being in the Mac OS I get a mostly blue rainbow (my Mac desktop image is the stock blue swirly thing), but when I reboot Ubuntu I get a strangely formatted picture of the demon from the old horror movie "Curse Of The Demon", which is my Ubuntu desktop picture.

Then once the reboot finishes everything is fine. Well, except for the lack of Flash. :D

---

### Post by stream303 on 2009-05-12
That dang splash-screen for Ubuntu has been an annoyance for ppc users forever.  It can sometimes lock up a card before it even reaches X !

The cure is to use the "nosplash" kernel option.

You can do this temporarily when booting up when you reach the second-stage yaboot boot: prompt by hitting TAB to stop the automatic countdown, and then entering:

```
Linux nosplash
```

(Capital "L")

But this is only temporary.  To make it permanent, you need to edit /etc/yaboot.conf with root priveleges, and either change or add **nosplash** to the **append=** lines.

You can use anything you like to edit that file, ie

```
sudo nano /etc/yaboot.conf
```

will do the trick.  Make the edit, and CTRL-O to write the new file, and CTRL-X to exit the editor.

Thing is, you now have to make your bootloader aware of the change:

```
sudo ybin -v
```

No more splash screen, and you can watch the boot process now in more detail...

---

### Post by Benboom on 2009-05-12
I tried it and it does show me a rolling list as it boots up now. I still get a strangely formatted picture of the previous desktop before it finally boots into the real thing, though. Does outputting the bootup sequence slow it down at all? (I'm guessing "no".)

---

### Post by stream303 on 2009-05-12
That boot sequence you are seeing is vital for catching your attention if it discovers an error - something that the splash screen hides, aside from being mostly unusable. :)

Boot times will be about the same, but you'll be more informed.

I'm not sure about the temporary desktop image - perhaps just some leftover video in a buffer that gets cleared.  Doesn't seem too terrible.

---

