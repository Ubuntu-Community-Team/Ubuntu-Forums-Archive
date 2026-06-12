---
title: "XMMS errorbug with playlist?"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by Nunyah on 2006-03-28
Hey all, not much of a deal but when I open XMMS with a current playlist (ie, the songs I listened to last time) I get an error message going something like this:
> Please check that: Your soundcard is configured properly, You have the correct output plugin selected, No other program is blocking the soundcard.

If I delete the playlist and add new mp3 it works like a charm.. The mp3's are stored in home folder.

As I said earlier, not much of a problem, just caught my mind and if someone's familiar with the problem, and maybe even the solution, I'm really interessted in hearing about it!

---

### Post by Qrk on 2006-03-28
Xmms doesn't use the Alsa sound daemon by default, so it can't play sounds when another application is monopolzing the sound card. 

Fortunately, it is an easy fix:

Right click on Xmms Options->Preferences->General I/O plugins->Output Plugin

Change  OSS (I believe) to Alsa.

Now Xmms is on the same page with the rest of Ubuntu when it comes to sound.

---

### Post by Nunyah on 2006-03-28
Thanks man, did the trick! ;)

Update: I'm a bit currious, why isn't this a default setting in XMMS?

---

### Post by Qrk on 2006-03-28
Xmms is a very old program designed to work with the minumum number of dependencies (it still uses gtk 1, for example.) It was started in 1997, before alsa was begun.

---

### Post by Nunyah on 2006-03-28
Aha, are there some alternatives I should check out? Personally I like XMMS because it's simple and quite identical to the old winamps, but I'm also openminded enough to be interessted in other alternatives that Linux has to offer.

---

### Post by trent dillman on 2006-03-28
amarok is awesome. The lyric/artist info download is sweeeeet.

---

### Post by Qrk on 2006-03-28
There isn't anything wrong with Xmms, it may be old but it still is very usable. Indeed, for a lightweight audio app, its hard to beat. Newer programs have more features, (like amarok and rhythmbox) but I still use xmms primarily. Another good program to try is beep music player, its very similar to xmms. 

And if you want to make xmms more functional, try installing gxmms (from the repositories) which is an applet where you can controll xmms right from your gnome panel.

---

### Post by Nunyah on 2006-03-28
Thanks, I'll check 'em out. I've already testet Amarok. The pop-up window at logon made me remove it quite fast, though I'm sure it's easy enough to disable.

---

