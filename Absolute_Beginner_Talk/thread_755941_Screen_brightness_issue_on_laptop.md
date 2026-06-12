---
title: "Screen brightness issue on laptop"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by rkakkar on 2008-04-15
I have a Sony Vaio VGN-FZ240E laptop. It has brightness adjustment via keyboard Fn keys. The volume Fn keys work ok but the brightness control has no effect. I even selected the Brightness Applet from list but moving the slider has no effect! Any help?

---

### Post by dedmonds on 2008-04-15
I have a similar problem on a Lenovo T61 laptop. The screen brightness buttons cause the icon to show that the brightness is being changed, but the actual brightness is unaffected. I haven't found a true solution to this, but I did find out that I could change the brightness by pressing Ctrl-Alt-F2 to get to a console, then pressing the brightness buttons to change the screen brightness, and then pressing Alt-F7 to return from the console.

I hope this is helpful.

---

### Post by |{urse on 2008-04-15
k guys, try this

write a little script if it works of course.

dcop `dcop | grep power-manager` power-manager brightnessUp

dcop `dcop | grep power-manager` power-manager brightnessDown

should do the trick

---

### Post by dedmonds on 2008-04-15
I'm not able to run dcop because I don't have it installed. It looks like it is part of a KDE library (kdelibs4c2a). I'm currently running GNOME.

---

### Post by rkakkar on 2008-04-16
any idea when is this going to be fixed in Ubuntu?! i'm going blind here!! :(

---

### Post by |{urse on 2008-04-17
> **rkakkar said:**
> any idea when is this going to be fixed in Ubuntu?! i'm going blind here!! :(

i've scoured the net and asked a few ppl on freenode about this, no dice =/ you can 

sudo apt-get install kubuntu-desktop

and try it but thtd be a pain in the **** indeed =/

sorry guys :( 

this thread needs a bump IMHO

---

### Post by tango_ninja on 2008-04-17
I had the same sort of problem on my Gateway mx6958 laptop....brightness didnt' work (Even from the power mgmt control). I could either have my laptop at 100% or completely dimmed (black). EVen putting it at 99% resulted in complete darkness....never got it resolved :(

---

### Post by rkakkar on 2008-04-17
wow! if so many users have been having this problem, then i think it should be a major priority on ubuntu's list! can anyone communicate this to theM?

---

### Post by dedmonds on 2008-04-25
FYI - This problem was fixed for me with the Hardy release.

---

### Post by rkakkar on 2008-04-25
> **dedmonds said:**
> FYI - This problem was fixed for me with the Hardy release.

you're lucky man! i have an up to date system (up to yesterday, that is) and it still doesn't work :(

---

