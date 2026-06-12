---
title: "Weird Problem with VLC"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by mrdosa on 2008-04-05
Lately sometimes my VLC plays all the videos in black and white [To be precise the colors are really dully, its almost black and white] I cant predict what triggers it, but it happens every now and then, and I have to reboot to play videos normally. Some times when I watch streaming videos they play in black & white too, and after that, every video [even offline, from local harddisk] plays in B&W both in totem and VLC. Some times opening more than one instance gets the Black and white thingy!!
I using Gutsy Gibbon. 
Can any one help me out. Please!!
Thanks in advance

---

### Post by joshrobinson on 2008-04-05
```
sudo rm -r ~/.gconf/apps/totem
```

log out and log back in, should work now

---

### Post by mrdosa on 2008-04-05
What does the code do!?

---

### Post by joshrobinson on 2008-04-05
it removes totem's preferences, so the next time it gets opened it re-writes them

i posted this fix before for someone else, and it fixed their problem, along with other peoples

[http://ubuntuforums.org/showthread.php?t=725660]("http://ubuntuforums.org/showthread.php?t=725660")

theres the other thread i posted it in, read through if you need some reassurance

---

### Post by mrdosa on 2008-04-07
Thanks a lot. That solved the problem. I was just waiting for a few days to check if everything worked fine. 
Thanks!
Wonder how lost I would have been without this great community!!!

---

