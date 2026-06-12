---
title: "What is Fluxbox?? and how to get it?"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-09-06
Well lol i guess my title says it all. Ive heard of these different windows managers or whatever theyre called. Can anyone tell me more or give me a link to learn more? Also how would you change these window managers? :D

---

### Post by shoot2kill on 2006-09-06
i dont know much bout it, i only used it for 5 mins.. lol

but install it as usuall... then when u logon, and can select session type, GTK, KDE..etc select FluxBox...

---

### Post by WalmartSniperLX on 2006-09-06
> **shoot2kill said:**
> i dont know much bout it, i only used it for 5 mins.. lol

but install it as usuall... then when u logon, and can select session type, GTK, KDE..etc select FluxBox...

o well that sounds easy lol Thanks :D 

EDIT: Is GTK Gnome?

---

### Post by whizbaby on 2006-09-06
To install fluxbox type (in terminal)
**apt-get install fluxbox fluxboxconf**
(additional fbdesk and fbpager)
To select it hit the session button on the login screen and select 'fluxbox'.
(you should try to gather a little information on the web,though:
[http://fluxbox.sourceforge.net/](http://fluxbox.sourceforge.net/))
Easy,huh?

---

### Post by WalmartSniperLX on 2006-09-06
> **whizbaby said:**
> To install fluxbox type (in terminal)
**apt-get install fluxbox fluxboxconf**
(additional fbdesk and fbpager)
To select it hit the session button on the login screen and select 'fluxbox'.
(you should try to gather a little information on the web,though:
[http://fluxbox.sourceforge.net/](http://fluxbox.sourceforge.net/))
Easy,huh?

yes it is lol. Thanks ill do that once i get home :D

---

### Post by zekopeko on 2006-09-06
[http://fluxbox.sourceforge.net/](http://fluxbox.sourceforge.net/)

try here. it is super minimalistic window manager that still manages to look nice :).
my friend installed it the other day on debian and it is using 60mb of RAM.  

just to add a fluxbox question.
i also installed it but the problem is that the menu wasn't generated. so i have just the desktop and no way to exit it (except ctrl+alt+backspace).

how to make fluxbox menu to show all of my ubuntu apps?

---

### Post by shoot2kill on 2006-09-06
yes.. WHAT HE SAID ^^^^^^^^^^

btw... i would sugest

```

sudo aptitude install fluxbox fluxboxconf

```

---

### Post by WalmartSniperLX on 2006-09-06
Ok everyone Thanks for all the help. Ill make sure to look over that site just so Im on the safe side of what im doing before I install it. :D

EDIT: BTW will all the things i had in my normal session be there in the fluxbox session???:confused:

---

### Post by WalmartSniperLX on 2006-09-06
O yeah and fluxbox will work fine in gnome (ubuntu) right?

---

### Post by skymt on 2006-09-06
Fluxbox will work very will in Ubuntu, but it will not be GNOME. It replaces GNOME (that is, you choose between GNOME and Fluxbox when you log in). I should point out that Fluxbox takes some work to make it usable for you. It's very flexible, but you need to flex it.

---

### Post by Jagot on 2006-09-06
If you hadn't come across it already, you may want to have a read of this too:

[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)

---

### Post by doobit on 2006-09-06
> **WalmartSniperLX said:**
> O yeah and fluxbox will work fine in gnome (ubuntu) right?

Fluxbox is a window manager, just like gnome is a window manager. If you are using Fluxbox, then you aren't using Gnome, and visa versa. I don't know if it would be possible to set up two simultaneous X sessions with fluxbox in one and Gnome in the other, but I think it's theoretically possible...

---

### Post by kerry_s on 2006-09-06
how to make fluxbox menu to show all of my ubuntu apps?

 i think it's "sudo update-menus" or just "update-menus"
I usally make my own.

---

### Post by whizbaby on 2006-09-07
> **doobit said:**
>  I don't know if it would be possible to set up two simultaneous X sessions with fluxbox in one and Gnome in the other, but I think it's theoretically possible...

Easy task (if you have xnest or xephyr installed, I prefer the latter one). Have both window managers installed and login to let's say gnome. In terminal type:
**Xephyr**(resp. **Xnest**) **-query *yourhostname* :5**
choose the fluxbox session et voila: c'est parti, mon kiki.
(be sure you have enabled remote login for that, otherwise it won't work (it's somewhere in system>loginscreen))

---

### Post by seshomaru samma on 2006-09-07
My main difficulty with fluxbox is that I never managed to set up desktop icons on it. I iknow it's possible but I never succeeded in Ubuntu.
Otherwise I think fluxbox is great

---

### Post by whizbaby on 2006-09-07
> **seshomaru samma said:**
> My main difficulty with fluxbox is that I never managed to set up desktop icons on it. I iknow it's possible but I never succeeded in Ubuntu.
Otherwise I think fluxbox is great
Really? Have you installed fbdesk?

---

### Post by seshomaru samma on 2006-09-07
Yeah I have fbdesk but I can never get the icons to come up on start up. It seems like fbdesk forgets them after log out. Or maybe there is something I dont know....
What I usually do is run nautilus on startup and so I have my icons from my Gnome session - not a very elegant solution....

---

### Post by WalmartSniperLX on 2006-09-07
OK everyone I got fluxbox up and running well. Now I must try and get all my menus updated. :D

EDIT: ok i did it but I didnt see a difference ](*,)  darn it >.<

---

### Post by WalmartSniperLX on 2006-09-07
> OK everyone I got fluxbox up and running well. Now I must try and get all my menus updated. :D



EDIT: ok i did it but I didnt see a difference ](*,)  darn it >.<

EDIT 2: Im leaving for school in a bit (darn school, but I only have 1 year left!) but when I get home Ill try the link to help.ubuntu.com and follow what it says. :D

---

