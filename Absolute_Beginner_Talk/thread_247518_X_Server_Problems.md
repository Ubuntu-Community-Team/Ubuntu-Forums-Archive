---
title: "X Server Problems"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by moricgaut on 2006-08-30
I just took out my Nvidea card out of my computer to send it for repairs. So for right now all i have is my onboard card which is an Nvidea. Now when i turn on my computer it loads and the gives me a x server problem with this jiberish and then it goes to like a black screen which i guess a command promt. ](*,)  It then says login so i login and then gave my password. But now i not sure what to do. I guess i need a command so that i can reconfigure the x windows system. So any ideas. :confused:  Thanks

---

### Post by meng on 2006-08-30
Try
sudo dpkg-reconfigure xserver-xorg
and if in doubt, choose nv rather than nvidia
By the way, sometimes you have to be patient with the "Send/Post" button, don't double post.

---

### Post by Toxicity999 on 2006-08-30
or
sudo nano /etc/X11/xorg.conf

find the video card section replace nvidia with nv (nv is the open source driver!) Probably your onboard just isnt supported by the proprietary nvidia driver. The open source is more broad.

then to save in nano press ctrl+O then enter.

The previous answer is the simpler solution but always good to know all routes :)

---

### Post by whizbaby on 2006-08-30
> **Toxicity999 said:**
> or
sudo nano /etc/X11/xorg.conf

find the video card section replace nvidia with nv (nv is the open source driver!) Probably your onboard just isnt supported by the proprietary nvidia driver. The open source is more broad.

then to save in nano press ctrl+O then enter.

The previous answer is the simpler solution but always good to know all routes :)
Really simpler? Your solution is far better, because reconfiguring will ask you a couple of useless (if you want to change the graphics driver) questions about keyboard layout and screen resolution. (besides, this way you learn something about the system)

---

