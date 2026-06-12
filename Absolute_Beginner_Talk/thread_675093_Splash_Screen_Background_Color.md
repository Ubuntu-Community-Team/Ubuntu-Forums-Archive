---
title: "Splash Screen Background Color"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by k8fox1 on 2008-01-22
Gutsy 7.10

Although I have selected black as the background color for my splash screen, it still displays as the default Ubuntu orange. What am I missing here?

Thanks!

---

### Post by chris200x9 on 2008-01-22
don't know but I'm interested in this too!

---

### Post by seventhc on 2008-01-22
If you right click on the top panel and click Add to Panel then choose 'switch user from the menu. Your user name should appear right click on that and choose 'set up login screen' go to local(second tab) choose plain or plain with faced browser (both will work) then you will be able to choose your color for the background. If that doesn't work then go to 'system'>'preferences'>'visual' and uncheck visual.
I am not sure if this is what you are looking for, but this is what I use. I am not sure if you are tying to get a black background or if you have a black splash screen that you are trying to use.
:note: if you follow my instructions, you can always remove the 'switch user' from the panel once you are finished.

---

### Post by k8fox1 on 2008-01-22
Thanks folks got it!

---

### Post by ice60 on 2008-01-22
here's a post i wrote on another forum, i'm not sure where i got it from originally. i think it's the same problem?

when gutsy boots part of the screen goes brown, you can change the colour to something else in this file -
```
gksudo gedit /etc/gdm/PreSession/Default
```
on line 61 (right near the end of the file) there's a bit that looks like this -

# Default value
 	if [ "x$BACKCOLOR" = "x" ]; then
 		BACKCOLOR="#dab082"

i think that is the original value - #dab082  i changed it to a dark colour, to this - BACKCOLOR="#1C1919"

---

### Post by seventhc on 2008-01-22
I'm not so sure that is so good to do, I just tried that and it had some strange results.
Maybe it's just my box but everything acted strange, although I did set my boot screen to defaults, maybe thats the difference.
At any rate, I think this problem has been solved.

---

### Post by tcommbee on 2008-02-09
in the long run it might be even better to change the $BACKCOLOR variable instead of editing the file directly which might be overridden with an update

---

