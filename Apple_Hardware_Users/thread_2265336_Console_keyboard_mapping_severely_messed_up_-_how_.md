---
title: "Console keyboard mapping severely messed up - how to fix?"
date: 2015-02-14
forum: Apple Hardware Users
---

### Post by T0nyI on 2015-02-14
I've installed Lubuntu 13.10 (PPC) on an old Powerbook G3 "Wallstreet". I intended to run Linux on this machine without any GUI whatsoever, and since the special characters weren't properly mapped, I used:

sudo dpkg-reconfigure keyboard-configuration

to try to fix it. This resulted in the most bizarre keyboard mapping I have ever seen. It's definitely not a real keyboard mapping (letters are missing, J is mapped as Enter, Space as Caps Lock, etc) and completely unusable. I tried rebooting, to no avail, the weird keyboard mapping remains. Using pen and paper I've written down the whole keyboard mapping and used that to log on. I thought I'd run dpkg-reconfigure keyboard-configuration again to fix it, BUT the letter "a" is not mapped at all in the weird keyboard mapping, and so I can't type the command!

If I boot into single-user mode I have access to my old mapping, which works fairly well. Is there any way I can fix this bizarre disaster from there?

---

### Post by T0nyI on 2015-02-14
I was able to solve it, the solution was staring me in the face all along. All I had to do was type "sudo dpkg-reconfigure key" and then locate Tab to autocomplete, thus getting the whole command. Once that was done, I could use the arrow keys (mapped to F1-F4 in the bizarre mapping) and Enter to change the mapping to one that works. Sometimes the simplest solutions are indeed the best.

---

### Post by Bashing-om on 2015-02-14
T0nyI; Hey !

> **T0nyI said:**
> I was able to solve it, the solution was staring me in the face all along. All I had to do was type "sudo dpkg-reconfigure key" and then locate Tab to autocomplete, thus getting the whole command. Once that was done, I could use the arrow keys (mapped to F1-F4 in the bizarre mapping) and Enter to change the mapping to one that works. Sometimes the simplest solutions are indeed the best.

Thanks for the sharing, your solution noted .

[INDENT][INDENT]all good now
[/INDENT][/INDENT]

---

