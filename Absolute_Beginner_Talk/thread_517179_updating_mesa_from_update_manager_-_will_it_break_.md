---
title: "updating mesa from update manager - will it break my nvidia feisty system's xorg.conf"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by vortex_noob on 2007-08-04
Hi

my machine is using nvidia proprietary driver in ubuntu feisty via envy.
There's a recent update for mesa-related deb from the update manager. I'm rather hesitant to upgrade because I don't want to break my system. Is my fears justified or am i just plain paranoid?? :(
I understand this updates have to do with intel-integrated graphics which I dont use. 
So what do u think guys... should I take the update or not.
If I dont, will it compromise the security of my system?

Thanks in advance

Long live Linux..... Cant wait for Linux to become the worthy adversary of MS-DirectX gaming platform!
Then I can completely forget about touching a windows machine... ever!

---

### Post by sad_iq on 2007-08-04
Well you could backup xorg.conf if you're too paranoid and if something goes wrong restore it, however i don't think the update will harm your system.To backup:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup
``` To restore : ```
sudo cp /etc/X11/xorg.conf.mybackup /etc/X11/xorg.conf
```

---

### Post by Mawy on 2007-08-04
I updated it yesterday, and it didn't break anything. I'm using the 9755 nvidia driver and the only update I am holding off on is nvidia-glx.

---

### Post by vortex_noob on 2007-08-04
great!
i'll start updating right now

thanks to both of u, man...

---

