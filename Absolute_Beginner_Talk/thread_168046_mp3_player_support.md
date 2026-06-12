---
title: "mp3 player support"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by cptjaben on 2006-04-29
hi i'm new to linux and i have a [creative nomad zen xtra]("http://www.nomadworld.com/products/Jukebox_ZenXtra/") and there doesn't seem to be drivers or software for ubuntu or even linux. does anyone know if there are some alternative way so that i can connect to my mp3 player?

Thanks,
cptjaben

---

### Post by Rinzwind on 2006-04-29
does this topic help:
[http://ubuntuforums.org/showthread.php?t=33040&highlight=creative+nomad+zen](http://ubuntuforums.org/showthread.php?t=33040&highlight=creative+nomad+zen)

---

### Post by MartinJ on 2006-04-29
Hi cptjaben,

Can you tell me what the firmware version of your zen is?

As for software, I'm using kzenexplorer (kde application) to manage my Zen Touch.  However, it should work for your player as well.  The breezy version needed some extra steps to get it working (on my machine anyway).  The version in dapper works perfectly.  All available in the repositories.

---

### Post by cptjaben on 2006-04-30
where do i find my firmware version? sorry for all the ignorance

---

### Post by MartinJ on 2006-04-30
On my mp3 player it's this:

Menu -> Information -> Version

But, since yours is newer, it might be different.  The reason I'm asking is that firmware versions 2 and up are a lot harder to get working (or so I'm told- [http://libnjb.sourceforge.net/)](http://libnjb.sourceforge.net).  Hope that doesn't put you off!

---

### Post by darkultra on 2006-04-30
Hi!

No solution but isn't this example that we should buy MP3 players that work as flash drives?

---

### Post by MartinJ on 2006-04-30
Yep,
Wish I'd known when I bought it.

But, when it works, kzenexplorer is a very good program.  Plenty of features that the official Creative program doesn't have.

---

### Post by cptjaben on 2006-05-03
my firmware version is: 1.03.02

---

### Post by MartinJ on 2006-05-04
Ok, good stuff.  Hopefully that means there shouldn't be any issues to do with Microsoft's MTP protocol.

You can choose the following programs from the universe repository:
kzenexplorer (KDE)
gnomad2 (Gnome)
neutrino (Gnome)
You can of course use any program in either desktop environment.

gnomad is more like an ftp client with a left and right pane, kzenexplorer is more like Creative's own program and I've never used neutrino.

---

### Post by ignorance on 2006-05-04
mine mp3 player has a flash drive and it sucks, rather buy an usbstick with a mp3 chip installed on. That gives no problems at all.

---

