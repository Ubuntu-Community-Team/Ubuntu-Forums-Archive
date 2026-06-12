---
title: "Sounds at login repeat...endless drumbeats"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by gigi1234 on 2006-10-02
I just installed Dapper on an old laptop (Armada 7800).

I had some issues getting the sound to work. Modprobe failed. Compaq's website says my computer has an ES1879 sound card. But the only way I could get sound to work was to add "snd-es1688" to my /etc/modules. It does NOT work if I use "snd-es1879."

Then, after the sound was working, upon login the drumbeat sound would repeat for some time ( a minute or two), then eventually the sound would stop. If I go to System->Administration->Login Window I can choose to listen to other sounds for the login. Doing this also causes any sound I choose to preview to repeat for a minute or two. The only fix I have come up with is to deselect all sounds in login window menu.  

Can someone please help me fix this issue? I know it is probably kind of obscure but perhaps someone has dealt with it before.

---

