---
title: "How do I undo this command?"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by NT4usB on 2006-07-01
Been working on this MythTV install for a month or so... Finally seeing daylight an the end of the tunnel!

Working through this guide (and others):
[http://www.abarbaccia.com/content/view/17/32/](http://www.abarbaccia.com/content/view/17/32/)

I ran the command near the end of the page to auto start mythfrontend:
```
$  echo "mythfrontend" | sudo tee /home/mythtv/.xsession
$  sudo chown mythtv.mythtv /home/mythtv/.xsession
```

How do I stop/edit/skip/, etc mythfrontend from starting so I can work on the install some more?
Soon as I close the front end it kicks me out to the login screen. 
I logged in as another user and commented out the 'mythfrontend' in [mythtv]/home/.Xsession but that jacked everything.

Suggestions?

---

### Post by aysiu on 2006-07-01
Well, you not only added the line ```
mythfrontend
``` to .xsession, but you also changed ownership to the user *mythtv* of the file.

Change that ownership back: ```
sudo chown nt4usb:nt4usb /home/mythtv/.xsession
```

---

### Post by NT4usB on 2006-07-01
Thanks for the reply. I understand what the commands did. 
I know how to change ownership. 
I don't know how to remove *mythfrontend* from the .Xsession.

[QUOTE=aysiu]Well, you not only added the line ```
mythfrontend
``` to .xsession, [/QUOTE]

How do I remove *mythfrontend* from .xsession so it doesn't launch when I log in as mythtv?

[QUOTE=aysiu]but you also changed ownership to the user *mythtv* of the file. Change that ownership back: ```
sudo chown nt4usb:nt4usb /home/mythtv/.xsession
```[/QUOTE]Does changing the ownership back to the default user stop the application from running?

---

### Post by scxtt on 2006-07-01
> echo "mythfrontend" | sudo tee /home/mythtv/.xsessionall this does is "tack on" *mythfrontend* to the end of /home/mythtv/.xsession ... so if you want to remove it, fire up vi and do a double-d on that line, then save the file ...
[indent]$:> sudo vi /home/mythtv/.xsession

hit the down arrow til you get to the 'mythfrontend' line
hit d twice, somewhat quickly
type ":wq" (no quotes)[/indent]

FWIW, "sudo chown mythtv[color=red][size=5].[/size][/color]mythtv /home/mythtv/.xsession" is wrong ... it should be "sudo chown mythtv[color=red][size=5]:[/size][/color]mythtv /home/mythtv/.xsession" ...

---

### Post by NT4usB on 2006-07-01
Thanks for the reply.
I was able to get back into mythtv user by choosing 'Gnome' at login instead of default. Now I can hunt down and change the way .Xsession starts...
I'm going to try to get it to launch on DISPLAY=:"0.1" that way I'll still have a screen to work on.

Anyway, I'm probably going to have to flatline the box and start over again. I screwed up formatting the drive and used up all the primary partitions so I have ~200GB unavailable... oops!

[QUOTE=scxtt]all this does is "tack on" *mythfrontend* to the end of /home/mythtv/.xsession ... so if you want to remove it, fire up vi and do a double-d on that line, then save the file ...
[indent]$:> sudo vi /home/mythtv/.xsession

hit the down arrow til you get to the 'mythfrontend' line
hit d twice, somewhat quickly
type ":wq" (no quotes)[/indent]
[/quote]
I did edit .Xsession but I only commented out (#) the line. When I rebooted it threw some errors at me so I didn't continue. I'm so close to getting mythtv going I didn't want to blow it all up and start over...
btw, *mythfrontend* is the only line in .Xsession.
[QUOTE=scxtt]FWIW, "sudo chown mythtv[color=red][size=5].[/size][/color]mythtv /home/mythtv/.xsession" is wrong ... it should be "sudo chown mythtv[color=red][size=5]:[/size][/color]mythtv /home/mythtv/.xsession" ...[/QUOTE]
I saw that too but it worked (mythfrontend launched) so I ignored it.
I'm doing a lot of copy/paste trying to get this going... learning along the way a little bit about Linux.

---

