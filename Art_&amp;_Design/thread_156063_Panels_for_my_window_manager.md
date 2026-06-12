---
title: "Panels for my window manager?"
date: 2006-04-06
forum: Art &amp; Design
---

### Post by ecto on 2006-04-06
Hello everybody :) . I was just wondering if anyone would like to suggest a nice looking panel I could use for my window manager... Perhaps something that looks more like this : [http://desintegr.free.fr/image.php?fichier=fvwm/fvwm20040426.jpg]("http://desintegr.free.fr/image.php?fichier=fvwm/fvwm20040426.jpg")
Perhaps you could tell me what kind of panel he or she is using :D? 
Ive tried to google for one but alli get is pypanel and fbpanel. Any help is appreciated thank you!

---

### Post by AdotB on 2006-04-06
Looks like they're using fvwm. You could install fvwm (which should install the panel), log into it and find out what the panel is called. Then try opening it in your window manager.

---

### Post by ecto on 2006-04-06
Yeh sorry i forgot to mention i am using fvwm... The Panel they provide is not the same as that one (or not to my knowledge at least). But thank you for the reply.

---

### Post by plb on 2006-04-06
That panel is part of FVWM. Look around on that site...that guys fvwm config should be on it.

---

### Post by super on 2006-04-06
[QUOTE=plb]That panel is part of FVWM. Look around on that site...that guys fvwm config should be on it.[/QUOTE]
plb is right. that dock is just a fvwmbutton function. here are the relevant parts from the config.

to execute the fvwm module and name it you need this line in your ~/.fvwm2rc:
```
+ I Module FvwmButtons -g 70x570-0+170 FvwmDock 
```

and to configure your new fvwmdock you also need this in your ~/.fvwm2rc:
```
###################################################################
### Dock
###################################################################
Style FvwmDock     Sticky, NoTitle, NoHandles, Borderwidth 0

DestroyModuleConfig FvwmDock: *
*FvwmDock: Rows 10
*FvwmDock: Columns 1
*FvwmDock: Frame 0
*FvwmDock: Colorset 30
*FvwmDock: (1x1, Icon dock/globes/home.png, ActionOnPress, Action(Mouse 1) `DockLaunch "nautilus --no-desktop" nautilus $left $top`, Action(Mouse 3) `Next (nautilus) Popup MenuFvwmWindowOps Rectangle +$left+$top -100m 0`, HoverIcon dock/globes/home_hover.png)
*FvwmDock: (1x1, Icon dock/globes/firefox.png, ActionOnPress, Action(Mouse 1) `DockLaunch firefox Firefox-bin $left $top`, Action(Mouse 3) `Next (Firefox-bin) Popup MenuFvwmWindowOps Rectangle +$left+$top -100m 0`, HoverIcon dock/globes/firefox_hover.png)
*FvwmDock: (1x1, Icon dock/globes/xmms.png, ActionOnPress, Action(Mouse 1) `DockLaunch xmms $left $top`, Action(Mouse 3) `Menu MenuMultimedia Rectangle +$left+$top -100m 0`, HoverIcon dock/globes/xmms_hover.png)
*FvwmDock: (1x1, Icon dock/globes/mail.png, ActionOnPress, Action(Mouse 1) `DockLaunch thunderbird Thunderbird-bin $left $top`, Action(Mouse 3) `Next (Thunderbird-bin) Popup MenuFvwmWindowOps Rectangle +$left+$top -100m 0`, HoverIcon dock/globes/mail_hover.png)
*FvwmDock: (1x1, Icon dock/globes/gimp.png, ActionOnPress, Action(Mouse 1) `DockLaunch gimp-2.0 gimp-2.0 $left $top`, Action(Mouse 3) `Next (gimp-2.0) Popup MenuFvwmWindowOps Rectangle +$left+$top -100m 0`, HoverIcon dock/globes/gimp_hover.png)
*FvwmDock: (1x1, Icon dock/globes/edit.png, ActionOnPress, Action(Mouse 1) `DockLaunch gvim gvim $left $top`, Action(Mouse 3) `Next (gvim) Popup MenuFvwmWindowOps Rectangle +$left+$top -100m 0`, HoverIcon dock/globes/edit_hover.png)
#*FvwmDock: (1x1, Icon dock/bluefish.png, ActionOnPress, Action(Mouse 1) `DockLaunch bluefish bluefish $left $top`, Action(Mouse 3) `Next (bluefish) Popup MenuFvwmWindowOps Rectangle +$left+$top -100m `)
#*FvwmDock: (1x1, Icon dock/ooo.png, ActionOnPress, Action(Mouse 1) `DockLaunch xooffice xooffice $left $top`, Action(Mouse 3) `Next (xooffice) Popup MenuFvwmWindowOps Rectangle +$left+$top -100m 0`)
*FvwmDock: (1x1, Icon dock/globes/console.png, ActionOnPress, Action(Mouse 1) `Exec gnome-terminal`, HoverIcon dock/globes/console_hover.png)
*FvwmDock: (1x1, Icon dock/globes/system.png, ActionOnPress, Action(Mouse 1) `Exec gvim -geom 115x46 ~/.fvwm/.fvwm2rc`, HoverIcon dock/globes/system_hover.png)

DestroyFunc DockLaunch
AddToFunc DockLaunch
+ C Any ($1) Next ($1) WindowListFunc
+ C TestRc (NoMatch) Exec $0
+ H Any ($1) WindowList ($1) Rectangle +$2+$3 0 -100m CurrentAtEnd UseListSkip SortByClass NoCurrentDeskTitle
+ D Exec $0
```

of course you actually need to have those icons, but i believe they are available in the config package on the site where you found that screenshot.

happy configuring! :p

---

### Post by n0dl on 2006-04-06
you should also look into the fvwm man pages:D

---

