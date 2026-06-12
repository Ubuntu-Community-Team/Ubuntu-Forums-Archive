---
title: "[SOLVED] panel in GNOME"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by esva on 2008-01-10
I first installed xubuntu from the live cd, which I like, but I wanted to see if gnome had more settings so i installed it from the terminal using sudo aptitude install ubuntu-desktop
I logged in GNOME session from the xubuntu login screen, but I don't see the panels here.
I had dissapered panels in xubuntu and fixed it quite easy typing something like xfce4-panel but this is no xfce how can I make the panel or panels appear in gnome?

---

### Post by nikoPSK on 2008-01-10
I don't really understand you that much in the way you wrote it, but you can add panels by right clicking an existing one and then new panel. ALso, If you want gnome applets, you can do this:

install:
xfce4-xfapplet-plugin

add it to the xfce panel then choose the  gnome applets to add!

---

### Post by esva on 2008-01-10
sorry is that I imagine that gnome use something that is not xfce panels?
right now I am in gnome and I have no panels, but in the xubuntu session I do. So I thought in making them work typing a command or something but I didn't know what to type. Sorry is that i am  new to linux.
Does gnome use xfce panels as well? Or they use their own panels with a different name? I can't click in an existing one cause they are not in the desktop at all.

---

### Post by Xavieran on 2008-01-10
do alt+F2 and then type in ```
gnome-panel
```

---

### Post by esva on 2008-01-11
it appeared now but it had nothing on! I added a menu bar I think it's called and it says aplications, places, system
I can see my files and open programs through alr+f2 but there are no applications in the application menu at all

---

### Post by nikoPSK on 2008-01-11
Add they menu applet and the open programs applet?

---

### Post by esva on 2008-01-11
I did add the menu applet but the aplications don't show anything, it refuses to open it just turns orange

---

### Post by nikoPSK on 2008-01-11
Could I have a screenshot please? 

Thanks

---

### Post by ryanVickers on 2008-01-11
I have seen problems with the keywords "xubuntu" "gnome", and "panels" before...

if you need gnome panels, first "killall gnome-panel" to make sure there isn't a defective instance running, and then "gnome-panel" to start them.

If they are blank, just add some stuff... the real obstacle here is just getting them (first getting a terminal, eh? ;)), but once they are running your on your way because you have access to the menus and all that that implies

---

### Post by esva on 2008-01-11
I tried to take the screenshot with the menus unfolded or me trying to unfold the applications menu and it doing nothing more than turning orange but for some reason the screeshot didn't take there.
btw sorry i talk english weird, it's not my native language

[http://farm3.static.flickr.com/2398/2184943426_71f8b11c1b_o.png]("http://farm3.static.flickr.com/2398/2184943426_71f8b11c1b_o.png")

---

### Post by esva on 2008-01-11
well I did try killall but the panel kept showing up. I also tried to uninstall it but I couldn't cause I had to be superuser. I thought maybe if i typed like sudo aptitude remove gnome-panel and then installed it again it would work. I can see home and the other things there but applications is like it doesn't recognize them or something

---

### Post by esva on 2008-01-11
I tried to uninstall ubuntu and it says I can't!!!!! it says that dpkg was interrupted, and that I have to manually run 'dpkg --configure -a' to fix the PROBLEM
what is this dpkg thing is this something of the ubuntu desktop I installed or a problem of the xubuntu session

---

### Post by ryanVickers on 2008-01-11
is sounds as if you should run sudo dpkg --configure -a to correct the problem ;)

---

### Post by esva on 2008-01-11
ok I did it now. Forst I couldn't cause I didn't undertand that I had to put sudo! that's what it meant with superuser GAH!
ANyway this is even more embarassing but I'll say it , I thiiink that I closed the terminal before the ubuntu-desktop completelly installed, I think that's what happened, cause after I did the dpkg thing it loaded lots and lots of things and now the desktop is perfect...
I like to think that other people that know absolutely nothing of linux did this as well sometimes (AJAJAJ) closing the terminal thinking that it finished doing whatever it was doing; cause it took so long and the screen didn't change at all, it didn't move, that i asumed it finished, since it doesn't say like "installation complete " or something. But now I know it's not over till my user name is again there....*humilliation*
Thanks for helping me

---

