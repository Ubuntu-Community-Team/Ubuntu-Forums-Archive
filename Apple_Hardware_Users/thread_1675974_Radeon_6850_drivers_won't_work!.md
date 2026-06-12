---
title: "Radeon 6850 drivers won't work!"
date: 2011-01-26
forum: Apple Hardware Users
---

### Post by Cam! on 2011-01-26
I installed 10.10, but when I installed the proprietary drivers of my ATI Radeon 6850, I'm unable to log in due to graphical glitches.

How do I make my card work with Ubuntu 10.10?

---

### Post by gordintoronto on 2011-01-26
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by BrokeMahPC on 2011-01-27
It's because that card isn't supported yet - I have it too :D

If you installed the radeon drivers through jockey you will need to  search "radeon driver" and find some instruction to start the PC and  force the use of the vesa drivers. Then once you get a stable screen you  can install fglrx / Catalyst 1.11 as described below.

I know it asks you to install drivers through jockey (system - admin -  hardware drivers) but don't - they don't work for HD 6xxx cards.

You need to download the Catalyst 11.1 (fglrx) for linux from amd / ati - follow the instructions on the ATI linux wiki to install it and then hack it to get rid of the unsupported hardware watermark.

The HD6xxx are not supported yet. I am told it will all come together for Natty Narwhal 11.4 in April with Kernel 2.6.38 and Catalyst 11.2 or 3 or maybe we will have to wait as long as Catalyst 11.4?

If you search HD6850 there are many posts on all the above.

---

### Post by atsvetkov on 2011-02-02
?

---

