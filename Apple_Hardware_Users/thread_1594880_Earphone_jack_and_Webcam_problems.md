---
title: "Earphone jack and Webcam problems"
date: 2010-10-12
forum: Apple Hardware Users
---

### Post by singh100 on 2010-10-12
Hello guys,
I am very new to Ubuntu and Linux in general and have just installed Ubuntu 10.10 on my MacBook. This is an old macbook (the white-intel based one) about 3-4 years old.
I have been trying to get my webcam and my earphone jack to work but it is just not happening. Please help me out. I need in-depth help since this is more or less the first time I am on Ubuntu. 
Thank You

---

### Post by opulentorca on 2010-10-14
It seems these problems are not uncommon with mac users migrating to maverick.

I use a macbook 2,1 and here is what I did to get the sound working.

Applications - Accessories - Terminal

There type: alsamixer

All the items should be unmuted except for maybe the S/PDIF. What I mean is that in the little boxes at the bottom, you should switch any that read mm to 00 by pressing m.

Others have reported a red light in their audio out port. You can turn it off by muting the S/PDIF.

This should fix the sound problem.

I still haven't found a solution for the isight camera. They have listed the following procedure
[https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight?action=show&redirect=AppleiSight](https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight?action=show&redirect=AppleiSight)
But I have had no success with it on my macbook 2,1 using 10,10.

---

### Post by singh100 on 2010-10-14
hey, 
thanks a lot for the help. I really appreciate it coz its kinda hard for me to concentrate on work if I am not listening to music haha
anyways, even I have been frantically hunting for a solution for the webcam....will post it up if I hit something useful

---

### Post by opulentorca on 2010-10-15
Also, it might be useful to set the settings in from the root account and then save them. Here is a link to that procedure:

[http://linux.dsplabs.com.au/alsamixer-and-alsactl-store-adjust-and-save-alsa-mixer-settings-p29/](http://linux.dsplabs.com.au/alsamixer-and-alsactl-store-adjust-and-save-alsa-mixer-settings-p29/)

I found that everything tends to reset each time you boot and not having the  S/PDIF muted at least on my macbook produces a gritty tone within the sound output.

---

