---
title: "Built in 5-in-1 Media Reader HP Laptop, Need Driver"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by LobbyDizzle on 2007-12-10
I looked everywhere on here and it seems that the only card readers that are being fixed are the Texas Instruments. I have the Ricoh 5-in-1 reader. Here are the last few lines of lspci.

05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

Any help will be greatly appreciated. Keep in mind I am still pretty new to Ubuntu.

Thanks

---

### Post by Harpoon on 2007-12-10
This probably won't make you feel any better, but I have the exact same entries in lspci, running a lenovo laptop with Feisty 7.04.  I haven't had any issues (worked oob), so if you are running the same version as me, then this is not a driver issue.  

I don't have time to test out Gutsy, so the answer may be different if that is what you are using.  I believe it did work off the live cd, though.

Someone with a more creative view out there can lend a hand?

---

### Post by LobbyDizzle on 2007-12-10
Ya, I'm using Gutsy... The reader was working perfectly fine before I put Ubuntu on my laptop.

---

### Post by Harpoon on 2007-12-10
Sorry 'bout that.  The only thing I can think of is searching the forums making sure you use the keywords Gutsy and card reader.  Should narrow it down a bit.  Also, there is a thread on here  talking about Gutsy problems, so you might wannt to try posting a question there.  This location may be a bit too general to get the specific help you need.

---

### Post by martinquested on 2007-12-30
Hello.

Those folks using the card reader without problems - just wondering, what card are you using in it?  SD?  MMC?  xD?  etc.  I had no problems using my SD card in the slot, but the xD one doesn't even seem to be noticed by the computer.  Wondering if the problem's at my end or whether Ubuntu doesn't yet support xD cards in the Ricoh built-in 5-in-1 slot.

Thanks for any advice you have.

---

### Post by heffo_j on 2008-04-11
Martin,

Yep Ihave the same issues. SD is okay; xD not good.

John

---

### Post by ddswanson@gmail.com on 2008-06-19
SD works with me.  xD does not, and also the Palm multimedia Cards do not work for me.

lspci | grep Ricoh
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by googatrix on 2008-06-21
There's a bug open about this [here]("https://bugs.launchpad.net/ubuntu/+bug/202490") and a related thread [here]("http://ubuntuforums.org/showthread.php?t=825735").

Same for me on HP Pavilion dv2699 - SD cards work, xD don't.

```

$ lspci | grep Ricoh
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

---

### Post by davidanderica on 2008-06-21
Thanks for pointing those out.

> **googatrix said:**
> There's a bug open about this [here]("https://bugs.launchpad.net/ubuntu/+bug/202490") and a related thread [here]("http://ubuntuforums.org/showthread.php?t=825735").

Same for me on HP Pavilion dv2699 - SD cards work, xD don't.

```

$ lspci | grep Ricoh
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

---

