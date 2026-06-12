---
title: "Screensavers &amp; Games"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by stoogiebuncho on 2008-02-17
I switched to Ubuntu Gutsy about a month ago and have been having the most positive experience.  Installation was much easier than I anticipated and most things only required minor tweaking.

Now everything is running perfectly, I'm taking some time trying to learn more about the terminal, and the only complaint I have is in regard to the screensaver.

I don't do a lot of gaming, but I occasionally play Frets on Fire or Nexuiz, and quickly learned that the screensaver breaks these games.  For some reason it doesn't register any activity while you're playing and comes on in the middle of a game.

It's a little annoying, but no problem, just turn off the screensaver before playing, right?  The problem is that when I am finished playing and turn the screensaver back on, it won't work right.  The screen will fade to black, but the screensaver doesn't come on - it just goes back to the screen it was on before.

Again, this isn't that big of a deal, except that the power-saving functions won't come on either, and that bugs me.

Restarting fixes it.  Sometimes if I stop the gnome-screensaver process and start it again it will fix it, but only about 50% of the time.

I've looked around online, and it looks like this might just be a bug that hasn't been fixed yet, but I wanted to check here and see if there's a solution to this problem that I just don't know about.

Thanks for taking the time to read this.

---

### Post by wolfen69 on 2008-02-17
i believe it is a long running bug, because the power saving feature (power down monitor) has always been hit or miss on my pc's. sometimes it works, sometimes not. oh well.

---

### Post by stoogiebuncho on 2008-02-29
Just wanted to update this to let people know of a little workaround I found.

For some reason, disabling and enabling the screensaver using the gconftool2 command always works for me without a restart.

To disable:
```
gconftool-2 --set /apps/gnome-screensaver/idle_activation_enabled --type bool 0
```

To Enable:
```
gconftool-2 --set /apps/gnome-screensaver/idle_activation_enabled --type bool 1
```

So what I've been doing is making some simple shell scripts for the games I want to play full-screen that disables the screensaver before starting the game, and then enables it when I exit the game.

Something like this:
```
#!/bin/bash
gconftool-2 --set /apps/gnome-screensaver/idle_activation_enabled --type bool 0
COMMAND TO START GAME OR PROGRAM
gconftool-2 --set /apps/gnome-screensaver/idle_activation_enabled --type bool 1
exit 0
```

Then I update my applications menu so the game shortcuts point to the shell script.

I've only been using these a little while, but so far they've worked perfectly.

---

### Post by krsk on 2008-02-29
thx for the hint.
i had the same problem with the screensaver
kicking in while playing games. 
i just put the script in the taskbar
with an on/off switch, so i can
enable/disable screen saver mode
anytime i want:)

---

