---
title: "DVDSanta"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by vishnu on 2006-03-02
I've noticed that Linux is none too quick when it comes to converting AVI format to DVD.  I've tried running DVDSants through WINE but everytime I go to add an AVI file to a new project it says "unable to add file".
Does anyone know of a good graphical interface app for Linux for converting AVI to VOB (DVD).  Or of a way to run a good Windows app through WINE that will do this?
Many thanks

---

### Post by Pragmatist on 2006-03-02
[http://www.linuxquestions.org/questions/showthread.php?t=360138](http://www.linuxquestions.org/questions/showthread.php?t=360138)

linux google is your friend ([www.google.com/linux](www.google.com/linux))

mencoder is in the repositories, so if you type ```
sudo synaptic
``` and search for mencoder, you should just be able to install it.

Incidentally, anything you run through WINE is by definition going to be slow since everything it does has to first go through the emulator.  If speed is what you want, you should look for specific Linux software whenever possible.

---

### Post by vishnu on 2006-03-03
Many thanks for the Linux Google link.  I didn't know about that.  As for conversion I can now convert a 350MB AVI file in 20 mins using "ConertXtoDVD" under WINE.  I know what you mean about slow speeds in WINE but for video compression conversion I've found Linux to be rather slow.  Slower than Windows and usign WINE.
On my older kit converting a 350MB avi file in Windows used to take 2 hours or so!  Now that I've upgraded the hardware it's much faster but still relativly slow in native Linux.

---

### Post by Lord Illidan on 2006-03-03
Do you have dma enabled? If not, then it is obvious that dvd encoding is going to be slow..

Try this link : [https://wiki.ubuntu.com/DMA?highlight=%28dma%29](https://wiki.ubuntu.com/DMA?highlight=%28dma%29)

---

