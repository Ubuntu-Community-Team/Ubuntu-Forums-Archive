---
title: "Problem installing Edgy desktop"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by softfarr on 2007-04-20
Dear Ubuntu users:

Recently I've tried to install Edgy (6.10) desktop in my laptop. Live CD starts very well, but when I selected Install, went very slow and stuck in step #5 recognizing disks to make partitions.

I tried Edgy server and installed in less than a half hour, and It went too fast end easy.

But definitely I prefer to have desktop installed than server because of the graphic environment.

What's the problem in desktop installation?

Thanx

---

### Post by jvc26 on 2007-04-20
It may be your RAM - a livecd loads totally into the ram and runs out of it so it can put a strain on your RAM. You could install via the alternate install cd (available from the site) which doesnt use a livecd, but rather uses a text based installer. Alternatively you can install the desktop to the server edition, I think with the command:
```

sudo aptitude install gdm ubuntu-desktop

```
Il

---

### Post by Sklasko on 2007-04-20
Your computer may not have quite enough RAM to run the Live CD at optimal speed, however, I'm fairly sure there is a text installer on the Alternate CD that will install the same thing that the desktop CD does. I would try that.

Edit: A little late on the reply, good luck though.

---

