---
title: "Can't shut down OR log out. At all. Major problem"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Seriphyn on 2007-04-21
I'm running Beryl and naturally I'm in the GNOME with XGL session.

When I press exit, only two options are presented to me....

- Suspend, but when I unsuspend it's just a black screen

- Hibernate (Which there is no free memory to do...it won't hibernate, even when it could before)

If I try to log out, it takes me to a black screen and not the login window. If I try to switch user, it comes up with "you are not logged into a console".

This is a major problem. If I can't shut down properly, I have to rely on by just holding down my laptop's power button. And I don't want to have to do that.

Any help would be very appreciated. Otherwise I would just have to wipe up my installation and start over. Without Beryl, which took me a long time to do. And I especially want to impress my friends with it too.

---

### Post by Seriphyn on 2007-04-21
bump, thought this woulda got responded to quicker coz of the urgency :lolflag:

---

### Post by Outrunner on 2007-04-21
You can type:

```
sudo shutdown -r now
```

to reboot. replace -r with -h when you want to shut down.

---

### Post by mikewhatever on 2007-04-21
It is not the best of choices, but you can both shutdown and reboot from the terminal.
> sudo shutdown -P 0
sudo reboot
For more info, use > man shutdown
man reboot

---

### Post by 3rdalbum on 2007-04-21
Easier to remember:

sudo halt

sudo reboot

You can do "gksudo halt" or "gksudo reboot" and assign them to launchers on your Gnome panel. Otherwise, get rid of Beryl.

---

### Post by dunedust on 2007-04-21
Ok i had a similar problem 
I had to edit my startxgl script 
Try this

```
sudo gedit /usr/local/bin/startxgl.sh
```

add the following lines to it

```
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
```

That should make your shutdown and restart buttons appear

---

### Post by Seriphyn on 2007-04-21
Okay, cool, thanks very much.

But do you know about the hibernate problems? It says it's got no free memory to do so...I'm going to need hibernate at college, since standby doesn't work when I shut the lid (it does but I can't restore it).

---

### Post by mikewhatever on 2007-04-21
> **Seriphyn said:**
> Okay, cool, thanks very much.

But do you know about the hibernate problems? It says it's got no free memory to do so...I'm going to need hibernate at college, since standby doesn't work when I shut the lid (it does but I can't restore it).

What are the sizes of your swap and RAM?

---

### Post by Seriphyn on 2007-04-21
512mb...as for the swap...no idea

It was able to hibernate before Beryl. I have resorted to a fresh reinstall.

I really want Beryl though. However, many problems came up. first of all was that shutdown problem, but i Could quite fix that easily now.

Another problem was the whole "logs out to black screen"

And another was that Beryl ceased to  function correctly. When I went to window manager or whatever it was, I clicked "Beryl" from "metacity" and it would activate (Complete with teh wavy beryl flag). Now, it wouldnt. Compiz mode works, but thats no good for me as the bar on top just disappears and i have no idea how to use it.

If I were to take the risk of yet another fresh install, how could I install Beryl and guarantee it'll work. The problems that need solving are...

1) Getting into hibernation is imperative
2) Beryl will not cease to work
3) Logging out will not take me to a black screen
4) Shutdown can be attempted standardly (though that gedit thing could solve it; haven't tried it)

---

### Post by Seriphyn on 2007-04-21
bump

---

### Post by borimrr on 2007-06-25
> **dunedust said:**
> Ok i had a similar problem 
I had to edit my startxgl script 
Try this

```
sudo gedit /usr/local/bin/startxgl.sh
```

add the following lines to it
 
```
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
```

That should make your shutdown and restart buttons appear

I have that on my script. I can restart or shutdown through the menu but when I log out or press my power button the screen goes black and I have to restart the computer. It should show me options when I press the  power button because thats how I have it set up. It also has the same problem on a regular gnome session. 
Here's my script:
```
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4  
export DISPLAY=:1 
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

---

### Post by dunedust on 2007-06-27
Ok heres my start xgl script

```
#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4 
export DISPLAY=:1 
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec /etc/X11/Xsession
```

Everything works fine with that
Backup yours and try using the script
However if you are having similar problems under gnome i doubt this will work.

---

