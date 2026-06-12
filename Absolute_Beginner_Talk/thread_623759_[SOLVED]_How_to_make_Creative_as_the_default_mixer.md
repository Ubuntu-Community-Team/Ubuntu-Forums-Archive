---
title: "[SOLVED] How to make Creative as the default mixer. Need guidance"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by onlytanmoy on 2007-11-26
Dear All, I am using Ubuntu 7.10 Gutsy Gibbon.
My machine has an onboard audio card(Nvidia CK804). 
But i have been using a Creative SB Audigy sound card from before in windows & wish to use the same in Linux also. Problem is sometimes ubuntu takes Nvidia CK804 as the default audio output & not CA0106(creative sb audigy). I just dont want the Nvidia CK804 one.
I can see both Nvidia CK804 & CA0106 in the mixer. I went in konsole & by alsaconf i was able to config the CA0106 as the audio output device. It worked fine but when i rebooted linux & logged back again, its the same story. It has taken nvidia ck804 as the default mixer :(:(
Plz let me know how can i permanently configure the Creative CA0106 as the default mixer.
Many thanks in advance.

---

### Post by deadgobby on 2007-11-26
Go into your BIOS and disable the on board sound device. This will default the SB card to play all the apps all the time. 
Gobby

---

### Post by onlytanmoy on 2007-11-26
ah..ok..nice hint m8..will try out n update this thread..thanks for the reply.

---

### Post by onlytanmoy on 2007-11-26
thanks a lotttt Gobby..ur tip worked as a charm :)

Mods/Admins: Since my problem is solved, plzz close this thread.

---

