---
title: "Can't Launch Frostwire"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2007-01-05
Hey folks. I'm trying to launch Frostwire, but it's not doing anything. The root file is still where it should be, and I've had it for a long time with no problems. Why won't it launch? Any thoughts?

---

### Post by taurus on 2007-01-05
Try to run it from a terminal, Applications -> Accessories -> Terminal, and see what the error message is.

---

### Post by CheshireMac on 2007-01-05
> **taurus said:**
> Try to run it from a terminal, Applications -> Accessories -> Terminal, and see what the error message is.

fmac@mac-desktop:~$ frostwire
runFrost.sh: 44: Syntax error: "(" unexpected (expecting "}")
That's odd . . .I'm going to try troubleshooting . . .if you can help, that's great, but I think it's time I took control of my Ubuntu troubles. ~LOL~ I've been relying too heavily on you guys (Which you've been very helpful with), but I need to start learning instead of asking for solutions. . . .if you can help figure this out, then great, but I'm doing this one solo until I come up with nothing. If I can't find anything I'll resort to this. ~LOL~ Thanks for the assistance.

---

### Post by meng on 2007-01-05
How did you install frostwire?

---

### Post by bodycoach2 on 2007-01-05
Frostwire has worked fine for me, but my son's installation does the same thing -doesn't come up. He loaded Gtk-gnutella on, and is able to get what he wants. He likes that better than frostwire.

Frostwire is Java based, so it might be a problem with that. Do your other java apps work fine?

> **CheshireMac said:**
> Hey folks. I'm trying to launch Frostwire, but it's not doing anything. The root file is still where it should be, and I've had it for a long time with no problems. Why won't it launch? Any thoughts?

---

### Post by CheshireMac on 2007-01-05
I found a string that opened it properly . . .I'm going to run a test right now to see if it opens regularly now. . . .and it doesn't . . .so I tried the string again. 
mac@mac-desktop:~$ #!/bin/bash
mac@mac-desktop:~$ cd /usr/lib/frostwire
mac@mac-desktop:/usr/lib/frostwire$ bash runFrost.sh
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_08]
Configuring environment...
Loading FrostWire:
log4j:WARN No appenders could be found for logger (com.limegroup.gnutella.gui.Initializer).
log4j:WARN Please initialize the log4j system properly.

I hate P2P programs . . .they're so irregular. Looks like I'm relying on you gurus again. ~LOL~

---

### Post by CheshireMac on 2007-01-05
Alright, so I can only open Frostwire with that string . . .I found somewhere that I should be changing a string of code in Frostwire since I moved on to Edgy from Dapper . . .my problem is that they're showing that Frostwire should be in ~/opt, but I don't have it there, and I don't know where my frostwire.sh file is to alter the code . . .I imagine it's a conflict with Java . . .should I update java and frostwire? I installed a lot of stuff via Automatix, which is turning out to be problematic . . .get what you pay for, I suppose. ;) ~LOL~

---

### Post by xpod on 2007-01-05
Frostwire can also be installed from their site with a single click or so.
I once had to alter some text file when getting fw for edgy but im sure thats no longer required as i`ve only just recently re-installed all our os`s and frostwire works perfectly ok in edgy without any tampering.

Why not un-install it via AX then try dl it from their site.Just a thought.
Good luck

---

### Post by CheshireMac on 2007-01-05
> **xpod said:**
> Frostwire can also be installed from their site with a single click or so.
I once had to alter some text file when getting fw for edgy but im sure thats no longer required as i`ve only just recently re-installed all our os`s and frostwire works perfectly ok in edgy without any tampering.

Why not un-install it via AX then try dl it from their site.Just a thought.
Good luck

That's actually a really good idea (Not that I doubted you . . .;)  ) I'll try that, and get back to you on it . . .
Also, I'm in the process of 14 updates . . .maybe that will fix a few things?

---

### Post by arnieboy on 2007-01-05
CheshireMac: Did you actually install Frostwire from Automatix? From what it appears, you seem to have tried a lot of stuff.

---

### Post by kerry_s on 2007-01-05
Grab the latest frostwire built with the edgy fix from the site.-> [http://www.frostwire.com/download.php?file=http://fuse.frostwire.com/frostwire/4.13.1/frostwire-4.13.1.4.i586.deb](http://www.frostwire.com/download.php?file=http://fuse.frostwire.com/frostwire/4.13.1/frostwire-4.13.1.4.i586.deb)

The problem is if you started with dapper, it was using bash, in edgy there was a switch to dash. The new one frostwire fixes that.

---

### Post by mahy on 2007-01-05
Or edit the run script (/usr/bin/frostwire) and replace "/bin/sh" with "/bin/bash" ...

---

