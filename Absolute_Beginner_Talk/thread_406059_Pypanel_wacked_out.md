---
title: "Pypanel wacked out"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by fobnicat on 2007-04-10
I just installed pypanel and installing it went pretty well once i found the howto in the tips & tricks section... but once i got it installed and ran pypanel... my computer lagged really hard and the actual panel was screwed.. it looked as though it were blinking really fast and was badly pixilated with random colors.. if i can get a screen shot up of it i will..

anyone have any idea?

---

### Post by bodhi.zazen on 2007-04-10
No, but it sounds like a cool effect.

Which how to are you following ? I though pypanel was in the repos ...

---

### Post by fobnicat on 2007-04-10
nah it sucks so far haha

pypanel is in the repos, but it is bugged...

[http://ubuntuforums.org/showthread.php?t=327514](http://ubuntuforums.org/showthread.php?t=327514) is what i followed

---

### Post by fobnicat on 2007-04-10
bump

---

### Post by bodhi.zazen on 2007-04-10
And did you follow K.Mandla ' s advice ?

Did you remove pypanel then install both python-xlib and PyPanel from source ?

If so, error messages ?

Log out and back in ?

---

### Post by fobnicat on 2007-04-10
yup .. did it all.. rebooted.. tried it in fluxbox and gnome... same in bothl..

---

### Post by bodhi.zazen on 2007-04-10
Post in that how-to thread and see if you draw attention ...

I have used pypanel from the repos without any problem. Pypanel did not like dual monitors.

Why not use the fluxbox panel ?

---

### Post by moore.bryan on 2007-04-11
[I]check this out:
[http://ubuntuforums.org/showthread.php?t=359228&highlight=pypanel](http://ubuntuforums.org/showthread.php?t=359228&highlight=pypanel)
but it didn't work for me...
[/I]

---

### Post by fobnicat on 2007-04-11
i wasnt real sure on how to follow those instructions... 


anyone have anything else?

---

### Post by moore.bryan on 2007-04-12
[I]that's okay, it's not as hard as it looks/sounds...

step one:  into a terminal, enter
```
sudo nano /usr/bin/pypanel-handler
```
then type
```
#! /bin/bash
sleep 5
pypanel &
```
hit ctrl+x and save the file.
step two: edit your .xinitrc file to reflect the changes
```
sudo nano ~/.xinitrc
```
and change your "pypanel &" line to read "pypanel-handler &"
fini.

but, like i said, this didn't work for me.  i find the only time pypanel flickers is when i open sylpheed; weird.
[/I]

---

### Post by fobnicat on 2007-04-13
how do I change my "pypanel &" line to "pypanel-handler &"

sorry I am new tot his and for some reason when it opens that file, there is nothign there for me to change.. its blank...

---

### Post by fobnicat on 2007-04-13
i guess blank is a bad way to put it.. more like...

```
 GNU nano 1.3.12              File: /home/fobnicat/.xinitrc                                    




















                                        [ Read 1 line ]
^G Get Help     ^O WriteOut     ^R Read File    ^Y Prev Page    ^K Cut Text     ^C Cur Pos
^X Exit         ^J Justify      ^W Where Is     ^V Next Page    ^U UnCut Text   ^T To Spell

```

---

### Post by moore.bryan on 2007-04-13
[I]how do you load openbox, then?
.xinitrc is a file which tells startx what to run when it starts.  anything you want to "automatically" run at log-on goes in this file.  for example, if i wanted pypanel, adesklets, and gnome-volume-manager to all run from the get go and start openbox, my .xinitrc file would contain:
```

#! /bin/bash
gnome-volume-manager &
pypanel &
adesklets &
exec openbox

```
wait a minute; do you use a visual login manager like gdm or kdm?
[/I]

---

### Post by fobnicat on 2007-04-13
i don't run openbox... guess i should have clarified that.. sorry..

---

### Post by fobnicat on 2007-04-13
yeh i use gdm (i think that is what came along with ubuntu)

---

### Post by moore.bryan on 2007-04-13
*but you use pypanel?  why?  what's wrong with gnome-panel?*

---

### Post by fobnicat on 2007-04-13
not sure... as I said, I am new to all of this so I was just experimenting to see what different features did and as I experimented was hoping to learn more and more about the OS

---

### Post by moore.bryan on 2007-04-13
[I]naw, it's good you're trying things out; many newer users are not as ambitious.

if you installed ubuntu, you are using the gnome "environment;" kubuntu, kde; xubuntu, xfce.

gnome comes with gnome-panel already running at the top and bottom of the screen.  can i assume you stopped that?
[/I]

---

### Post by fobnicat on 2007-04-13
nah didnt stop it..

wasnt really sure what pypanel was capable of so I wasnt aware i needed to..

---

### Post by moore.bryan on 2007-04-14
*does it flicker all the time or just when you're using a certain program?  mine works fine until i start my email client (sylpheed); strange.*

---

### Post by arbulus on 2007-10-01
I've followed all the instructions in this thread and nothing works.  The pypanel-handler script didn't work for me.

If I set pypanel to launch on startup or if I just launch it, it flickers and goes nuts.  But if I kill it, then relaunch it, it works perfectly.  I just have to launch > kill > launch again which is a pain.

Any suggestions?

---

### Post by Echow on 2008-01-13
Late reply but just incase anyone is looking:
You might have to make a bash script which makes pypanel wait while your window manager loads up. So instead of executing "pypanel" try "sleep 3 && pypanel".

---

