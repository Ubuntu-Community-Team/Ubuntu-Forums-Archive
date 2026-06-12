---
title: "XFCE/Fluxbox questions"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by bobbocanfly on 2007-09-07
Im thinking of switching to XFCE or another lighter DE like Fluxbox but not really sure if i should. Have quite a lto of questions about the two DE's.

1 - Is XFCE/Fluxbox actually any faster than GNOME?
2 - Does Beryl work in XFCE/Fluxbox?
3 - I dont use GDM or any other Login Manager (Boot directly to a TTY Env) so how would i start Flux/XFCE?
4 - Can you use GNOME themes with FLux/XFCE?

---

### Post by scrooge_74 on 2007-09-07
1- Yes it is faster
2- Don't know I am not much into 3D desktops
3- startxfce4
4- yes, you can even use some of Gnome's apps to better manage Xfce

---

### Post by por100pre1 on 2007-09-07
IMHO XFCE is not that fast as many people say, specially if enabling GNOME and KDE services at startup. Fluxbox is actually faster but requires more tweaking, and you'll need a light file browser cause Fluxbox doesn't have one. Hope this helps. :)

---

### Post by bobbocanfly on 2007-09-07
Decided to download Fluxbox and so far im liking it. Using openbox as a Window manager but have to manually change it everytime i load into Flux. Is there a way to edit my .xinitrc to run openbox on startx?

---

### Post by bone2006 on 2007-09-07
Xubuntu has less resource requirements, 64mb vs ubuntu's 128mb.  I've put xubuntu on a few older laptops and it does seem to perform better.

---

### Post by gn2 on 2007-09-07
> **bone2006 said:**
>  I've put xubuntu on a few older laptops and it does seem to perform better.

I would agree that older hardware will show a significant benefit from running XFCE, but with newer high-spec kit the difference is negligible.

---

### Post by jviscosi on 2007-09-07
> **bobbocanfly said:**
> 
1 - Is XFCE/Fluxbox actually any faster than GNOME?


In my experience, yep.  Flux is faster than XFCE (but see #2).  Also in my experience, Openbox is faster than Fluxbox.

> **bobbocanfly said:**
> 
2 - Does Beryl work in XFCE/Fluxbox?


You can run Beryl/Compiz in XFCE (I've done so) but that kind of defeats the purpose of using a light(er)weight desktop, in my opinion.   (But if you're only running XFCE 'cuz you like it, and not because it's lighter, then go for it.)

You can't run Beryl/Compiz in Fluxbox because Fluxbox is only a window manager, so you can't replace it with another window manager (i.e., B/C).  XFCE is a whole environment that uses XFWM as its window manager, and when you run B/C, you're replacing XFWM while leaving XFCE running around it.  Think of it as scraping the cream (XFWM) out of an Oreo sandwich cookie and replacing it with peanut butter (Beryl/Compiz).  With Flux, it's all filling, no cookie.

Also, note that XFWM includes pretty capable composite management in and of itself (shadows, transparency, etc.) and in my experience, XFCE/XFWM with compositing enabled is faster and more stable than Fluxbox with compositing enabled via, say, xcompmgr.

---

### Post by LaRoza on 2007-09-07
I just switched to Xfce, here is my post:

[http://ubuntuforums.org/showthread.php?t=545207\](http://ubuntuforums.org/showthread.php?t=545207\)

Yes, I can use Beryl in it.

---

