---
title: "[SOLVED] screen resolution: help! how do I revert?"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by jakelute on 2008-03-16
Hi,
I was messing around with screen resolution settings because I've had a little problem with temporary freezing, and thought this might solve it. However, I've clearly chosen an inappropriate resolution, because now when I turn on my computer the screen is a mess and nothing is legible. Which means I can't go into the screens and graphics control panel to put it back the way it was. In fact I can't do anything at all because nothing is properly visible on my screen.
I just want to know how to go back to a screen resolution in which I can see what I'm doing!
I'm sorry to say I'm pretty much a beginner in Ubuntu (I've been using it in a dual-boot system with XP for a couple of months now), so I don't know how to do even the simplest repair, such as this one.
Can someone give me instructions for reverting? A very simple "plug n play" 800X600 would be fine for the moment. (I'm writing from my windows installation at the moment.)
Many thanks in advance.
J

---

### Post by jken146 on 2008-03-16
When it has finished booting and got to the log in screen, press Ctrl+Alt+F1.  This will take you to a terminal.  Log in.  Then type ```
sudo /etc/init.d/gdm stop
```
Then ```
sudo dpkg --reconfigure -phigh xserver-xorg
```
Change your resolution to something sensible that your graphics card and screen can handle, then type ```
sudo /etc/init.d/gdm start
```

---

### Post by jakelute on 2008-03-16
Thank you very much! I will try it.

---

### Post by jakelute on 2008-03-16
Hello again. I have tried what you suggested.

First of all, Cntrl+Alt+F1 just brought up a black screen, so I had to abandon that.

Then, I restarted and chose recovery mode.

Then I logged in and typed in the first of the three commands you gave me. This was successful.

Then I typed the second of your commands (the one about reconfiguring), and got an error message saying that the --reconfigure command was not recognized.

So I'm afraid that's as far as I've managed to get. Was that second command definitely correct?

Many thanks again!

---

### Post by jakelute on 2008-03-16
I'd really appreciate any help with solving this!
Until then, I'm stuck.
Many thanks!

---

### Post by iris-n on 2008-03-16
jken made a typo, the command is ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Remember that in recovery mode you don't use sudo. 

and depending on your bootup parameters, the CRTL-ALT-F1 doesn't quite show the login screen, but F2 to F6 also gives you the console.

---

### Post by jakelute on 2008-03-16
Thank you very much. I thought it might be a typo. Will report back.

---

### Post by jakelute on 2008-03-16
Thank you very much, iris-n -- your information did the trick.

I'm up and running again, thanks to you. It's still the case that I can only make Ubuntu 7.04 and 7.10 work with a very basic screen resolution: 800x600 Plug n Play, Graphics Card (ATI Radeon) Generic VESA-compliant video cards -- if I set it for LCD Panel 1024X768, which looks a lot better, I get frequent freezes (usually lasting about ten minutes before everything resumes again, but with the clock in the upper right-hand corner ten minutes slow). And if I try to use the ATI proprietary driver, it messes up the system too. So that's not great. And I have had no luck finding out how to get around this problem. I'm hoping that 8.04 might work better for me.

Any suggestions much appreciated. Meanwhile, thanks again very much for the generous help from those who responded.

---

### Post by jakelute on 2008-03-16
Correction:
it's still freezing even with this more basic screen resolution -- so I'm as far as ever from figuring out the cause of the freezes -- but thanks anyway for the help.
I'll mark this one solved, though I'm still looking for help and advice on the freeze issue.

---

