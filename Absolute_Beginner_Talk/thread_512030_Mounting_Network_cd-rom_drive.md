---
title: "Mounting Network cd-rom drive"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by Duffadash on 2007-07-28
Now, the cd-rom drive in my laptop has some kindda hardware failure, and won't open, this however is not why I'm writing here (it not having a whole lot to do with ubuntu), the reason why I'm writing here is that I'm sitting in a tent in the backyard of one of my friends places (with him of course), and we're going to play Darwinia. But since my cd-rom drive is fried my friend told that he once heard that it was possible to mount a cd-rom drive on a computer on the same network, making me abole to install the game from his computer. However, none of us has any idea how to accomplice this deed, beeing why I ask for help... Any ideas, O deities of the holy coffee and enlightened terminals?

---

### Post by Mornedhel on 2007-07-28
Hello again. Yes, I do spend too much time around here.

Another possibility would be to burn an ISO and mount it on your laptop.

Did the game work, by the way ?

---

### Post by Duffadash on 2007-07-28
Aye, it worked flawlessly...
Any specific programs you recommend for this?

---

### Post by Mornedhel on 2007-07-29
To burn an ISO, about every burning application for Linux will let you choose between your standard burner and a "burn to ISO image" option (the ability to burn ISO image now comes standard on most Linuxes). To mount the ISO, just mount -t iso9660 /media/cdrom0 /path/to/your/iso -o loop (the order is important and I think I got it wrong : please check with the mount man page).

---

