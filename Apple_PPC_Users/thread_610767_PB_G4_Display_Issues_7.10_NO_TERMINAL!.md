---
title: "PB G4 Display Issues 7.10 NO TERMINAL!"
date: 2007-11-12
forum: Apple PPC Users
---

### Post by travnewmatic on 2007-11-12
just recently upgraded to 7.10 to discover that when i tried to switch to the terminal (cont+alt+F1), my screen is black, shows some crappy, fuzzy line spanning the screen (one vertica and a black bar at the bottom of the screen), and never shows me the terminal.  it also changes color gradually until becoming a kind of burnt black.  doesn't do it before the OS loads, like it shows a couple of terminal lines being done prior to the login screen, so it works there, but terminal, as well as when I shutdown.

what controls the screen in terminal?

---

### Post by stream303 on 2008-01-21
Same deal on my late 2004 G4 iBook. I fixed it with this workaround by deleting some lines from yaboot.conf and reinitializing it.

Not only do I have my virtual terminals back (CTRL-ALT-F!-F6), but now my BRIGHTNESS control for the screen works too automatically dimming when on battery etc.  yeah!

I got the hint from this general ubuntu thread:
[http://ubuntuforums.org/showthread.php?t=582962](http://ubuntuforums.org/showthread.php?t=582962)

Basically, we just remove the lines in yaboot.conf that contain:
append="quiet splash video=ofonly"

You'll lose that ugly ubuntu logo, and will be able see all the startups scroll past instead while booting.  Worth it!

typically,
```
sudo cp /etc/yaboot.conf   /etc/yaboot.conf.bak
sudo nano /etc/yaboot.conf
delete the append="quiet splash video=ofonly" lines
save the edited file as /etc/yaboot.conf
.
Now make it active:
sudo ybin -v
.
reboot!
```

Works great now on my G4 iBook!

---

