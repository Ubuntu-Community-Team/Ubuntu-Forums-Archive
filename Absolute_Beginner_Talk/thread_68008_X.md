---
title: "X"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by timjuanita on 2005-09-21
Hello, My first post here and I am a linux newbie. I have only used windows 95 thru XP. I tried Mandrake 10.1 and was very confusing to me. I gave up on linux. I was duel booting XP and mandrake on all my pc's. Mandrake  ](*,)  made no sence to me and the software that came with it was overwelming to me to say the least. I since then removed mandrake form my pc's. I have a linux friend on ICQ. He is the one to blam for me even getting interested in  Linux. He knew I was fed up with Mandrake and removed it from my pc's. A few days ago he told me about Ubuntu. After a respectful short download I put it on a DVD and installed it on my pc and was surprised how simple it install. I was very happy with the installation of Ubuntu.

Now about my problem. Since I installed Ubuntu I have noticed a few updates now and then. I been updateing everything that comes by. Have had no problems till this morning. This morning I clicked the update and had a few updates.  After updating was complete I rebooted. have not been able to boot the pc since. Somethign is not working right since I did the update. It has something to do with X Server.

---

### Post by timjuanita on 2005-09-21
Last picture

---

### Post by TristanMike on 2005-09-21
Looks like you're using Breezy, that's still under development so you may want to look at downloading the 5.04 Hoary Hedgehog version to install until Breezy is up and running, sometime in October.

---

### Post by holiday on 2005-09-21
[QUOTE=timjuanita]Last picture[/QUOTE]
 There was a bug in this mornings update. 

this worked for me (from the users mailing list)

sudo /etc/init.d/udev restart
sudo /etc/init.d/gdm restart

Pretty scary though

---

