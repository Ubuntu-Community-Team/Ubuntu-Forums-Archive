---
title: "Setting up XP to work with Samba"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2007-01-09
Hey folks. I've got Samba installed on my Edgy, and I'm to the point that I'm on my XP machine to do the settings on there. I just don't know what to do from here. ~LOL~
I've got both of my machines plugged in to a D-Link router, along with a printer. If someone could help me from there, I'd be super happy. ~LOL~

---

### Post by rbhigday on 2007-01-09
try this guide

[Samba]("http://www.ubuntuforums.org/showthread.php?t=202605&highlight=samba")

---

### Post by CheshireMac on 2007-01-09
This is awesome. Thank you. :) I have one question though . . .what drive should I be selecting in the Windows setup?

---

### Post by CheshireMac on 2007-01-09
Anyone know how to set that part up? 
With WINS enabled:
- Click "START"
- Right-click "My Computer"
- Select "Map network drive"
- Choose the drive letter
- Type \\DAPPER\MyFiles
NOTE: Adjust this to the hostname and sharename you chose above!
- Click "Finish"
The drive letter is confusing to me . . .is that the Windows drive I want networked?

---

### Post by rbhigday on 2007-01-10
I thought that was the shared drive on the unix machine.

---

### Post by CheshireMac on 2007-01-10
> **rbhigday said:**
> I thought that was the shared drive on the unix machine.

So I would have to specify that the drive was just "/"?

---

### Post by rbhigday on 2007-01-11
not sure as that is where I got stuck. My xp did not have permission to look at my unix pc at all.

Was not able to fix that and not had time to get back to it and try. May be able to in a day or two If I  stumble across something I will let you know.

---

