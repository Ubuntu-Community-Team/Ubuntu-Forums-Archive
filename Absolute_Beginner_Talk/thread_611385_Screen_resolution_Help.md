---
title: "Screen resolution Help"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by GeorgiaBoot on 2007-11-12
Hi,
I just have installed Ubuntu on my external Hard Drive and now am getting into Linux. When I start Ubuntu after the first screen of it loading it turns black and says "screen resolution not supported" then it goes to the welcome screen and I can log on. 

When I go to the screen resolution window it does not have my resolution and refresh rate. When looking at my desktop right now it looks as if it is going off the screen. With windows I was at 1280-1024 at 75refresh

 I have an ati graphics card and a dell 19inch monitor. Any help is appreciated.

---

### Post by taurus on 2007-11-12
Try reconfigure your X server again with

Applications -> Accessories -> Terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by GeorgiaBoot on 2007-11-12
I did that and clicked the ati one then clicked my resolution and restarted. Now the new resolutions showed up but the 1280 1024 still pushes some stuff on my desktop off the screen. In windows 128-1024 was perfect. Also it does not show 75refresh rate. Any more help is appreciated. Also remember I am a complete noob when it comes to linux. Thanks

---

