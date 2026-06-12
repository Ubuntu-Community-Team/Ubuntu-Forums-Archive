---
title: "DVD Movies do not play correctly"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by Ramon Lasa on 2006-01-06
I have a two drives in my computer.  A cdrom in the top bay and a dvdrw in the second bay.  When I play DVD movies they were playing jerky so I read and followed the instructions for turning on the DMA.  But my DVD movies still play jerky.  How can I edit the hdparm.conf script to turn on the DMA for the second DVDrw drive.  I tried adding:       /dev/hdc {
                                                       dma = on
                                                       }
to the bottom of the hdparm.conf script but this did not help.

Thanks in advance for your help.
Ramon

---

### Post by sharke on 2006-01-06
[QUOTE=Ramon Lasa]I have a two drives in my computer.  A cdrom in the top bay and a dvdrw in the second bay.  When I play DVD movies they were playing jerky so I read and followed the instructions for turning on the DMA.  But my DVD movies still play jerky.  How can I edit the hdparm.conf script to turn on the DMA for the second DVDrw drive.  I tried adding:       /dev/hdc {
                                                       dma = on
                                                       }
to the bottom of the hdparm.conf script but this did not help.

Thanks in advance for your help.
Ramon[/QUOTE]
Try sudo hdparm -d1 /dev/hdc  and this should turn on dma . Then try to play your dvd.
Regards
Sharke

---

### Post by mistergq on 2006-01-06
Which application where you using to play the DVD movies?  In my experimenting with Ubuntu, I found that some of the DVD players would play my DVDs jerky while other played them flawlessly.  I do not remember which one worked, but I suggest you try that too!

---

### Post by kingsidy on 2006-01-07
you might want to try vlc, or if you use totem install totem-xine, see if it make any differene.

---

