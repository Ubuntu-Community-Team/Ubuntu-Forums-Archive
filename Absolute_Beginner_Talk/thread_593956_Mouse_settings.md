---
title: "Mouse settings"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Excalibre on 2007-10-27
So Ubuntu appears to have recognized my mouse (Logitech mx610) well enough at least to activate the volume buttons (hats off, it's more than Windows managed. But why is it set so that by default, keyboard and mouse volume buttons affect the front mic instead of the speakers?!)

But I'd like to change some of the mouse behaviors (shuffle buttons around, assign some to keystrokes, etc.) The Logitech drivers in Windows did an okay (though not great) job of that; since Ubuntu seems to be recognizing all the buttons I press, I'm guessing this isn't a driver issue but just an issue in terms of how much configurability the Gnome mouse preferences thingy offers. Is there a better way to configure my mouse? And hopefully, some way to enable acceleration of the scroll wheel?

---

### Post by linuxwizard on 2007-10-27
Look over these 

[https://help.ubuntu.com/community/Logitech_MX610](https://help.ubuntu.com/community/Logitech_MX610)

[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

---

### Post by Excalibre on 2007-10-27
Okay, so I'm still struggling with this. I followed the instructions on the Logitech MX610 thing and succeeded at completely disabling my scroll wheel. This was not quite what I was hoping for, though.

I'm just going to bump this thread in hopes someone can give me a slightly more lucid explanation than that howto.

---

### Post by Excalibre on 2007-10-28
Okay, in hopes that maybe someone will come back and look at this thread again, I'll explain the situation in a bit more detail.

The mouse has 5 of those media/application launcher type buttons you see on keyboards, and Ubuntu recognized those, no problem. But it also has nine mouse buttons: left, middle, right, four scroll directions, and two thumb buttons.

The ManyMouseHowTo linked above gives simple instructions for getting seven buttons just by altering the relevant lines in xorg.conf, and they worked - it was enough to get my thumb buttons working, and I managed to, for instance, map one to the Rotate Cube compiz effect.

What I couldn't get working were the left and right tilt-scroll thingies. I tried telling xorg.conf I had 9 buttons, but it didn't seem to do anything. I tried assigning buttons 8 and 9 to compiz effects, and nothing. I'm not sure if it's not possible for X to deal with 9 buttons, or if compiz won't accept them, or what.

So I tried the Logitech MX610 howto, and when I did, I totally lost my scroll wheel entirely. No good. Except that, weirdly enough, it would work if I held down either of the thumb buttons, which otherwise weren't doing anything.

Meanwhile, I can't even tell what 'imwheel' is for. Unfortunately, most of the help documentation out there is limited to instructions to paste certain things into config files and run commands in a terminal, with no explanations of what's actually happening. The problem is that these machines (and linux installs) are not all the same, and if an "explanation" is just a list of text to be typed verbatim into a config file or a terminal, it leaves the user with no way to figure out what went wrong or how to fix it.

I'm trying to have patience with this and if I ever manage to figure anything out, I hope to do some work to make for more adequate documentation here. But in the meantime, I'd really appreciate it if someone who knows something about this could give me a little better explanation than those guides so that maybe I could actually get my mouse working.

---

### Post by Excalibre on 2007-10-28
Meanwhile, I'm still looking for some way to enable acceleration of the scroll wheel, so that if you scroll faster, it scrolls the screen in larger increments. It's a pretty standard thing; I'm sure there must be some program I can install to do it but I don't know what.

---

### Post by Excalibre on 2007-10-28
Okay, I'm bumping this in case anyone knows anything about multi-button mice. There HAS to be someone here who has configured a mouse with more than seven buttons.

---

### Post by linuxwizard on 2007-10-28
Looks like no one is answering you. Have you seen this maybe something that will help.

[http://ubuntuforums.org/showthread.php?t=332256&highlight=Logitech+mx610](http://ubuntuforums.org/showthread.php?t=332256&highlight=Logitech+mx610)

---

### Post by Excalibre on 2007-10-28
I have indeed seen it. It didn't work for me. I was thinking of posting again and describing what I've tried lately but obviously no one is interested.

That guide calls for the evdev driver, but if I try to use evdev, it causes X to fail spectacularly -- the display driver gets screwed up somehow, and it tries to start X in low graphics mode, but the screen is still completely messed up. I had to ctrl-alt-backspace and fix it from the console.

---

