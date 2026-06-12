---
title: "using arm-linux-gcc for vga input TFT"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by ramandeep on 2008-01-28
Dear All,
              I have an 8 inch TFT module with a analog VGA input.I want to interface this with an ARM9 board(which has VGA output) and am using arm-linux-gcc as crosstool.I want to display graphics on the TFT.Does arm-linux-gcc provide libraries for displaying text and images on VGA input LCDs .If yes how can I use them?
              Any help will be gratefully appreciated.

Thanks,
Ramandeep

---

### Post by Cypher on 2008-01-28
The cross tool is JUST the compiler and it doesn't do anything with LCD's. The crosstools paired with cross-GLIBC will get you a valid C/C++ envrionment.

Are you trying to run Linux on this ARM9 board? If so, you'll probably first want Kernel support for your LCD controller, then a JFFS2 filesystem (assuming you only have access to Flash) with a basic Linux system and Kdrive for x-windows applications.

Explore [http://openembedded.org](http://openembedded.org) for some help..

---

### Post by ramandeep on 2008-02-06
yes the arm9 board is running on linux.I have the kernel core loaded on the board and kffs2 file system with framebuffer.but i am still not sure how acn i display images on the tft?

---

