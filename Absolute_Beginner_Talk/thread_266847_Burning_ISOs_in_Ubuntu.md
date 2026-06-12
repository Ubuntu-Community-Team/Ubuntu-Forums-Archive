---
title: "Burning ISOs in Ubuntu"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by DiJEH on 2006-09-27
Could someone please tell me what a good way to burn ISOs is please? I suck with terminal so something which will appear in the applications menu and has a simple interface would be nice.

---

### Post by halitech on 2006-09-27
K3B works great for burning ISO's, almost the same as Nero but works better IMHO

---

### Post by henriquemaia on 2006-09-27
> **DiJEH said:**
> Could someone please tell me what a good way to burn ISOs is please? I suck with terminal so something which will appear in the applications menu and has a simple interface would be nice.

If you're using Gnome Desktop, you can select it with you mouse and press the right button. On the menu, select Write to Disc.

---

### Post by bodhi.zazen on 2006-09-27
> **halitech said:**
> K3B works great for burning ISO's, almost the same as Nero but works better IMHO

I agree. K3b works best on my box, I'v tried several.

k3b will check md5 sums and the quality of the burn very easily.

---

### Post by Buffalo Soldier on 2006-09-27
> **DiJEH said:**
> Could someone please tell me what a good way to burn ISOs is please? I suck with terminal so something which will appear in the applications menu and has a simple interface would be nice.

Just right-click on the ISO and click "Write to Disc".

---

### Post by DiJEH on 2006-09-27
Awesome, is there any way to turn CDIs to ISOs as well?

---

### Post by Joh_ on 2006-09-29
Indeed there is. Both GnomeBaker and K3b can do this (I do not like K3b too much though, as it has serious issues with keeping the buffer full but if that's something you can live with it's a good choise).

Other than that there is a terminal command which unfortunately requires you to know what device you want to make the iso from.
```
dd if=/dev/hdc of=~/disc.iso
```
[FONT="Courier New"]if[/FONT] being the device and [FONT="Courier New"]of[/FONT] the filename of the iso to create.

---

