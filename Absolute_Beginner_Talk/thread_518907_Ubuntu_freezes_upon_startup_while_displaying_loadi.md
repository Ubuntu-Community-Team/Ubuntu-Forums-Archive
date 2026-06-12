---
title: "Ubuntu freezes upon startup while displaying loading bar - ndiswrapper?"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by mchnhed on 2007-08-06
For some reason my Ubuntu system randomly freezes upon startup (about 40% of the time), **when it displays the loading bar**. It freezes at approximately at the 1/4 mark.

I was told by someone who has Ubuntu on the same laptop model (see signature) that ever since they installed ndiswrapper they have experienced this sporadic freezing upon startup. He said that it seems like it only happens when he boots the laptop **outside of a wireless area**, and when it's plugged in to the network through a cable it doesn't happen. However, **I have experienced the freeze up at least twice now even when connected with a network cable**, so I'm suspicious that it has anything to do with ndiswrapper, but I just thought I would include that information just in case...** I have the ndiswrapper install for my Broadcom 4309.**

Does anyone have any idea what's going on? or perhaps how I could even **diagnose this problem or see a boot log when it happens**? Thanks in advance! (I''m afraid to uninstall ndiswrapper because I finally got it working.)

---

### Post by 505 on 2007-08-06
When you see the Grub boot screen, press 'e' en go to the second line (I believe). At the end of the line, there should be 'quiet splash'. Remove these two words, and press 'b' to boot. You'll see a lot of text, but you should read the text when it freezes and see if any devices or software is mentioned.

---

