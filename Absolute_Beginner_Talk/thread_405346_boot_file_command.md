---
title: "boot file command"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Donhu on 2007-04-09
i need to add a few things to my boot file, but i cannot find the location in my kmenu, can someone just tell me the command to open the actual file in the terminal

---

### Post by rai4shu2 on 2007-04-09
If you mean the grub menu, you can edit it this way:

kdesu kate /boot/grub/menu.lst

---

### Post by Donhu on 2007-04-09
well...wat i actually wanna do i to get beryl and emerald replace to run on start up..

---

### Post by bodhi.zazen on 2007-04-09
> To start Beryl automatically with Gnome, go to System->Preference->Sessions. Under "Startup Programs" add 'beryl' and also 'emerald --replace' (without the quotes, obviously). Each user who wants to run Beryl at startup will need to have the commands added to their own accounts.

~

---

