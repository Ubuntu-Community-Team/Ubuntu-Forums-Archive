---
title: "Steam not going"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by nikoPSK on 2008-02-02
Well, to get the orangebox working, I obviously need steam. I installed it but get this every time:

Please help me

---

### Post by Rocket2DMn on 2008-02-02
```
killall Steam SteamTmp wine wineserver wine-preloader
```
?

How did you go about installing steam?

---

### Post by nikoPSK on 2008-02-02
> **Rocket2DMn said:**
> ```
killall Steam SteamTmp wine wineserver wine-preloader
```?

How did you go about installing steam?

with both the msi and through wine doors, tried your little command, nope. Same error every time. :(

---

### Post by Rocket2DMn on 2008-02-02
Why don't you try logging out and logging back in, since something seems to be running that we can't get rid of (or even rebooting the whole machine :( ).  Then run steam from the terminal and see what happens.  We just need to get steam fully closed so we can open it again.
I followed this guide when I setup steam + counter-strike - [http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/](http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/)
Obviously, all that matters there for you is installing wine + steam, you can deal with the orangle box separately (once you actually get into steam!)

---

### Post by nikoPSK on 2008-02-02
> **Rocket2DMn said:**
> Why don't you try logging out and logging back in, since something seems to be running that we can't get rid of (or even rebooting the whole machine :( ).  Then run steam from the terminal and see what happens.  We just need to get steam fully closed so we can open it again.
I followed this guide when I setup steam + counter-strike - [http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/](http://linux.wordpress.com/2007/02/07/wine-gaming-steam-half-life-half-life-2-counter-strike-source-and-16/)
Obviously, all that matters there for you is installing wine + steam, you can deal with the orangle box separately (once you actually get into steam!)

yay, after a reboot I got it nicely working. I can play games in all they're glory though, right? Nothing sacrificed through wine? :confused:

---

### Post by Rocket2DMn on 2008-02-02
> **nikoPSK said:**
> yay, after a reboot I got it nicely working. I can play games in all they're glory though, right? Nothing sacrificed through wine? :confused:

Sometimes a little speed can be lost, depends on your computer whether you notice it.  All in all, if your computer is on the edge to begin with, you might see a drop in framerate and latency, but if it's good enough, you won't really notice.
You will need to play with OpenGL to get the best results (since you obviously can't do Direct3D on a non-windows system).

---

### Post by nikoPSK on 2008-02-03
Good, it's mainly for portal and Team Fortress 2, so I should be fine. Just to aid users in need, I followed this guide, restarted and logged in. :)

[https://wiki.ubuntu.com/UbuntuMagazine/HowTo/InstallingSteam](https://wiki.ubuntu.com/UbuntuMagazine/HowTo/InstallingSteam)

I cannot seem to edit information in the online page though (avatar etc... not avatar, but the stuff in that area online. ) Also, the grey around the task icon is annoying... :[

---

### Post by Rocket2DMn on 2008-02-03
You mean the Steam Community stuff?  You can do it through the web if you want - [http://steamcommunity.com/](http://steamcommunity.com/)
Show me a screenshot of the gray task icon, I've never seen that.

---

### Post by nikoPSK on 2008-02-03
> **Rocket2DMn said:**
> You mean the Steam Community stuff?  You can do it through the web if you want - [http://steamcommunity.com/](http://steamcommunity.com/)
Show me a screenshot of the gray task icon, I've never seen that.
it's for all wine stuff, I really want a fix. I could probably make one myself... :)

I took the time of outlining it in red, it's beside my name.

---

### Post by Rocket2DMn on 2008-02-03
Oh crikey!  That seems a little insignificant to me.  In steam's case you would probably have to replace steam.ico in ~/.wine/drive_c/Program\ Files/Steam to be the correct size, but I'm not sure it's worth the trouble.
Good luck!

---

### Post by nikoPSK on 2008-02-03
> **Rocket2DMn said:**
> Oh crikey!  That seems a little insignificant to me.  In steam's case you would probably have to replace steam.ico in ~/.wine/drive_c/Program\ Files/Steam to be the correct size, but I'm not sure it's worth the trouble.
Good luck!

well, I don't mind, what size would be appropriate? Also, can portal and team fortress 2 and the rest of the orange box run on 512 RAM and a GeForce 5200 GTX? I've been meaning to upgrade for awhile. :)

---

### Post by nikoPSK on 2008-02-03
I cannot type, must be mouldy.... Won't let me type in boxes... :(

EDIT: like in the search area and text fields

---

### Post by Rocket2DMn on 2008-02-03
You probably won't be able to type anything into the primary steam window, I was never really able to.  It relies on IE I think and even if you have ie6 installed (ies4linux) it still won't work.  Any configurations like that you do need to be done through windows or through steam's website.  Sorry, but you know how imperfect wine is, we're lucky we can use steam at all.

I don't know what size the icon needs to be, why don't you compare it to other icon sizes that appear in the tray.

---

### Post by nikoPSK on 2008-02-03
> **Rocket2DMn said:**
> You probably won't be able to type anything into the primary steam window, I was never really able to.  It relies on IE I think and even if you have ie6 installed (ies4linux) it still won't work.  Any configurations like that you do need to be done through windows or through steam's website.  Sorry, but you know how imperfect wine is, we're lucky we can use steam at all.

I don't know what size the icon needs to be, why don't you compare it to other icon sizes that appear in the tray.

around 20 pixels. I'll try changing, see if it helps. I think it's just a "feature" of wine.

---

