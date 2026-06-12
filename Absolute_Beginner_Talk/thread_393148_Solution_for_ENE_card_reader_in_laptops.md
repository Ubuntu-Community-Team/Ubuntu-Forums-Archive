---
title: "Solution for ENE card reader in laptops"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by dptxp on 2007-03-25
The solution to detect SD cards in UBUNTU is to use KERNEL 2.6.20-11
as per this page.

[http://www.linuxquestions.org/questions/showthread.php?p=2673740](http://www.linuxquestions.org/questions/showthread.php?p=2673740)

Has anyone tried ? 

Can anyone tell me how I upgrade the KERNEL ?
Can anyone tell me how I upgrade in 64-bit EDGY EFT ?

[HTML]There is a fix for ENE controllers in the 2.6.20 series; if you're using Ubuntu kernels, you should upgrade to 2.6.20-11 which has this fix, and then try with sdhci again to see if you can read SD cards.[/HTML]

[HTML]Ok I updated to the 2.6.20-11 ubuntu kernel and it works perfect. [/HTML]

---

