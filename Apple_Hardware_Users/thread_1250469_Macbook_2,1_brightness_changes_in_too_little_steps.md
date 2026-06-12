---
title: "Macbook 2,1 brightness changes in too little steps"
date: 2009-08-26
forum: Apple Hardware Users
---

### Post by El Menda on 2009-08-26
Hi.
I followed the guide to make Ubuntu Jaunty work in my Macbook 2,1.

However I realised that after aplying the "xrandr --output LVDS --set BACKLIGHT_CONTROL combination" command I have to press the F1 key 40 times to turn down the backlight supposing I have the maximum brightness level.

Is there any config file in which I could change the number of steps to control the backlight so I can turn the light quicker?

Thanks guys!

---

### Post by El Menda on 2009-08-29
No idea guys?
Does anybody have the same problem?

---

### Post by tiagobt on 2009-08-30
You could try to use pommed instead of the command you posted:

```
sudo apt-get install pommed
```

---

### Post by frikker on 2009-12-01
My brightness in 9.04 also had identical behavior to what you have described.  When I upgraded to 9.10, my buttons and gnome panel applet were diabled completely.  pommed solved this problem for me.  Thansk!

---

