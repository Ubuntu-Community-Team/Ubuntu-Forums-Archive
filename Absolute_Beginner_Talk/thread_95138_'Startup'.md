---
title: "'Startup'?"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by OmegaOne on 2005-11-25
when i used to use windows, i could just shove programs in start>programs>startup and they would automatically run for me. what i cant figure out is how to get programs to automatically start whenever i log into ubuntu :( 

is there some kind of initiation script i could edit or something? i dont particularly want to add more tools just to mess with what starts up :(

---

### Post by keithb on 2005-11-25
I am new here but under System pull down menu -- Preferences -- Sessions.

The third tab is startup programs.

I have not tried it but that would be where I would start.

---

### Post by RaymondQE on 2005-11-25
That would probably work.  Just make sure you set the order to 50 or above for your start up programs.  This prevents it from running before metacity and other  gnome startup programs.

---

### Post by OmegaOne on 2005-11-25
any idea what an equivelant thing to go to in KDE is?  cant find anything simliar here, and this seems so much nicer than gnome.

edit: found it

home/james/.kde/Autostart

does the same thing as the startup folder in windows

thanks for the help guys ^_^

---

### Post by kwaanens on 2005-11-26
[QUOTE=RaymondQE]That would probably work.  Just make sure you set the order to 50 or above for your start up programs.  This prevents it from running before metacity and other  gnome startup programs.[/QUOTE]

I have NetworkManager installed, and want to start nm-applet when I log in to Gnome. It then connects to my wlan.
The problem right now is that it starts a bit slow, so that I get an error message from gaim-notify because it couldn't connect.
What value should I give nm-applet, so that it starts fast enough, but not too fast, if that's a possibility?

- Ketil

---

### Post by RaymondQE on 2005-11-26
[QUOTE=kwaanens]I have NetworkManager installed, and want to start nm-applet when I log in to Gnome. It then connects to my wlan.
The problem right now is that it starts a bit slow, so that I get an error message from gaim-notify because it couldn't connect.
What value should I give nm-applet, so that it starts fast enough, but not too fast, if that's a possibility?

- Ketil[/QUOTE]

Don't know if this will work, but try setting the order for the nm-applet to 45 and gaim to 60+.  Use a high enough order # to ensure that gaim starts up last.  I'm not sure how low you can set nm-applet, but I'm guessing it needs to be at least 40 or higher since it docks? into the gnome-panel (order=40).

Well, it seems that other users are setting the order to 10-20.  Check out this thread.

[http://www.ubuntuforums.org/showthread.php?t=77726&highlight=nm-applet](http://www.ubuntuforums.org/showthread.php?t=77726&highlight=nm-applet)

---

