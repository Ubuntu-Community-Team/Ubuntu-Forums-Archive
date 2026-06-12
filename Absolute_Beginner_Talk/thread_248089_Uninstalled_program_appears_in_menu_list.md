---
title: "Uninstalled program appears in menu list"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by Sweet Spot on 2006-08-31
I had installed "Listen" media player during the Automatix install process, and decided later to get rid of it. I followed the instructions on the Automatix site for uninstalling it, which seemed to work fully well at the time. It actually uninstalled, and the name of the program wasn't on my sounds and video menu list either after that. A few boots later, (I've installed other programs since then) and the item name is back on that list. 

The icon associated with it, isn't there, it's just a blank white square, and of course the program isn't running because it's not there. However, the wierd thing is that I think this happened after having installed K9 DVD ripper. Coincidentally, 
K9 Copy hasn't got an icon either, but also has that blank white square next to its name. 

First I guess, how do I get rid of Listen from the list completely ? (I deleted the Listen folder from my /home folder and it's still there) and secondly, should I re-install K9 copy ? It seems to work fine, but I tend to be anal about little things like this. 

Doug

---

### Post by Anonii on 2006-08-31
Use the "alacarte" menu editor.
Also, you shouldnt rm application dot folders without a reason. You clearly didnt install it correctly or something, thats why you had still traces of it. You could have tried "sudo aptitude remove --purge listen" to remove the onfigurations file too.

---

### Post by Sweet Spot on 2006-08-31
Well ok, I'll use alacarte, but I didn't install it the wrong way, because Automatix did the installation, not me. I also used its instructions to uninstall it, so I've no idea what went wrong. Sounds like a bug/glitch to me. Thanks anyway though.

---

### Post by Sweet Spot on 2006-08-31
One more thing, I just used "sudo aptitude remove --purge" for dvd::rip and this also left dvd rip in the menu. Yes, I used alacarte to remove it, but why do these things get left at all ? 

Doug

---

