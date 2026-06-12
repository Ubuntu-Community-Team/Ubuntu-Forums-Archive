---
title: "would reinstalling the distro fix the problem?"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by Irishpolyglot on 2007-12-22
Hi everyone!! I've been stuck at absolute newbie status for months because of an issue with the wireless card. I have a 4965AGN Intel on a Dell Inspiron 9400 laptop. I installed Ubuntu 6 months ago and drivers didn't exist so I went through the forums but unfortunately never came up with a solution that worked for me. The drivers do exist now and I still couldn't fix the issue (probably because it's a bit above my head). I tried updating to distro 7.10, but at the very end it ran into bugs so it didnt' fully install... and on top of that my ndiswrapper drivers (that I tried for the non-Linux drivers originally) are still in place. 
So, would wiping the installation and starting over from scratch install the new drivers?? They were available before the new distro was made so I assume they are a part of it now and everything should just work?? Once I get over this step I can gradually get into the distro and abandon my Windows dual boot!!
Thanks for any advice or help on this!! Much appreciated :)

---

### Post by blueridgedog on 2007-12-22
If you are game to re-install, try it, but elect to format the ubuntu partitions so you get a fresh setup guaranteed.

---

### Post by cmnorton on 2007-12-22
I did have a problem with my Acer 630 Travelmate laptop trying to do an upgrade-install from 6.10. I would up doing a clean install after backing up important directories, files, and so on. It was not a wireless card problem as you discuss, but trying a clean install might help you out. However, there might be a problem with the age of your laptop and the wireless card.

What kind of wireless card do you have built-in, USB, or Cardbus? How old is your laptop. Before you re-install, you might consider trying a different wireless card. My Acer's built-in wireless card just cannot cut it, and absolutely does not work with VPN.

---

### Post by Irishpolyglot on 2007-12-22
The laptop is just over 6 months old and was just released by Dell this year... the card etc. works fine in Windows so I'm not replacing it; it's built in. I may just format and start over and keep my fingers crossed that it works this time!! How should I format the drive - obviously I can't do it from within Windows or in Ubuntu itself.. how did you do your clean install? Will the CD installation do that automatically? I think I saw that step when I originally installed it the first time.

---

### Post by louieb on 2007-12-22
> **Irishpolyglot said:**
> ... I may just format and start over and keep my fingers crossed that it works this time!! How should I format ...
Its not automatic. but its easy. When you get to the partition part of the install - choose manual - then pick your current / (root) partition and check mark the format box. Just make sure you know which partition Ubuntu is currently installed.

---

### Post by Irishpolyglot on 2007-12-23
Thanks for your help!! I didn't quite manage to format the previous installation; I have them all installed simultaneously :rolleyes:Oh well... how can I format the other installations from within this new one so I have the space they are using? I still see the previous installation as an option in the boot-up. Most important thing is that wireless is working :D It's a little slow, and the light W-ifi light isn't on though. Will this cause problems?
Finally I can really dive into the Ubuntu spirit :)
Thanks!!

---

