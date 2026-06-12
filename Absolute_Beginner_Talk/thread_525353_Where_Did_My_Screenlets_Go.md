---
title: "Where Did My Screenlets Go?"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by lepz on 2007-08-14
I updated this morning and most of my screenlets have disappeared, anyone know anything?

---

### Post by Inxsible on 2007-08-14
Do you have compiz fusion running with the widget plugin on ?

if yes, simply press F9 to see your screenlets or disable the widget plugin if you want the screenlets to show all the time.

---

### Post by lepz on 2007-08-14
Sorry I should have explained better, the screenlets that I did have like calendar and weather are now no longer available to me since I downloaded, in fact very few are available.

---

### Post by LastHylian on 2007-08-14
Me too. It's really annoying. When I try to run screenletsd start I get :

Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
/usr/local/bin/screenletsd: line 99: syntax error near unexpected token `('
/usr/local/bin/screenletsd: line 99: `          echo " 'add <name>' : add a Screenlet (e.g. 'add Clock')"'

I saw a forum topic for it on the compiz fusion website by googling it, but it says it has been shut down. Any thoughts?

---

### Post by djxcon on 2007-08-14
Just updated to 0.0.9 and that definitely broke screenlets.  I am getting the same error as LastHylian when running screenletsd from a terminal.  When running screenlets from the Applications --> Accessories menu, I get "Failed to execute child process screenlets-tray" No Such File or Directory.

:mad:

---

### Post by Izobalax on 2007-08-14
Same here. Updated and now my "Now Playing" screenlet has disappeared. Screenlets has also disappeared from my notification area.
I am woe.

/izo

---

### Post by djxcon on 2007-08-14
OK I retract my last statement now that I have read the following from this link: [http://forum.compiz-fusion.org/showthread.php?t=323]("http://forum.compiz-fusion.org/showthread.php?t=323")

> NOTE: screenletsd is NOT used anymore. Please start each screenlet individually now 

This is a bit of a change and now starting your screenlets one by one seems to work fine.  Just double click on your .py files and click Run.

---

### Post by Izobalax on 2007-08-14
> **djxcon said:**
> OK I retract my last statement now that I have read the following from this link: [http://forum.compiz-fusion.org/showthread.php?t=323]("http://forum.compiz-fusion.org/showthread.php?t=323")


This is a bit of a change and now starting your screenlets one by one seems to work fine.  Just double click on your .py files and click Run.
I see. However, I still have a problem. 
I've located the "Now Playing" .py file in /usr/local/share/screenlets, however when I ask to install it, screenlets tells that I *have* installed it, but it's not there!
Any ideas?

/izo

---

### Post by djxcon on 2007-08-14
Try running the ControlScreenlet in /usr/local/share/screenlets/Control first.  Once this screenlet loads, right click on it, choose screenlets -> Add -> NowPlaying. 

You could also use alacarte to edit your Applications menu item for Screenlets and change the command from screenlet-tray to /usr/local/share/screenlets/Control/ControlScreenlet.py

---

### Post by Izobalax on 2007-08-15
> **djxcon said:**
> Try running the ControlScreenlet in /usr/local/share/screenlets/Control first.  Once this screenlet loads, right click on it, choose screenlets -> Add -> NowPlaying. 

You could also use alacarte to edit your Applications menu item for Screenlets and change the command from screenlet-tray to /usr/local/share/screenlets/Control/ControlScreenlet.py
Yep, your first suggestion worked. Thanks man!

/izo

---

### Post by cnr437 on 2007-08-17
> **LastHylian said:**
> Me too. It's really annoying. When I try to run screenletsd start I get :

Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
/usr/local/bin/screenletsd: line 99: syntax error near unexpected token `('
/usr/local/bin/screenletsd: line 99: `          echo " 'add <name>' : add a Screenlet (e.g. 'add Clock')"'

I saw a forum topic for it on the compiz fusion website by googling it, but it says it has been shut down. Any thoughts?

Here there is fix of your problem, enter this command.

```
sudo gedit /usr/local/share/screenletsd
```

find 96th line and add double quote as like this,

```
 " 
```

end of the 96th line.

---

### Post by Inxsible on 2007-08-17
> **djxcon said:**
> Try running the ControlScreenlet in /usr/local/share/screenlets/Control first.  Once this screenlet loads, right click on it, choose screenlets -> Add -> NowPlaying. 

You could also use alacarte to edit your Applications menu item for Screenlets and change the command from screenlet-tray to /usr/local/share/screenlets/Control/ControlScreenlet.py

Do the screenlets come up on every reboot, or do we have to open the control screenlet and add all the screenlets everytime ?

---

### Post by Izobalax on 2007-08-17
> **Inxsible said:**
> Do the screenlets come up on every reboot, or do we have to open the control screenlet and add all the screenlets everytime ?
I can't get Screenlets to remember my settings either, which is now ANNOYING.

/izo

---

