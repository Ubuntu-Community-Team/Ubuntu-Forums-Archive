---
title: "hda: &lt;3&gt; hda: lost interrupt"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Mwelsh on 2008-01-16
During a PXE boot, I get this at startup and it never gets past... I can't get onto the computer, because it has no OS (thus the PXE boot). I was able to PXE boot it before, and as far as I know, nothing changed.... help anyone?

```

Partition Check:
hda: <3>hda: lost interrupt
hda: lost interrupt
hda: lost interrupt
hda: dma_timer_expiry: dma status==0x21
hda: error waiting for DMA
hda: dma timeout retry: status=0x40 {Drive Ready}
hda: lost interrupt
hda: lost interrupt
hda: lost interrupt
hda: lost interrupt
hda: lost interrupt
hda: lost interrupt
.
.
.
etc

```

There is about 30 seconds to a minute between each interrupt. There is also code above the partition check where it reads the size of hda (4045 MB I believe) and how many blocks/cylinders etc. and then checks it being IDE.

Thanks in advance, please help :)

---

### Post by bodhi.zazen on 2008-01-16
[http://www.jimohalloran.com/2004/02/15/hda-lost-interrupt/](http://www.jimohalloran.com/2004/02/15/hda-lost-interrupt/)

---

### Post by Mwelsh on 2008-01-17
Thanks for your reply, but since it's PXE booting, I can't get to any of its hard drive options and I don't know enough to be able to implement that into the kernel it downloads. My hard drive is also not a Seagate... although it is the exact problem I am having. However, as they say the machine returns and actually boots after a few minutes, mine does not. I left it for 15 minutes and still no change.

Thanks again

---

### Post by Mwelsh on 2008-01-21
For anyone who happened to have the same problem as me, the solution is an odd one. I managed to fix my problem by enabling the hard disk to boot. I had previously disabled it for a PXE boot. To get the PXE boot to work, I had to leave the hard disk able but change the boot order. It seems when the hard drive is disabled as a boot device and ahead in order, it locks it and does not allow the system to read it. Strange... There's my solution!

---

