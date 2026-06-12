---
title: "Negitive 2 Monitors"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by gmutt on 2007-03-04
.

---

### Post by gmutt on 2007-03-04
.

---

### Post by pveith on 2007-03-04
I have a working configuration in edgy. One second i will post it here in a minute.

---

### Post by pveith on 2007-03-04
Here it is. I works like a champ for me.

Your section "ServerLayout" looks a bit strange to me, as you are missing the "rightOf" part...
And your monitor section look strange to. Perhaps you could try using my configuration, if you have Flatpanels capeable of 1280x1024 resolution.

Her is mine:

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "0 Default Screen"
	Screen		1 "1 Default Screen" RightOf "0 Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Other than this it would be helpfull to see your Xorg.0.log (/var/log/Xorg.0.log)...

---

### Post by dasunst3r on 2007-03-04
gmutt: I can understand how frustrated you are about the situation you are in, but remember that this is a forum and that people need some time to research your problem to give you a good solution.  Also, people check forums on more sparse intervals than they do chat messages.  If you would like a faster response, you could consider checking out IRC.

I had to say that because I noticed that you posted a sign of giving up seven minutes after starting the thread.  Please don't take this personally.

---

### Post by gmutt on 2007-03-04
Tried your setup - it didn't work either -- Thanks for the effort anyways Pveith

---

