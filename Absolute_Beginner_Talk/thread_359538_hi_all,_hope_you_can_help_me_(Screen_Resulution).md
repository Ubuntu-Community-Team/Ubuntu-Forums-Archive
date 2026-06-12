---
title: "hi all, hope you can help me (Screen Resulution)"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by master.zen on 2007-02-12
Alright hi everyone,
I'm brand new to ubuntu I have it install and everything thank god it went without a problem :) I was wondering I think right now I'm stuck on 800 x 600 but I need to get it to 1280 by 1024 I hope I can do this because right now my screen resolution doesn't like to great the font is fuzzy and windows are small so if you can help out thanks alote.! :D

---

### Post by ESPOiG on 2007-02-12
first of all "alote" :P

second what brand is your graphics card and monitor

---

### Post by master.zen on 2007-02-12
Sorry to double post but I just used the search function (Lol yes thats right I know its there) and I found something about opening a terminal Im in the terminal with a blue screen I'm also running on a gforce 6200 and my monitor is the HP f1905

---

### Post by master.zen on 2007-02-12
bump

---

### Post by meborc on 2007-02-12
hey,

start your terminal from applications...

write:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

now chose your resolutions...

answer the default to all things you can't really comprehend yet :)

then restart X via ctrl+alt+backspace

...................

also check this site, if my way didn't work : [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by AndreyS on 2007-02-12
I had the same problem and this thread was very helpful. Thx! 

Can any one explain what this command actually does? I know that "sudo" gives the user some administrative rights.. What are the other strange words? :)

---

