---
title: "Boot Ubuntu CD - How to"
date: 2005-06-09
forum: Absolute Beginner Talk
---

### Post by Sniffer on 2005-06-09
Maybe someone needs this too so, after receiving this PM at Ubuntu Forum i decided to post just as a How to:


[QUOTE=giveit]hi, I'm new to linux. I just burned an ubuntu image in a cd. But I can't seem to boot from it. I'm on xp. Can you help me out?[/QUOTE]

It's really simple ;-) 

1st - restart your XP
2nd - in the first moments when booting you need to access your bios, is different from bios to bios but most of the times is by pressing F10 or delete (Keep pressing) - The button to press appears at the end of your screen when booting, like this "Press F10 to Bios"

3rd - Then it appears a blue screen with the bios options, you need to go to the boot Order option..just search for it.

4 - Then when you find it, put your CDROM as your 1st boot device and your Hard drive as second.

5 - Save your changes

6 - And with your Ubuntu CD on the drive and restart it will boot from the CD.

7 - Remember that if you have XP as you have, you will need to format all your hard drive to Ubuntu or reserve some space for it (Dual Booting - XP and Ubuntu).

Keep in mind that most of the times it's better to post this kind of questions at the forums instead of private messages - You get different views and more support.

Hope it helps
Sniff.

---

### Post by dweeb on 2005-06-09
What if you have done the above steps, and ubuntu freezes?  Pressing F1 or enter does nothing?  I have posted under "dead in the water..." and have so far not found any solutions.

I guess what I am asking is what would be a logical sequence for troubleshooting?

dweeb

---

### Post by Sniffer on 2005-06-09
[QUOTE=dweeb]What if you have done the above steps, and ubuntu freezes?  Pressing F1 or enter does nothing?  I have posted under "dead in the water..." and have so far not found any solutions.

I guess what I am asking is what would be a logical sequence for troubleshooting?

dweeb[/QUOTE]


I have read your dead in the water thread and.....

Did you after burning Ubuntu CD, have tested the MD5SUMS, if it's equal and the problem is not with the CD??

If the MD5SUMS is correct then try just to test, unplug your Sata Drive (if you can't disable it on the bios) and Boot again with Ubuntu CD.

It could be as well from your ATI AGP Card (do you have possibilitie to test with a nVidia one??, me as well had BAD experiences with ATI....then i have bought an Nvidia one :)

---

### Post by dweeb on 2005-06-09
Thank you, I will try those suggestions and post the outcome.

dwb

---

