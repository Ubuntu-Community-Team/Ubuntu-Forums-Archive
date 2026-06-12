---
title: "Problems with X"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by matey3 on 2008-02-29
Hello:

I rebooted my machine yesterday and now I can't get into the GUI ever since??

I have tried running different kind of display managers but they go so far as to bring the light-brown, blue and gray screen up with the mouse working and do bring the login screen on but as soon as I log in the screen stays the same way until I push the power button?

Is there a setup or init program that I could run to setup the X from scratch? I do not know why this happened?? I was only installing apps in the application manager (things like calculator,games etc.)
It is Feisty 7.04 I am running.

thanks a lot for your good suggestions.. as always...

(I used some one's advice in here before and learned how to disable the X from starting up. I wrote a little script and put those lines in there and put it in the /bin. it was hard to stop the OS from going in th GUI and getting stuck but I did Alt F2/3/etc to get a new login (tty)and before X started I ran my script which I call "deactivate-x" .lts just 3 lines : update-rc.d -f gdm/xdm/kdm (ur choice in each line) remove.)this server is running fine it is just the windows portion of which is screwed up :(

I miss it already dammit heh...

---

### Post by Kilz on 2008-02-29
It sounds like something might have been uninstalled when you were doing that installation of games and such. While drastic reinstalling the ubuntu-desktop package may be the easiest way to fix whatever went wrong. If someone cant give you another option soon
```
sudo apt-get -f install ubuntu-desktop
```
if you have kubuntu installed it would be kubuntu-desktup,
xubuntu  would be xubuntu-desktop
Should force everything to be reinstalled. This may overwrite some custom settings, but it should get the desktop back.

---

### Post by matey3 on 2008-02-29
I'll try.. thanks very much..
lol it says it  is unpacking 750 megs?? lol :)

I hope it works..
regards;

---

### Post by matey3 on 2008-03-03
cool man, thanks a lot I just typed xdm and bingo.. i got my desktop back ...
thanks again..
:)

---

