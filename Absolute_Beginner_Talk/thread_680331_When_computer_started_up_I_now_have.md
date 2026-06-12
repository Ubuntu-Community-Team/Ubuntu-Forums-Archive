---
title: "When computer started up I now have"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by captgadget on 2008-01-27
5 blurry screens. I can see enough to log in and that's it. Any suggestions on how I fix this mess?

---

### Post by ke4ke on 2008-01-27
Did you make any adjustments to your video settings or change monitors or video card before this occurred?

Tim

---

### Post by captgadget on 2008-01-27
Well, I had a resolution of 1280 X 1024. I made some changes in the mouse, rebooted and then it asked me for a resolution of like 800 X 640. I chose yes and when it restarted now I have this mess.

---

### Post by sumguy231 on 2008-01-27
Press Ctrl+Alt+F1 to get to a terminal, log in, and run this command:
```
sudo dpkg-reconfigure xserver-xorg
```
Answer the questions about your video hardware - if you don't know what to put, just leave it blank and it should do its best to detect things for you. Then run this:
```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

```
If the first one takes you to a different screen, just press Ctrl+Alt+F1 again to get back to the terminal.

---

### Post by captgadget on 2008-01-27
That worked perfectly!!!!!!!! Thanks for all your help!!!

---

