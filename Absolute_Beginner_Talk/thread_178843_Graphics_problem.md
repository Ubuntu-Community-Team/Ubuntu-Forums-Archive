---
title: "Graphics problem"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by Zennosuk on 2006-05-18
Hi all, 

i'm a complete n00b in Linux/Ubuntu. And i want to know if it's normal that i only have 1 resolution. I only have 640*480. My graphicscard is GeForce FX 5500, but I can't use the cd witch came along with the card (I think it's only for windows). Now how do I get a better screen resolution, if at all possible?

greetz,
Zennosuk

---

### Post by johnc4510 on 2006-05-18
did you install and enable the glx drivers?

---

### Post by Klaidas on 2006-05-18
I think you should follow this guide: [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)
I've had the same problem :)

---

### Post by johnc4510 on 2006-05-18
Well anyway, I have the same card so try this in the terminal (Applications>Accessories>Terminal
sudo apt-get install nvidia-glx
It will ask you for your password, type it in and hit enter
sudo nvidia-glx-config enable
hit enter again
Then type in exit and hit enter
Then ctrl+alt+backspace to restart x
Works perfect for me and that same card

---

### Post by Zennosuk on 2006-05-18
Thanks johnc4510 your method worked perfect! 
And Klaidas, thnx for the link, i couldn't find it myself ...

---

