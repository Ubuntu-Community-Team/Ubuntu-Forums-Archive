---
title: "Grub problems hda2 unmountable"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Flamespectre on 2007-07-25
I have been trying to install Ubuntu and I cant boot with grub, something about "Error 17: Couldnt mount selected partition" or something similar. There are two hard drives present, and the installation is a default clean install on hard drive 2, Any ideas?

---

### Post by Jeek Elemental on 2007-07-25
try changing root drive, press e at the grub menu
find the line that says

root		(hd<x>,<y>)

and press e again.

<x> is drive number, starts at 0
<y> is partition number on that drive

try changing the number after hd, to 0 if it says 1 and to 1 if it says 0.

press enter, then b to boot. The change wont be saved.

Im not sure why this happens, have the same issue (2xsata, 1xide). I guess either ubuntu installer or grub gets confused, maybe by boot order in bios?

Im a gnu/linux nub btw so I hope I got this right, it should be safe to try tho :-\"

---

### Post by MQMike on 2007-07-25
Hey Flamespectre, please give us more details.

What was existing?  What was on the first hard drive?  what partition?
Where exactly did you install Ubuntu?
Are both drives IDE, SATA, or mixed?
What exactly do you see whn you turn on your PC . . . POST . . . then what?
Etc.

---

