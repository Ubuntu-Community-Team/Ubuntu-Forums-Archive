---
title: "Live CD doesn't boot anything"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by moopy456 on 2006-11-29
Ok, so i pop in the live CD and restart the computer. The ubuntu screen comes up and I choose the first option install or boot ubuntu. little status bar pops up and says it loads the linux kernel, then wham! it just restarts the computer and the ubuntu screen pops up again. Is it just my computer and is there some way to make it work?

---

### Post by munkyeetr on 2006-11-29
what are your system specs?

---

### Post by LLRNR on 2006-11-29
Hi!

Regarding LiveCDs, there are a few things you might want to get done, it's a fact that on some systems LiveCDs cause problems if not burned correctly:

0. if you have less than 192 MB of RAM, use the alternate install CD instead;
1. first off, be sure to burn the CD at a really slow speed (like 4x for instance);
2. just in case... be sure you downloaded the version corresponding to your system (i.e. i386, AMD, PPC);
3. when booting from the CD, run the option "Check CD for defects"
4. almost forgot... after you downloaded the .iso file you should have done a md5sum check - just to be sure that your download wasn't somehow corrupted. From where you downloaded the iso file, you should check for a file with the extension "md5" - it's a small text file, save it somewhere (for example on your desktop) and then get [md5summer](http://www.md5summer.org/download.html) and install it. You should have both the .iso and the .iso.md5 saved in the same location (for instance, on your desktop). Then simply right-click the md5 file and select "verify with md5summer" - if the check fails... it's not ok.

LLRNR

---

### Post by utnubon on 2006-11-29
So I'm not the only one. And the answer is another 45 steps of frustration.

---

### Post by moopy456 on 2006-12-03
This happened when i downloaded the iso image, so i ordered a cd from canonical, the exact same thing happened.

---

### Post by moopy456 on 2006-12-03
i have a copmaq with 2.66 ghz processer and 512 mb ram.

---

